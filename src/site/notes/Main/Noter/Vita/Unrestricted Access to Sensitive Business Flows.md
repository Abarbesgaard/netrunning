---
{"dg-publish":true,"permalink":"/main/noter/vita/unrestricted-access-to-sensitive-business-flows/","created":"2024-11-07T09:31:30.120+01:00"}
---

![Unrestricted Access to Sensitive Business Flows.png](/img/user/Unrestricted%20Access%20to%20Sensitive%20Business%20Flows.png)
> [!NOTE]- Opsummering af UASBF
> APIs, der er sårbare over for denne risiko, eksponerer en forretningsproces – såsom at købe en billet eller poste en kommentar – uden at tage højde for, hvordan funktionaliteten kan skade virksomheden, hvis den bruges i overdreven grad på en automatiseret måde. Dette skyldes ikke nødvendigvis implementeringsfejl.

For at løse sårbarheder med Unrestricted Access to Sentitive Business Flows kan man:
1. Rate Limiting med IP-baserede grænser
2. Captcha-validering på kritiske handlinger
3. Brugerens Anmodningskvoter med Rate Limiting baseret på Bruger-ID
4. Implementering af en "Circuit Breaker" for Forretningskritiske Tjenester

## Rate Limiting med IP-baserede grænser
**Rate limiting** er en teknik til at begrænse antallet af *API-anmodninger* fra en klient over et bestemt tidsinterval. 
Dette er særligt nyttigt til at forhindre overdreven brug eller misbrug af API'er, der kan påvirke virksomhedens ressourcer negativt. Ved at implementere IP-baserede grænser kan man forhindre, at en enkelt bruger eller en gruppe af brugere automatisk spammer API’en med forretningskritiske handlinger.

```json
{
  "ReverseProxy": {
    "Routes": {
      "route1" : {
        "ClusterId": "cluster1",
        "RateLimiterPolicy": "customPolicy",
        "Match": {
          "Hosts": [ "localhost" ]
        }
      }
    },
    "Clusters": {
      "cluster1": {
        "Destinations": {
          "cluster1/destination1": {
            "Address": "https://localhost:10001/"
          }
        }
      }
    }
  }
}
```
Enstående eksempel er en integration af **Rate Limiting** i [YARP](https://microsoft.github.io/reverse-proxy/articles/rate-limiting.html)
#### Hvor bruges dette i en microservice?

**Rate limiting middleware** som ovenfor kan implementeres i en **API gateway** i microservice-arkitekturen for at beskytte alle services mod overdreven brug fra enkelte IP-adresser. Denne kontrol kan også bruges til at beskytte specifikke endpoints i forretningskritiske tjenester, f.eks. billetbestilling eller køb.

## Captcha-validering på kritiske handlinger

Ved at tilføje en captcha-mekanisme på forretningskritiske handlinger som billetkøb eller kommentarfunktioner kan man reducere risikoen for, at automatiserede scripts misbruger API'en. *Captcha-validering* kræver en manuel handling fra brugeren, hvilket gør det vanskeligere at bruge API'en til automatiserede angreb.

```csharp
app.post('/buy-ticket', async (req, res) => {
    const captchaToken = req.body.captchaToken;

    // Validér captcha
    const isHuman = await verifyCaptcha(captchaToken);
    if (!isHuman) {
        return res.status(400).send('Captcha-validering fejlede');
    }

    // Fortsæt med billetkøb
    processTicketPurchase(req);
    res.send('Billet købt');
});

async function verifyCaptcha(token) {
    // Kalder en ekstern CAPTCHA-tjeneste
    const response = await fetch(`https://captcha-service.com/verify?token=${token}`);
    const data = await response.json();
    return data.success;
}
```
#### Hvor bruges dette i en microservice?

Captcha-validering implementeres *typisk i brugerrelaterede services* i en microservice-arkitektur. For eksempel kan en separat "Ticket Service" kontrollere captcha-validering inden billetkøb for at forhindre automatiseret misbrug.

## Brugerens Anmodningskvoter med Rate Limiting baseret på Bruger-ID

En mere præcis tilgang til **rate limiting** er at indføre kvoter baseret på brugerens identitet frem for IP-adresser. Dette sikrer, at individuelle brugere ikke kan overskride deres tilladte anmodninger, uanset hvilken IP-adresse de bruger. Denne metode er effektiv for API'er, der er tiltænkt autentificerede brugere med adgange til kritiske handlinger.

```csharp
public class UserQuotaService
{
    private readonly Dictionary<string, int> _userQuota = new();

    public bool IsQuotaExceeded(string userId)
    {
        if (!_userQuota.ContainsKey(userId))
        {
            _userQuota[userId] = 1;
            return false;
        }

        _userQuota[userId]++;
        return _userQuota[userId] > 50; // Max 50 anmodninger per bruger pr. time
    }
}

// Brug i controller
if (_userQuotaService.IsQuotaExceeded(userId))
{
    return StatusCode(429, "For mange anmodninger");
}
```

#### Hvor bruges dette i en microservice?

**Bruger-baseret rate limiting** kan implementeres i en *"User Service"* eller *"Authentication Service"*, og integrationen kan distribueres via **API-gatewayen** for at sikre, at brugere ikke overskrider deres kvoter.

## Implementering af en "Circuit Breaker" for Forretningskritiske Tjenester

En "Circuit Breaker" beskytter systemet mod overbelastning ved midlertidigt at afvise nye anmodninger, når API'en eller en bagvedliggende tjeneste er overbelastet. Denne metode reducerer risikoen for fuldstændig nedetid og hjælper med at håndtere anmodninger mere effektivt under perioder med høj belastning.
```csharp
public class CircuitBreaker
{
    private bool _isOpen = false;
    private readonly int _failureThreshold = 10;
    private int _failureCount = 0;

    public async Task<IActionResult> ExecuteAsync(Func<Task<IActionResult>> action)
    {
        if (_isOpen)
        {
            return new StatusCodeResult(StatusCodes.Status503ServiceUnavailable);
        }

        try
        {
            var result = await action();
            _failureCount = 0; // Reset fejl
            return result;
        }
        catch
        {
            _failureCount++;
            if (_failureCount >= _failureThreshold)
            {
                _isOpen = true;
            }
            return new StatusCodeResult(StatusCodes.Status503ServiceUnavailable);
        }
    }
}
```

#### Hvor bruges dette i en microservice?

**Circuit breakers** bruges ofte i **API gateways** eller *forretningskritiske services* for at undgå nedetid og beskytte mod pludselige trafikstigninger, såsom bulk-anmodninger mod et billetkøbssystem. Dette sikrer, at tjenester ikke bliver utilgængelige under høje belastninger, og at en service kan "køle ned", før den genaktiveres.