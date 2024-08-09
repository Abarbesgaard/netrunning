---
{"dg-publish":true,"permalink":"/content/programmering/principper/grasp/","title":"GRASP","hide":true,"tags":["Principper","Programmering"]}
---


> [!tldr]
> GRASP står for “General Responsibility Assignment Software Patterns” og
> er en samling af principper til objektorienteret design.

## GRASP

### Informations Ekspert

- Problem: Hvordan tildeler man ansvar til objekter?
- Løsning: Giv ansvar til den klasse, der har den nødvendige
  information til at opfylde det.

### Kreatør

- **Problem:** Hvem skaber objekt A?

- **Løsning:** Lad klasse B skabe objekt A, hvis:

B allerede har objekter af A.
B holder styr på objekter af A.
B bruger objekter af A ofte.
B ved, hvordan objekter af A skal startes op og giver denne information videre
ved oprettelsen.

### Controller

- **Problem:** Hvem skal håndtere en systemhændelse?
- **Løsning:** Brug en use case controller til at håndtere alle
  systemhændelser for et use case.

### Indirection

- **Problem:** Hvor tildeler man ansvar for at undgå direkte kobling mellem
  to eller flere ting?
- **Løsning:** Tildel ansvaret til et mellemobjekt for at mægle mellem andre
  komponenter eller tjenester.

### Low Coupling

Dette er et mønster, der foreskriver, hvordan man tildeler ansvar for at opnå
lav afhængighed mellem klasser og høj genbrugspotentiale.

### High cohesion

Dette mønster forsøger at holde objekter fokuserede og forståelige. Høj
samhørighed betyder, at ansvaret for en given gruppe af elementer er
stærkt relateret og fokuseret på et specifikt emne.

### Polymorphism

- **Problem:** Hvordan håndterer man alternativer baseret på type?
- **Løsning:** Tildel ansvaret for adfærdsvariation til typen (klassen), hvor
  adfærden varierer.

### Protected Variations

Dette mønster beskytter elementer mod variationer ved at indkapsle
ustabilitetsfokus med et interface og bruge polymorfi til at skabe
forskellige implementeringer af dette interface.

### Pure Fabrication

En ren fabrikation er en klasse, der ikke repræsenterer et koncept i
problemområdet, men som er skabt for at opnå lav kobling, høj samhørighed
og deraf afledt genbrugspotentiale.

### Kilder

[WIKI - GRASP](<https://en.wikipedia.org/wiki/GRASP_(object-oriented_design)>)
[Medium artikkel om GRASP](https://patrickkarsh.medium.com/object-oriented-design-with-grasp-principles-8049fa63e52)
[Geeksforgeeks](https://www.geeksforgeeks.org/grasp-design-principles-in-ooad/)
