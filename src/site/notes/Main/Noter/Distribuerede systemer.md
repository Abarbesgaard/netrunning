---
{"dg-publish":true,"permalink":"/main/noter/distribuerede-systemer/","created":"2024-11-15T09:27:37.059+01:00"}
---

> [!important] Opsummering 
> Distributed systems er *en samling af computerprogrammer* eller komponenter, der *arbejder sammen på tværs af flere separate computere* eller enheder for at opnå et fælles mål. 


![Pasted image 20241115093329.png](/img/user/98_Images/Pasted%20image%2020241115093329.png)
*Billede fra [Atlassian*](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture)
## Kilder:
1. [Atlassian - What is a distributed system](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture)
2. [Splunk - Distributed Systems Explained](https://www.splunk.com/en_us/blog/learn/distributed-systems.html)
3. [Wiki - Distributed Computing](https://en.wikipedia.org/wiki/Distributed_computing)
## Grundlæggende karakteristika

- **Ressourcedeling**: Distributed systems kan dele hardware, software eller data på tværs af netværket [1](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture).
- **Samtidig behandling**: Flere maskiner kan udføre samme funktion samtidigt [1](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture).
- **Skalerbarhed**: Beregnings- og behandlingskapaciteten kan skaleres op efter behov ved at tilføje flere maskiner [1](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture).
- **Fejltolerance**: Hvis en enkelt komponent fejler, fortsætter resten af systemet med at fungere [3](https://en.wikipedia.org/wiki/Distributed_system).

## Arkitektur og komponenter

Distributed systems består typisk af:

- **Noder**: Separate computere eller enheder i netværket.
- **Kommunikationsnetværk**: Tillader noderne at udveksle beskeder og koordinere deres handlinger [3](https://en.wikipedia.org/wiki/Distributed_system).
- **Middleware**: Software, der faciliterer kommunikation og dataadministration mellem noderne.

## Fordele ved distributed systems

1. **Øget ydeevne**: Ved at fordele arbejdsbyrden kan systemet håndtere større opgaver mere effektivt [2](https://www.splunk.com/en_us/blog/learn/distributed-systems.html).
2. **Pålidelighed**: Redundans i systemet reducerer risikoen for komplet systemnedbrud [2](https://www.splunk.com/en_us/blog/learn/distributed-systems.html).
3. **Fleksibilitet**: Systemet kan nemt udvides eller opgraderes ved at tilføje nye noder [2](https://www.splunk.com/en_us/blog/learn/distributed-systems.html).
4. **Geografisk distribution**: Muliggør samarbejde og ressourcedeling på tværs af forskellige lokationer[1](https://www.atlassian.com/microservices/microservices-architecture/distributed-architecture).

## Udfordringer

- **Kompleksitet**: Distributed systems er ofte mere komplekse at designe, implementere og vedligeholde [3](https://en.wikipedia.org/wiki/Distributed_system).
- **Konsistens**: At sikre datakonsekvens på tværs af alle noder kan være udfordrende.
- **Netværksproblemer**: Latens og netværksfejl kan påvirke systemets ydeevne og pålidelighed.

## Anvendelsesområder

Distributed systems finder anvendelse i mange områder, herunder:
- Cloud computing
- Databaser (f.eks. distribuerede databaser)
- [[Main/Noter/Emner/Backend/Microservice\|Mikroservicearkitekturer]]
- Internet of Things (IoT)

Distributed systems er grundlaget for mange moderne teknologier og tjenester, der kræver høj ydeevne, skalerbarhed og pålidelighed.
