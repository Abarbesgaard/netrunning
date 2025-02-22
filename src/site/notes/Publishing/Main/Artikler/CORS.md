---
{"dg-publish":true,"permalink":"/publishing/main/artikler/cors/","title":"CORS","tags":["Teknologi","Programmering"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-08-11T08:37:19.809+02:00"}
---

Se hvad jeg ellers har skrevet [[Publishing/Main/Artikler/Artikler jeg har skrevet\|her]]
- ![Cors](https://cskarp2.wordpress.com/wp-content/uploads/2024/04/cors-1.png?w=1024)

## [CORS i… Dybden](https://cskarp2.wordpress.com/2024/04/09/cors-i-dybden/)

Dette opslag vil lave en mere dybdegående forklaring om hvad **CORS** er og
hvordan det bruges i en ASP.NET Core app.

## Hvad er CORS?

**CORS** er et akronym, som står for:

**C** ross

**O** rigin

**R** equest

**S** haring

Browser sikkerhed forhindrer en web side i at foretage anmodninger til et andet
domæne end den, der tjente web siden. Denne begrænsning kaldes **same-origin-policy**.

## Problem

![Cors2](https://cskarp2.wordpress.com/wp-content/uploads/2024/04/cors2.png?w=1024)

Du har udviklet en webapplikation, der består af to separate frontend-komponenter,
hvor hver kører på sit eget domæne – `https://frontend1.com` og `https://frontend2.com.`

Derudover er der en backend, som kører på domænet `https://backend.com`.
Begge frontend-komponenter skal kommunikere med backenden for at hente data via HTTP-anmodninger.

Men når **frontend**-komponenterne forsøger at foretage anmodninger til
**backenden**, modtager de en **CORS**-fejl, fordi standardbrowsere implementerer
en same-origin-politik, der forhindrer anmodninger fra at blive sendt til andre
domæner end det, hvor frontendkoden blev indlæst.

## Løsning

Du kan konfigurere din backend-server til at tillade anmodninger fra både
`https://frontend1.com` og `https://frontend2.com`-domænerne ved hjælp
af **CORS**.

Dette indebærer typisk at tilføje **CORS-headers** til svar fra backend-serveren.

Ved at gøre dette kan begge **frontend**-komponenter sende anmodninger til
**backenden**, og browseren vil ikke længere blokere dem på grund af
same-origin-policy.

**Same-origin-policy** forhindrer en ondsindet side i at læse følsomme data
fra en anden side. Nogle gange kan du ønske at tillade andre sider at
foretage Cross-Origin anmodninger til din app.

## Definitioner før vi går videre

### Same-Origin

Same-Origin er defineret ved:

> At URL’er har samme oprindelse, hvis de har identiske _schemes_, _Hosts_ og _Ports_.

Følgende hjemmesider har samme Origin:

```bash
https://example.com/foo.html
https://example.com/bar.html
```

Følgende hjemmesider har ikke samme origin:

```bash
https://example.net: Andet domæne
https://www.example.com/foo.html: Andet subdomæne
http://example.com/foo.html: Andet scheme
https://example.com:9000/foo.html: Andet port
```

## Hvorfor bruge CORS?

**CORS** er vigtigt, fordi det giver browsere mulighed for at håndhæve
`same-origin-policy`. Denne policy er en sikkerhedsforanstaltning, der
forhindrer et ondsindet script i at få adgang til ressourcer, som det
ikke burde have adgang til.

Uden CORS kunne et ondsindet script foretage en anmodning til en server
på et andet domæne og få adgang til ressourcer, som brugeren af siden
ikke er meningen skulle have adgang til.

## Sådan aktiverer du CORS

Der er **tre** måder at aktivere **CORS**:

- Ved brug af _middleware_ med enten en named-policy eller en default-policy.
- Ved hjælp af endpoint routing..
- Med [EnableCors]-attributten.

Brugen af **[EnableCors]**-attributten med en named-policy giver den bedste
kontrol med at begrænse endpoints, der understøtter CORS.

> **UseCors** skal kaldes i den korrekte rækkefølge. For eksempel skal
**UseCors** kaldes før **UseResponseCaching**, når du bruger
**UseResponseCaching**.

## CORS med named policy og middleware

CORS-middleware håndterer cross-origin-anmodninger. Følgende kode
anvender en CORS-politik på alle appens endpoints med de angivne
oprindelser:

```c#
var  MyAllowSpecificOrigins = "_myAllowSpecificOrigins";

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddCors(options =>
{
    options.AddPolicy(name: MyAllowSpecificOrigins,
                      policy  =>
                      {
                          policy.WithOrigins("<http://example.com>",
                                              "<http://www.contoso.com>");
                      });
});

// services.AddResponseCaching();

builder.Services.AddControllers();

var app = builder.Build();
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();

app.UseCors(MyAllowSpecificOrigins);

app.UseAuthorization();

app.MapControllers();

app.Run();
```

koden ovenfor:

- Sætter policy-name til \__myAllowSpecificOrigins_. Politikkens navn er arbitrært.
- Kalder **UseCors**-udvidelsesmetoden og specificerer \__myAllowSpecificOrigins_
**CORS**-politikken. UseCors tilføjer CORS-middleware. _Kaldet til **UseCors**
skal placeres efter **UseRouting**, men før **UseAuthorization**_.
- Kalder **AddCors** med et lambda-udtryk. Lambdaen tager et **CorsPolicyBuilder**-objekt.
Konfigurationsmuligheder, såsom WithOrigins, beskrives senere i denne artikel.
- Aktiverer \_myAllowSpecificOrigins CORS-politikken for alle controller-slutpunkter.
Se slutpunktrouting for at anvende en CORS-politik på specifikke slutpunkter.
- Når du bruger Response Caching Middleware, skal du kalde UseCors før UseResponseCaching.

Med slutpunktsrouting skal CORS-middlewaren konfigureres til at eksekvere
mellem opkaldene til UseRouting og UseEndpoints.

Se Test CORS for instruktioner om at teste kode lignende den foranstående kode.

Opkaldet til AddCors-metoden tilføjer CORS-tjenester til appens tjenestecontainer.

Hvis du vil lære mere om CORS vil jeg anbefale
[denne](https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-8.0#dp)
fra Microsoft’s dokumentation. Jeg har brugt kode eksemplet i mit opslag, men
der er
meget mere at finde.

## Litteratur brugt til ovenstående

[https://aws.amazon.com/what-is/cross-origin-resource-sharing/](https://aws.amazon.com/what-is/cross-origin-resource-sharing/)

[https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-8.0#dp](https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-8.0#dp)
[https://hackernoon.com/understanding-cors-why-its-important-and-how-it-works](https://hackernoon.com/understanding-cors-why-its-important-and-how-it-works)

## Andre artikler med samme emne
| File | Title | Tags |
| ---- | ----- | ---- |

{ .block-language-dataview}
