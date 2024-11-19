---
{"dg-publish":true,"permalink":"/main/noter/data-transfer-object/","created":"2024-11-11T10:29:38.075+01:00"}
---


## Hvad er en DTO (Data Transfer Object)?
![Data Transfer Object.png](/img/user/Data%20Transfer%20Object.png)

> [!Important] 
> En **DTO (Data Transfer Object)** er et designmønster, der bruges til at overføre data mellem forskellige lag eller komponenter i en applikation. DTO'er bruges ofte i situationer, hvor der er behov for at sende data over et netværk, eksempelvis mellem klient og server, eller mellem forskellige [[Main/Noter/Emner/Backend/Microservice\|microserivces]] i en distribueret applikation.

DTO'er bruges primært til at forenkle og optimere dataoverførsel. De indeholder kun de data, der er nødvendige for den specifikke operation ell er transaktion, og de er ofte enklere og lettere end de interne datamodeller, som bruges i systemets forretningslogik.

### Hvorfor bruge DTO'er?

DTO'er anvendes af flere grunde:

- **Fjernelse af unødvendig kompleksitet**: DTO'er indeholder kun de data, der er nødvendige for en operation, og skjuler interne data, som ikke behøver at blive delt.
- **Forbedring af ydeevnen**: Ved at sende kun relevante data mellem lagene reduceres netværksbelastningen og antallet af operationer, hvilket kan forbedre applikationens ydeevne.
- **Separation af bekymringer**: DTO'er giver en klar grænse mellem datamodellerne, som repræsenterer systemets interne tilstand, og de objekter, der sendes over netværket eller til andre lag. Dette gør koden mere modulær og lettere at vedligeholde.
- **Fleksibilitet**: DTO'er gør det lettere at ændre interne datamodeller uden at påvirke den måde, hvorpå data udveksles med andre systemer.

### Eksempel på en DTO i C#

```csharp
// DTO for en simpel bruger 
	public class UserDto 
	{     
		public Guid Id { get; set; }     
		public string Name { get; set; }     
		public string Email { get; set; }     
		public DateTime CreatedAt { get; set; } 
	}
```

Dette DTO objekt kan bruges til at sende data om en bruger mellem lagene i en applikation, f.eks. fra en controller til en view, eller fra en service til en database.
### Hvordan fungerer en DTO i en Microservice-arkitektur?

I en **microservice-arkitektur** bruges DTO'er til at kommunikere mellem de forskellige [[Main/Noter/Emner/Backend/Microservice\|microserivces]]. For eksempel, når en service skal hente data fra en anden service, kan det gøre det via en DTO, som indeholder *den nødvendige information*, men undgår at afsløre interne detaljer om datamodellen.

> [!example] Eksempel 1
 En **User Service** kunne bruge et **UserDto** til at sende oplysninger om en bruger til en **Notification Service**, som derefter bruger disse data til at sende en e-mail eller SMS.

> [!Example ] Eksempel 2
> Når data skal sendes fra et [[Main/Noter/API\|API]] til frontend-applikationen, kan en DTO bruges til at formatere de nødvendige data, som derefter vises i brugergrænsefladen.

#### Eksempel på brug i en microservice

Lad os sige, vi har to [[Main/Noter/Emner/Backend/Microservice\|microserivces]] i en applikation: **User Service** og **Order Service**. **Order Service** har brug for at få oplysninger om brugeren, der har lavet en bestilling. **User Service** sender en DTO til **Order Service**.

**UserService (Controller)**

```csharp
[ApiController] [Route("api/users")] 
public class UserController : ControllerBase 
{     
	private readonly IUserService _userService;      
	public UserController(IUserService userService)     
	{         
		_userService = userService;     
	}      
		
	[HttpGet("{id}")]     
	public ActionResult<UserDto> GetUser(Guid id)     
	{         
		var user = _userService.GetUserById(id);
		if (user == null)         
		{             
			return NotFound();         
		}                  
		var userDto = new UserDto         
		{             
			Id = user.Id,             
			Name = user.Name,             
			Email = user.Email,             
			CreatedAt = user.CreatedAt         
		};                  
	return Ok(userDto);     
	} 
}
```


**OrderService (Controller)**

```csharp
[ApiController] [Route("api/orders")] 
public class OrderController : ControllerBase 
{     
	private readonly IOrderService _orderService;     
	private readonly HttpClient _httpClient;      
	public OrderController(IOrderService orderService, HttpClient httpClient)
	{         
		_orderService = orderService;         
		_httpClient = httpClient;     
	}      
	[HttpPost]     
	public async Task<IActionResult> CreateOrder([FromBody] OrderDto orderDto)
	{         
		// Hent brugerdata ved at kalde UserService API'en         
		var userResponse = await _httpClient.GetAsync($"http://userservice/api/users/{orderDto.UserId}"); 
		if (!userResponse.IsSuccessStatusCode)         
		{             
			return BadRequest("User not found");         
		}          
		var userDto = await userResponse.Content.ReadAsAsync<UserDto>();
		// Skab ordren baseret på både brugerdata og bestillingsdata         
		var order = new Order         
		{             
			UserId = userDto.Id,             
			Product = orderDto.Product,             
			Quantity = orderDto.Quantity,             
			OrderDate = DateTime.Now         
		};          
		await _orderService.CreateOrder(order);         
		return Ok();     
	} 
}
```
I dette eksempel sender **UserService** et **UserDto** til **OrderService**, som så bruger denne DTO til at validere og oprette en bestilling.

#### Fordele ved at bruge DTO'er

- **Ydeevne**: DTO'er hjælper med at sende kun nødvendige data, hvilket reducerer belastningen på systemet og forbedrer svartiderne.
- **Sikkerhed**: DTO'er tillader, at interne datamodeller (f.eks. entity- eller databaseklasser) ikke bliver afsløret direkte, hvilket kan forbedre sikkerheden.
- **Enkel kommunikation**: DTO'er tilbyder en simpel og standardiseret måde at overføre data på tværs af systemer eller applikationslag.
- **Skalering**: DTO'er hjælper med at håndtere væksten i applikationens kommunikation mellem forskellige [[Main/Noter/Emner/Backend/Microservice\|services]] og klienter, især når der er mange [[Main/Noter/Emner/Backend/Microservice\|microservices]].

#### Konklusion

En **DTO** er et vigtigt værktøj i moderne applikationer, især i **microservices-arkitekturer**, da det gør det muligt at overføre data mellem services på en effektiv og sikker måde. 

Ved at bruge DTO'er kan man opretholde [separation af bekymringer,](https://en.wikipedia.org/wiki/Separation_of_concerns) forbedre ydeevnen, og sikre at kun relevante data bliver delt. DTO'er hjælper med at gøre applikationer mere *modulære* og lettere at *vedligeholde*.