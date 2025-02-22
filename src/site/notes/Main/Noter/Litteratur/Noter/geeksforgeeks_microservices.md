---
{"dg-publish":true,"permalink":"/main/noter/litteratur/noter/geeksforgeeks-microservices/","title":"Geeks for Geeks Microservices","tags":["Backend","Microservice","Projektarbejde"],"created":"2024-09-06T08:19:32.245+02:00"}
---



> ![TLDR]
> Microservices are a design approach where a large application is divided into
> smaller, independently deployable services. Each microservice handles a
> specific business function and communicates via APIs. This approach enhances
> scalability, flexibility, and maintainability, but introduces complexity in
> inter-service communication and data management.

---

## 1. Hvad er Microservices?

- **Definition:** Små, løst koblede tjenester, der hver især udfører en specifik
forretningsfunktion. De kan udvikles, deployeres og skaleres uafhængigt.
- **Formål:** Opdele en stor applikation i mindre komponenter med klart
definerede ansvarsområder.
- **Teknologier:** Kan skrives i forskellige programmeringssprog og frameworks.

## 2. Hvordan fungerer Microservices?

- **Modulær Struktur:** Opdeling af store monolitiske applikationer i mindre,
uafhængige tjenester.
- **Uafhængige Funktioner:** Hver microservice håndterer en specifik funktion.
- **Kommunikation:** Via veldefinerede API'er.
- **Fleksibilitet:** Forskellige teknologier kan anvendes for hver tjeneste.
- **Uafhængighed og Opdateringer:** Opdatering af én service påvirker ikke hele systemet.
- **Skalérbarhed:** Individuelle tjenester kan skaleres uafhængigt.
- **Kontinuerlig Forbedring:** Hurtigere udvikling og opdatering.

## 3. Hovedkomponenter i Microservices Arkitektur

- **Microservices:** Selvstændige tjenester med specifikke funktioner.
- **API Gateway:** Central indgangspunkt til microservices.
- **Service Registry og Discovery:** Holder styr på tjenester og deres adresser.
- **Load Balancer:** Fordeler trafik mellem tjenesteinstanser.
- **Containerization:** Brug af containere som Docker og orkestrering med Kubernetes.
- **Event Bus/Message Broker:** Faciliterer asynkron kommunikation.
- **Centraliseret Logging og Overvågning:** Spor præstation og helbred af tjenester.
- **Database per Microservice:** Hver tjeneste har sin egen database.
- **Caching:** Forbedrer ydeevne ved at gemme ofte tilgået data.
- **Fejltolerance og Resiliens:** Håndterer fejl og sikrer systemets stabilitet.

## 4. Designmønstre for Microservices

- **Aggregator:** Samler data fra flere tjenester og kombinerer resultater.
- **API Gateway:** Håndterer anmodninger og ruting til de rette tjenester.
- **Event Sourcing:** Skaber hændelser for ændringer i applikationens tilstand.
- **Strangler:** Gradvis udskiftning af monolit med microservices.
- **Decomposition:** Opdeling af applikationen i mindre tjenester baseret på forretningskrav.

## 5. Anti-Mønstre i Microservices

- **Data Monolith:** Centraliseret database der underminerer uafhængighed.
- **Chatty Services:** Overdreven kommunikation mellem tjenester.
- **Overusing Microservices:** For mange små tjenester til trivielle funktioner.
- **Inadequate Service Boundaries:** Dårligt definerede grænser mellem tjenester.
- **Ignoring Security:** Forsømmelse af sikkerhed kan føre til sårbarheder.

## 6. Virkelige Eksempler på Microservices

- **Amazon:** Dele af applikationen som brugeradministration, produktkatalog, ordrebehandling.
- **Netflix:** Brug af microservices til streaming og håndtering af trafik.
- **Uber:** Skift fra monolitisk til microservice for bedre skalerbarhed og ydeevne.

## 7. Microservices vs. Monolitisk Arkitektur

| Aspekt                | Microservices                      | Monolitisk Arkitektur         |
|-----------------------|-----------------------------------|--------------------------------|
| **Arkitektur**        | Opdelt i små, uafhængige tjenester | En samlet kodebase              |
| **Udviklingsteam**    | Små, tværfaglige teams             | Større, centraliseret team      |
| **Skalering**         | Uafhængig skalering af tjenester   | Skalering af hele applikationen |
| **Deployment**        | Uafhængig deployment               | Hele applikationen deployeres   |
| **Ressourceudnyttelse**| Effektiv udnyttelse                | Basere sig på applikationens behov |
| **Udviklingshastighed**| Hurtigere cyklus                   | Langsommere cyklus              |
| **Fleksibilitet**     | Teknologisk mangfoldighed          | Begrænset fleksibilitet         |
| **Vedligeholdelse**   | Nem vedligeholdelse                | Kompliceret vedligeholdelse     |
| **Testning**          | Uafhængig testning af tjenester    | Omfattende test af hele system  |
| **Infrastruktur**     | Mindre afhængig                    | Afhænger af specifik infrastruktur |

## 8. Hvordan flytte fra Monolitisk til Microservices?

![MONO to Micro.png](/img/user/Resource/98_Images/MONO%20to%20Micro.png)

