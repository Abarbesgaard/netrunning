---
{"dg-publish":true,"permalink":"/main/artikler/dormands-monsteret/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-05T13:05:12.608+01:00"}
---

I softwareudvikling er det vigtigt at sikre, at kun gyldige data slipper gennem systemet. Et effektivt designmønster til dette er **Dørmandens Mønster**. 

Ideen er enkel: ligesom en dørmand ved en natklub kontrollerer gæsterne, før de får adgang, validerer vi input tidligt i en metode og afviser straks ugyldige data.

---
### **Hvad er Dørmandens Mønster?**

Dørmandens Mønster handler om:

1. *At stoppe ugyldige data ved indgangen* (typisk i API-metoder, services eller lignende).
2. At sikre, at kun gyldige og forventede data slipper videre i applikationen.
3. At gøre systemet mere robust og lettere at vedligeholde ved at centralisere valideringslogik.

Dette mønster kan kombineres med tidlig returnering for at holde koden læsbar og let at følge.

### **Et Generisk Eksempel**

Her er et simpelt eksempel på Dørmandens Mønster i en metode, der opdaterer en bruger:

```csharp
public async Task<IActionResult> UpdateUser(Guid userId, User? user)
{
    // Dørmand 1
    if (user == null)
    {
        return BadRequest("Brugerdata må ikke være null.");
    }
	// Dørmand 2
    if (userId != user.Id)
    {
        return BadRequest("Bruger-ID matcher ikke det angivne ID.");
    }
	// Dørmand 3
    if (string.IsNullOrWhiteSpace(user.Name))
    {
        return BadRequest("Brugernavnet må ikke være tomt.");
    }

    // Hvis valideringen består, fortsæt behandlingen
    await userService.UpdateUserAsync(user);

    return NoContent();
}
```
### **Hvordan Dørmands Mønster Hjælper**

1. **Tidlig Fejlregistrering:**  
    Metoden afviser ugyldige data tidligt, hvilket reducerer risikoen for runtime-fejl.
    
2. **Tydelig Logik:**  
    Valideringsreglerne er nemme at læse og vedligeholde.
    
3. **Defensiv Programmering:**  
    Ved at kontrollere input sikrer du, at resten af metoden ikke behøver at håndtere uforudsete situationer.
    

---

### **Abstraktion af Validering**

Hvis du har mange metoder, der kræver lignende validering, kan det være nyttigt at abstrahere reglerne i en hjælpermetode:

```csharp
private bool ValidateUserInput(Guid userId, User? user, out string? errorMessage)
{
	// Dørmand 1
    if (user == null)
    {
        errorMessage = "Brugerdata må ikke være null.";
        return false;
    }
	// Dørmand 2
    if (userId != user.Id)
    {
        errorMessage = "Bruger-ID matcher ikke det angivne ID.";
        return false;
    }
	// Dørmand 3
    if (string.IsNullOrWhiteSpace(user.Name))
    {
        errorMessage = "Brugernavnet må ikke være tomt.";
        return false;
    }

    errorMessage = null;
    return true;
}
```

Metoden ovenfor kan nu bruges i din API:
```csharp
public async Task<IActionResult> UpdateUser(Guid userId, User? user)
{
    if (!ValidateUserInput(userId, user, out var errorMessage))
    {
        return BadRequest(errorMessage);
    }

    await userService.UpdateUserAsync(user);

    return NoContent();
}
```
