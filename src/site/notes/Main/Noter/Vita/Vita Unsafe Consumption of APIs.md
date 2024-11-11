---
{"dg-publish":true,"permalink":"/main/noter/vita/vita-unsafe-consumption-of-ap-is/","created":"2024-11-11T09:23:09.866+01:00"}
---

![Unsafe Consumption of APIs.png](/img/user/Unsafe%20Consumption%20of%20APIs.png)
> [!Note]- Opsummering af UCoA
> Udviklere har en *tendens til at stole mere på data modtaget fra tredjeparts-API'er end på brugerinput*, og derfor anvender de ofte svagere sikkerhedsstandarder. For at kompromittere API'er går angribere efter integrerede tredjepartstjenester i stedet for at forsøge at kompromittere selve mål-API'en direkte.

For at løse sårbarheder med **Unsafe Consumption of API's** lan man:
1. Kryptér interaktion med andre [[Main/Noter/API\|API'er]] via en ubeskyttet kanal
2. Validerer og Saniterer Ikke Data Hentet Fra Andre [[Main/Noter/API\|API'er]]
3. Ikke følge omdirigeringer blindt
4. Begræns antallet af ressourcer tilgængelige til behandling af tredjeparts [[Main/Noter/API\|API-svar]]

## Kryptér interaktion med Andre [[Main/Noter/API\|API'er]] via en ubeskyttet kanal

**[[Main/Noter/API\|API'er]] bør altid bruge krypteret kommunikation (TLS/SSL) for at sikre, at følsomme data er beskyttet under transmission**. Ubeskyttede kanaler efterlader data sårbare overfor aflytning og "man-in-the-middle"-angreb.


```csharp

Copy code

// Eksempel på en usikker API-anmodning (ukrypteret HTTP) 
var httpClient = new HttpClient(); 
var response = await httpClient.GetAsync("http://api.thirdparty.com/data"); 
// Usikker, HTTP  
// Sikker API-anmodning ved brug af HTTPS 
var secureHttpClient = new HttpClient(); 
var secureResponse = await secureHttpClient.GetAsync("https://api.thirdparty.com/data"); 
// Sikker, HTTPS
```
#### Hvor Det Bruges i En Microservice Arkitektur
I en microservice arkitektur interagerer hver service muligvis med eksterne [[Main/Noter/API\|API'er]] til databerigelse eller tredjepartstjenester. Ved at sikre, at alle interne servicekommunikation bruger HTTPS, garanteres det, at alle data forbliver sikre under overførsel, hvilket reducerer risikoen for datalæk.

---

## Validerer og Saniterer Ikke Data Hentet Fra Andre API'er

Når data hentes fra eksterne [[Main/Noter/API\|API'er]], er det nødvendigt at **validere** og **sanitere** dataene, før de bruges, for at forhindre angreb som SQL-injektion, XSS eller andre former for ondsindet datamanipulation.

```csharp

// Eksempel på ikke-valideret input fra et tredjeparts API 
var unsafeData = await GetDataFromApi("https://thirdparty.com");  
// Farlig operation med usanitiseret input 
var query = $"SELECT * FROM users WHERE username = '{unsafeData}'";  
// Risiko for SQL-injektion  
// Korrekt validering og sanitering 
if (IsValid(unsafeData))  
{     
	var sanitizedData = SanitizeInput(unsafeData);     
	var query = $"SELECT * FROM users WHERE username = '{sanitizedData}'";  
	// Sikker 
}
```

#### Hvor Det Bruges i En Microservice Arkitektur
**I microservices interagerer tjenester ofte med flere tredjeparts [[Main/Noter/API\|API'er]] for at hente data**. Tjenesten, der forbruger disse data, skal validere og sanitere input, før de sendes videre til nedstrømskomponenter som databaser eller andre tjenester for at forhindre sikkerhedssårbarheder.

---

## Ikke følge omdirigeringer blindt

At følge omdirigeringer blindt kan føre til, at følsomme data bliver eksponeret for ondsindede tredjepartstjenester, hvis mål-[[Main/Noter/API\|API'ens]] omdirigeringer er kompromitteret. Det er vigtigt at begrænse de domæner og URL'er, som omdirigeringer kan pege på.


```csharp

Copy code

// Usikker håndtering af omdirigeringer 
var client = new HttpClient(); 
var response = await client.GetAsync("https://trustedservice.com"); 
var redirectUrl = response.Headers.Location; 
var redirectedResponse = await client.GetAsync(redirectUrl);  
// Potentielt usikker  
// Sikker håndtering af omdirigeringer med validering 
var allowedRedirects = new List<string> { "https://trustedservice.com", "https://anothertrustedservice.com" }; 
if (allowedRedirects.Contains(response.Headers.Location.ToString())) 
{     
	var redirectedResponse = await client.GetAsync(redirectUrl);  
	// Sikker, tilladt omdirigering 
	} 
	else 
	{     
		throw new InvalidOperationException("Omdirigerings-URL er ikke tilladt"); 
	}
```
#### Hvor Det Bruges i En Microservice Arkitektur
Microservices, der interagerer med tredjeparts [[Main/Noter/API\|API'er]], kan modtage svar, der involverer omdirigering. Det er kritisk at sikre, at omdirigeringerne peger på betroede domæner for at forhindre, at følsomme data sendes til ondsindede servere.

---

## Begræns Antallet af Ressourcer Tilgængelige til Behandling af Tredjeparts [[Main/Noter/API\|API-svar]]

Ved at begrænse antallet af ressourcer, der er tilgængelige til at behandle svar fra tredjeparts [[Main/Noter/API\|API'er]], kan man forhindre angreb som DoS (Denial of Service) eller udnyttelse af systemressourcer.

```csharp
// Usikker håndtering af API-svar 
var response = await httpClient.GetAsync("https://thirdparty.com/large-response"); 
var data = await response.Content.ReadAsStringAsync();  
// Potentielt stor data  
// Sikker håndtering ved at begrænse ressourcer 
var maxResponseSize = 1024;  
var data = await ReadWithLimit(response.Content, maxResponseSize);  
async Task<string> ReadWithLimit(HttpContent content, int maxSize) 
{     
	using (var stream = await content.ReadAsStreamAsync())     
	{         
		var buffer = new byte[maxSize];         
		var bytesRead = await stream.ReadAsync(buffer, 0, maxSize);  
		return Encoding.UTF8.GetString(buffer, 0, bytesRead);     
	} 
}
```
#### Hvor Det Bruges i En Microservice Arkitektur
**Når en microservice forbruger et tredjeparts [[Main/Noter/API\|API]], kan svaret være stort.** Det er vigtigt at sætte grænser for svarets størrelse for at forhindre overdreven brug af systemressourcer og potentielle DoS-angreb.