- **Evaluér Monolit:** Forstå den nuværende applikation og identificer komponenter.
- **Definér Microservices:** Opdel monolit i forretningsfunktioner.
- **Strangler Pattern:** Gradvis udskiftning med microservices.
- **API Definition:** Definer klare API'er.
- **CI/CD Implementering:** Automatiser test og deployment.
- **Decentraliser Data:** Overgang til database-per-service.
- **Service Discovery:** Implementér mekanismer for serviceopdagelse.
- **Logging og Overvågning:** Implementér centraliseret overvågning.
- **Cross-Cutting Concerns:** Håndter fælles bekymringer som sikkerhed.
- **Iterativ Forbedring:** Kontinuerlig forbedring og udvidelse.

## 9. Service-Oriented Architecture (SOA) vs. Microservices

| Aspekt                 | SOA                                | Microservices                  |
|------------------------|------------------------------------|--------------------------------|
| **Omfang**             | Bredt sæt af arkitekturprincipper   | Små, uafhængige tjenester       |
| **Størrelse af Tjenester**| Store og omfattende tjenester     | Små og enkeltformålstjenester   |
| **Datastyring**        | Fælles datamodel og databaser       | Hver tjeneste har sin egen database |
| **Kommunikation**      | Standardprotokoller som SOAP        | Letvægtsprotokoller som REST    |
| **Teknologisk Mangfoldighed** | Standardiseret middleware      | Forskellige teknologier          |
| **Deployment**         | Ofte samlet                       | Uafhængig deployment             |
| **Skalering**          | Horisontal skalering af hele tjenester | Uafhængig skalering af tjenester |
| **Udviklingshastighed**| Langsommere cyklus                 | Hurtigere cyklus                |
| **Fleksibilitet**      | Fleksibel, men ændringer påvirker flere tjenester | Høj fleksibilitet med uafhængige tjenester |
| **Ressourceudnyttelse**| Kan være underudnyttet             | Effektiv ressourceudnyttelse    |
| **Afhængighedsstyring** | Afhænger af delte komponenter       | Håndtering af afhængigheder uafhængigt |
| **Adoptionssværhedsgrad**| Mere planlægning og organisatorisk ændring | Lettere at adoptere gradvist    |

## 10. Cloud-native Microservices

- **Forenklede Operationer:** Cloud-udbydere håndterer
infrastrukturvedligeholdelse og sikkerhed.
- **Omkostningseffektivitet:** Betal kun for de ressourcer, der bruges.
- **Fleksibilitet:** Hurtig tilpasning til ændringer og behov.

## 11. Rolle af Microservices i DevOps

- **CI/CD:** Automatisering af bygning, test og deployment.
- **Agil Udvikling:** Støtter hurtige iterationer og deployment.
- **Kontinuerlig Overvågning og Logging:** Overvåger helbred og præstation af tjenester.

## 12. Fordele ved Microservices Arkitektur

- **Modularitet og Decoupling:** Uafhængig udvikling og fejlisolering.
- **Skalérbarhed:** Granulær og elastisk skalering.
- **Teknologisk Mangfoldighed:** Frihed til at vælge teknologi.
- **Autonome Teams:** Mindre koordinationsbehov og hurtigere beslutningstagning.
- **Hurtigere Deployment:** Uafhængig udvikling og deployment.
- **Lettere Vedligeholdelse:** Isolerede kodebaser og rolling updates.

## 13. Udfordringer ved Microservices Arkitektur

- **Kompleksitet af Distribuerede Systemer:** Netværkslatens og datahåndtering.
- **Øget Udviklings- og Driftsomkostning:** Kræver ekstra indsats til administration.
- **Kommunikationsomkostninger:** Øget latency og kompleksitet.
- **Datakonsistens og Transaktionsstyring:** Vanskeligheder med distribuerede transaktioner.
- **Deployering og Orkestrering:** Kræver avanceret værktøjer og processer.

## 14. Ressourcer

- **Bøger:**
  - [*Microservices Patterns: With examples in Java*](https://microservices.io/book)
  af Chris Richardson
  - [*Building Microservices*](https://samnewman.io/books/building_microservices_2nd_edition/)
  af Sam Newman
  - [*Microservices in Action*](https://www.manning.com/books/microservices-in-action)
  af Morgan Bruce og Paulo A. Pereira

- **Online Kurser:**
  - Coursera: *Microservices Fundamentals* af University of Alberta
  - Udacity: *Microservices Architectures* af Google

- **Værktøjer:**
  - [Docker](https://www.docker.com/)
  - [Kubernetes](https://kubernetes.io/)
  - [Spring Boot](https://spring.io/projects/spring-boot) (Java)
  - [ASP.NET Core](https://dotnet.microsoft.com/en-us/learn/aspnet/what-is-aspnet-core)

- **Artikler og Blogs:**
  - [Martin Fowler: *Microservices*](https://martinfowler.com/microservices/)
  - [ThoughtWorks: *Microservices at Scale*](https://www.thoughtworks.com/insights/blog/microservices/scaling-microservices-gRPC-part-one)

## 15. Glossar

- **API Gateway:** En enhed der styrer trafik og ruter anmodninger.
- **Containerization:** Isolering af applikationer i containere for enklere deployment.
- **Service Discovery:** Metode til at finde og kommunikere med tjenester.
- **Event Sourcing:** Teknik til at gemme ændringer som hændelser.
- **Load Balancer:** Fordeler trafik mellem servere for at optimere ydeevne.

---
