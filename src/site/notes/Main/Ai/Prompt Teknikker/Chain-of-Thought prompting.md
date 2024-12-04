---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/chain-of-thought-prompting/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T17:10:35.163+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐⭐

Chain-of-thought (CoT) prompting muliggør for modellen at lave komplekse ræsonnement. Det fungerer ved at modellen ikke kun genererer et endeligt svar, men også de mellemtrin, der fører til konklusionen. 

Dette gør det muligt for modellen at forstå og håndtere mere komplekse opgaver, der kræver mere logik, før den giver et svar.

CoT prompting kan kombineres med [[Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]] for at opnå bedre resultater på mere komplekse opgaver, hvor det er nødvendigt at gøre processen tydelig og dele den op i forståelige trin. 

Denne tilgang hjælper modellen med at forstå, hvordan man løser et problem trin for trin, hvilket kan forbedre præstationen, *især* i situationer, der involverer matematiske beregninger, logik og andre komplekse beslutningstagning.

**Eksempel:**  
Hvis vi tager eksemplet med at finde ud af, om de ulige tal i en gruppe summerer til et lige tal, kan CoT prompting hjælpe modellen med at vise sine mellemtrin:

> [!example] eksempel
De ulige tal i denne gruppe lægges sammen til et lige tal: 4, 8, 9, 15, 12, 2, 1. 
S: Hvis man lægger alle de ulige tal sammen (9, 15, 1) giver det 25. Svaret er Falsk. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 17, 10, 19, 4, 8, 12, 24. 
S: Hvis man lægger alle de ulige tal sammen (17, 19) giver det 36. Svaret er Sandt. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 16, 11, 14, 4, 8, 13, 24. 
S: Hvis man lægger alle de ulige tal sammen (11, 13) giver det 24. Svaret er Sandt. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 17, 9, 10, 12, 13, 4, 2. 
S: Hvis man lægger alle de ulige tal sammen (17, 9, 13) giver det 39. Svaret er Falsk. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 15, 32, 5, 13, 82, 7, 1. 
S: 
**Output:** 
Hvis man lægger alle de ulige tal sammen (15, 5, 13, 7, 1) giver det 41. Svaret er Falsk.

Ved at inkludere disse mellemtrin får modellen ikke kun mulighed for at forstå processen, men også at give et korrekt og begrundet svar. Denne metode er især nyttig, *når opgaven er kompleks*, og der er behov for en logisk progression for at nå frem til den rigtige løsning.


## Øvelser
> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Chain-of-Thought Prompting. Øvelserne skal være til for at gøre forståelsen for Chain-of-Thought prompring lettere at forstå. Kom med 5 bud

### 1. Forklaringsstafetten

**Formål:** Øve trin-for-trin-logik gennem fælles forklaring.

**Opgave:**  
Du får en simpel opgave, fx:  
_"Hvor mange ben har 3 hunde og 2 katte tilsammen?"_

**Øvelse:**

1. Skriv først en kort prompt: _"Forklar trin for trin, hvordan du når frem til svaret."_
2. Studér modelens svar, fx:
    - En hund har 4 ben, så 3 hunde har 12 ben.
    - En kat har 4 ben, så 2 katte har 8 ben.
    - Samlet bliver det 12 + 8 = 20.
3. Gentag med mere komplekse opgaver for at udforske, hvordan modellen håndterer forskellige opgaver.

---

### 2. Hvad sker der bagefter?

**Formål:** Forstå, hvordan sekventiel tænkning fungerer.

**Opgave:**  
Skriv en prompt som:  
_"En mand lægger en kop te på bordet. Hvad kan ske som det næste? Forklar trin for trin."_

**Øvelse:**

1. Skriv tre plausible trin-for-trin-scenarier, der fører til forskellige slutresultater, fx:
    - Trin 1: Koppen vælter, fordi bordet er ujævnt.
    - Trin 2: Teen løber ud på gulvet.
    - Trin 3: Han tørrer det op.
2. Eksperimentér med kreative og realistiske alternativer.

---

### 3. Debugging CoT-logik

**Formål:** Identificere og rette fejl i CoT-processer.

**Opgave:**  
Præsenter en forkert ræsonneret Chain-of-Thought, fx:  
_"En hund har 4 ben. 3 hunde har 4 + 3 = 7 ben."_

**Øvelse:**

1. Skriv en prompt som: _"Dette svar er forkert. Forklar hvorfor, og ret det trin for trin."_
2. Arbejd med modellen om at spotte fejlen og rette den.

---

### 4. Skab din egen kæde

**Formål:** Lære at skabe logiske kæder fra bunden.

**Opgave:**  
Giv en open-ended opgave, fx:  
_"Hvordan planlægger man en fest for 10 personer? Forklar trin for trin."_

**Øvelse:**

1. Lad modellen bryde opgaven op i trin, fx:
    - Bestem dato og tidspunkt.
    - Lav en gæsteliste.
    - Find et passende sted.
2. Eksperimentér med forskellige prompts for at se, hvordan trinnene ændrer sig baseret på promptens formulering.

---

### 5. Konkurrence mellem kort og lang CoT

**Formål:** Sammenligne præcision mellem simple og detaljerede prompts.

**Opgave:**  
Brug to prompts til samme opgave, fx:  
_"Hvad er 45 + 27?"_

- Kort prompt: _"Giv mig svaret."_
- Lang prompt: _"Forklar trin for trin, hvordan du lægger de to tal sammen."_

**Øvelse:**

1. Evaluer forskellene i svarenes kvalitet.
2. Diskutér, hvornår en Chain-of-Thought er nødvendig, og hvornår en simpel tilgang er tilstrækkelig.