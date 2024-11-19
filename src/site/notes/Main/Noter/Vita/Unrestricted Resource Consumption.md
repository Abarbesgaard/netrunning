---
{"dg-publish":true,"permalink":"/main/noter/vita/unrestricted-resource-consumption/","created":"2024-11-07T09:05:13.214+01:00"}
---

![Unrestricted Resource Consumption.png](/img/user/Unrestricted%20Resource%20Consumption.png)
> [!NOTE]- Opsummering af URC
> At imødekomme API-anmodninger kræver ressourcer som **netværksbåndbredde**, **CPU**, **hukommelse** og **lagerplads**. Andre ressourcer, såsom e-mails/SMS/telefonsamtaler eller biometrisk validering, stilles til rådighed af tjenesteudbydere via API-integrationer og betales per anmodning. *Lykkedes et angreb, kan det føre til service-nedbrud eller øgede driftsomkostninger*.

For at løse sårbarheder med **Unrestricted Resource Consumption** kan man:
1. Resource Management og Rate Limiting
2. Ressource- og Memory-begrænsninger på hver Mikroservice
3. Validering og Begrænsning af API Anmodninger
4. Omkostnings- og Forbrugsstyring

## Resource Management og Rate Limiting
*Resource management* og *rate limiting* er afgørende for at beskytte mikroservices mod angreb og overforbrug. Ved at bruge en **API Gateway** kan man centralisere styringen af begrænsninger, så hver mikroservice ikke skal håndtere disse individuelt. **API Gatewayen** kan kontrollere, hvor mange anmodninger en enkelt bruger kan sende inden for en tidsramme, og hvor meget data der må returneres i et enkelt svar.

Eksemplet viser en opsætning af rate limiting med [YARP](https://microsoft.github.io/reverse-proxy/) i en **API Gateway.** Her begrænses antal kald pr. minut pr. IP-adresse til en given endpoint.
```json
{
  "Routes": [
    {
      "RouteId": "profileRoute",
      "ClusterId": "profileService",
      "Match": {
        "Path": "/api/profile/{**catch-all}"
      },
      "Transforms": [
        {
          "RateLimiting": {
            "Window": "1m",
            "MaxRequests": 100,
            "ClientKey": "{RemoteIpAddress}"
          }
        }
      ]
    }
  ],
  "Clusters": {
    "profileService": {
      "Destinations": {
        "profileDestination": {
          "Address": "https://profileservice.example.com/"
        }
      }
    }
  }
}
```

#### Hvor bruges dette i en microservice?

**Resource management** og **rate limiting** er afgørende i **API Gatewayen** i en mikroservice-arkitektur, hvor de fungerer som et forsvar mod *uautoriseret* eller overdreven brug af API’er. Det beskytter backend-mikroservices mod overbelastning og gør det muligt at kontrollere ressourcetræk centralt.

## Ressource- og Memory-begrænsninger på hver Mikroservice
Ved at sætte **ressourcebegrænsninger** på mikroservices kan man undgå, at et uheldigt servicekald eller en anmodningsstorm tømmer *CPU* og *hukommelse*. Når mikroservices køres i containere eller en Kubernetes-klynge, kan man begrænse CPU, hukommelse, netværk og andre ressourcer for hver tjeneste. 
Dette giver en ekstra beskyttelse mod Denial of Service (DoS)-angreb.

> [!IMPORTANT] Unden for mit fagområde
Dette er uden for mit enme da der er tale om kubernetes og orkestartion af services.
#### Hvor bruges dette i en microservice?

Ressource- og memory-begrænsninger er især nyttige i *Kubernetes* og *Docker-miljøer*, hvor man kan opsætte begrænsninger på hver enkelt mikroservice. Det giver en sikkerhed for, at hver tjeneste kun bruger de nødvendige ressourcer og ikke risikerer at overbelaste hele systemet.

## Validering og Begrænsning af API Anmodninger
At **validere** og **begrænse** API-anmodningerne er afgørende for at sikre, at API'en kun behandler legitime data. Ved at indføre parametre som maksimalt antal dataelementer i arrays, begrænsninger på *uploadstørrelse*, og *paginering* kan API'er undgå at returnere for store datasæt, som kan føre til *ydeevneproblemer*.

Eksemplet viser en C#-controller, der **validerer** en anmodning *ved at begrænse array-længden og sætte en grænse for sideantal og maksimum resultater pr. side.*
```csharp
[HttpGet]
public IActionResult GetProducts([FromQuery] int page = 1, [FromQuery] int pageSize = 10)
{
    const int MaxPageSize = 50;

    if (pageSize > MaxPageSize)
    {
        return BadRequest($"Page size cannot exceed {MaxPageSize}");
    }

    var products = _productService.GetProducts(page, pageSize);
    return Ok(products);
}
```

#### Hvor bruges dette i en microservice?
**Validering** og **begrænsning** af API-anmodninger bruges ofte *i de enkelte mikroservices*, der håndterer dataanmodninger. Ved at indføre *validering* kan services forhindre klienter i at anmode om for mange data på én gang, hvilket beskytter både performance og ressourcer.

## Omkostnings- og Forbrugsstyring
**Omkostnings**- og **forbrugsstyring** er afgørende, når mikroservices integrerer med tredjeparts-tjenester, som typisk har *omkostninger pr. anmodning* (f.eks. SMS-verifikation eller cloud storage). For at forhindre eskalerende omkostninger kan man konfigurere alarmer og grænser for brug af tredjeparts-tjenester, så der hurtigt kan reageres på uventet forbrug.

Eksemplet viser en simpel monitor, der tjekker og sender en advarsel, hvis omkostningerne overstiger en vis grænse. Denne monitor kan integreres som en mikroservice, der periodisk tjekker omkostninger via et API-kald.
```csharp
public class CostMonitor
{
    private readonly IThirdPartyBillingService _billingService;

    public CostMonitor(IThirdPartyBillingService billingService)
    {
        _billingService = billingService;
    }

    public async Task CheckCosts()
    {
        var currentCost = await _billingService.GetCurrentCost();
        const decimal MaxAllowedCost = 1000m;

        if (currentCost > MaxAllowedCost)
        {
            // Send alert
            Console.WriteLine("Warning: Monthly spending limit exceeded!");
        }
    }
}
```

#### Hvor bruges dette i en microservice?
**Omkostnings**- og **forbrugsstyring** er vigtigt i mikroservices, der bruger *eksterne API’er* eller tredjeparts-tjenester. Her er det muligt at overvåge og styre forbrug via dedikerede cost-monitoring services, som kan advare om uventede omkostninger og forhindre økonomisk overbelastning af systemet.