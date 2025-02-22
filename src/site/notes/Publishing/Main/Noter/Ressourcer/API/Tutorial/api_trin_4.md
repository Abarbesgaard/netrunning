---
{"dg-publish":true,"permalink":"/publishing/main/noter/ressourcer/api/tutorial/api-trin-4/","title":"Trin 4","tags":["ressource","API","Web Api","Tutorial"],"created":"2024-08-16T10:50:20.122+02:00"}
---


## Trin 4

Nu skal vi til at lave modellen for vores API.

Til dette skal vi have en mappe ved navn models og en klasse ved navn
TodoItem.cs. Ingen af disse eksisterer endnu, så vi skal lave dem.

Indsæt følgende kode i TodoItem.cs:

```csharp
namespace TodoApi.Models;
 
public class TodoItem
{
    public long Id { get; set; }
    public string? Name { get; set; }
    public bool IsComplete { get; set; }
}
```

Id'et vil her fungere som en unik identifikator for en TodoItem.

[[Publishing/Main/Noter/Ressourcer/API/Tutorial/api_trin_3\|Tilbage til trin 3]]
[[Publishing/Main/Noter/Ressourcer/API/Tutorial/api_trin_5\|Videre til trin 5]]
