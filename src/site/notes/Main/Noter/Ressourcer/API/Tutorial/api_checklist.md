---
{"dg-publish":true,"permalink":"/main/noter/ressourcer/api/tutorial/api-checklist/","title":"Checklist til API","tags":["ressource","API","Web Api","Tutorial"],"created":"2024-08-16T11:11:22.409+02:00"}
---


## Checklist til API

## 1. Projektopsætning

- [ ] Opret et nyt projekt i det valgte framework (f.eks. ASP.NET Core, Spring Boot).
- [ ] Konfigurer relevante dependencies (f.eks. Entity Framework, AutoMapper, Swagger).
- [ ] Definer de grundlæggende mapper for arkitekturen:
  - `Controllers`
  - `Services`
  - `Repositories`
  - `Models`
  - `Data` (til kontekst og seed data, hvis nødvendigt)

## 2. Datamodel (Models)

- [ ] Definer dataentiteter (klasser) baseret på forretningskrav.
- [ ] Tilføj nødvendige attributter og datavalidering.
- [ ] Opret relationer mellem modellerne, hvis det er relevant.

## 3. Databasekonfiguration

- [ ] Konfigurer databasekonteksten (DbContext for Entity Framework).
- [ ] Definer DbSets for hver model.
- [ ] Konfigurer databaseforbindelse i `appsettings.json` eller en tilsvarende konfigurationsfil.
- [ ] Implementer migrations (hvis nødvendigt) for at oprette database og tabeller.

## 4. Repository Layer

- [ ] Opret interface for generisk repository (`IGenericRepository<T>`).
- [ ] Implementer CRUD-operationer i den generiske repository (Create, Read,
Update, Delete).
- [ ] Opret specifikke repositories for hver model, hvis nødvendigt
(f.eks. `IUserRepository`, `ProductRepository`).
- [ ] Injekter repository i services via dependency injection.

## 5. Service Layer

- [ ] Opret interface for services (f.eks. `IUserService`, `IProductService`).
- [ ] Implementer forretningslogik i services (med kald til repository lag).
- [ ] Håndter undtagelser og fejlhåndtering i services.
- [ ] Injekter services i controllers via dependency injection.

## 6. Controller Layer

- [ ] Opret controllers for de forskellige endpoints (f.eks. `UserController`, `ProductController`).
- [ ] Definer RESTful endpoints (GET, POST, PUT, DELETE) for hver ressource.
- [ ] Tilføj routing og nødvendige attributter
(f.eks. `[Route("api/[controller]")]`, `[HttpGet]`).
- [ ] Håndter request validation og returner relevante HTTP-statuskoder
(200 OK, 400 Bad Request, 404 Not Found, etc.).

## 7. DTOs og Mapping

- [ ] Opret Data Transfer Objects (DTOs) for indgående og udgående data, hvis nødvendigt.
- [ ] Brug AutoMapper eller tilsvarende værktøj til at mappe mellem modeller og DTOs.

## 8. Ekstra (Valgfrit)

- [ ] Implementer logning for at spore API-kald.
- [ ] Tilføj sikkerhed (f.eks. JWT authentication).
- [ ] Dokumenter API'et med Swagger eller tilsvarende værktøj.
- [ ] Skriv unit tests for controllers, services, og repositories.
