---
{"dg-publish":true,"permalink":"/main/noter/emner/backend/microservice/","title":"Microservice","hide":true,"tags":["Backend","Microservice","Projektarbejde"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-09-05T09:15:05.478+02:00"}
---



> [!important] hvad er microservices?
> En microservice er en arkitektonisk tilgang til softwareudvikling, hvor en applikation opbygges som en samling af små, uafhængige tjenester [1](https://azure.microsoft.com/da-dk/solutions/microservice-applications) [2](https://en.wikipedia.org/wiki/Microservices). 

![Microservice.png](/img/user/Main/Images/Microservice.png)

Disse tjenester er:

1. [[Main/Noter/Loose Coupling\|Løst koblede]] og fint granulerede
2. Kommunikerer via lette protokoller
3. Organiseret omkring forretningskapabiliteter
4. Uafhængigt udviklede og implementerede
5. Kan implementeres med forskellige programmeringssprog og teknologier

Microservices gør det muligt for teams at udvikle, implementere og skalere deres tjenester uafhængigt af hinanden [2](https://en.wikipedia.org/wiki/Microservices). Dette øger fleksibiliteten og reducerer kompleksiteten i kodebasen ved at mindske afhængigheder mellem komponenter [2](https://en.wikipedia.org/wiki/Microservices).

## Fordele ved microservices

- **Modulær struktur**: Gør applikationen lettere at forstå, udvikle og teste [2](https://en.wikipedia.org/wiki/Microservices).
- **Skalerbarhed**: Individuelle tjenester kan overvåges og skaleres uafhængigt [2](https://en.wikipedia.org/wiki/Microservices).
- **Teknologisk fleksibilitet**: Forskellige programmeringssprog og teknologier kan bruges til forskellige tjenester [1](https://azure.microsoft.com/da-dk/solutions/microservice-applications) [2](https://en.wikipedia.org/wiki/Microservices).
- **Hurtigere udvikling**: Muliggør hurtig, hyppig og pålidelig levering af store, komplekse applikationer [3](https://www.cegal.com/da/ordbog/microservices).
- **Nemmere vedligeholdelse**: Ændringer i én del af applikationen kræver kun genopbygning og genimplementering af den specifikke tjeneste [2](https://en.wikipedia.org/wiki/Microservices).

## Udfordringer

Implementering af **microservices** kræver omhyggelig planlægning og infrastruktur. Det indebærer:

- Behov for et robust infrastrukturelt fundament.
- Kompleks initial implementering sammenlignet med [[Main/Noter/Monolitiske Applikationer\|monolitiske systemer]].
- Nødvendigheden af at designe grænseflader omhyggeligt som API'er [2](https://en.wikipedia.org/wiki/Microservices).

![Pasted image 20241122082637.png](/img/user/Main/Images/Pasted%20image%2020241122082637.png)
*Billedet er fra [ByteByteGo](https://blog.bytebytego.com/p/a-crash-course-on-microservices-design)*

Microservices er særligt velegnede til virksomheder, der *kræver hyppige opdateringer* og *høj fleksibilitet* i deres softwarearkitektur, såsom [Netflix](https://www.netflix.com/dk-en/), der bruger over 1000 microservices i deres applikationsarkitektur [5](https://www.computerworld.dk/art/247872/microservices-naeste-boelge-inden-for-moderne-software-udvikling).

I forhold til dette er det vigtigt at minde sig selv om Conways lov:

> [!Quote] Melvin Conway
> Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure. [6](https://martinfowler.com/bliki/ConwaysLaw.html)

