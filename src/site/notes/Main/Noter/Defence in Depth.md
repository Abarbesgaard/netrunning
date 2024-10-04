---
{"dg-publish":true,"permalink":"/main/noter/defence-in-depth/","created":"2024-10-04T08:30:04.395+02:00"}
---

**"Defence in depth"** er en sikkerhedsstrategi, der fokuserer på at implementere flere lag af beskyttelse for at sikre systemer og data. 

Ideen er, at hvis én sikkerhedsforanstaltning svigter, vil de øvrige lag stadig give beskyttelse mod angreb. 

Denne tilgang omfatter forskellige sikkerhedsniveauer, såsom netværkssikkerhed, adgangskontrol, kryptering, fysisk sikkerhed og brugersikkerhed. 

Ved at have flere lag kan organisationer bedre beskytte sig mod både interne og eksterne trusler og minimere risikoen for databrud.
## Med udgangspunkt i Mikroservices

Mikroservices er en softwareudviklingsmetode, hvor en applikation er struktureret som en samling af løst koblede tjenester. Hver tjeneste er designet til at udføre en specifik forretningsfunktion og kan udvikles, implementeres og skaleres uafhængigt. 
De kommunikerer med hinanden via veldefinerede API'er (Application Programming Interfaces), typisk ved hjælp af letvægtsprotokoller som HTTP eller #MessageBrokers.

## Sikkerhed i Microservice Arkitektur

At sikre microservices kræver en omfattende tilgang, der adresserer forskellige aspekter af sikkerhed gennem hele udviklings-, implementerings- og driftslivscyklussen.

## Nøgleområder for Sikkerhed

1. **Autentifikation og Autorisation**: Implementer #OAuth til #Autorisation og #OpenID-Connect til #Autentifikation for at sikre brugeradgang.
2. **API Gateway**: Brug en #APIGateway til at håndtere almindelige sikkerhedsproblemer som #Autentifikation og #RateLimiting.
3. **Service Mesh**: Implementer en #ServiceMesh (f.eks. Istio) til at styre kommunikation mellem tjenester sikkert.
4. **Netværkssikkerhed**: Segmentér netværket for at isolere Microservices og reducere muligheden for angreb.
5. **Databeskyttelse**: Krypter data både under transport (ved hjælp af TLS/mTLS) og i hvile.
6. **Logging og Overvågning**: Implementer centraliseret logging for at samle logs fra alle microservices.

## Udfordringer ved Sikkerhed i microservices

Microservices introducerer også specifikke sikkerhedsudfordringer:

- **Øget Angrebsoverflade**: Hver Microservice har sine egne eksponerede endpoints.
- **Sikker Kommunikation mellem Tjenester**: Det er kritisk at sikre kommunikation mellem tjenester i et distribueret miljø.
- **Identitets- og Adgangsstyring**: At administrere identiteter på tværs af mange Microservices kan føre til inkonsekvente adgangskontroller.

## Bedste Praksis for Sikkerhed i Microservices

1. **Defence in Depth**: Implementér flere lag af sikkerhed på tværs af forskellige tjenester.
2. **Token Management**: Brug JSON Web Tokens ( #JWT ) til sikkert at transmittere information mellem parter.
3. **API Gateways**: Beskyt tjenester ved hjælp af tokenautentifikation via #APIGateways.
4. **Distribueret Logging**: Anvend distribueret logging til at identificere fejl og sikkerhedsproblemer.

## Værktøjer til Sikkerhed i Microservices

Der findes flere værktøjer til sikring af Microservices:

- **Service Meshes**: Istio, Linkerd
- **API Gateways**: Kong, Nginx
- **Autentifikationsløsninger**: Keycloak
- **Overvågningsværktøjer**: Prometheus, Grafana
- **Sikkerhedstestværktøjer**: OWASP ZAP, Burp Suite

## Konklusion

Microservices arkitektur tilbyder betydelige fordele i forhold til traditionel monolitisk arkitektur ved at forbedre skalerbarhed, fleksibilitet og modstandsdygtighed. 

Dog kræver det også nøje overvejelse af sikkerhedsforanstaltninger gennem hele udviklingsprocessen for effektivt at håndtere de risici, der er forbundet med distribuerede systemer.
### Links til yderligere læsning:

1. [Microservices security - Challenges and best practices](https://www.solo.io/topics/microservices/microservices-security/) 
2. [Microservices Security: Best Practices, Strategies, and Defense Against Cyber Threats](https://www.linkedin.com/pulse/microservices-security-best-practices-strategies-defense-kumar-palxf/)