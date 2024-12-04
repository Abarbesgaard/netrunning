---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/generate-knowledge-prompting/","tags":["⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T08:35:03.729+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐

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

*Det er vigtigt at Viden: kommer med i den endelige prompt, jeg har delt det op for læsbarhedes skyld*

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


> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til General knowledge Prompting. Øvelserne skal være til for at gøre forståelsen for General knowledge prompring lettere at forstå. Kom med 5 bud

### Øvelse 1: Kategorisering af generelle spørgsmål

1. Lav en liste med 10 generelle spørgsmål, der dækker forskellige emner (f.eks. geografi, historie, videnskab, kultur). Eksempel:
    - _Hvad er hovedstaden i Italien?_
    - _Hvem malede Mona Lisa?_
    - _Hvad er det kemiske symbol for vand?_
2. Kategorisér spørgsmålene efter emne.
3. Reflekter over, hvordan spørgsmål inden for forskellige kategorier kan kræve specifikke eller brede prompts for at give korrekte svar.

---

### Øvelse 2: Formulering af åbne og lukkede prompts

1. Tag et emne (f.eks. "Månen") og skriv to typer prompts:
    - En **lukket prompt**, der leder til et specifikt svar (f.eks. _Hvor mange måner har Jorden?_).
    - En **åben prompt**, der giver mulighed for et mere detaljeret svar (f.eks. _Beskriv månens rolle i Jordens tidevandssystem._).
2. Diskutér, hvornår det er passende at bruge åbne vs. lukkede prompts i en samtale.

---

### Øvelse 3: Forbedring af prompts

1. Tag en generel prompt, f.eks. _Hvad er klimaændringer?_
2. Lav tre forskellige versioner af prompten, som:
    - Forbedrer præcisionen (f.eks. _Hvordan påvirker klimaændringer verdenshavene?_).
    - Tilpasser sværhedsgraden til et barn (f.eks. _Hvad betyder det, når klimaet bliver varmere?_).
    - Gør den kontekstspecifik (f.eks. _Hvilken rolle spiller Danmark i kampen mod klimaændringer?_).

---

### Øvelse 4: Prompt-feedback-cyklus

1. Skriv en general knowledge prompt, f.eks. _Hvad er Newtons tre bevægelseslove?_
2. Brug den til at generere et svar.
3. Evaluer svaret og justér prompten for at forbedre nøjagtighed eller dybde (f.eks. _Kan du forklare Newtons tre bevægelseslove med eksempler?_).
4. Gentag cyklussen, indtil du får det ønskede resultat.

---

### Øvelse 5: Quiz med uklar prompts

1. Lav 5 "uklare" prompts, som kan tolkes på forskellige måder, f.eks.:
    - _Fortæl mig om bjerge._
    - _Hvad ved du om grænsen?_
2. Diskutér, hvorfor de kan give upræcise svar, og omskriv dem til mere præcise prompts, f.eks.:
    - _Hvilket bjerg er det højeste i verden?_
    - _Hvad er funktionen af grænsen mellem to lande?_
3. Vurder, hvordan specifikke prompts skaber mere nyttige svar.