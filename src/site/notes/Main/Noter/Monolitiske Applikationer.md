---
{"dg-publish":true,"permalink":"/main/noter/monolitiske-applikationer/","created":"2024-11-15T10:01:57.240+01:00"}
---

> [!Important] Opsummering
> En monolitisk applikation er en softwareløsning, hvor alle komponenter og funktionaliteter er integreret i en enkelt enhed eller blok. Denne arkitekturtype har følgende kendetegn:

![Pasted image 20241115100249.png](/img/user/98_Images/Pasted%20image%2020241115100249.png)
*Billede fra [Guru99](https://www.guru99.com/da/microservices-tutorial.html)*

## Kilder
1. [dream](https://www.perplexity.ai/search/hvad-er-en-monolittisk-applika-ByVc0nSuQp6zO8KAc8rUOg)
2. [novicell](https://www.novicell.com/dk/viden/guide-til-udfasning-af-legacy-systemer/)
3. [guru99](https://www.guru99.com/da/microservices-tutorial.html)
## Struktur og opbygning

En monolitisk applikation er opbygget som en samlet enhed, hvor alle dele af systemet er tæt integreret og afhængige af hinanden [1](https://dream.dk/monolitisk/). Det betyder, at både frontend, backend, forretningslogik og datalag typisk er samlet i én kodebase [2](https://www.novicell.com/dk/viden/guide-til-udfasning-af-legacy-systemer/).

## Karakteristika

- **Enkelhed**: Monolitiske applikationer er relativt enkle at forstå og implementere, da alle komponenter er samlet ét sted [1](https://dream.dk/monolitisk/).
- **Tæt integration**: Alle dele af applikationen er tæt forbundet, hvilket kan give god ydeevne, da der ikke er overhead i kommunikationen mellem komponenter [1](https://dream.dk/monolitisk/).
- **Deployment**: Når der laves ændringer, skal hele applikationen deployes på ny, uanset hvor lille ændringen er [2](https://www.novicell.com/dk/viden/guide-til-udfasning-af-legacy-systemer/).

## Fordele og ulemper

## Fordele:

- Let at teste som en helhed
- God ydeevne grundet tæt integration
- Enkel at udvikle og vedligeholde for mindre applikationer

## Ulemper:

- **Lang time-to-market**: Det kan tage lang tid at implementere nye features, da hele systemet skal deployes ved ændringer [2](https://www.novicell.com/dk/viden/guide-til-udfasning-af-legacy-systemer/).
- **Skaleringsudfordringer**: Det kan være svært at skalere enkelte dele af applikationen uafhængigt [3](https://www.guru99.com/da/microservices-tutorial.html).
- **Teknologisk lock-in**: Det er vanskeligt at adoptere nye teknologier, da en ændring påvirker hele systemet [2](https://www.novicell.com/dk/viden/guide-til-udfasning-af-legacy-systemer/).

## Anvendelse

**Monolitiske applikationer** er velegnede til *mindre projekter* med lav kompleksitet, hvor der ikke er behov for høj skalerbarhed eller fleksibilitet [1](https://dream.dk/monolitisk/). De kan også være en god løsning, hvis der er begrænsede ressourcer til at implementere og vedligeholde en mere kompleks arkitektur.

Eksempler på monolitiske applikationer kan være simple webapplikationer, hvor både frontend og backend er integreret, eller mobilapplikationer, hvor al funktionalitet er samlet i én pakke [1](https://dream.dk/monolitisk/).