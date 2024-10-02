---
{"dg-publish":true,"permalink":"/main/4-semester/pokedex/sprint/forste-sprint/","created":"2024-10-01T12:52:11.310+02:00"}
---

[link til github repo](https://github.com/Abarbesgaard/pokedex-monolit)
Jeg var heldig at få den mulighed at samarbejde med **professor Oak** for at lave en [[Main/4. Semester/Pokedex/Hvad er en Pokédex\|Pokédex]].

Hvis ud vil se vores indledende samtale hvor vi gennemgik de forskellige ting denne skulle kunne så [[Main/4. Semester/Pokedex/Møder/Første møde med Oak\|klik her]].

Det som Oak bad om til at starte med var følgende:
- **Monolitisk applikation**:
    - Vi starter med én samlet applikation for at holde det simpelt og overskueligt.
    - Monolitten giver også mulighed for at lave en mvp super hurtigt, for at se om det er noget pokemon trænerne kunne være interesseret i at bruge.
    - Backend'en vil håndtere både datalagring og forespørgsler.
- **API-backend**:
    - Der skal laves en API-backend, hvor vi kan interagere med Pokédex'en via HTTP-anmodninger.
    - Der skal bruges JSON som dataformat for at udveksle information.
- **MongoDB til datalagring**:
    - Pokémon-data såsom navn, type, evner og udviklinger gemmes i en MongoDB-database.
- **API-endpoints**:
    - Hente alle Pokémon.
    - Hente en specifik Pokémon.
    - Oprette en ny Pokémon.
    - Opdatere information om en eksisterende Pokémon.
- **Pokémon-model**:
    - Pokémon-data indeholder felter som id, navn, type, evner og en liste over udviklinger.
    - Alle data struktureres i et JSON-objekt.
- **Skalering i fremtiden**:
    - Applikationen starter som monolitisk, men vi kan overveje at opdele den i microservices, hvis behovet for skalering opstår.
    - Mulige fremtidige microservices kunne håndtere specifikke områder som Pokémon-typer, udviklinger eller lokationsdata.

De vigtigste elementer i dette er at jeg for øvet de [[Main/4. Semester/Læringsmål/Læringsmål\|Læringsmål]]som underviserne har sat.