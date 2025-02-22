---
{"dg-publish":true,"permalink":"/publishing/main/ai/prompt-teknikker/meta-prompting/","tags":["⭐⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T09:29:36.364+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐⭐⭐

> [!important] Hvad er Meta Prompting
> Meta Prompting er en sofistikeret teknik, hvor man instruerer AI'en om selve måden at tilgå og løse en opgave på. I stedet for blot at stille et spørgsmål, definerer du de strategiske tilgange, tankemønstre og evalueringskriterier, som AI'en skal følge.
## Kerneprincippet
Forestil dig at give en ekspert ikke bare en opgave, men også en detaljeret vejledning om, hvordan de skal tænke, analysere og levere løsningen.

## Grundlæggende Strategier

### 1. Rolletildeling
- Definér en specifik ekspertrolle
- Angiv baggrund og kompetencer
- Skab et mentalt rammesæt

> [!example] Eksempel
> Du er nu en erfaren strategisk planlægger med 25 års erfaring i virksomhedsledelse. 
   Anvend følgende tilgang:
   Analyser problemet fra forskellige perspektiver
   Prioriter løsninger efter implementerbarhed
   Vær kritisk og selvreflekterende

### 2. Tænkemetoder
- Definér specifikke tænkningsværktøjer
- Angiv analytiske fremgangsmåder
- Strukturer den intellektuelle tilgang

#### Metoder:
- [Videnskabelig metode](https://da.wikipedia.org/wiki/Videnskabelig_metode)
- [Design Thinking](https://www.interaction-design.org/literature/article/5-stages-in-the-design-thinking-process)
- [Systemisk tænkning](https://www.lederweb.dk/systemisk-taenkning-at-forstaa-systemet-moensteret-og-sammenhaengene/)
- Kritisk analyse

### 3. Evalueringskriterier
- Fastsæt klare vurderingsparametre
- Skab gennemsigtighed i bedømmelsen
- Muliggør selvvurdering

#### Eksempel på Evalueringskriterier:
- Originalitet: 30%
- Praktisk gennemførlighed: 40%
- Innovation: 30%

## Praktiske Eksempler

### Scenarie 1: Strategisk Forretningsudvikling
> [!example] eksempel
> Meta-prompt:
>   1. Anvend SWOT-analyse
>   2. Tænk i scenarier
>   3. Prioriter løsninger efter:
>   - Risiko
>   - Potentiel indtjening
>   - Implementeringstid
>   
   4 Rapporter med klare anbefalinger



### Scenarie 2: Videnskabelig Problemløsning
> [!example] eksempel
> Meta-prompt:
> - Brug hypotetisk-deduktiv metode
> - Identificer eksisterende videnshuller
> - Foreslå eksperimentelle designs
> - Vurder metodologiske begrænsninger

## Fordele

✅ Mere strukturerede svar
✅ Dybere analyse
✅ Reduceret bias
✅ Øget præcision
✅ **Reproducerbare resultater**

## Udfordringer

❗ Kræver avanceret prompt engineering
❗ Afhænger af AI-modelens evner
❗ Kan blive for kompleks

## Tekniske Tips

### Konstruktion af Meta-Prompt
1. Vær specifik
2. Anvend klart sprog
3. Definer forventede outputformat
4. Inkluder evalueringsmekanismer

### Eksempel på Fuld Meta-Prompt
```
Du er nu en verdensklasse innovationskonsulent. 
Løs følgende opgave ved at:
- Anvende Design Thinking
- Gennemføre trinvis analyse
- Evaluere løsninger kritisk
- Rapportere med:
  * Problemdefinition
  * Mulige løsninger
  * Anbefalet strategi
  * Implementeringsplan

Evaluer din egen proces og løsning ud fra:
- Originalitet (30%)
- Gennemførlighed (40%)
- Innovationspotentiale (30%)
```

## Konklusion

Meta Prompting handler om at transformere AI fra et simpelt svar-værktøj til en strategisk samarbejdspartner.

**Nøglen**: Skriv ikke blot hvad der skal løses, men **hvordan det skal løses**.

### Læringsvej
1. Start simpelt
2. Eksperimenter
3. Raffinér løbende

## Øvelser
> [!note]- Prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Meta Prompting. Øvelserne skal bepreg af at de er lave til at gøre forståelsen for meta prompring lettere at forstå. Kom med 5 bud

### Øvelse 1: Prompt dissecting

**Formål:** Forstå, hvad der gør en prompt effektiv ved at analysere den.

1. Tag en kompleks prompt (f.eks. "Lav en opskrift, der kombinerer italiensk og japansk køkken").
2. Del prompten op i dens elementer:
    - **Intention**: Hvad vil vi opnå?
    - **Nøgleinformation**: Hvilke detaljer styrer output?
    - **Ramme**: Er der stil, format eller begrænsninger?
3. Omformuler den til at inkludere en meta-reflektion, f.eks.:
    - "Generer en opskrift, der kombinerer italiensk og japansk køkken. Forklar også, hvordan du kombinerede elementerne, og hvorfor de fungerer godt sammen."

### Øvelse 2: Prompt self-awareness

**Formål:** Skabe prompts, der kommenterer på deres egne dele.

1. Start med en simpel opgave: "Lav en liste over tre øvelser til en yoga-session."
2. Forbedr prompten med meta-lag:
    - "Lav en liste over tre øvelser til en yoga-session, og beskriv samtidig, hvorfor hver øvelse er valgt, og hvordan denne liste kan justeres til begyndere."
3. Reflekter over resultatet: Hvordan hjalp meta-elementet på klarheden eller dybden af svaret?
> [!hint]- Hint
> Det kan være en god ide at gøre det i 2 forskellige chats, så resultaterne ikke præger hinanden.
### Øvelse 3: Rewrite with meta goals

**Formål:** Træn omformulering af prompts med et meta-perspektiv.

1. Tag en basal prompt: "Skriv et digt om havet."
2. Tilføj et meta-lag: "Skriv et digt om havet, og giv en kort forklaring efterfølgende om, hvordan tone og ordvalg afspejler havets egenskaber."
3. Diskuter, hvordan den ekstra refleksion påvirker svaret.

### Øvelse 4: Meta-feedback loops

**Formål:** Integrere løbende selvevaluering i prompt-design.

1. Start med en iterative prompt:
    - "Beskriv, hvad en ideel arbejdsdag for en programmør indebærer."
2. Tilføj en feedback-sløjfe:
    - "Beskriv, hvad en ideel arbejdsdag for en programmør indebærer, og vurder, om svaret er detaljeret nok. Hvis ikke, forbedr det og forklar, hvad der blev ændret."
3. Analysér, hvordan svaret udvikler sig over tid, når feedback inkluderes.

### Øvelse 5: Prompt-ception (nested prompting)

**Formål:** Øve at bygge prompts, der skaber prompts.

1. Start med en opgave: "Lav en prompt, der hjælper nogen med at lære Python."
2. Byg et meta-lag:
    - "Skriv en effektiv prompt, der hjælper nogen med at lære Python, og inkluder en kort forklaring af, hvorfor prompten er formuleret sådan."
3. Evaluer resultatet og diskuter, hvordan meta-refleksion påvirker promptens kvalitet.