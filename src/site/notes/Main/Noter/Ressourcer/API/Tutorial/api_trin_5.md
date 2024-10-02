---
{"dg-publish":true,"permalink":"/main/noter/ressourcer/api/tutorial/api-trin-5/","title":"Trin 5","tags":["ressource","API","Web Api","Tutorial"],"created":"2024-08-16T11:12:31.206+02:00"}
---


## 5. Trin: Database kontekst

Databasekonteksten er hovedklassen, der koordinerer Entity
Framework-funktionalitet for et datamodel.

Denne klasse oprettes ved at arve fra Microsoft.EntityFrameworkCore.DbContext-klassen.

Så nu skal du tilføje en ny klasse til din models mappe ved navn TodoContext.cs

```csharp
using Microsoft.EntityFrameworkCore;
 
namespace TodoApi.Models;
 
public class TodoContext : DbContext
{
    public TodoContext(DbContextOptions<TodoContext> options)
        : base(options)
    {
    }
 
    public DbSet<TodoItem> TodoItems { get; set; } = null!;
}
```

[[Main/Noter/Ressourcer/API/Tutorial/api_trin_4\|tilbage til trin 4]]

[[Main/Noter/Ressourcer/API/Tutorial/api_trin_6\|videre til trin 6]]
