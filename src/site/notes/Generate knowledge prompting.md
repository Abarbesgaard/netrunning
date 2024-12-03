---
{"dg-publish":true,"permalink":"/generate-knowledge-prompting/","tags":["⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T08:35:03.729+01:00"}
---


> [!example] Hvad er General Knowledge Prompting
> General Knowledge Prompting er en teknik, hvor man hjælper AI-modeller med at forbedre deres svar ved at tilføre kontekstuel baggrundsviden inden selve spørgsmålet besvares. Det handler om at give modellen "forberedende information", så den kan lave mere præcise og nuancerede svar.

### Hvorfor er dette vigtigt?

Traditionelle AI-modeller kan:
- Give overfladiske svar.
- Mangle dybere forståelse.
- Komme til at lave faktuelle fejl.

## Hvordan fungerer General Knowledge Prompting?

### Grundlæggende trin:
1. **Identificer vidensbehov**: Find ud af hvilket emneområde der mangler dybde
2. **Generer relevant baggrundsviden**: Saml præcise, neutrale informationer
3. **Indsæt viden før hovedspørgsmålet**
4. **Bed AI om at anvende den nye viden**

### Eksempel: Fra generisk til specifik viden

> [!example] Uden baggrundsviden
> **Prompt**: Er det sundt at løbe?
   **Output**: Ja, det er sundt at løbe.

#### Med General Knowledge Prompting:

> [!example] General Knowledge Prompting
> **Viden**: Løb er en aerob træningsform, der styrker hjerte-karsystemet. Dog kan overdreven løbetræning medføre risiko for ledbetændelse og overbelastningsskader.
> **Prompt**: Er det sundt at løbe?
   **Output**: Ja, det at løbe kan være sundt, når det udføres med rette teknik og i passende mængder. Det forbedrer kardiovaskulær sundhed, men kræver opmærksomhed på kroppens signaler for at undgå skader.

*det er vigtigt at Viden: kommer med i den endelige prompt, jeg har delt det op for læsbarhedes skyld*

## Praktiske Teknikker

### Teknik 1: Faktuel Baggrundsviden
- Tilføj præcise, videnskabelige fakta
- Brug troværdige kilder
- Hold informationen neutral

### Teknik 2: Kontekstuel Uddybning
- Tilføj historisk eller kulturel baggrund
- Forklar komplekse sammenhænge
- Vis nuancer i emnet

### Teknik 3: Perspektivisk Viden
- Præsenter forskellige synsvinkler
- Vis kompleksiteten i et emne
- Undgå entydige ja/nej svar

## Eksempel på Kompleks Prompting


> [!example] Eksempel
> **Viden om klimaforandringer**: 
> Global gennemsnitstemperatur er steget med 1,1°C siden før-industriel tid
> Hovedårsag er menneskelige CO2-udledninger
> Konsekvenser inkluderer havniveaustigning, flere ekstreme vejrbegivenheder
> **Prompt**: Løser vi klimakrisen?
   **Output**: Klimakrisen kræver global, koordineret indsats. Teknologiske fremskridt og internationale aftaler viser potentiale, men udfordringerne er komplekse og kræver vedvarende, ambitiøse tiltag fra regeringer, virksomheder og borgere.

## Begrænsninger

- Ikke alle emner egner sig
- Kræver høj kvalitet af baggrundsviden
- Risiko for bias i den valgte viden

## Øvelse og Læring

1. Start simpelt
2. Vær kritisk med videnskilderne
3. Eksperimenter løbende
4. Lær af resultaterne

## Konklusion

General Knowledge Prompting er en kraftfuld metode til at forbedre AI's forståelse og svarkvalitet. Det handler om at give kontekst, nuancer og dybde.

**Husk**: God viden = Bedre svar
