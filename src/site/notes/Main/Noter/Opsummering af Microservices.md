---
{"dg-publish":true,"permalink":"/main/noter/opsummering-af-microservices/","created":"2024-11-13T07:56:06.862+01:00"}
---

Igennem mit fokus på **microservices** og især på message brokers, som RabbitMQ, har jeg opnået både en dybere teoretisk forståelse og praktisk færdighed i at bygge distribuerede systemer. 
Mit læringsarbejde har kredset om at implementere en fleksibel og skalerbar microservice-arkitektur, og jeg har gennem *Kolbs læringscirkel* (oplevelse, refleksion, abstraktion og eksperimentering) fået skabt en solid viden og kompetencer til fremtidige projekter.

## Læringsmål og opnåelser

### §1 og §2: Viden om Microservices vs. Monolitiske Applikationer

Jeg har tilegnet mig en grundlæggende forståelse af, hvordan microservices adskiller sig fra monolitiske applikationer, både på strukturelt og organisatorisk niveau. 

*Fordele* ved microservices, såsom modularitet og skalerbarhed, står klart, men også *ulemper* som den øgede kompleksitet i distribution og opsætning af kommunikation mellem tjenester.

> [!Important] citat
> Microservices **køber** dig flere muligheder

### §3: Kommunikation mellem Microservices

*Kommunikation mellem microservices* er en afgørende faktor i opbygning af et distribueret system, og her har jeg arbejdet med REST [[Main/Noter/API\|API’er]], og [[Main/Noter/Message Brokers\|message brokers]]. 

[[Main/Noter/RabbitMQ\|RabbitMQ]] har været mit primære fokus som  [[Main/Noter/Message Brokers\|message brokers]], hvilket har åbnet mulighederne for asynkron kommunikation og bidraget til at implementere *Eventual Consistency*.

### §4: Eventual Consistency med Message Brokers

Ved at arbejde med *Eventual Consistency* og [[Main/Noter/RabbitMQ\|RabbitMQ]], har jeg opnået en praktisk erfaring i at håndtere distribuerede transaktioner, hvor [[Main/Noter/RabbitMQ\|RabbitMQ’s]] event-drevne model muliggør effektiv håndtering af data uden risiko for synkroniseringsproblemer. 

Dette opfylder målet om at skabe dataanomalier på et minimum og at sikre stabil drift.

### §5: API Gateway med Autentifikation og Autorisation

Implementeringen af en [[Main/Noter/API-Gateway\|API Gateway]], der håndterer autentifikation og autorisation via [[Main/Noter/JWT token\|JWT]], har styrket applikationens sikkerhed og isoleret identitetsstyringen. 

Jeg har indset betydningen af sikker og konsistent brugerhåndtering, hvilket har givet mig færdigheder, som kan overføres til fremtidige applikationer.

### §6: Evaluering af Arkitekturer

Med min forståelse for microservices og monolitiske applikationers sikkerhed, skalerbarhed og vedligeholdelse, kan jeg nu evaluere og rådgive om arkitekturvalg i forskellige projektstørrelser. 

Min erfaring gør det muligt at anbefale den optimale løsning afhængigt af projektets behov og ressourcer.

### §7: Robust Design og Message Brokers

[[Main/Noter/RabbitMQ\|RabbitMQ]] har været et væsentligt element i design og implementering af microservices med høj tilgængelighed. Ved at anvende en [[Main/Noter/Message Brokers\|message broker]] har jeg sikret, at systemets komponenter kan kommunikere stabilt, hvilket skaber en robust arkitektur. 

Jeg har udviklet løsninger, der udnytter [[Main/Noter/Message Brokers\|message brokers]] til at sikre fault tolerance og datahåndtering i realtid.

### §8 og §9: Optimering og Skalerbarhed

Jeg har opnået færdigheder i at optimere backend-performance gennem caching-strategier og korrekt datalagring, og jeg kan nu opsætte en skalerbar og vedligeholdelsesvenlig backend med containerteknologier og CI/CD-principper. 

Dette sikrer, at applikationen kan håndtere stigende krav uden at kompromittere ydeevne og stabilitet.

## Læringsmetode: Kolbs Læringscirkel

[[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] har været central i min læringsproces. Ved at starte med praktiske oplevelser i opsætningen af [[Main/Noter/RabbitMQ\|RabbitMQ]], reflektere over de udfordringer, jeg har mødt, og dernæst abstrahere fra erfaringerne til teoretisk forståelse, har jeg opbygget en konkret viden. 

Sidst har eksperimentering og praktisk anvendelse af disse erfaringer hjulpet mig til at styrke mine færdigheder og udvikle en intuitiv forståelse af microservices, som jeg nu kan anvende på fremtidige projekter.

## Opsummering

I arbejdet med microservices har jeg fået en omfattende viden og praktisk erfaring, især med [[Main/Noter/RabbitMQ\|RabbitMQ]] som [[Main/Noter/Message Brokers\|message broker]]. 

Mine færdigheder er styrket gennem aktiv anvendelse af [[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]], og jeg er nu bedre rustet til at bygge og optimere distribuerede systemer, der er både skalerbare og robuste.