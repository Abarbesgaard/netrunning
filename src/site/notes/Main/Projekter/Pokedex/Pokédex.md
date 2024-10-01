---
{"dg-publish":true,"permalink":"/main/projekter/pokedex/pokedex/","created":"2024-10-01T12:21:28.579+02:00"}
---

Jeg var heldig at få den mulighed at samarbejde med **professor Oak** for at lave en [[Main/Projekter/Pokedex/Hvad er en Pokédex\|Pokédex]].

Hvis ud vil se vores indledende samtale hvor vi gennemgik de forskellige ting denne skulle kunne så [[Main/Projekter/Pokedex/Møder/Første møde med Oak\|klik her]].

Det som Oak bad om til at starte med var følgende:
- **Monolitisk applikation**:
    - Vi starter med én samlet applikation for at holde det simpelt og overskueligt.
    - Backend'en vil håndtere både datalagring og forespørgsler.
- **API-backend**:
    - Vi bygger en API-backend, hvor vi kan interagere med Pokédex'en via HTTP-anmodninger.
    - Vi bruger JSON som dataformat for at udveksle information.
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

