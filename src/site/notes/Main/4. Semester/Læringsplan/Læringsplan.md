---
{"dg-publish":true,"permalink":"/main/4-semester/laeringsplan/laeringsplan/","title":"Læringsplan","tags":["læringsmål","systemudvikling","projektarbejde","programmering"],"created":"2024-09-20T11:50:02.756+02:00"}
---


## Om udformningen af læringsplanen

Følgende læringsplan er udarbejdet i  starten af semesteret, for at skabe et
overblik over de emner som er relevante for semesterprojektet, og opfylde de
[[Main/4. Semester/Læringsmål/Læringsmål fra studiet\|Læringsmål fra studiet]], som er sat for semesteret af underviserne.
Men også de personlig mål som jeg selv har sat for [[Main/4. Semester/Læringsmål/Microservices læringsmål\|Microservices læringsmål]] og
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål\|It-Sikkerhedslæringsmål]].

Det store mål for mig i dette semester er at få en dybere forståelse for
hvordan man laver **Microservices**.

Med udgangspunkt i dette [[Main/Noter/Emner/Mindmap\|Mindmap]] og [[Main/Noter/Systemudvikling/Smart_Mål\|smart mål]] har jeg udarbejdet
følgende læringsplan:

Nedenfor ses den læringsplan som jeg har udarbejdet for 4. Semester.

## Læringsplan

### **Uge**: [[Main/4. Semester/Læringsplan/33_34\|33 - 34]]

#### Grundlæggende Research

**Fokus**: Backend, IT-Sikkerhed og grundlæggende forståelse af microservices.
At finde ukendte og ukendte ukendte.

##### Blog opslag i denne periode

[[Main/4. Semester/Blog/2024-08-13\|2024-08-13]], [[Main/4. Semester/Blog/2024-08-14\|2024-08-14]], [[Main/4. Semester/Blog/2024-08-15\|2024-08-15]], [[Main/4. Semester/Blog/2024-08-16\|2024-08-16]],
[[Main/4. Semester/Blog/2024-08-19\|2024-08-19]], [[Main/4. Semester/Blog/2024-08-20\|2024-08-20]], [[Main/4. Semester/Blog/2024-08-21\|2024-08-21]],
[[Main/4. Semester/Blog/2024-08-22\|2024-08-22]], [[Main/4. Semester/Blog/2024-08-23\|2024-08-23]]

---

### **Uge**: [[Main/4. Semester/Læringsplan/35_36\|35 - 36]]

- Introduktion til Microservices: Forstå grundprincipperne og fordelene ved
microservices.
- Service-Oriented Architecture (SOA): Undersøg SOAP, WSDL, og hvordan
SOA adskiller sig fra microservices.
- Opgave: Design en simpel microservices-arkitektur og dokumenter forskellene
mellem microservices og SOA.

#### Fine-grained vs. Coarse-grained Microservices

- Fine-grained vs. Coarse-grained: Læs om de to tilgange og deres implikationer
på design.
- Event-Based Communication: Forstå hvordan event-baseret kommunikation
fungerer, og lær om messaging-systemer som RabbitMQ og Kafka.
- Opgave: Implementér en simpel event-baseret kommunikation ved hjælp af
RabbitMQ eller Kafka.

##### Blog opslag i denne periode, 35-36

[[Main/4. Semester/Blog/2024-08-26\|2024-08-26]], [[Main/4. Semester/Blog/2024-08-28\|2024-08-28]], [[Main/4. Semester/Blog/2024-09-02\|2024-09-02]], [[Main/4. Semester/Blog/2024-09-06\|2024-09-06]]

---

### **Uge**: [[Main/4. Semester/Læringsplan/37_38\|37 - 38]]

#### Sikkerhed i Database via MongoDB

- **Brugerautentifikation og Autorisation**:
  Læs om MongoDB's rollebaserede adgangskontrol (RBAC), og hvordan du opsætter
brugere med forskellige rettigheder. Undersøg, hvordan du opretter sikre
roller og begrænser adgang til bestemte operationer.

- **Kryptering**:
  Udforsk, hvordan MongoDB understøtter kryptering, både af data i transit
(SSL/TLS) og data i hvile (encrypted storage engines). Læs om
sikkerhedspraksis for krypteringsnøgler og nøglehåndtering.

- **Netværkssikkerhed**:
  Forstå, hvordan man sikrer MongoDB-netværk ved hjælp af firewalls,
IP-whitelisting, og VPN’er. Lær om vigtigheden af at isolere databaser
på private netværk og anvende VPN'er for adgang.

- **Sårbarheder og Overvågning**:
  Udforsk MongoDB’s indbyggede værktøjer til overvågning og logning af
sikkerhedshændelser. Læs om fælles sikkerhedssårbarheder og best practices
for at overvåge og reagere på sikkerhedshændelser.

- **Opgave**:
  Konfigurer en MongoDB-database med korrekt adgangskontrol, kryptering,
og netværkssikkerhed, og dokumenter de trin, der sikrer databasen mod
eksterne trusler.

#### Blog opslag i denne periode, 37-38

[[Main/4. Semester/Blog/2024-09-13\|2024-09-13]] [[Main/4. Semester/Blog/2024-09-20\|2024-09-20]]

### **Uge**: 39 - 40

#### Reverse Proxy / API Gateway

- **Introduktion til API Gateway**:
  Læs om, hvad en API Gateway er, og hvordan den adskiller sig fra en
traditionel reverse proxy. Udforsk dens rolle i en microservice-arkitektur.

- **Fordele ved API Gateways**:
  Undersøg de forskellige fordele ved at bruge en API Gateway, såsom
centraliseret adgangskontrol, load balancing, caching, rate limiting og sikkerhed.

- **Sammenligning af API Gateways**:
  Gennemgå og sammenlign populære API Gateways såsom Ocelot, YARP og Kong.
Undersøg, hvornår man bør vælge en løsning frem for en anden baseret på behov.

- **Implementering af API Gateway**:
  Lær, hvordan du opsætter en API Gateway ved hjælp af YARP i en .NET
Core-applikation. Forbind den med forskellige microservices (f.eks. Player og
Zone service).

- **Sikkerhed i API Gateways**:
  Udforsk, hvordan API Gateways kan bruges til at forbedre sikkerhed, herunder
brugen af OAuth2 til autentifikation, IP-whitelisting og rate limiting for at
beskytte mod angreb.

- **Overvågning og Logning**:
  Læs om vigtigheden af centraliseret logning og overvågning via API Gateways,
og hvordan de kan integreres med overvågningsværktøjer.

- **CI/CD for API Gateways**:
  Lær, hvordan du automatiserer deployment af API Gateways ved hjælp af GitHub
Actions, og hvordan du sikrer, at gateways opdateres ved pull requests og releases.

- **Opgave**:
  Implementer en API Gateway med YARP, som håndterer dine Player og Zone services.
Tilføj funktioner som autentifikation med OAuth2, logning og rate limiting.
Dokumentér opsætningen og deployment-processen via GitHub Actions.
