---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/retrieval-argumented-generation/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-04T08:40:24.665+01:00"}
---

**Retrieval-Augmented Generation (RAG)** er en teknik, der hjælper AI-modeller med at blive bedre til at finde og bruge information fra eksisterende kilder, så de kan give bedre svar.

Forestil dig, at du skal besvare et spørgsmål, men du ved ikke svaret lige med det samme. I stedet for at forsøge at finde svaret alene, går du på internettet eller kigger i en bog for at finde information. Når du har fundet den, bruger du den til at give et godt og præcist svar.

Det er præcis det, **RAG** gør. Modellen søger efter information i en stor mængde tekst (som en database, et dokument eller internettet), og når den har fundet noget, bruger den denne information til at generere et bedre svar.

Så i stedet for at stole på sin egen hukommelse, kan AI'en “hente” den viden, den mangler, og derefter “skabe” et svar baseret på den. Dette gør svarene mere præcise og relaterede til det, brugeren spørger om.

**Hvordan fungerer det?**

1. **Søgning**: Modellen kigger først efter relevant information. Det kan være i en tekstbase, et dokument eller et API.
    
2. **Generering**: Når den har fundet noget nyttigt, bruger modellen denne information til at skabe et svar. Dette svar er baseret på de fakta, den har fundet.
    

Denne teknik er virkelig nyttig, fordi den gør AI'en mere kraftfuld og præcis, da den ikke bare gætte på svar, men faktisk bruger den nyeste og mest relevante information, den kan finde.

Så kort sagt, **RAG** er som at give en AI en evne til at “researchere” før den svarer!

## Øvelser
> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Retrieval Argumented Generation Prompting. Øvelserne skal være til for at gøre forståelsen for Retrieval Argumented Generationprompring lettere at forstå. Kom med 5 bud
### 1. **RAG med Ekstern Viden**

- **Formål:** Øv retrieval-delen af RAG ved at hente ekstern information og generere svar baseret på den.
- **Øvelse:** Giv deltagerne et spørgsmål, som ikke kan besvares korrekt uden ekstern viden. Brug en retrieval-algoritme (f.eks. Elasticsearch, eller en simpel nøgleordsøgning) til at hente de mest relevante dokumenter. Generér derefter et svar ved hjælp af en LLM (som GPT-4) baseret på de fundne dokumenter.

**Eksempel:**

- Spørgsmål: “Hvad er den nyeste opdagelse inden for kvantecomputing?”
- Retrieval: Find de tre nyeste artikler eller forskning om kvantecomputing.
- Generering: Brug LLM til at sammenfatte de fundne informationer til et præcist og opdateret svar.

**Mål:** Forstå hvordan retrieval kan forsyne LLM med relevant viden, som den kan bruge til at generere et bedre og mere præcist svar.

### 2. **Forbedring af Svar med RAG**

- **Formål:** Demonstrere hvordan retrieval forbedrer svarene genereret af en LLM.
- **Øvelse:** Giv deltagerne en generativ prompt, hvor de først forsøger at generere et svar uden retrieval, og derefter bruger retrieval for at hente relevant information og forbedre svaret.

**Eksempel:**

- Spørgsmål uden retrieval: “Hvordan virker maskinlæring?”
- Genereret svar uden retrieval: LLM forsøger at give et svar på baggrund af dens træning.
- Retrieval: Find et dokument om maskinlæring.
- Generering med retrieval: Brug de fundne informationer til at forbedre svaret.

**Mål:** Øv dig i at forstå, hvordan retrieval kan give LLM'en adgang til nøjagtig og relevant viden, som kan forbedre svaret.

### 3. **Opbygning af en Retrieval Pipeline**

- **Formål:** Øv opbygningen af en retrieval-pipeline, hvor dokumenter hentes og bruges til at generere svar.
- **Øvelse:** Byg en simpel retrieval-pipeline, der bruger et dokumentindeks (fx et tekstkorpus eller et API) til at hente relevante oplysninger og derefter generere et svar ved hjælp af en LLM. Inkluder trin som at vælge et passende dokument, generere et prompt til LLM’en, og integrere LLM's output med de retrievede data.

**Eksempel:**

- Spørgsmål: “Hvordan kan man træne en neuralt netværk?”
- Retrieval: Find relevante artikler om træning af neurale netværk.
- LLM genererer et svar baseret på de fundne artikler.

**Mål:** Øv opbygningen af et effektivt workflow, der kombinerer retrieval og LLM-generation til at producere præcise svar.

### 4. **Håndtering af Uenigheder i Retrieval**

- **Formål:** Øv at generere svar, når retrieval-resultaterne indeholder modstridende eller ufuldstændige informationer.
- **Øvelse:** Giv deltagerne et spørgsmål, hvor retrieval henter modstridende eller ikke-helt-relevant information, og bed dem om at generere et svar, der adresserer denne usikkerhed. Brug LLM til at generere et svar, der enten afspejler flere perspektiver eller håndterer modstridende informationer på en hensigtsmæssig måde.

**Eksempel:**

- Spørgsmål: “Hvad er den højeste bygning i verden?”
- Retrieval: Find information om Burj Khalifa, men også om andre bygninger, der påstår at være højere (f.eks. futuristiske projekter).
- Generering: LLM giver et svar, der både anerkender den aktuelle rekord og nævner kommende projekter.

**Mål:** Øv hvordan retrieval og generativ model kan bruges til at håndtere uenigheder og usikkerheder i svar.

### 5. **Langsigtet Information Retrieval**

- **Formål:** Lær at bruge RAG til at hente information over længere tid og generere svar baseret på historisk eller kompleks data.
- **Øvelse:** Giv deltagerne et spørgsmål, der kræver historisk viden eller en dybdegående forklaring, som ikke nødvendigvis kan besvares med én retrieval. Instruer dem i at hente flere kilder, syntetisere information og derefter generere et overbevisende svar, der tager hensyn til hele konteksten.

**Eksempel:**

- Spørgsmål: “Hvordan har kunstig intelligens udviklet sig over de sidste 50 år?”
- Retrieval: Find flere artikler og kilder om AI’s udvikling fra de sidste fem årtier.
- Generering: Brug LLM til at syntetisere udviklingen og lave en tidslinje eller sammenfatte nøglepunkter.

**Mål:** Øv hvordan retrieval af dybdegående og langsigtede informationer kan bruges til at generere detaljerede og nuancerede svar.