---
{"dg-publish":true,"permalink":"/main/programmering/rest-api/","title":"REST API","tags":["Programmering","API","REST_API"],"created":"2024-08-11T07:52:47.752+02:00"}
---


> En REST API bruger HTTP til at manipulere ressourcer identificeret af URI'er.
> Den har seks begrænsninger og kan interagere med mange typer [[Main/Teknologi/Web Dev/Client\|klienter]],
> som webbrowsere og mobilapps.

## Hvad er en REST API?

En REST API (`R`epresentational `S`tate `T`ransfer `A`pplication `P`rogramming
`I`nterface) er en måde at bygge webservices på, der tillader forskellige
applikationer at kommunikere med hinanden over internettet. REST er en
arkitekturstil, som definerer en række begrænsninger og principper, der
gør det muligt at skabe skalerbare og effektive webservices.

**RESTful API**'er bruger [[Main/Teknologi/Web Dev/HTTP\|HTTP]]-protokollen og dens metoder (GET,
POST, PUT, DELETE) til at udføre operationer på ressourcer, som er
identificeret ved URI'er (Uniform Resource Identifiers). Data udveksles
typisk i formater som JSON eller XML.

### URL vs URI

**URL (Uniform Resource Locator)**: En URL er en specifik type URI, som
indeholder både en adresse (hvor en ressource er placeret) og en metode
til at få adgang til den (såsom [[Main/Teknologi/Web Dev/HTTP\|HTTP]]). For eksempel: `https://www.example.com/resource`.

**URI (Uniform Resource Identifier)**: En URI er en generel betegnelse
for identifikatorer, som kan være enten en URL eller en URN (Uniform
Resource Name), der kun specificerer ressourceens navn uden at angive
en metode til at få adgang til den. For eksempel: `urn:isbn:0451450523`.

### REST's 6 begrænsninger

### Client-Server Arkitektur

Skiller klient og server for at forbedre portabilitet og skalerbarhed.
[[Main/Teknologi/Web Dev/Client\|Klienten]] håndterer brugergrænsefladen, mens serveren håndterer
dataopbevaring og logik.

### Statelessness

Hver [[Main/Teknologi/Web Dev/HTTP\|HTTP]]-anmodning fra [[Main/Teknologi/Web Dev/Client\|klienten]] til serveren skal indeholde
alle de oplysninger, der er nødvendige for at forstå og behandle anmodningen.
Serveren gemmer ingen klientkontekst mellem anmodninger.

### Cacheability

Svar fra serveren bør definere, om de er cachebare eller ej, for at forbedre
ydeevnen ved at undgå gentagne behandlinger af identiske forespørgsler.

### Layered System

[[Main/Teknologi/Web Dev/Client\|Klienter]] kan ikke fortælle, om de er direkte forbundet med
slutserveren eller en mellemliggende server. Dette fremmer skalerbarhed
ved at tillade load balancing og caching.

### Uniform Interface

En ensartet grænseflade mellem komponenter, som gør det lettere at forstå
og interagere med tjenesten. Dette inkluderer:

- Identifikation af ressourcer via URI'er.
- Manipulation af ressourcer via repræsentationer.
- Selvbeskrivende beskeder.
- Hypermedia as the Engine of Application State (HATEOAS).

## Code on Demand (Valgfrit)

Serveren kan levere eksekverbar kode eller scripts til [[Main/Teknologi/Web Dev/Client\|klienten]], som
kan udføres efter behov (f.eks. [[Main/Teknologi/Web Dev/JavaScript\|JavaScript]]).

### REST og HTTP

[[Main/Teknologi/Web Dev/HTTP\|HTTP]] er den protokol, som oftest bruges til at implementere RESTful
webservices. De centrale [[Main/Teknologi/Web Dev/HTTP\|HTTP]]-metoder i REST er:

- **GET**: Henter en repræsentation af en ressource.
- **POST**: Opretter en ny ressource.
- **PUT**: Opdaterer en eksisterende ressource.
- **DELETE**: Sletter en ressource.
- **PATCH**: Delvis opdatering af en ressource.

[[Main/Teknologi/Web Dev/HTTP\|HTTP]]-statuskoder bruges til at indikere resultatet af en anmodning
(f.eks. 200 OK, 404 Not Found, 500 Internal Server Error).

### Hvad interagerer med en REST API?

En bred vifte af klienter og systemer kan interagere med en REST API, herunder:

- **Webbrowsere**: Via [[Main/Teknologi/Web Dev/JavaScript\|JavaScript]] og AJAX-anmodninger.
- **Mobilapps**: På forskellige platforme (iOS, Android) for at kommunikere med servere.
- **Server-side applikationer**: For at integrere forskellige systemer og tjenester.
- **IoT-enheder**: For at sende data til og modtage data fra servere.
- **Command-line tools**: Som cURL til direkte kommunikation med API'er.

REST API'er er designet til at være fleksible og interoperable, hvilket gør det muligt
for mange forskellige typer enheder og applikationer at interagere med dem effektivt.

[Linkedin Learning - Rest API](https://www.linkedin.com/learning/learning-rest-apis/the-restful-librarian?resume=false&u=57075649)