---
{"dg-publish":true,"permalink":"/main/noter/vita/vita-security-misconfiguration/","created":"2024-11-11T08:56:46.569+01:00"}
---

![Security Misconfiguration.png](/img/user/Security%20Misconfiguration.png)> [!NOTE]- Opsummering af SM
API'er og deres understøttende systemer har ofte komplekse konfigurationer, som gør dem mere tilpasselige. Men disse konfigurationer kan være nemme at overse, og hvis sikkerhedsstandarder ikke følges nøje, kan det føre til sårbarheder. Dette kan åbne op for forskellige typer af angreb, da *fejlkonfigurationer* kan misbruges af ondsindede aktører.

For at løse sårbarheder med **Security Misconfiguration** kan man:
1. Begrænsning af "HTTP-verber" 
2. Implementering af en korrekt CORS-politik
3. Tilføjelse af sikkerhedshoveder og cache-kontrol
4. Validering af indholdstyper og dataformater

## Begrænsning af HTTP-verber

Sikre at kun *de nødvendige HTTP-verber* er tilladt for hver API-endpoint for at minimere potentielle angrebsoverflader. For eksempel bør man undgå unødvendige verb som `TRACE` eller `OPTIONS`, *medmindre de er nødvendige for API’ens funktion*.

**Kodeeksempel:**

```csharp


// ASP.NET Core eksempel - tillader kun GET og POST for en specifik endpoint 
app.MapMethods("/api/data", new[] { "GET", "POST" }, async context => 
{    
	// Your endpoint logic here 
});
```
#### Hvor det bruges i en microservice arkitektur 
Dette bruges typisk i **API-gateways** eller individuelle microservices for at kontrollere, hvilke HTTP-verber der accepteres pr. endpoint, hvilket begrænser mulighederne for ukendte eller uventede anmodninger.

---

## Implementering af en korrekt CORS-politik

En korrekt **CORS**-konfiguration begrænser, hvilke domæner der kan få adgang til API’en, og hvilke HTTP-metoder der er tilladt, for at beskytte mod ondsindet adgang fra uautoriserede domæner.

**Kodeeksempel:**

```csharp
// ASP.NET Core eksempel - indstilling af CORS-politik 
builder.Services.AddCors(options => 
	{     
	options.AddPolicy("AllowSpecificOrigins", policy =>     
		{         
		policy.WithOrigins("https://example.com") 
		        .AllowAnyMethod()               
		        .AllowAnyHeader();     
		}); 
	});  
// Aktivering af CORS-politik 
app.UseCors("AllowSpecificOrigins");
```
#### Hvor det bruges i en microservice arkitektur
Bruges typisk på **API-gatewayen** eller på en *frontend-facing service* for at forhindre uautoriserede ***klienter*** i at interagere med API’en.

---

## Tilføjelse af sikkerhedshoveder og cache-kontrol

Ved at tilføje HTTP-sikkerhedshoveder som `Cache-Control`, `Strict-Transport-Security` og `X-Content-Type-Options` kan man sikre, at API-svarene behandles korrekt og ikke caches på usikre måder.

```csharp
// ASP.NET Core middleware til sikkerhedshoveder 
app.Use(async (context, next) => 
		{     
		context.Response.Headers.Add("Cache-Control", "no-store");  
		context.Response.Headers.Add("Strict-Transport-Security", "max-age=31536000; includeSubDomains");
		context.Response.Headers.Add("X-Content-Type-Options", "nosniff");
		await next(); 
		});
```
#### Hvor det bruges i en microservice arkitektur
Typisk anvendt på **API-gateway niveau** for at sikre, at sikkerhedshoveder anvendes globalt på alle services og beskyttes mod *usikker caching og cross-origin trusler.*

---

## Validering af indholdstyper og dataformater

For at undgå sikkerhedsproblemer, som fx command injection, **er det vigtigt at validere indgående data og tillade kun de indholdstyper,** som API’en faktisk kræver.

```csharp
// ASP.NET Core - begrænsning af indholdstyper 
app.Use(async (context, next) => 
		{     
			if (context.Request.ContentType != "application/json") 
		    {         
			    context.Response.StatusCode = StatusCodes.Status415UnsupportedMediaType;
			    return;     
		    }     
			await next(); 
		});
```

#### Hvor det bruges i en microservice arkitektur
Bruges på **API-gatewayen** eller *direkte på microservices* for at sikre, at kun specificerede dataformater accepteres, hvilket hjælper med at forhindre injektionsangreb og forkerte dataformater.