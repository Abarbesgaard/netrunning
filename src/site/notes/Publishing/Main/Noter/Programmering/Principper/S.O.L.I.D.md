---
{"dg-publish":true,"permalink":"/publishing/main/noter/programmering/principper/s-o-l-i-d/","title":"S.O.L.I.D","hide":true,"tags":["Principper","Programmering","SOLID"],"created":"2024-09-20T10:05:41.534+02:00"}
---

> **SOLID** er en akronym, der repræsenterer fem grundlæggende principper for
>objektorienteret programmering og design. Disse principper fremmer god
>softwarestruktur og design, som er nemmere at forstå, vedligeholde og
>udvide.

## SOLID's 5 principper

### Single-Responsibility

Princippet om `single responsibilitry` siger, at en klasse eller modul skal have
én og kun én grund til at ændre sig. Dette betyder, at hver klasse skal have
*ét fokus eller ansvar*.

*Eksempel:* Forestil dig en `Report` klasse, der har metoder til at redigere
rapportens indhold (`editContent`) og til at formatere rapportens layout
(`formatReport`). Ifølge SRP bør disse ansvarsområder adskilles i to
klasser, fordi ændringer i rapportens indhold ikke bør påvirke
formateringslogikken.

### Open-Closed

Softwareenheder bør være åbne for udvidelse, men lukkede for ændringer.
Dette betyder, at man bør kunne tilføje ny funktionalitet uden at ændre
eksisterende kode.

*Eksempel:* En `Shape` interface med en `draw` metode kan implementeres af
flere klasser som `Circle`, `Square`, osv. Hvis du vil tilføje en ny
form, `Triangle`, kan du gøre dette ved at oprette en ny klasse, der
implementerer `Shape`, uden at ændre de eksisterende klasser.

### Liskov substitution

Objekter af en supertype skal kunne erstattes med objekter af en
subtype uden at ændre programmets korrekthed.

*Eksempel:* Hvis `Bird` er en klasse, og `Duck` er en underklasse af
`Bird`,så bør du kunne erstatte alle instanser af `Bird` med `Duck`
uden at programmet går i stykker. Hvis `Duck` har en metode `fly`,
som ikke giver mening for alle `Bird` objekter, bryder det LSP.

### Interface segregation

Ingen kode bør tvinges til at afhænge af metoder, den ikke bruger.

*Eksempel:* Hvis du har et `MultifunctionPrinter` interface med metoder
som `print`, `scan`, og `fax`, og en simpel printer, der kun kan printe,
bør denne printer ikke implementere `MultifunctionPrinter`. I stedet
bør der være separate interfaces for hver funktionalitet.

### Dependency inversion

Højniveau moduler bør ikke afhænge af lavniveau moduler. Begge bør afhænge
af abstraktioner. Desuden bør abstraktioner ikke afhænge af detaljer;
detaljer bør afhænge af abstraktioner.

*Eksempel:* I stedet for at en `OrderProcessor` klasse direkte instantierer
et `EmailService` til at sende bekræftelser, bør `OrderProcessor` afhænge
af et `INotificationService` interface. `EmailService` implementerer dette
interface, og `OrderProcessor` kan nu bruge enhver `INotificationService`
 implementering, hvilket gør det nemmere at udskifte eller udvide
funktionaliteten.

## Kilder

[Liskov substitution principle](https://www.youtube.com/watch?v=-Z-17h3jG0A)
[Christopher Okravi - LSP](https://www.youtube.com/watch?v=7hXi0N1oWFU)
[WIKI - SOLID](https://en.wikipedia.org/wiki/SOLID)
