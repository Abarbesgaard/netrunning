---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/few-shot-prompting/","tags":["⭐"],"dgHomeLink":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T11:57:03.978+01:00"}
---

> [!important] Sværhedsgrad
> ⭐


Few-shot prompting er en teknik inden for prompt engineering, hvor du indsætter eksempler i din prompt for at træne modellen til at forstå, hvordan du ønsker, at output skal se ud og lyde.

Denne metode bygger på [[Main/Noter/Ai/Large language model\|LLM'ers]] evne til at lære og generalisere information fra en lille mængde data. Det gør den særligt nyttig, når du ikke har nok data til at finjustere en model.

Her er et meget enkelt eksempel på en few-shot prompt.

Målet med prompten er, at[[Main/Noter/Ai/Large language model\|LLM'en]] skal bestemme sentimentet i en filmanmeldelse.

## Eksempel på few-shot prompting
> [!example] eksempel
> **Prompt**
Filmen var god // positiv  
Filmen var ret dårlig // negativ  
Jeg kunne virkelig godt lide filmen, men slutningen manglede noget // neutral  
JEG ELSKEDE filmen //
> **Output**
> positiv

Som du kan se, sender vi tre par eksempler med data. Denne tilgang hjælper ikke kun modellen med at lære, hvad vi betragter som positivt, negativt eller neutralt, men viser også, at det ønskede outputformat er et enkelt ord med små bogstaver.

Lad os prøve et par eksempler. Først tager vi et eksempel med *tilfældige* labels (hvor labels som Negative og Positive er tilfældigt tildelt inputs):
> [!example] eksempel
**Prompt:**  
This is awesome! // Negative  
This is bad! // Positive  
Wow that movie was rad! // Positive  
What a horrible show! //
**Output:**  
Negative

Vi får stadig det korrekte svar, selvom labels er blevet randomiseret. Bemærk også, at vi holdt formatet konsistent, hvilket hjælper.

> [!example] eksempel
**Prompt:**  
Positive This is awesome!  
This is bad! Negative  
Wow that movie was rad!  
Positive  
What a horrible show! --
**Output:**  
Negative

Der er ingen konsistens i formatet ovenfor, men modellen forudsagde stadig det korrekte label. Vi skal udføre en mere grundig analyse for at bekræfte, om dette gælder for forskellige og mere komplekse opgaver, herunder variationer af prompts.
### Begrænsninger ved Few-shot Prompting
Standard few-shot prompting fungerer godt for mange opgaver, men det er stadig ikke en perfekt teknik, især når det gælder mere komplekse ræsonnementer. 
For nylig er [[Main/Ai/Prompt Teknikker/Chain-of-Thought prompting\|Chain-of-Thought prompting]]blevet populært til at tackle mere komplekse opgaver.

## Konklusion
At give eksempler kan være nyttigt for at løse visse opgaver. Men når [[Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot]] og few-shot prompting ikke er tilstrækkeligt, kan det betyde, at modellen ikke har lært nok til at løse opgaven korrekt. Herfra anbefales det at overveje at finjustere dine modeller eller eksperimentere med mere avancerede prompting-teknikker.

> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Few-Shot Prompting. Øvelserne skal være til for at gøre forståelsen for Few-Shot prompring lettere at forstå. Kom med 5 bud


### **1. Kategorisering af korte sætninger**

**Mål**: Forstå hvordan få eksempler kan guide modellen til at kategorisere tekst.

**Øvelse**:

- Giv modellen følgende prompt:

Classify the following sentences as either "Positive" or "Negative":  
Example 1: Sentence: "I love this weather!" Category: Positive  
Example 2: Sentence: "This is the worst experience ever." Category: Negative  

Sentence: "{din sætning her}" Category:`

- Test med forskellige sætninger som input, og se hvordan eksemplerne påvirker klassifikationen.

---

### **2. Færdiggørelse af en opgave**

**Mål**: Illustrere, hvordan modellen kan udføre opgaver baseret på et par demonstrationer.

**Øvelse**:

- Giv modellen denne prompt:

Translate the following English sentences to Danish:  
Example 1: English: "Good morning" Danish: "Godmorgen"  
Example 2: English: "How are you?" Danish: "Hvordan har du det?"  
English: "{din sætning her}" Danish:`

- Prøv med flere engelske sætninger og analyser nøjagtigheden af oversættelserne.

---

### **3. Format transformation**

**Mål**: Demonstrere, hvordan modellen kan transformere data til en ny struktur.

**Øvelse**:

- Brug denne prompt:

Convert the following user data to JSON format:  
Example 1: Input: Name: John Doe, Age: 29, City: Copenhagen 
Output: {"Name": "John Doe", "Age": 29, "City": "Copenhagen"}  
Example 2: Input: Name: Jane Smith, Age: 34, City: Aarhus 
Output: {"Name": "Jane Smith", "Age": 34, "City": "Aarhus"}  

Input: {din data her} Output:`

- Test med forskellige datasæt, og evaluér modellens evne til at lave omformningen.

---

### **4. Kreativ skrivning**

**Mål**: Forstå, hvordan modellen kan generere kreativt indhold baseret på eksempler.

**Øvelse**:

- Prøv med denne prompt:

Write a short poem about nature:  
Example 1: The sun rises high,   In the azure blue sky,   Trees sway in delight,   As birds take their flight.  
Example 2: Rivers flow with grace,   Mountains hold their place,   Nature whispers low,   A beauty we all know.  

Your turn:`

- Undersøg, hvordan forskellige eksempler påvirker tonen og stilen i outputtet.

---

### **5. Spørgsmål-svar øvelse**

**Mål**: Demonstrere, hvordan modellen kan svare præcist ved hjælp af få eksempler.

**Øvelse**:

- Prøv denne prompt:

Answer the following questions based on the context provided:  
Example 1: Context: "The Eiffel Tower is located in Paris, France." 
Question: "Where is the Eiffel Tower located?" Answer: "Paris, France."  
Example 2: Context: "The Amazon rainforest is known as the lungs of the Earth." 
Question: "What is the Amazon rainforest known as?" 
Answer: "The lungs of the Earth." 

Context: "{din kontekst her}" 

Question: "{dit spørgsmål her}" Answer:`

- Eksperimentér med forskellige kontekster og spørgsmål for at se, hvor præcis modellen kan være.