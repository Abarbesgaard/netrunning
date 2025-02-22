---
{"dg-publish":true,"permalink":"/publishing/main/noter/programmering/eventual-consistency/","created":"2024-11-15T09:35:55.560+01:00"}
---

> [!Important] Opsummering
> **Eventual consistency** er en model, der bruges i [[Publishing/Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]] for at opnå høj tilgængelighed. 

![Pasted image 20241115093723.png](/img/user/Resource/98_Images/Pasted%20image%2020241115093723.png)
*Billede fra [Designgurus](https://www.designgurus.io/answers/detail/what-is-strong-vs-eventual-consistency)*
## Kilder:
1. [Wiki](https://en.wikipedia.org/wiki/Eventual_consistency)
2. [aerospike](https://aerospike.com/glossary/eventual-consistency/)
3. [Designgurus](https://www.designgurus.io/answers/detail/what-is-strong-vs-eventual-consistency)
## Grundlæggende koncept

**Eventual consistency** garanterer *uformelt*, at hvis der ikke foretages nye opdateringer til et givet dataelement, vil alle tilgange til det element til sidst returnere den senest opdaterede værdi [1](https://en.wikipedia.org/wiki/Eventual_consistency) . 

## Karakteristika

- **Asynkron propagering**: Opdateringer behøver ikke at blive replikeret øjeblikkeligt på tværs af alle noder, hvilket reducerer latens [2](https://aerospike.com/glossary/eventual-consistency/).
- **Fleksibilitet**: Systemer kan prioritere tilgængelighed og partitionstolerance over øjeblikkelig konsistens [2](https://aerospike.com/glossary/eventual-consistency/).
- **Skalerbarhed**: Understøtter horisontal skalering ved at tillade distribution af data uden streng synkronisering [2](https://aerospike.com/glossary/eventual-consistency/).
- **Fejltolerance**: Systemet kan fortsætte med at fungere ved netværkspartitioner eller nodefejl [2](https://aerospike.com/glossary/eventual-consistency/).

## Fordele og ulemper

**Fordele:**

- Høj tilgængelighed og fejltolerance
- Bedre ydeevne og skalerbarhed
- Lavere operationelle omkostninger

**Ulemper:**

- Risiko for midlertidigt inkonsistente data
- Øget kompleksitet for applikationsudviklere
- Potentielle udfordringer med konfliktløsning

## Anvendelser

**Eventual consistency** bruges ofte i distribuerede systemer, hvor høj tilgængelighed og partitionstolerance prioriteres. Typiske anvendelser omfatter:

- Store webapplikationer som sociale medieplatforme
- E-handelswebsteder
- Systemer, der ikke kræver øjeblikkelig datakonsistens

## Sammenligning med stærk konsistens

I modsætning til stærk konsistens, hvor alle brugere ser de samme data på samme tid, tillader eventual consistency en periode, hvor data kan være inkonsistente, men til sidst bliver ensartet [3](https://www.designgurus.io/answers/detail/what-is-strong-vs-eventual-consistency). Dette giver bedre ydeevne og tilgængelighed på bekostning af øjeblikkelig datakonsistens.

## Konklusion

Valget mellem **eventual consistency** og **stærkere konsistensmodeller** afhænger af de specifikke krav til applikationen. Systemer, der kan tolerere midlertidig inkonsistens til fordel for bedre ydeevne og tilgængelighed, kan drage fordel af eventual consistency.

