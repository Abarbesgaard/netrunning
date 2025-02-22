---
{"dg-publish":true,"permalink":"/publishing/main/noter/vita/broken-function-level-authorization/","created":"2024-11-07T09:19:35.648+01:00"}
---

![Broken Function Level Authorization.png](/img/user/Resource/98_Images/Broken%20Function%20Level%20Authorization.png)
> [!NOTE]- Opsummering af BFLA
> **Komplekse adgangskontrolpolitikker** med forskellige *hierarkier*, *grupper* og *roller* samt en uklar adskillelse mellem administrative og almindelige funktioner har en tendens til at føre til autorisationsfejl. Ved at udnytte disse problemer kan angribere få adgang til andre brugeres ressourcer og/eller administrative funktioner.

For at løse sårbarheder med **Broken Funciton Level Authorization**
1. Standardiser og centraliser autorisation med en fælles kontrolmodul
2. Tildel adgang baseret på rolle- og gruppespecifikke tilladelser
3. Brug et abstrakt administrativt controllerlag til administrative funktioner
4. Begræns og gennemgå [[Publishing/Main/Noter/Programmering/API\|API-endepunkter]] mod autorisationsproblemer

## Standardiser og centraliser autorisation med en fælles kontrolmodul
I en microservice-arkitektur er det afgørende at *sikre en standardiseret og central autorisationsmekanisme*, da hver service skal have ensartede sikkerhedsregler for at undgå sårbarheder. Ved at bruge et **fælles autorisationsmodul**, som håndterer adgangskontrol, kan du *sikre ensartede autorisationsregler* på tværs af services og minimere risikoen for utilsigtet adgang.

Her bruger vi en centraliseret `AuthorizationService` til at håndtere autorisationskontrol. Dette modul kan bruges på tværs af services, så alle autorisationskontroller bliver samlet og administreret ét sted.

```csharp
public class AuthorizationService
{
    public bool Authorize(string userRole, string requiredRole)
    {
        return userRole == requiredRole;
    }
}

public class SomeController
{
    private readonly AuthorizationService _authorizationService;

    public SomeController(AuthorizationService authorizationService)
    {
        _authorizationService = authorizationService;
    }

    public IActionResult AdminFunction()
    {
        if (!_authorizationService.Authorize(User.Role, "Admin"))
        {
            return Unauthorized("You do not have access to this function.");
        }
        // Udfør administrativ handling
        return Ok();
    }
}
```

#### Hvor bruges dette i en microservice arkitektur?
I en microservice-arkitektur kan **en centraliseret autorisationsservice** bruges som en fælles komponent, der integreres i hver enkelt service. Dette hjælper med at håndtere ensartede adgangsregler på tværs af [[Publishing/Main/Noter/Programmering/API-Gateway\|API-gateways]] og **services**, så alle kald til en service gennemgår den samme kontrolmekanisme for at sikre, at kun autoriserede brugere kan udføre funktioner baseret på deres rolle.

## Tildel adgang baseret på rolle- og gruppespecifikke tilladelser
**Rolle- og gruppespecifikke tilladelser** giver dig mulighed for præcist at definere, hvilke funktioner der er tilgængelige for bestemte brugerroller og grupper. 

Dette sikrer, at ingen *uautoriserede brugere* får adgang til funktioner, som de ikke har tilladelse til, hvilket er vigtigt i applikationer med mange roller og hierarkier.

Her er et eksempel på en metode, der tjekker brugerens rolle og gruppe før adgang gives til bestemte funktioner.
```csharp
public class UserService
{
    public bool HasAccess(string userRole, List<string> allowedRoles)
    {
        return allowedRoles.Contains(userRole);
    }
}

public class GroupedController
{
    private readonly UserService _userService;

    public GroupedController(UserService userService)
    {
        _userService = userService;
    }

    public IActionResult SensitiveFunction()
    {
        var allowedRoles = new List<string> { "Admin", "Manager" };
        if (!_userService.HasAccess(User.Role, allowedRoles))
        {
            return Unauthorized("Insufficient privileges.");
        }
        // Udfør funktion
        return Ok();
    }
}
```

#### Hvor bruges dette i en microservice arkitektur?
I en microservice-arkitektur bruges **rollebaserede kontroller** på [[Publishing/Main/Noter/Programmering/API-Gateway\|Api-Gateway-niveau]] eller direkte i hver microservice for at sikre, at kun brugere med de nødvendige rettigheder kan få adgang til bestemte endpoints. 
Dette er især vigtigt i scenarier, hvor visse endpoints eller operationer kun bør være tilgængelige for bestemte brugergrupper, f.eks. administratorer eller teamledere.

## Brug et abstrakt administrativt controllerlag til administrative funktioner

Et *abstrakt* **administrativt controllerlag** giver en sikker måde at håndtere alle administrative funktioner på ét sted. Ved at samle alle **autorisationskontroller** for administrative funktioner i en abstrakt controller kan du nemt genbruge og håndtere adgangen til følsomme funktioner i en applikation.

Dette eksempel viser, hvordan en `AdminControllerBase` anvendes som basis for alle controllers med administrative funktioner.
```csharp
public abstract class AdminControllerBase : Controller
{
    protected bool IsAuthorizedAdmin()
    {
        return User.Role == "Admin";
    }
}

public class UserAdminController : AdminControllerBase
{
    public IActionResult GetAllUsers()
    {
        if (!IsAuthorizedAdmin())
        {
            return Unauthorized("Access denied.");
        }
        // Udfør administrativ handling
        return Ok();
    }
}
```

#### Hvor bruges dette i en microservice arkitektur?
Dette mønster bruges ofte til at håndtere administrative funktioner centralt i en microservice-arkitektur, så alle services, der kræver administrative kontroller, kan arve fra den abstrakte base-controller. 
Dette sikrer, at *hver controller*, der arver fra `AdminControllerBase`, anvender samme adgangskontrol.

## Begræns og gennemgå API-endepunkter mod autorisationsproblemer
I en applikation med *mange endpoints* er det nødvendigt regelmæssigt at gennemgå [[Publishing/Main/Noter/Programmering/API\|API-strukturen]] og sikre, at der er passende autorisationskontrol for alle endpoints. Dette inkluderer både administrative og regulære endpoints, da manglende kontrol kan føre til utilsigtet adgang.

Nedenfor er et *eksempel på en autorisationskontrol*, der implementeres for at gennemgå adgangskontrol for hvert endpoint i en routing-konfiguration.

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapGet("/api/admin/data", async context =>
    {
        if (!context.User.HasClaim("role", "Admin"))
        {
            context.Response.StatusCode = 403;
            await context.Response.WriteAsync("Access denied.");
            return;
        }
        // Returner data
        await context.Response.WriteAsync("Sensitive admin data.");
    });

    endpoints.MapGet("/api/user/data", async context =>
    {
        // Bruger endpoint med mindre følsomme data
        await context.Response.WriteAsync("Public user data.");
    });
});
```

#### Hvor bruges dette i en microservice arkitektur?
I microservices bruges dette som en sikkerhedspraksis til at håndtere adgangskontrol på alle *services’ endpoints*, især for [[Publishing/Main/Noter/Programmering/API-Gateway\|API-gateways]] og andre eksternt eksponerede services.

Denne praksis sikrer, at både *administrative og regulære endpoints* har korrekt adgangskontrol, så følsomme endpoints kun er tilgængelige for autoriserede brugere.
