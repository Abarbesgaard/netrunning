---
{"dg-publish":true,"permalink":"/main/noter/vita/broken-authentication/","created":"2024-11-05T10:13:22.248+01:00"}
---

## Broken Authentication
![Broken Auth.png](/img/user/98_Images/Broken%20Auth.png)

> [!note]- Opsummering af Broken Auth
> API-sikkerhed er afgørende, især ved autentificering og følsomme operationer som "glemt adgangskode". En API betragtes som sårbar, hvis den tillader credential stuffing, mangler beskyttelse mod brute force-angreb, tillader svage adgangskoder, sender følsomme oplysninger i URL'en, og ikke kræver bekræftelse af brugerens identitet ved ændringer af følsomme data. Mikroservices er også udsatte, hvis de kan tilgås uden autentificering eller bruger svage tokens. For at forhindre disse sårbarheder bør man implementere strenge autentificeringsprotokoller, kræve re-autentificering ved kritiske ændringer, beskytte mod brute force-angreb og sikre, at API-nøgler kun anvendes til autentificering af API-klienter.

Måden vi kan løse denne sikkerhedsudfordring er ved blandt andet:
1. Implementer *Rate Limiting* og *Brute Force* Beskyttelse.
2. Krav om *Re-Autentificering* ved Følsomme Handlinger.
3. Anvend en *Stærk Password Policy* og *To-Faktor Autentificering*. 
4. *Validér* og Beskyt Tokens.

## Rate Limiting
**Rate limiting** forhindrer angribere i at udføre *brute force*-angreb ved at begrænse antallet af login-forsøg, hvilket beskytter brugerkonti mod **uautoriseret** adgang.

```csharp
builder.services.AddRateLimiter(options => 
{ 
	options.AddPolicy("RateLimitPolicy", policy => 
	{ 
		policy.Limit = 3; // Maksimalt antal anmodninger policy.
		Period = TimeSpan.FromMinutes(1); // Tidsperiode 
	}); 
});

// ...

app.UseEndpoints(endpoints => 
{ 
	endpoints.MapPost("/login", async context => 
	{ 
		// Logik til login 
	}); 
});


```

#### Hvor det bruges i microservices? 
**Rate limiting** bruges typisk i **autentificeringstjenester** og [[Main/Noter/API-Gateway\| API-Gateways]] for at forhindre brute force-angreb på login-endpoints.

## Krav om Re-Autentificering ved Følsomme Handlinger
Ved at kræve **re-autentificering** ved *ændringer af følsomme oplysninger* som e-mail adresser sikres det, at kun autoriserede brugere kan foretage kritiske ændringer, hvilket reducerer risikoen for  misbrug.

```csharp
[HttpPut("account/email")]
public async Task<IActionResult> UpdateEmail([FromBody] UpdateEmailRequest request)
{
    var user = await _userService.GetUserByIdAsync(User.Identity.Name);

    // Bekræft brugerens nuværende adgangskode
    if (!VerifyPassword(request.CurrentPassword, user.PasswordHash))
    {
        return Unauthorized("Invalid password");
    }

    // Opdater e-mail
    user.Email = request.NewEmail;
    await _userService.UpdateUserAsync(user);
    return Ok();
}
```

#### Hvor det bruges i microservices? 
Dette punkt implementeres *i services, der håndterer brugeroplysninger,* som for eksempel bruger- eller konto-microservices.

## Anvend Stærk Password Policy og To-Faktor Autentificering
En stærk **adgangskodepolitik** kombineret med 2FA tilføjer ekstra lag af sikkerhed, hvilket gør det betydeligt sværere for angribere at få adgang til brugerkonti, selvom de lykkes med at stjæle adgangskoden.

```csharp
public async Task<IActionResult> Register(UserRegisterModel model)
{
    var user = new ApplicationUser { UserName = model.Email, Email = model.Email };

    // Tjek for stærk adgangskode
    var result = await _userManager.CreateAsync(user, model.Password);
    if (result.Succeeded)
    {
        // Aktiver 2FA for brugeren
        await _userManager.SetTwoFactorEnabledAsync(user, true);
        return Ok();
    }

    return BadRequest(result.Errors);
}
```

#### Hvor det bruges i microservices? 
**2FA** kan implementeres i **autentificeringstjenester**, og *stærk adgangskodepolitik anvendes i enhver service, der håndterer brugerkonti.*

## Validér og Beskyt Tokens
Ved at **validere** og beskytte JWT-tokens forhindres uautoriseret adgang til [[Main/Noter/API\|API’en]], og man sikrer, at kun gyldige og autentiske brugere kan få adgang til beskyttede ressourcer, hvilket reducerer risikoen for angreb som token-forgery og uautoriseret dataadgang.

```csharp

builder.services.AddAuthentication(options =>
{
	options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
})
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = "YourIssuer",
            ValidAudience = "YourAudience",
            IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("YourSecretKey"))
        };
    });
}
// ...
    app.UseAuthentication();
    app.UseAuthorization();

```

#### Hvor det bruges i microservices? 
**Token-validéringsmekanismer** anvendes i alle services, der kræver autentificering, som f.eks.[[Main/Noter/API-Gateway\|API-gateways]]  og individuelle microservices, der håndterer brugeranmodninger.