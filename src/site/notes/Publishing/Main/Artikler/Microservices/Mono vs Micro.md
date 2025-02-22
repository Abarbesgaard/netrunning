---
{"dg-publish":true,"permalink":"/publishing/main/artikler/microservices/mono-vs-micro/","title":"Mono vs Micro","tags":["Monolith","Microservices","Architecture"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-09-30T08:26:24.046+02:00"}
---


> Hvad er bedst for dit projekt? [[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|Monolith]] eller [[Publishing/Main/Noter/Emner/Backend/Microservice\|Microservices]]?

Når det kommer til valg af arkitektur, kan det være svært at afgøre, hvad der er bedst for din virksomhed. Valget mellem en [[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|monolitisk applikation]] og en [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservice-arkitektur]] afhænger af en række faktorer, såsom *skaleringsbehov*, *udviklingsteamets* *størrelse*, og hvor kompleks applikationen forventes at blive.

---
## Hvad er en Monolith?
En **[[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|monolitisk applikation]]** er en enkelt, samlet kodebase, hvor alle funktionaliteter er integreret og afhængige af hinanden.

![Monolith_architecture.png](/img/user/Resource/98_Images/Monolith_architecture.png)

Dette kan være en god løsning for *små* eller *mellemstore* projekter, der ikke har behov for omfattende skalering. 
I projektets *startfase* kan det være hensigtsmæssigt at bruge en monolitisk tilgang, da det ofte er hurtigere at udvikle og implementere. Hvis projektet senere kræver mere fleksibilitet eller skalering, kan en overvejelse af [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]] blive relevant.

### Fordele ved Monolith

- En enkelt kodebase gør det enklere at arbejde med for mindre teams.
- Kræver ikke ekspertise i flere teknologier eller services.
- Nem deployment, da alt er samlet i én pakke.

## Modular Monolit
En **modulær monolith** er en monolitisk arkitektur, der er opdelt i separate moduler. Hvert modul har sit eget ansvarsområde, hvilket gør det lettere at udvikle, teste og vedligeholde.

![Modular monolith.png](/img/user/Resource/98_Images/Modular%20monolith.png)

Denne tilgang fungerer som en overgang mellem [[Publishing/Main/Noter/Programmering/Monolitiske Applikationer\|monolith]] og [[Publishing/Main/Noter/Emner/Backend/Microservice\|microservices]], da modulerne kan behandles næsten som selvstændige services.
### Fordele ved Modular Monolith

- **Bedre vedligeholdelse:** Opdeling i moduler gør det lettere at lokalisere og rette fejl.
- **Teknologisk fleksibilitet:** Enkeltmoduler kan lettere opgraderes eller udskiftes.
- **Forbedret skalerbarhed:** Moduler kan tilpasses individuelt til behovene.
- **Mere fokuseret testning:** Hvert modul kan testes separat.
## [[Publishing/Main/Noter/Emner/Backend/Microservice\|Microservices]]

**[[Publishing/Main/Noter/Emner/Backend/Microservice\|Microservices]]** er en arkitektur, hvor applikationen opdeles i mindre, selvstændige services. Hver service repræsenterer et domæne eller ansvarsområde og kan udvikles, implementeres og vedligeholdes uafhængigt.


![Microservice_Arch.png](/img/user/Resource/98_Images/Microservice_Arch.png)

Denne tilgang er ideel for komplekse applikationer, der skal skaleres op, eller hvor dele af applikationen skal kunne udskiftes uden at påvirke resten af systemet.

---
## Hvordan vælger du den rette arkitektur?

Valget mellem [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Hvad er en Monolith?\|monolith]], [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Modular Monolit\|modular monolith]] og [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Microservice Microservices\|microservices]] afhænger af:

1. **Skaleringsbehov:** Hvis applikationen forventes at vokse betydeligt, kan [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Microservice Microservices\|microservices]] være en bedre løsning.
2. **Teamets størrelse og ekspertise:** Mindre teams kan drage fordel af en enklere arkitektur som en [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Hvad er en Monolith?\|monolith]].
3. **Projektets kompleksitet:** En simpel applikation kræver sjældent [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Microservice Microservices\|microservices]].
4. **Fremtidige ændringer:** [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Modular Monolit\|modular monolith]] kan være et godt kompromis, hvis du ønsker fleksibilitet uden kompleksiteten ved [[Publishing/Main/Artikler/Microservices/Mono vs Micro#Microservice Microservices\|microservices]].

---

### Konklusion

- **Monolith:** God til små projekter eller i en opstartsfase.
- **Modular Monolith:** Perfekt til mellemstore projekter, der ønsker fleksibilitet uden at miste enkelheden.
- **Microservices:** Ideel til store, komplekse projekter, der kræver høj skalerbarhed og teknologisk frihed.

Ved at starte med en modular monolith kan du senere migrere til microservices, hvis behovet opstår.

## Kilder
> [!source]- Chronosphere: Comparing Monolith and Microservice Architectures for Software Delivery
>   Tilgængelig på: [https://chronosphere.io/learn/comparing-monolith-and-microservice-architectures-for-software-delivery/](https://chronosphere.io/learn/comparing-monolith-and-microservice-architectures-for-software-delivery/)

> [!source]- freeCodeCamp: Microservices vs Monoliths Explained
> Tilgængelig på: [https://www.freecodecamp.org/news/microservices-vs-monoliths-explained/](https://www.freecodecamp.org/news/microservices-vs-monoliths-explained/)

> [!source]- AWS: The Difference Between Monolithic and Microservices Architecture
> Tilgængelig på: [https://aws.amazon.com/compare/the-difference-between-monolithic-and-microservices-architecture/](https://aws.amazon.com/compare/the-difference-between-monolithic-and-microservices-architecture/)

> [!source]- N-iX: Microservices vs Monolith: Which Architecture is the Best Choice for Your Business?
> Tilgængelig på: [https://www.n-ix.com/microservices-vs-monolith-which-architecture-best-choice-your-business/](https://www.n-ix.com/microservices-vs-monolith-which-architecture-best-choice-your-business/)

> [!source]- Atlassian: Microservices vs Monolith
> Tilgængelig på: [https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith)

> [!source]- OpenLegacy: Monolithic Application
> Tilgængelig på: [https://www.openlegacy.com/blog/monolithic-application](https://www.openlegacy.com/blog/monolithic-application)

## Andre artikler med samme emne
| File | Title | Tags |
| ---- | ----- | ---- |

{ .block-language-dataview}
