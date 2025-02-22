---
{"dg-publish":true,"permalink":"/main/noter/vita/improper-inventory-management/","created":"2024-11-11T09:10:59.182+01:00"}
---

![Improper Inventory Management.png](/img/user/Resource/98_Images/Improper%20Inventory%20Management.png)
> [!Note]- Opsummering af IIM
> **API'er har ofte flere endepunkter** end traditionelle webapplikationer, hvilket gør korrekt og opdateret dokumentation særligt vigtig. En ordentlig opgørelse over hosts og implementerede API-versioner er også vigtig for at minimere problemer som forældede API-versioner og eksponerede debug-endepunkter.

For at løse sårbarheder med **Improper Inventory Management** kan man:
1. Inventory and Documentation of API Host
2. Integrerede Tjenester og Datainventar
3. Begræns Tilgængeligheden af Dokumentation
4. Undgå Brug af Produktionsdata i Testmiljøer

## Inventory og Documentation af API Hosts

For at sikre overblik over, hvor API’er kører, og hvem der har adgang til dem, **bør alle API-værter "inventorieres" og dokumenteres**. Fokus er især på miljøet (produktions-, staging- eller testmiljø), adgangsregler og versionskontrol.

**Kodeeksempel:**

```yaml
# Eksempel på OpenAPI-dokumentation 
servers: 
	- url: https://api.example.com 
	description: Produktionsmiljø
	- url: https://staging.api.example.com 
	description: Staging-miljø 
components: 
	securitySchemes: 
		apiKeyAuth: 
			type: apiKey 
			in: header 
			name: X-API-KEY
```
#### Brug i en microservice-arkitektur
Hjælper med at definere og begrænse adgangsrettigheder for forskellige API-miljøer og understøtter versionskontrol i større API-infrastrukturer.

---

## Integrerede Tjenester og Datainventar
**Dokumentation af alle integrerede tjenester**, deres rolle i systemet, og hvilken type data, der udveksles, kan minimere risici ved dataflow til tredjepartsintegrationer.

**Kodeeksempel:**

```yaml
# Eksempel på CI/CD pipeline-dokumentation 
- name: Inventory Service   
	dataFlow:     
	- service: PaymentGateway       
	description: Behandler betalinger       
	dataType: finansielle data     
	- service: AnalyticsService       
	description: Indsamler brugeraktivitet       
	dataType: anonymiserede data
```
#### Brug i en microservice-arkitektur
Sikrer overblik over dataflows på tværs af microservices og tredjepartstjenester, hvilket er essentielt i tilfælde af datasikkerhedsbrud.

---

## Begræns Tilgængeligheden af Dokumentation
**Kun autoriserede brugere bør have adgang til API-dokumentation**, hvilket kan sikres gennem adgangskontrol og beskyttede endpoints.

```yaml

# Begrænsning af dokumentation i en CI/CD-pipeline
- name: Deploy API Documentation   
  if: contains(github.actor, 'authorized-user')   
  run: |
  deploy_docs

```
#### Brug i en microservice-arkitektur
Denne praksis forhindrer, at uautoriserede brugere får adgang til API-dokumentation og potentielt afslører sensitive endpoints eller datatilgange.

---

## Undgå Brug af Produktionsdata i Testmiljøer
Hvis produktionsdata er nødvendigt i testmiljøer, bør det beskyttes med samme sikkerhedsniveau som i produktionen for at undgå datalækager.

**Kodeeksempel:**

```csharp

Copy code

// Eksempel på data-sanitizing før brug i ikke-produktionsmiljø 
var testData = productionData.Clone().SanitizeSensitiveInformation();
```
#### Brug i en microservice-arkitektur
Forhindrer utilsigtet eksponering af følsomme data i test- eller staging-miljøer og sikrer, at alle miljøer overholder sikkerhedsstandarder.