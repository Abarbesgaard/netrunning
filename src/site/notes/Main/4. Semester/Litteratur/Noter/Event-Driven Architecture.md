---
{"dg-publish":true,"permalink":"/main/4-semester/litteratur/noter/event-driven-architecture/","title":"Event-Driven Architecture","hide":true,"created":"2024-09-05T09:00:41.650+02:00"}
---


## Event-driven arkitektur (EDA) - En dybere forståelse

![EventDrivenArchitecture.png](/img/user/EventDrivenArchitecture.png)

Event-driven arkitektur (EDA) er en softwarearkitektur, der fokuserer på at
fange, kommunikere og bearbejde begivenheder (events) i et system, hvor
tjenester er løsrevne (decoupled). Dette betyder, at systemkomponenter
kan fungere asynkront og uafhængigt af hinanden, hvilket gør systemet mere
fleksibelt, skalerbart og responsivt over for ændringer.

Moderne applikationer, såsom kundehåndteringssystemer, der arbejder med
realtidsdata, bruger ofte event-drevne principper for at sikre hurtig
reaktion på ændringer. Denne arkitektur kan implementeres i ethvert
programmeringssprog, fordi event-drevenhed er en tilgang og ikke bundet
til et specifikt sprog.

![EventRounter.png](/img/user/EventRounter.png)
### Hovedkomponenter i event-driven arkitektur

1. **Event-producenter**: De enheder, der skaber begivenheder, såsom en
brugerhandling (klik, tastetryk) eller en systemændring (start af et
program).
2. **Event-forbrugere**: De enheder, der reagerer på disse begivenheder.
Event-forbrugere ved ikke nødvendigvis, hvem der har produceret eventet,
hvilket muliggør løs kobling.
3. **Event-kanaler**: De medier eller kanaler, gennem hvilke begivenheder sendes
fra producenter til forbrugere.

### Decoupling og løs kobling

**Decoupling** refererer til praksissen med at eliminere eller minimere direkte
afhængigheder mellem komponenter i et system. I en event-driven arkitektur
sender event-producenter data uden at vide, hvilke forbrugere der vil modtage
det. Dette gør komponenterne uafhængige af hinanden, hvilket skaber et mere
fleksibelt system.

**Løs kobling** reducerer graden af interaktion mellem systemkomponenter uden
at adskille dem helt. Dette muliggør, at komponenter kan interagere uden at
blive afhængige af hinanden, hvilket er afgørende for systemets fleksibilitet
og skalerbarhed.

### Hvordan virker event-driven arkitektur?

I en EDA fungerer event-producenter og event-forbrugere asynkront. Når en
event-producent opdager en begivenhed, oversættes denne til en meddelelse,
der sendes gennem en event-kanal. Producenten ved ikke, hvilken forbruger
der modtager eventet eller resultatet af dets udførelse. Event-forbrugeren,
der modtager begivenheden, kan herefter behandle denne asynkront, hvilket
skaber en høj grad af fleksibilitet og muliggør realtidsreaktioner på begivenheder.

### Arkitekturmodeller i EDA

1. **Pub/Sub-model**: En model, hvor begivenheder publiceres og sendes til
abonnenter, der har brug for at blive informeret om en given begivenhed.
Denne model sikrer, at begivenheder leveres til de relevante forbrugere uden
behov for direkte afhængigheder.

2. **Event-streaming-model**: I denne model skrives begivenheder til en log, og
forbrugere kan læse fra enhver del af event-strømmen og tilslutte sig når som
helst. Det er især nyttigt til behandling af store datamængder i realtid,
f.eks. med Apache Kafka.

### Fordele ved event-driven arkitektur

1. **Fleksibilitet og skalerbarhed**: EDA gør det muligt for systemer at
skalere ved at tilføje nye komponenter uden at påvirke de eksisterende.
  
2. **Realtidsbeslutninger**: Event-driven systemer muliggør, at beslutninger
kan træffes hurtigt og baseret på de nyeste data.
  
3. **Decoupling af komponenter**: Med løsrevet kommunikation mellem
event-producenter og forbrugere fremmes fejltolerance og robusthed i
systemet.

### Event-driven arkitektur og middleware

Middleware som Apache Kafka anvendes ofte i event-drevne systemer, da det
håndterer event-streaming i realtid. Kafka giver mulighed for høj throughput
og lav latenstid, hvilket gør det til et populært valg til event-behandling,
hvor data skal deles hurtigt og effektivt mellem systemkomponenter.
