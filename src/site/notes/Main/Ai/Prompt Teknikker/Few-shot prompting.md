---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/few-shot-prompting/","tags":["⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T11:57:03.978+01:00"}
---

> [!important] Sværhedsgrad
> ⭐


Few-shot prompting er en teknik inden for prompt engineering, hvor du indsætter eksempler i din prompt for at træne modellen til at forstå, hvordan du ønsker, at output skal se ud og lyde.

Denne metode bygger på [[Main/Noter/Large language model\|LLM'ers]] evne til at lære og generalisere information fra en lille mængde data. Det gør den særligt nyttig, når du ikke har nok data til at finjustere en model.

Her er et meget enkelt eksempel på en few-shot prompt.

Målet med prompten er, at[[Main/Noter/Large language model\|LLM'en]] skal bestemme sentimentet i en filmanmeldelse.

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