---
{"dg-publish":true,"permalink":"/main/artikler/mono-vs-micro/","title":"Mono vs Micro","tags":["Monolith","Microservices","Architecture"],"created":"2024-09-30T08:26:24.046+02:00"}
---


> Hvad er bedst for din virksomhed? Monolith eller Microservices?

Hvordan afgør man hvilken arkitektur der er bedst for ens virksomhed?

Der er mange faktorer at tage hensyn til, og det er ikke altid lige
let at finde ud af.

Jeg vil i denne artikel forsøge at give et overblik
over fordele og ulemper ved de to forskellige arkitekturer, og
forhåbentlig gøre det lidt lettere at vælge.

Det første jeg vil gøre er at definere hvad en **Monolith** og en
**Microservice** er.

## Hvad er en Monolith?

![Monolith_architecture.png](/img/user/Monolith_architecture.png)

Dette billede fra *net solutions* viser hvordan alt i applikationen
er samlet i en stor klump. Dette kan være en god løsning for et mindre projekt
som ikke har brug for at skalere.
Så i projektets startfase kan det være en god ide at at få afklaret om projektet
har grobund for at populært og brugt at mange brugere. Hvis det er tilfældet kan
det være en god ide at overveje at bruge en Microservice arkitektur, i stedet
for.

### Fordele ved Monolith

- Der er en enkelt kodebase
- Ikke brug for ekspertise i flere teknologier
- Nemmere deployment

Der er dog en mellemting inden vi går helt over til Microservices. Nemlig en
modular monolith. Dette er en monolith der er opdelt i moduler, som hver især
har sit eget ansvarsområde.

## Modular Monolit

![Modular monolith.png](/img/user/Modular%20monolith.png)

Dette billede fra harrison clarke viser hvordan en monolith kan deles op i moduler.
Dette er en god mellemting mellem en monolith og microservices.
Når man bruger en moduler monolith er det en grundlæggende ændring i hvordan
monolitten er. Denne ændring gør at man nærmest kan køre modulerne som
microservices.

### Fordele ved Modular Monolith

- Nemmere at vedligeholde
- Nemmere at skifte teknologi ud
- Nemmere at skalere
- Nemmere at teste

## Microservices

Hvis du har brug for at skalere din applikation, og har brug for at kunne
udskifte forskellige dele af din applikation, så er Microservices det rigtige valg.

Microservices er en arkitektur hvor applikationen er opdelt i flere små
services. Disse services er inddelt efter deres ansvarsområder/domæner.

![Microservice_Arch.png](/img/user/Microservice_Arch.png)

### Fordele ved Microservices

- Skalerbar
- Fleksibel
- Nemmere at udskifte dele af applikationen
- Nemmere at teste dele af applikationen
- Nemmere at vedligeholde

## Kilder

- [Medium - What is better modular monolit vs microservice](https://medium.com/codex/what-is-better-modular-monolith-vs-microservices-994e1ec70994)
