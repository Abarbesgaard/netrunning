---
{"dg-publish":true,"permalink":"/main/noter/vita/broken-object-property-level-authorization/","created":"2024-11-06T07:49:50.035+01:00"}
---

![Broken Object Level Auth.png](/img/user/Resource/98_Images/Broken%20Object%20Level%20Auth.png)
> [!NOTE]- Opsummering af BOPLA
> Et API-endpoint er sårbart, hvis det tillader en bruger at tilgå eller ændre følsomme objektdata *uden autorisation*, kendt som "**Excessive Data Exposure**" og "**Mass Assignment**". Eksempler på angreb viser, hvordan manglende validering kan give adgang til private oplysninger eller uautoriserede ændringer, som at justere bookingpriser eller låse blokeret indhold op. For at forhindre dette bør API'er begrænse data, vælge specifikke egenskaber, der returneres, og implementere skemabaseret validering af adgang til følsomme data.

For at løse sårbarheder ved "**Excessive Data Exposure**" og "**Mass Assignment**" i [[Main/Noter/Programmering/API\|API-endpoints]] kan man:

1. **Valider brugeradgang til objekt-egenskaber**: Sørg for, at kun autoriserede brugere kan tilgå de eksponerede objektdata. Dette reducerer risikoen for adgang til følsomme oplysninger.
2. **Begræns data, der returneres**: Undgå generiske metoder som `to_json()` og `to_string()`. Vælg i stedet præcise objekt-egenskaber, der er nødvendige for formålet, og returnér kun dem.
3. **Implementer skemabaseret validering**: Brug en skemavalidering for at definere, hvilke data der må returneres og ændres, som en ekstra sikkerhed.
4. **Undgå automatisk data-binding**: Brug ikke funktioner, der binder input direkte til objekt-egenskaber. Tillad kun opdatering af egenskaber, der specifikt skal kunne ændres af brugeren.

## Validér brugeradgang til objekt-egenskaber
I en microservice-arkitektur kan man bruge en **middleware** eller en **adgangsvalidering**, som kontrollerer, om brugeren har adgang til de specifikke dataegenskaber.

```csharp
public class AccessValidator
{
    public bool ValidateUserAccess(Guid userId, string propertyName)
    {
        // Logik til at validere brugeradgang for specifikke dataegenskaber
        var authorizedProperties = GetAuthorizedPropertiesForUser(userId);
        return authorizedProperties.Contains(propertyName);
    }

    private List<string> GetAuthorizedPropertiesForUser(Guid userId)
    {
        // Returner en liste over tilladte egenskaber baseret på brugerens rolle
        return new List<string> { "Name", "Email" };
    }
}
```

#### Hvor bruges dette i en microservice?
Denne type validering kan implementeres i en *fælles auth-service* eller *som middleware*, der håndterer alle [[Main/Noter/Programmering/API\|API-requests]] til de relevante endpoints og sikrer, at kun nødvendige egenskaber er tilgængelige for brugeren.

## Begræns data, der returneres
For at undgå utilsigtet eksponering af data, kan du kun vælge specifikke egenskaber til responsen i *controlleren*.

```csharp
public class UserService
{
    public object GetUserData(Guid userId)
    {
        var user = GetUserFromDatabase(userId);

        // Returner kun nødvendige egenskaber
        return new {
            Name = user.Name,
            Email = user.Email
        };
    }
}
```

#### Hvor bruges dette i en microservice?
Her kan man skabe en [[Main/Noter/Programmering/Data Transfer Object\|DTO]] for kun at returnere de nødvendige egenskaber i microservices, som typisk håndterer brugerprofiler eller følsomme data. [[Main/Noter/Programmering/Data Transfer Object\|DTO]]'er hjælper også med at standardisere datainput/output på tværs af services.

## Implementer skemabaseret validering
Brug en **skemavalidering** som en ekstra sikkerhed, *især hvis API'et modtager inputdata*, hvor kun nogle egenskaber må kunne ændres.

```csharp
public class UpdateUserRequest
{
    public string Name { get; set; }
    public string Email { get; set; }

    // Denne egenskab er privat og kan ikke ændres via API
    private string Role { get; set; }
}

public class UserController : ControllerBase
{
    [HttpPut("api/user/update")]
    public IActionResult UpdateUser([FromBody] UpdateUserRequest request)
    {
        if (!ModelState.IsValid)
            return BadRequest();

        // Kun Name og Email kan opdateres
        UpdateUserInDatabase(request);
        return Ok();
    }
}
```

#### Hvor bruges dette i en microservice?
Dette kan bruges i services, hvor *opdateringer modtages fra klienten*. Skemavalidering forhindrer uautoriserede ændringer af egenskaber, som kun backend eller bestemte services bør håndtere.

## Undgå automatisk data-binding
Undgå `ObjectMapper` eller lignende teknikker, som kan føre til "**Mass Assignment**" sårbarhed. Lav i stedet manuelt *felt-for-felt-binding*, så kun specifikke egenskaber kan opdateres.
```csharp
public class UserController : ControllerBase
{
    [HttpPut("api/user/update")]
    public IActionResult UpdateUser(Guid userId, string name, string email)
    {
        var user = GetUserFromDatabase(userId);
        
        // Kun specifikke egenskaber opdateres manuelt
        user.Name = name;
        user.Email = email;
        
        SaveUserToDatabase(user);
        return Ok();
    }
}
```

#### Hvor bruges dette i microservices?
Denne metode er effektiv i **brugerservices**, hvor man ønsker manuel kontrol over, hvilke felter brugeren kan opdatere, og hvor uautoriserede felter som "role" eller "permissions" ikke må kunne ændres.