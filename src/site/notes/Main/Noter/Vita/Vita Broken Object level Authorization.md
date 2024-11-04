---
{"dg-publish":true,"permalink":"/main/noter/vita/vita-broken-object-level-authorization/","created":"2024-11-04T09:40:00.677+01:00"}
---


## Broken Object level Authorization
 
> [!NOTE]- Opsummering af BOLA
> API'er er sårbare over for **Broken Object Level Authorization** (*BOLA*), hvis de ikke kontrollerer, om en *bruger* har ret til at tilgå eller ændre specifikke objekter. ***BOLA* opstår, når API’en tillader manipulation af objekters ID'er**, så brugere kan få adgang til andre brugeres data. For at beskytte sig bør API'er validere, at den aktuelle bruger har adgangsrettigheder til hvert objekt. Løsningen omfatter hierarkibaserede adgangskontroller, brug af uforudsigelige GUIDs for objekter, og omfattende tests for at sikre korrekt adgangskontrol.

Måde vi kan løse denne sikkerhedsudfordring er ved blandt andet: 
1. Ved at skabe *en bedre autorisations mekanisme* der hviler på *user policies* og bruger hieraki.
2. Ved at bruge en mekanisme som kontrollerer om den bruger, som er logget ind, har rettigheder  til at udføre den handling de gerne vil.
3. Ved brugen af random GUID'er til at gemme ting og sager.
4. Ved at skrive tests der evaluerer sårbarheden af auth mekanismen og ikke *deployer* hvis testen fejler.

## Kode eksempler

==Med udgangspunkt i nummer ovenstående punkter kan dette løses på følgende måde.==
### Opsæt bruger hierarki
Det første man skal have spurgt sig serv om er om der er brug for flere *slags brugere* end: *Admin*, *Manager* og *User*. Men også hvilke rettigheder disse roller har brug for. Er der nogle rettigheder som kræder en ny form for bruger?
### Claim Based Authorization
Når dette er på plads kan man opsætte en *Claim Based Authorization*
ved logind tilknyttes *claims*(brugerdata) til en [[Main/Noter/JWT token\|JWT token]] . Dette gøres så brugerens rolle, rettigheder og adgang til ressourcer kan bekræftes i hver forespørgsel.

```csharp
var claims = new List<Claim> 
{ 
	new Claim(ClaimTypes.Name, user.Username), 
	new Claim(ClaimTypes.Role, user.Role), 
	new Claim("Department", user.Department), 
	new Claim("UserHierarchyLevel", 
	user.HierarchyLevel.ToString()) 
};
```
#### Hvor gøres dette i en Microservice Arkitektur?
Dette kan gøres i en central *Identity Service*, som fx i vores *User Service*. Denne service vil så kunne blive brugt til at udstede [[Main/Noter/JWT token\|tokens]] med bruger claims som hver services så vil kunne bruge til at verificere.
### Definere Autorisations politik
En implementering af følgende kan systemet mulighed for at validere adgang baseret på de før nævnte claims.

```csharp
services.AddAuthorization(options => 
{ 
options.AddPolicy("CanAccessSensitiveData", policy => 
	policy.RequireClaim(ClaimTypes.Role, "Admin", "Manager")
		  .RequireClaim("UserHierarchyLevel", "2", "3")); 
});
```

#### Hvor gøres dette i en Microservice Arkitektur?
Policies defineres som regel i *de enkelte microservices*. Hver microservice kan have specifikke policies afhængigt af de operationer, de tillader fx kun at Admins oprette nye ressourcer.

###  Brug Policies i API Controllers
I API-metoderne kan man bruge `[Authorize(Policy = "CanAccessSensitiveData")]` til at sikre, at kun brugere, der opfylder politikken, kan tilgå bestemte endpoints.

```csharp
[Authorize(Policy = "CanAccessSensitiveData")] 
[HttpGet("sensitive-data")] 
public IActionResult GetSensitiveData() { // Logic to retrieve sensitive data }
```

#### Hvor gøres dette i en Microservice Arkitektur?
*I den enkelte microservice*, der håndterer adgang til specifikke endpoints. Når en service modtager en request med et [[Main/Noter/JWT token\|JWT token]], kan den udtrække og verificere brugerens claims og rolle mod policies, før den udfører handlinger.

### Implementer Objektkontrol i Hvert Endpoint
I selve endpoints skal man tilføje checks for, at finde ud af om brugeren har ret til det specifikke objekt (eksempelvis ved at kontrollere om brugeren ejer objektet eller har den nødvendige hierarkitilladelse).

```csharp
[HttpGet("documents/{id}")] 
public async Task<IActionResult> GetDocument(Guid id) 
{ 
	// Forsøger at hente dokumentet fra databasen via document service 
	var document = await _documentService.GetDocumentByIdAsync(id); 
	
	// Tjekker om brugeren, der laver forespørgslen, er ejeren af dokumentet 
	// (baseret på OwnerId i dokumentet og brugerens ID fra claims) 
	if (document.OwnerId != User.FindFirst(ClaimTypes.NameIdentifier).Value) 
	{ 
	
	// Returnerer en 403 Forbudt-fejl, hvis brugeren ikke har tilladelse 
		return Forbid(); 
		
	} 
	// Returnerer dokumentet, hvis brugeren har tilladelse til at tilgå det 
	return Ok(document); 
}
```

#### Hvor gøres dette i en Microservice Arkitektur?
*Objektkontrol* er en afgørende del af hver microservice, især hvis services skal sikre, at brugerne kun kan tilgå deres egne data. Dette gøres ved at tjekke ejerskab direkte i endpoints eller i de services, der tilgår data.

### TESTS!
Skriv tests for at sikre, at policies og objektkontroller fungerer som forventet, og at kun autoriserede brugere kan udføre specifikke handlinger.

#### Hvor gøres dette i en Microservice Arkitektur?
Tests kan være *centralt organiseret for Identity Service* og *i de enkelte microservices* for at sikre, at autorisationen fungerer som forventet. 

>[!WARNING] Meget Vigtigt
>Testene bør indeholde kontrol for uautoriseret adgang til endpoints og objekt
> ejerskabskontrol.
