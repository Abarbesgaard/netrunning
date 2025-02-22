---
{"dg-publish":true,"permalink":"/publishing/main/noter/litteratur/noter/microservices-explained/","title":"Literatur Liste","created":"2024-09-06T08:19:23.257+02:00"}
---

Troværdighed: 3/5
Relevans: 5/5

[[Publishing/Main/Noter/Litteratur/LitteraturListe\|Gå til litteratur listen]]
[Microservices Explained - YouTube](https://www.youtube.com/watch?v=rv4LlmLmVWk)

## Hvad er Microservices?

### Monolit

Før i tiden brugte man monolitiske applikationer, hvor alt var samlet i én
stor applikation. Dette gjorde det svært at vedligeholde og opdatere
applikationen, da alt skulle ændres på én gang.

Alt er udviklet, testet og deployet som én stor enhed.

Teamet skal i højere grad samarbejdet for at undgå at ramme ind i hinanden
arbejde.

#### Udfordringerne ved den monotiske arkitektur

- Applikationer er for store og komplekse
- Dele af applikationen kan være tæt koblet
- Man kan kun skalere hele applikationen og ikke individuelle dele, som
  kan være en flaskehals.
- Udfordringer ved dependencies

## Microservices arkitektur

- Man deler applikationen op i mindre services.
- Hvordan skal man dele applikationen op?
  - Efter forretningsfunktioner (best practice).
  - Efter teknologier.
  - Efter data.
- Hver microservice må kun gøre én ting.
- hver service skal være uafhængig af hinanden.
- Hver service kan udvikles med deres egen sprog.

## Kommunikation mellem services

- REST API
- Message brokers
  - disse vil være med til at sikre at beskeder bliver leveret.
- Service Mesh

## Monorepo vs. Polyrepo

Med ét projekt er det simpelt da der er et projekt der skal have ét repository.
Med et monorepo er det nemmere at dele kode.
Det kan være en udfordring med monorepo da der kan være risiko for at man laver
tæt kobling mellem services.
Det at pushe til et monorepo kan være langsommere.
Ved polyrepo er det nemmere at have en hurtigere CI/CD pipeline.
Det kan også være udfordringer at lave ændringer på tværs af services.
Det at dele ressourcer kan være en udfordring
