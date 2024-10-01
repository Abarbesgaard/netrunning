---
{"dg-publish":true,"permalink":"/main/projekter/pokedex/moder/forste-mode-med-oak/","hide":true,"created":"2024-10-01T12:41:33.855+02:00"}
---

**Andreas**: Hej, Professor Oak! Jeg har tænkt på noget. Hvad nu hvis vi lavede en digital database til at holde styr på alle Pokémon? Det kunne være en slags Pokédex, som vi har snakket om.

**Professor Oak**: Hej, Andreas! Det lyder som en fremragende idé. En Pokédex, siger du? Hm... En enhed, der registrerer oplysninger om alle Pokémon, vi støder på. Men hvordan har du tænkt dig at bygge det op?

**Andreas**: Jeg tænkte, vi kunne starte med en **simpel monolitisk applikation**. Du ved, én samlet applikation, hvor al logikken er samlet i ét sted. Det gør det nemmere at komme i gang, inden vi evt. opdeler det i flere tjenester senere.

**Professor Oak**: En monolitisk applikation – det giver god mening som et første skridt. Så du forestiller dig, at vi har én backend, der indeholder al logikken og håndterer data om Pokémon? Hvordan vil du strukturere den?

**Andreas**: Præcis. Vi kan lave en **API-backend**, hvor vi kan kommunikere med Pokédex'en via HTTP-anmodninger. Så kunne vi have forskellige endpoints for at hente Pokémon-data, registrere nye Pokémon og måske opdatere information om dem.

**Professor Oak**: Interessant! Så i praksis kunne man forespørge på forskellige Pokémon gennem API’et? Og backend’en håndterer alt fra datalagring til forespørgsler?

**Andreas**: Ja, lige præcis. For nu vil vi starte med en MongoDB til datalagring. Vi kan bruge det til at gemme Pokémon-data som navn, type, evner osv. I første omgang skal API’et kunne håndtere følgende:

- Hente alle Pokémon
- Hente en specifik Pokémon
- Oprette en ny Pokémon
- Opdatere en Pokémon

**Professor Oak**: Det lyder solidt! Så vi kan både tilføje nye Pokémon og opdatere dem, efterhånden som vi opdager mere om dem. Hvordan vil du håndtere dataformatet?

**Andreas**: Jeg vil foreslå, at vi bruger JSON som dataformat for API’et. Det gør det let at udveksle information, og mange systemer kan arbejde med det uden problemer. Hver Pokémon kunne repræsenteres som et JSON-objekt med felter som *id*, *navn*, *type* og *udviklinger*.

**Professor Oak**: Det lyder meget overskueligt. Hvordan vil du så håndtere forskellige Pokémon-typer og deres udviklinger? Skal det være en separat model eller en del af Pokémon-modellen?

**Andreas**: Vi kan starte med at inkludere det direkte i Pokémon-modellen. Hver Pokémon kan have *en liste over sine typer* og *en liste over udviklinger*. På den måde holder vi det simpelt i starten, og så kan vi altid lave det mere avanceret senere.

**Professor Oak**: Enig! Simplicitet er nøglen, især i starten. Det vigtigste er, at vi får fundamentet på plads. Jeg kan allerede se potentialet i en sådan applikation. Hvordan vil du sikre, at API'et er skalerbart, hvis Pokédex'en vokser?

**Andreas**: Det er en god pointe. Når vi når et punkt, hvor vi har brug for at skalere, kan vi overveje at splitte applikationen op i flere microservices. Men til en start vil en monolit være lettere at udvikle og vedligeholde. Senere kunne vi have separate services for ting som Pokémon-typer, udviklinger og lokationsdata.

**Professor Oak**: Fornuftigt. Lad os starte simpelt og bygge det op over tid. Det lyder som et solidt første udkast. Når det er klar, kan vi teste det med nogle trænere og se, hvordan det fungerer i praksis!

**Andreas**: Perfekt! Jeg går i gang med at skitsere API’et og lave de første endpoints. Vi kan altid tilføje flere funktioner hen ad vejen, når behovet opstår. Tak for sparringen, Professor Oak!

**Professor Oak**: Det var mig en fornøjelse, Andreas. Jeg glæder mig til at se, hvordan din Pokédex tager form!