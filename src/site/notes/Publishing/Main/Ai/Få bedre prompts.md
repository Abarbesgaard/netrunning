---
{"dg-publish":true,"permalink":"/publishing/main/ai/fa-bedre-prompts/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T08:14:30.582+01:00"}
---

Når du arbejder med store sprogmodeller som ChatGPT, er det vigtigt at vide, hvordan du formulerer dine forespørgsler (prompts) for at få **de bedste resultater**. Jo mere *præcis* og *velovervejet* din prompt er, desto bedre vil modellen kunne forstå og svare på det, du behøver.
> [!note] Hvad er en Prompt?
> En _prompt_ er den besked, du giver til en sprogmodel for at få et svar. Det kan være et spørgsmål, en opgave eller bare en forespørgsel, hvor du ønsker en specifik type respons. Sprogmodellen vil generere et svar baseret på den information, du giver i prompten.

## Enkle Teknikker til Bedre Prompts

### 1. [[Publishing/Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot prompting]]

[[Publishing/Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot prompting]] betyder, at du ikke giver modellen nogen specifik instruktion eller eksempler på, hvordan den skal besvare en opgave. Du stoler på, at modellen forstår opgaven ud fra din beskrivelse. Her er ét skud i bøssen.
> [!example] Eksempel
**Prompt:** "Skriv et resumé af denne tekst."
**Resultat:** Modellen vil forsøge at opsummere den tekst, du giver den, uden at du behøver at give specifikke eksempler på, hvordan det skal gøres.

**Fordele:**

- Hurtigt og effektivt, da du ikke behøver at give ekstra information.
- Godt til generelle forespørgsler, hvor du bare ønsker et simpelt resultat.

**Udfordring:**

- Hvis opgaven er kompleks eller har flere nuancer, kan resultatet blive mindre præcist.

### 2. [[Publishing/Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]]

[[Publishing/Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]] er en teknik, hvor du giver modellen et par eksempler på, hvordan du ønsker, at opgaven skal løses, før du stiller den egentlige opgave. Dette hjælper modellen med at forstå, hvad du leder efter, og hvordan den bedst kan besvare din forespørgsel.

> [!example] Eksempel
>"Her er et eksempel på, hvordan du opsummerer en tekst: 
Eksempel 1: 'Teksten handler om miljøforurening og dets indvirkning på økosystemer.' Eksempel 2: 'Denne tekst diskuterer de økonomiske konsekvenser af global opvarmning.'
Nu, opsummer denne tekst: 'Den videnskabelige forskning viser, at klimaforandringer forårsager ændringer i vejrmønstre og ødelæggelse af naturressourcer.'"  
>
**Resultat:** Modellen vil forsøge at generere en opsummering baseret på eksemplerne.


**Fordele:**

- Giver modellen mere kontekst, hvilket kan føre til et mere præcist og målrettet svar.
- Kan anvendes til mere komplekse opgaver.

**Udfordring:**

- Kræver, at du giver relevante eksempler for at hjælpe modellen med at forstå opgaven korrekt.

### 3. Vær Klar og Konkret

En af de nemmeste måder at forbedre din prompt på er at være så specifik som muligt i din forespørgsel. Jo mere præcis du er, desto bedre vil modellen kunne levere et svar, der matcher dine behov.

> [!Eksempel] Uklar Prompt
"Fortæl mig om teknologi."

> [!note] Klarere Prompt
> "Giv mig en oversigt over de nyeste trends inden for kunstig intelligens i 2024."

**Fordele:**

- Modellen får en klar idé om, hvad du ønsker, hvilket øger chancerne for, at den leverer et relevant og præcist svar.

**Udfordring:**

- Du skal tænke på, hvilke oplysninger der er nødvendige, og hvilke du kan undvære.

### 4. Brug Afklarende Spørgsmål

Hvis du får et svar, som ikke helt passer til det, du leder efter, kan du stille opfølgende spørgsmål. Dette hjælper med at finjustere modellen og få mere præcise resultater.

> [!Example] Eksempel
**Prompt:** "Hvad er de vigtigste fordele ved at bruge solenergi?"
**Svar:** "Solenergi er en vedvarende energikilde, der kan reducere CO2-udledningen."
**Opfølgende spørgsmål:** "Kan du give flere eksempler på, hvordan solenergi bruges i praksis?"

**Fordele:**

- Giver mulighed for at dykke dybere ned i emnet og få flere detaljer.

**Udfordring:**

- Det kræver, at du aktivt engagerer dig i at følge op på resultaterne.

## Ekstra Tips til Bedre Prompts

1. **Kontekst er vigtig**: Hvis du arbejder med en specifik opgave, f.eks. en teknisk analyse eller et kodningsproblem, kan det være nyttigt at give modellen lidt baggrundsinformation. Dette kan være med til at få præcise og relevante svar.
    
2. **Undgå at være for vag**: Hvis du spørger om noget generelt, som f.eks. "Hvordan laver jeg en hjemmeside?", kan svaret blive meget bredt. Prøv i stedet at fokusere på, hvad du specifikt ønsker at vide: "Hvordan laver jeg en enkel hjemmeside med HTML og CSS?"
    
3. **Sørg for at give eksempler, når det er muligt**: Hvis du ønsker, at modellen skal følge en bestemt struktur, kan det være nyttigt at give et eksempel på, hvordan du ønsker, at svaret skal se ud.
    

At få bedre prompts handler om at forstå, hvordan du bedst kommunikerer med sprogmodellen. Ved at bruge teknikker som [[Publishing/Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot prompting]] og [[Publishing/Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]], være konkret i din forespørgsel og aktivt stille opfølgende spørgsmål, kan du opnå langt bedre og mere præcise svar. Med disse enkle strategier kan du begynde at finjustere din kommunikation og få langt mere ud af dine interaktioner med sprogmodeller.

[[Publishing/Main/Ai/Advanceret Prompting\|Du kan finde flere teknikker her]]