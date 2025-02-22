---
{"dg-publish":true,"permalink":"/publishing/main/ai/prompt-teknikker/zero-shot-prompting/","tags":["⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T11:44:48.999+01:00"}
---

> [!important] Sværhedsgrad
> ⭐

[[Publishing/Main/Noter/Ai/Large language model\|Store sprogmodeller]] som [GPT-3.5 Turbo](https://openai.com/index/gpt-3-5-turbo-fine-tuning-and-api-updates/), [GPT-4](https://openai.com/index/gpt-4/) og [Claude 3](https://www.anthropic.com/news/claude-3-family) er i dag trænet til at følge instruktioner og er blevet trænet på store mængder data. 

Denne store trænings mængde gør modellerne i stand til at udføre visse opgaver uden forudgående eksempler – det kaldes "**zero-shot**" prompting. 

> [!important] Hvad er Zero-Shot
> Zero-shot prompting betyder, at prompten, du bruger til at interagere med modellen, ikke indeholder eksempler eller demonstrationer. Den giver simpelthen instruktionen om, hvad modellen skal gøre, uden at der er brugt yderligere eksempler til at lede modellen.

Vi prøvede et par zero-shot eksempler i den forrige sektion. Her er et af de eksempler, vi brugte (tekstklassifikation):

> [!example] eksempel
**Prompt:**
Klassificer teksten som neutral, negativ eller positiv.  
Tekst: "Frodo og hans venner begiver sig ud på en lang rejse for at ødelægge ringen i Mordor."  
Sentiment:
**Output:**
Positiv

Bemærk, at vi i prompten ovenfor ikke gav modellen eksempler på tekst og deres klassifikationer. [[Publishing/Main/Noter/Ai/Large language model\|LLM'en]] forstår allerede, hvad "sentiment" betyder – det er zero-shot funktionaliteten i spil.

Når zero-shot ikke fungerer godt, anbefales det at give modellen demonstrationer eller eksempler i prompten, hvilket fører til "few-shot" prompting. 

> [!note]- Prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Zero Shot Prompting. Øvelserne skal være til for at gøre forståelsen for zero shot prompring lettere at forstå. Kom med 5 bud


### Øvelse 1: Enkelt formål og outputformat

**Mål:** Forstå vigtigheden af klart defineret output.

- **Opgave:** Bed modellen om at generere en liste over tre fordele ved at bruge kunstig intelligens.
    - **Prompt:** _"List three benefits of using artificial intelligence."_
- **Refleksion:** Undersøg, om outputtet er klart og struktureret. Overvej, om prompten kunne være mere specifik for at forbedre resultatet.

---

### Øvelse 2: Ingen kontekst, men præcision

**Mål:** Lær at fokusere på præcise svar uden at give yderligere kontekst.

- **Opgave:** Stil en specifik forespørgsel og bed modellen om at forklare et begreb som om den taler til en 10-årig.
    - **Prompt:** _"Explain gravity to a 10-year-old."_
- **Refleksion:** Analyser, hvordan modellen klarer at reducere kompleksiteten uden kontekstuelle hints.

---

### Øvelse 3: Optimering af ufuldstændige prompts

**Mål:** Lær at identificere svage punkter i zero-shot prompts og optimere dem.

- **Opgave:** Start med en minimal prompt og forfinede den trinvis.
    - **Trin 1 Prompt:** _"Describe a cat."_
    - **Trin 2 Prompt:** _"Describe a cat in 2-3 sentences, focusing on its physical features and behavior."_
- **Refleksion:** Diskuter forskellen i output mellem de to versioner og hvad der gør den anden bedre.

---

### Øvelse 4: Skift perspektiv eller rolle

**Mål:** Forstå hvordan specifikke roller kan påvirke output.

- **Opgave:** Bed modellen om at svare som en ekspert inden for et felt.
    - **Prompt 1:** _"What is the importance of cybersecurity?"_
    - **Prompt 2:** _"As a cybersecurity expert, explain the importance of cybersecurity."_
- **Refleksion:** Sammenlign output for at se, hvordan rollehints kan ændre svaret.

---

### Øvelse 5: Test af flertydige prompts

**Mål:** Lær hvordan modellen håndterer flertydige eller åbne prompts, og hvordan man kan gøre dem tydeligere.

- **Opgave:** Giv en flertydig prompt og observer resultatet. Optimer den derefter.
    - **Flertydig Prompt:** _"Describe the process."_
    - **Optimeret Prompt:** _"Describe the process of photosynthesis in 2-3 sentences suitable for a high school biology class."_
- **Refleksion:** Identificer, hvordan output ændrer sig, når prompten bliver mere specifik.

---