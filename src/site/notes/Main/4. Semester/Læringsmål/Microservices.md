---
{"dg-publish":true,"permalink":"/main/4-semester/laeringsmal/microservices/","title":"Microservices Læringmål","created":"2024-08-19T13:03:38.000+02:00"}
---

## Viden

- Jeg har viden om, hvordan microservices fungerer, og deres fordele og ulemper
sammenlignet med monolitiske applikationer.
- Jeg har viden om forskellige microservice-arkitekturer, såsom API Gateway,
Event-Driven, og Service Mesh.
- Jeg har viden om forskellige microservice-mønstre, herunder Saga-mønsteret,
Circuit Breaker, og CQRS.
- Jeg har viden om forskellige kommunikationsmetoder mellem microservices,
såsom REST API'er, gRPC, og Message Brokers (f.eks. Kafka, RabbitMQ).

## Færdigheder

- Jeg kan implementere et microservice-mønster, som f.eks. Saga-mønsteret, for
at håndtere distribuerede transaktioner.
- Jeg kan designe og implementere en microservice-arkitektur, der inkluderer
sikkerhedsmekanismer som API Gateways og Service Mesh til at styre trafik og
beskytte mod trusler.
- Jeg kan sammenligne forskellige microservice-arkitekturer med monolitiske
arkitekturer og evaluere deres sikkerhedsmæssige fordele og udfordringer.

## Kompetencer

- Jeg kan skabe en sikker microservice-løsning.
- Jeg kan integrere sikkerhedsprincipper i designet af microservices, herunder
brug af TLS, OAuth2, og rate limiting for at beskytte mod trusler som
API-misbrug og DDoS-angreb.
- Jeg kan udvikle og dokumentere en sikkerhedsstrategi for microservices, der
inkluderer trusselsmodelering, logging, overvågning, og kontinuerlig
sikkerhedsovervågning for at opdage og reagere på sikkerhedshændelser.

## Udstedelse af Identitetstokens med OpenID Connect (OIDC)

OAuth 2.0 fokuserer primært på autorisation, men mangler retningslinjer for
brugeridentifikation og autentifikation. OpenID Connect (OIDC) blev
introduceret for at udfylde dette hul ved at tilføje et identitetslag
ovenpå OAuth 2.0.

## OpenID Connect (OIDC)

OpenID Connect er en udvidelse af OAuth 2.0, der tilføjer funktioner til
autentifikation og levering af brugerprofilinformation. Her er, hvordan
OIDC fungerer:

### Nøglekomponenter

- **Identitetsudbyder (IDP):** En autorisationsserver, der følger
OIDC-standarder og tilbyder autentifikation og brugerinformation.
- **ID Token:** En struktureret token, der indeholder standardoplysninger om
autentifikationseventet og brugerens identitet i JWT-format.
- **User Info Endpoint:** Et endpoint, hvor klienten kan sende en adgangstoken
for at få identitetsoplysninger om ressourceejeren.

### OIDC Flow

1. **Autentifikationsanmodning**
   - Klienten tilføjer `openid` scope til anmodningen for at anmode om
   autentifikation.
   - Resursejeren bliver omdirigeret til identitetsudbyderen for at
   autentificere og give samtykke.

2. **Autorisation og Token Udstedelse**
   - Efter autentifikation returnerer identitetsudbyderen en autorisationskode
   til klientens redirect URI.
   - Klienten udveksler autorisationskoden med identitetsudbyderen for at få en
   adgangstoken og en ID token.

3. **ID Token**
   - ID tokenet, der er i JWT-format, indeholder standardkrav som
   autentifikationsbegivenhed, tokenudsteder, brugeroplysninger og
   tokenudløb.
   - ID tokenet er beskyttet af en kryptografisk signatur for at forhindre
   ændringer.

4. **Brug af Adgangstoken**
   - For at få yderligere brugeroplysninger kan adgangstokenet sendes til User
   Info Endpoint for at modtage krav med information om slutbrugeren.

### Eksempel på Anvendelse

- **OpenID Connect Playground:** Auth0’s OpenID Connect Playground kan bruges
til at gennemgå hver anmodning i autentifikationsflowet.
- **Autentifikationsanmodning:** Når autentifikationsanmodningen konstrueres,
skal `openid` scope inkluderes. Det tillader identitetsudbyderen at
autentificere slutbrugeren og tilbyde ekstra scopes som `profile`, `email`,
`phone` og `address`.

### Flow Beskrivelse

- Klienten sender en autentifikationsanmodning til autorisationsendpointet.
- Slutbrugeren bliver bedt om at logge ind og give samtykke.
- En kode returneres til klienten, som derefter udveksles for adgangstoken og
ID token.

## Implementering

ID tokens skal kun bruges af klienten og bør ikke bruges til API-adgang.
For at identificere slutbrugeren i en microservice skal adgangstokenet sendes
til identitetsudbyderens User Info Endpoint for at få oplysninger om slutbrugeren.

Denne tilgang sikrer en sikker og standardiseret metode til
brugerautentifikation og profilhåndtering i moderne applikationer.
