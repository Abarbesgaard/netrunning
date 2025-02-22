---
{"dg-publish":true,"permalink":"/publishing/main/noter/vita/server-side-request-forgery/","created":"2024-11-11T08:46:27.958+01:00"}
---

![Server Side Request Forgery.png](/img/user/Resource/98_Images/Server%20Side%20Request%20Forgery.png)
> [!NOTE]- Opsummering af SSRF
> **Server-side request forgery** (SSRF)-sårbarheder kan opstå, når en **API** henter en ekstern ressource uden at *validere den URI*, som brugeren har angivet. Dette gør det muligt for en angriber at tvinge applikationen til at sende en tilpasset forespørgsel til en uventet destination, *selv hvis systemet er beskyttet af en firewall eller en VPN*.


For at løse sårbarheder med **Server Side Request Forgery** kan man:
1. Implementér og brug en allow-liste
2. Brug en sikker URL-parser og valider input
3. Isoler ressourcehentningsmekanismer
4. Deaktiver HTTP-omdirigeringer og begræns responsvisning

## Implementér og brug en Allow-liste
For at undgå SSRF-angreb kan en allow-liste begrænse de eksterne URI'er, API'en har lov til at anmode om.
```csharp
public static readonly List<string> AllowedHosts = new List<string>
{
    "https://example.com",
    "https://trusted-resource.com",
    "https://api.partner-service.com"
};

public static bool IsUrlAllowed(string url)
{
    Uri uri;
    return Uri.TryCreate(url, UriKind.Absolute, out uri) && AllowedHosts.Contains(uri.GetLeftPart(UriPartial.Authority));
}

// Anvender allow-listen
public async Task FetchResource(string url)
{
    if (!IsUrlAllowed(url))
        throw new UnauthorizedAccessException("URL not allowed.");

    using var client = new HttpClient();
    var response = await client.GetAsync(url);
    // Håndter response...
}
```
#### Anvendelse i en microservice-arkitektur  
Allow-liste-implementeringen bruges i *services, hvor microservicen henter data fra eksterne kilder*, fx ved integration med eksterne API'er, så kun tilladte domæner kan bruges som ressourcer.
## Brug en Sikker URL-parser og Valider Input
Ved at bruge en sikker URL-parser kan man validere og undgå fejl i URL-strukturering, som SSRF-angreb ofte udnytter.
```csharp
public static Uri ParseAndValidateUrl(string url)
{
    if (!Uri.TryCreate(url, UriKind.Absolute, out Uri uri))
        throw new ArgumentException("Invalid URL format.");

    if (uri.Scheme != Uri.UriSchemeHttps)
        throw new UnauthorizedAccessException("Only HTTPS is allowed.");

    return uri;
}

// Brug URL-parseren
public async Task FetchResourceSafely(string url)
{
    var validatedUri = ParseAndValidateUrl(url);
    using var client = new HttpClient();
    var response = await client.GetAsync(validatedUri);
    // Håndter response...
}
```
#### Anvendelse i en microservice-arkitektur  
Denne metode er nyttig i **API-gateways** og *services, der modtager brugerdefinerede URI'er*, især når der skal hentes ressourcer på brugerspecificerede steder, fx webhook-implementeringer.

## Isoler Ressourcehentningsmekanismer

Isolering af ressourcehentning kan sikre, at en service kun har adgang til eksterne ressourcer og ikke interne ressourcer som f.eks. databaser eller interne netværk.
```csharp
public class ResourceFetcher
{
    private readonly HttpClient _client;

    public ResourceFetcher(HttpClient client)
    {
        _client = client;
        _client.DefaultRequestHeaders.Add("Host", "example.com"); // Angiver kun specifikt domæne
    }

    public async Task<string> FetchExternalResource(Uri uri)
    {
        if (IsInternalUri(uri))
            throw new UnauthorizedAccessException("Access to internal resources is not allowed.");

        var response = await _client.GetAsync(uri);
        return await response.Content.ReadAsStringAsync();
    }

    private bool IsInternalUri(Uri uri)
    {
        // Tjek for interne IP-ranges, fx 10.x.x.x, 192.168.x.x
        return uri.IsLoopback || uri.Host.StartsWith("10.") || uri.Host.StartsWith("192.168");
    }
}
```

#### Anvendelse i en microservice-arkitektur
Denne teknik er *velegnet i microservices, der kommunikerer med tredjepartstjenester*, fx en filhentningsservice, som skal være begrænset til at kontakte eksterne ressourcer og ikke få adgang til lokale netværksadresser.