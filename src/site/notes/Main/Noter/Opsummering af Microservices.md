---
{"dg-publish":true,"permalink":"/main/noter/opsummering-af-microservices/","created":"2024-11-13T07:56:06.862+01:00"}
---

Gennem mit fokus på [[Main/Noter/Emner/Backend/Microservice\|Microservice]] og især på [[Main/Noter/Programmering/Message Brokers\|message brokers]] , som [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], har jeg opnået både en dybere teoretisk forståelse og praktisk færdighed i at bygge [[Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]]. 
Mit læringsarbejde har kredset om at implementere en fleksibel og skalerbar [[Main/Noter/Emner/Backend/Microservice\|microservice-arkitektur]], og jeg har gennem [[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] (*oplevelse*, *refleksion*, *abstraktion* og *eksperimentering*) fået skabt et solidt videns fundament og kompetencer til fremtidige projekter.

## Læringsmål

### §1 og §2: Viden om Microservices vs. Monolitiske Applikationer

Jeg har tilegnet mig en grundlæggende forståelse af, hvordan [[Main/Noter/Emner/Backend/Microservice\|microservices]] adskiller sig fra [[Main/Noter/Programmering/Monolitiske Applikationer\|monolitiske applikationer]], både på strukturelt og organisatorisk niveau. 

*Fordele* ved [[Main/Noter/Emner/Backend/Microservice\|microservices]], såsom *modularitet* og *skalerbarhed*, står klart, men også *ulemper* som den øgede kompleksitet i distribution og opsætning af kommunikation mellem [[Main/Noter/Emner/Backend/Microservice\|services]].

> [!quote] James Lewis
> Microservices **køber** dig flere muligheder

### §3: Kommunikation mellem Microservices

*Kommunikation mellem microservices* er en afgørende faktor i opbygning af et distribueret system, og her har jeg arbejdet med REST [[Main/Noter/Programmering/API\|API’er]], og [[Main/Noter/Programmering/Message Brokers\|message brokers]]. 

[[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] har været **mit primære fokus**, og udfyldt rollen so  [[Main/Noter/Programmering/Message Brokers\|message brokers]], hvilket har åbnet mulighederne for asynkron kommunikation og bidraget til at implementere [[Main/Noter/Programmering/Eventual Consistency\|Eventual Consistency]].

### §4: Eventual Consistency med Message Brokers

Ved at arbejde med [[Main/Noter/Programmering/Eventual Consistency\|Eventual Consistency]] og [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], har jeg opnået en praktisk erfaring i at håndtere distribuerede transaktioner, hvor [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ’s]] event-drevne model muliggør effektiv håndtering af data uden risiko for synkroniseringsproblemer. 

Dette opfylder målet om at skabe dataanomalier på et minimum og at sikre stabil drift.

### §5: API Gateway med Autentifikation og Autorisation

Implementeringen af en [[Main/Noter/Programmering/API-Gateway\|API Gateway]], der håndterer autentifikation og autorisation via [[Main/Noter/Programmering/JWT token\|JWT]], har styrket applikationens sikkerhed og isoleret identitetsstyringen. 

Jeg har indset betydningen af sikker og konsistent brugerhåndtering, hvilket har givet mig færdigheder, som kan overføres til fremtidige applikationer.

### §6: Evaluering af Arkitekturer

Med min forståelse for [[Main/Noter/Emner/Backend/Microservice\|microservices]] og [[Main/Noter/Programmering/Monolitiske Applikationer\|monolitiske applikationers]] sikkerhed, skalerbarhed og vedligeholdelse, kan jeg nu evaluere og rådgive om arkitekturvalg i forskellige projektstørrelser. 

Min erfaring gør det muligt, for mig, at anbefale den optimale løsning afhængigt af projektets behov og ressourcer.

### §7: Robust Design og Message Brokers

[[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] har været et væsentligt element i design og implementering af [[Main/Noter/Emner/Backend/Microservice\|microservices]] med høj tilgængelighed. Ved at anvende en [[Main/Noter/Programmering/Message Brokers\|message broker]] har jeg sikret, at systemets komponenter kan kommunikere stabilt, hvilket skaber en robust arkitektur. 

Jeg har udviklet løsninger, der udnytter [[Main/Noter/Programmering/Message Brokers\|message brokers]] til at sikre fault tolerance og datahåndtering i realtid.

### §8 og §9: Optimering og Skalerbarhed

Jeg har opnået færdigheder i at optimere backend-performance, og jeg kan nu opsætte en skalerbar og vedligeholdelsesvenlig backend med [[Main/Noter/Programmering/Docker\|containerteknologier]] og CI/CD-principper. 

Dette sikrer, at applikationen kan håndtere stigende krav uden at kompromittere ydeevne og stabilitet.

## Læringsmetode: Kolbs Læringscirkel

[[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] har været central i min læringsproces. Ved at starte med praktiske oplevelser i opsætningen af [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], reflektere over de udfordringer, jeg har mødt, og dernæst abstrahere fra erfaringerne til teoretisk forståelse, har jeg opbygget en konkret viden. 

Sidst har eksperimentering og praktisk anvendelse af disse erfaringer hjulpet mig til at styrke mine færdigheder og udvikle en intuitiv forståelse af [[Main/Noter/Emner/Backend/Microservice\|microservices]], som jeg nu kan anvende på fremtidige projekter.

## Opsummering

I arbejdet med microservices har jeg fået en omfattende viden og praktisk erfaring, især med [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] som [[Main/Noter/Programmering/Message Brokers\|message broker]]. 

Mine færdigheder er styrket gennem aktiv anvendelse af [[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]], og jeg er nu bedre rustet til at bygge og optimere [[Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]], der er både skalerbare og robuste.

### Sådan implementerede jeg RabbitMQ
jeg har lavet et lille gennemgang af hvordan jeg fik implemtereret [[Main/Noter/Programmering/RabbitMQ\|RabbitMQ]]i en [[Main/Noter/Emner/Backend/Microservice\|microservice]].

[[Main/Noter/Programmering/Implementering af RabbitMQ\|Den kan du finde her]]