---
{"dg-publish":true,"permalink":"/main/4-semester/ressourcer/api/tutorial/api-trin-6/","title":"Trin 6","tags":["ressource","API","Web Api","Tutorial"],"created":"2024-08-16T10:56:32.236+02:00"}
---


## Trin 6: Registering af database kontekst

Følgende linjer skal indsættes med dependency injection i Program.cs

```csharp
using Microsoft.EntityFrameworkCore;
using TodoApi.Models;

builder.Services.AddDbContext<TodoContext>(opt =>
    opt.UseInMemoryDatabase(“TodoList”)); 
```

Så din Program.cs fil vil se sådan ud:

```csharp
using Microsoft.EntityFrameworkCore;
using TodoApi.Models;
 
var builder = WebApplication.CreateBuilder(args);
 
builder.Services.AddControllers();
builder.Services.AddDbContext<TodoContext>(opt =>
    opt.UseInMemoryDatabase("TodoList"));
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
 
var app = builder.Build();
 
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}
 
app.UseHttpsRedirection();
 
app.UseAuthorization();
 
app.MapControllers();
 
app.Run();
```

Nu er din database kontekst registreret og klar til brug.

[[Main/4. Semester/Ressourcer/API/Tutorial/api_trin_5\|Tilbage til trin 5]]

[[Main/4. Semester/Ressourcer/API/Tutorial/api_trin_7\|Videre til trin 7]]
