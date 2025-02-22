---
{"dg-publish":true,"permalink":"/publishing/main/noter/opsummering-af-microservices/","created":"2024-11-13T07:56:06.862+01:00"}
---

Gennem mit fokus på [[Publishing/Main/Noter/Emner/Backend/Microservice\|Microservice]] og især på [[Publishing/Main/Noter/Programmering/Message Brokers\|message brokers]] , som [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], har jeg opnået både en dybere teoretisk forståelse og praktisk færdighed i at bygge [[Publishing/Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]]. 
Mit læringsarbejde har kredset om at implementere en fleksibel og skalerbar [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservice-arkitektur]], og jeg har gennem [[Publishing/Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] (*oplevelse*, *refleksion*, *abstraktion* og *eksperimentering*) fået skabt et solidt videns fundament og kompetencer til fremtidige projekter.

## Læringsmål

### §1 og §2: Viden om Microservices vs. Monolitiske Applikationer

Jeg har tilegnet mig en grundlæggende forståelse af, hvordan [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]] adskiller sig fra [[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|monolitiske applikationer]], både på strukturelt og organisatorisk niveau. 

*Fordele* ved [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]], såsom *modularitet* og *skalerbarhed*, står klart, men også *ulemper* som den øgede kompleksitet i distribution og opsætning af kommunikation mellem [[Publishing/Main/Noter/Emner/Backend/Microservice\|services]].

> [!quote] James Lewis
> Microservices **køber** dig flere muligheder

### §3: Kommunikation mellem Microservices

*Kommunikation mellem microservices* er en afgørende faktor i opbygning af et distribueret system, og her har jeg arbejdet med REST [[Publishing/Main/Noter/Programmering/API\|API’er]], og [[Publishing/Main/Noter/Programmering/Message Brokers\|message brokers]]. 

[[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] har været **mit primære fokus**, og udfyldt rollen so  [[Publishing/Main/Noter/Programmering/Message Brokers\|message brokers]], hvilket har åbnet mulighederne for asynkron kommunikation og bidraget til at implementere [[Publishing/Main/Noter/Programmering/Eventual Consistency\|Eventual Consistency]].

### §4: Eventual Consistency med Message Brokers

Ved at arbejde med [[Publishing/Main/Noter/Programmering/Eventual Consistency\|Eventual Consistency]] og [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], har jeg opnået en praktisk erfaring i at håndtere distribuerede transaktioner, hvor [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ’s]] event-drevne model muliggør effektiv håndtering af data uden risiko for synkroniseringsproblemer. 

Dette opfylder målet om at skabe dataanomalier på et minimum og at sikre stabil drift.

### §5: API Gateway med Autentifikation og Autorisation

Implementeringen af en [[Publishing/Main/Noter/Programmering/API-Gateway\|API Gateway]], der håndterer autentifikation og autorisation via [[Publishing/Main/Noter/Programmering/JWT token\|JWT]], har styrket applikationens sikkerhed og isoleret identitetsstyringen. 

Jeg har indset betydningen af sikker og konsistent brugerhåndtering, hvilket har givet mig færdigheder, som kan overføres til fremtidige applikationer.

### §6: Evaluering af Arkitekturer

Med min forståelse for [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]] og [[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|monolitiske applikationers]] sikkerhed, skalerbarhed og vedligeholdelse, kan jeg nu evaluere og rådgive om arkitekturvalg i forskellige projektstørrelser. 

Min erfaring gør det muligt, for mig, at anbefale den optimale løsning afhængigt af projektets behov og ressourcer.

### §7: Robust Design og Message Brokers

[[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] har været et væsentligt element i design og implementering af [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]] med høj tilgængelighed. Ved at anvende en [[Publishing/Main/Noter/Programmering/Message Brokers\|message broker]] har jeg sikret, at systemets komponenter kan kommunikere stabilt, hvilket skaber en robust arkitektur. 

Jeg har udviklet løsninger, der udnytter [[Publishing/Main/Noter/Programmering/Message Brokers\|message brokers]] til at sikre fault tolerance og datahåndtering i realtid.

### §8 og §9: Optimering og Skalerbarhed

Jeg har opnået færdigheder i at optimere backend-performance, og jeg kan nu opsætte en skalerbar og vedligeholdelsesvenlig backend med [[Publishing/Main/Noter/Programmering/Docker\|containerteknologier]] og CI/CD-principper. 

Dette sikrer, at applikationen kan håndtere stigende krav uden at kompromittere ydeevne og stabilitet.

## Læringsmetode: Kolbs Læringscirkel

[[Publishing/Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] har været central i min læringsproces. Ved at starte med praktiske oplevelser i opsætningen af [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]], reflektere over de udfordringer, jeg har mødt, og dernæst abstrahere fra erfaringerne til teoretisk forståelse, har jeg opbygget en konkret viden. 

Sidst har eksperimentering og praktisk anvendelse af disse erfaringer hjulpet mig til at styrke mine færdigheder og udvikle en intuitiv forståelse af [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]], som jeg nu kan anvende på fremtidige projekter.

## Opsummering

I arbejdet med microservices har jeg fået en omfattende viden og praktisk erfaring, især med [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]] som [[Publishing/Main/Noter/Programmering/Message Brokers\|message broker]]. 

Mine færdigheder er styrket gennem aktiv anvendelse af [[Publishing/Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]], og jeg er nu bedre rustet til at bygge og optimere [[Publishing/Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]], der er både skalerbare og robuste.

### Sådan implementerede jeg RabbitMQ
jeg har lavet et lille gennemgang af hvordan jeg fik implemtereret [[Publishing/Main/Noter/Programmering/RabbitMQ\|RabbitMQ]]i en [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservice]].

[[Publishing/Main/Noter/Programmering/Implementering af RabbitMQ\|Den kan du finde her]]