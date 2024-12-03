---
{"dg-publish":true,"permalink":"/main/ai/hvad-er-prompting/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T09:53:20.402+01:00"}
---

## Prompting 
Du kan opnå meget med enkle prompts, men kvaliteten af resultaterne afhænger af, hvor meget information du giver modellen, og hvor godt udformet prompten er. 

En prompt kan indeholde information som *instruktionen* eller spørgsmålet, du sender til modellen, samt andre detaljer som kontekst, input eller eksempler. Du kan bruge disse elementer til at instruere modellen mere effektivt og forbedre kvaliteten af resultaterne.

Lad os starte med et grundlæggende eksempel på en *simpel prompt*:
> [!example] eksempel 1
**Prompt**  Frodo er
**Output:**  en hobbit.

Lad os prøve at forbedre det lidt:

> [!example] eksempel 1 fortsat 
> **Prompt:**
Afslut sætningen:  
Frodo er
**Output:**
en hobbit fra Shire, der påtager sig en episk rejse for at ødelægge Ringen og forhindre den onde Sauron i at få magten.

Med prompten ovenfor instruerer du modellen til at afslutte sætningen. Robotten følger *præcist* det, du har bedt om ("afslut sætningen"). Denne tilgang til at designe effektive prompts for at instruere modellen til at udføre en ønsket opgave kaldes *prompt engineering*.

## Prompt Formatering
Du har nu prøvet en meget simpel prompt ovenfor, eksemplet med Frodo. 

En standard prompt har følgende format:

`<Spørgsmål>?`
eller
`<Instruktion>`

Du kan formatere dette til et QA format, som er standard i mange QA-datasets, på følgende måde:

Q: <Spørgsmål>?
A:

Når du prompt'er på denne måde, kaldes det også [[Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot prompting]], dvs. du prompt'er direkte modellen om at give et svar *uden eksempler eller demonstrationer* om opgaven, du vil have den til at udføre. 

Nogle store sprogmodeller har evnen til at udføre [[Main/Ai/Prompt Teknikker/zero-shot prompting\|zero-shot prompting]], men det afhænger af kompleksiteten og viden om den aktuelle opgave samt de opgaver, modellen er trænet til at udføre godt.

Et konkret eksempel på en prompt er som følger:

**Prompt**  
Hvad er prompt engineering?

Givet det standardformat, der er beskrevet ovenfor, er en populær og effektiv teknik til prompting kendt som [[Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]], hvor du giver eksempler (dvs. demonstrationer). Du kan formatere [[Main/Ai/Prompt Teknikker/Few-shot prompting\|few-shot prompts]] som følger:

**Spørgsmål**?  
**Svar**  
**Spørgsmål**?  
**Svar**  
**Spørgsmål**?  
**Svar**  
**Spørgsmål**?

**Prompt:**  
Dette er fantastisk! // Positiv  
Dette er dårligt! // Negativ  
Wow, den film var fed! // Positiv  
Sikke et forfærdeligt show! //

**Output:**  
Negativ

[[Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompts]] muliggør in-context learning, som er sprogmodellernes evne til at lære opgaver givet et par demonstrationer. 