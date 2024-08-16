---
{"dg-publish":true,"permalink":"/main/4-semester/litteratur/noter/what-are-microservices-ibm/","title":"What Are Microsevices - IBM","hide":true,"created":"2024-08-16T13:25:37.719+02:00"}
---

Troværdighed: 4/5
Relevans: 5/5

[[Main/4. Semester/Litteratur/LitteraturListe\|Gå til litteratur listen]]
[What are Microservices? - IBM](https://www.ibm.com/topics/microservices)

## Hvad er Microservices?

Microservices er en cloud-native arkitektur, hvor en enkelt applikation er
opdelt i mange små, løst koblede og uafhængigt implementerbare komponenter
eller tjenester. Hver microservice har sin egen teknologistak og kommunikerer
med andre tjenester via REST API'er, event-streaming og message brokers.

De organiseres ofte efter forretningsfunktioner, hvilket giver fleksibilitet
og muliggør, at teams kan bruge forskellige teknologier og sprog til
forskellige komponenter.

## Fordele ved microservices

Opdatering af kode er nemmere, og nye funktioner kan tilføjes uden at påvirke
hele applikationen.
Komponenter kan skaleres individuelt, hvilket reducerer omkostninger.
Organisationer kan oprette små, tværfunktionelle teams, hvilket fremmer agil udvikling.

## Udfordringer ved microservices

Øget kompleksitet i styringen af mange tjenester og afhængigheder.

Logging og overvågning bliver mere krævende.

Fejl i én tjeneste kan påvirke andre.

For at få succes med microservices er det nødvendigt med en DevOps-tilgang
samt passende værktøjer som containere (Docker), Kubernetes, API gateways
og message brokers.

Artiklen anbefaler ikke at begynde med microservices, men først overveje dem,
når kompleksiteten i en monolitisk applikation bliver uoverskuelig.

Desuden frarådes det at overkomplicere strukturen ved at have for mange eller for
små microservices.

Til sidst understreges vigtigheden af at undgå at kopiere avancerede løsninger
som Netflix, medmindre man har lignende behov og ressourcer.
