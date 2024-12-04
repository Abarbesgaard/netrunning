---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/prompt-chaining/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T08:51:11.343+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐⭐

> [!important] Hvad er Prompt Chaining
> Prompt Chaining er en avanceret teknik, hvor man *opdeler komplekse opgaver i mindre, mere håndterbare delopgaver.* I stedet for at bede AI'en løse hele problemet på en gang, bygger man en sekvens af prompts, hvor output fra ét trin bliver input til næste trin.

### Hvorfor Prompt Chaining?

Fordele:
- Øget præcision
- Bedre kontrol over processen
- Mulighed for at håndtere komplekse opgaver
- Reducerer risikoen for fejl

## Grundlæggende Struktur

### Typisk Prompt Chaining Workflow:
1. **Opgavedefinition**
2. **Opdeling i delopgaver**
3. **Sekventiel behandling**
4. **Sammenlægning af resultater**

## Praktisk Eksempel: Forskningsrapport-Generator

### Trin 1: Emneudvikling
> [!example] Prompt
> Generer 3 potentielle forskningsemner inden for kunstig intelligens, som er aktuelle og innovative.

### Trin 2: Emnevalg
Nu benytter vi så output'et fra [[Main/Ai/Prompt Teknikker/Prompt Chaining#Trin 1 Emneudvikling\|Trin 1]].
> [!example] Prompt
> Vælg det mest lovende emne fra følgende liste:
>
Begrund valget ud fra:
Videnskabelig relevans
Innovationspotentiale
Samfundsmæssig betydning

### Trin 3: Litteraturoversigt
Nu benytter vi så output'et fra [[Main/Ai/Prompt Teknikker/Prompt Chaining#Trin 2 Emnevalg\|Trin 2]].
> [!example] Prompt
> Præsenter en foreløbig litteraturoversigt for det valgte emne:
> Identificer 5-7 centrale forskningsartikler
> Opsummer hovedkonklusioner
> Påpeg nuværende videnhuller

### Trin 4: Forskningsspørgsmål
Nu benytter vi så output'et fra [[Main/Ai/Prompt Teknikker/Prompt Chaining#Trin 3 Litteraturoversigt\|Trin 3]].
> [!example] Prompt
> Formuler 2-3 præcise forskningsspørgsmål baseret på litteraturoversigten:
>
Forskningsspørgsmålene skal være:
Specifikke
Målbare
Relevante for feltet


### Trin 5: Metodeudvikling
Nu benytter vi så output'et fra [[Main/Ai/Prompt Teknikker/Prompt Chaining#Trin 4 Forskningsspørgsmål\|Trin 4]].
> [!example] Prompt
> Foreslå forskningsmetoder til at besvare forskningsspørgsmålene:
>
Overvej:
Kvalitative metoder
Kvantitative metoder
Blandede metoder

## Avancerede Teknikker

### 1. Kontekst
- Viderefør relevant information mellem trin
- Anvend tidligere outputs som kontekst

### 2. Fejlhåndtering
- Indbyd til selvkritisk evaluering
- Tilføj valideringstrin
- Implementer "check-point" mekanismer

## Eksempel på Kompleks Prompt Chain
> [!example] Trin 1
> Foreslå innovative løsninger på klimakrisen

> [!example] Trin 2
> Evaluer de foreslåede løsningers praktiske implementerbarhed

> [!example] Trin 3
> Beregn potentielle omkostninger og gevinster

> [!example] Trin 4
> Diskuter de etiske implikationer af løsningerne

## Fejl at Undgå

 **Undgå**:
- For store spring mellem trin
- Manglende kontekstoverførsel
- Uklar opgavedefinition

 **Gør**:
- Hold trin simple og fokuserede
- Genbrug relevant kontekst
- Vær specifik i hver prompt

## Tekniske Overvejelser

### Valg af AI-Model
- Forskellige modeller har forskellige styrker
- Vælg model efter opgavetype
- Overvej at skifte model mellem trin

| Model                                                                              | Fordele                                                                                                                                             |
| ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Claude 3](https://claude.ai/)                                                     | - Fremragende til kompleks analytisk tænkning<br>- Høj præcision ved nuancerede problemstillinger<br>- Stærk etisk bevidsthed og kontekstforståelse |
| [GPT-4](https://chatgpt.com/)                                                      | - Overlegen til kreativ skrivning<br>- Kan håndtere lange, sammenhængende tekster<br>- Stærk til kodningsopgaver og programmeringsudfordringer      |
| [Gemini Ultra](https://gemini.google.com/app)                                      | - Multimodal håndtering (tekst, billeder, lyd)<br>- Hurtig ved store datamængder<br>- Særligt stærk til videnskabelige og tekniske analyser         |
| [LLaMA 2](https://www.llama.com/llama2/)                                           | - Open-source model med stor fleksibilitet<br>- God til lokale, mindre kompute-intensive opgaver<br>- Hurtig ved specifikke domeneopgaver           |
| [PaLM 2](https://blog.google/technology/ai/google-palm-2-ai-large-language-model/) | - Enestående til flersproget kommunikation<br>- Stærk matematisk reasoning<br>- God til logiske ræsonnementer og problemløsning                     |
### Prompt Engineering
- Brug klare, specifikke instruktioner
- Anvend eksempler hvor relevant
- Strukturer prompts konsekvent

## Konklusion

Prompt Chaining er en kraftfuld teknik, der tillader os at bygge komplekse AI-løsninger ved systematisk at opdele opgaver og behandle dem i små inkrementelle moduler.

## Kilder
> [!source]- Learn Prompting: Prompt Chaining Technique  
Tilgængelig på: [Prompting Guide](https://www.promptingguide.ai/techniques/prompt_chaining)

## Øvelser
> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til Chain Prompting. Øvelserne skal være til for at gøre forståelsen for Chain prompring lettere at forstå. Kom med 5 bud

### 1. Opgave: Opskriftsgenerator

**Formål:** At demonstrere sekventiel forarbejdning gennem trin.

1. **Prompt 1:** _“Beskriv ingredienserne til en traditionel spaghetti bolognese.”_
2. **Prompt 2:** _“Ud fra ingredienserne, lav en liste over trin til at tilberede retten.”_
3. **Prompt 3:** _“Beskriv, hvordan man præsenterer retten på en tallerken for gæster.”_
4. **Øvelse:** Diskutér, hvordan det hjælper at opdele processen, fremfor at bede om hele opskriften på én gang.

---

### 2. Opgave: Artikelopsummering

**Formål:** At forstå, hvordan komplekse informationer opdeles og bearbejdes.

1. **Prompt 1:** _“Hvad er hovedidéen i denne artikel?”_
2. **Prompt 2:** _“List tre centrale pointer, der støtter hovedidéen.”_
3. **Prompt 3:** _“Skriv en 2-sætningers opsummering af artiklen baseret på de centrale pointer.”_
4. **Øvelse:** Analyser resultatet og evaluer fordelene ved trinvis opbygning af opsummeringen.

---

### 3. Opgave: Skabe en karakter til en historie

**Formål:** At illustrere, hvordan Chain Prompting kan bygge detaljer gradvist.

1. **Prompt 1:** _“Beskriv en karakter, inklusive deres navn, alder og profession.”_
2. **Prompt 2:** _“Giv karakteren et personlighedstræk og en motivation.”_
3. **Prompt 3:** _“Beskriv en konflikt, karakteren står overfor.”_
4. **Øvelse:** Diskutér, hvordan processen skabte en mere nuanceret karakter, sammenlignet med én enkelt prompt.

---

### 4. Opgave: Planlægning af en rejse

**Formål:** At lære, hvordan sekventiel promptning kan nedbryde planlægningsopgaver.

1. **Prompt 1:** _“List tre destinationer, der kunne være interessante for en uge i Italien.”_
2. **Prompt 2:** _“For hver destination, foreslå en aktivitet, der passer til et budget under 100 EUR.”_
3. **Prompt 3:** _“Lav en dagsplan for én af destinationerne.”_
4. **Øvelse:** Evaluer, hvordan denne tilgang hjælper med at organisere og afgrænse valgmuligheder.

---

### 5. Opgave: Løsningsforslag til et komplekst problem

**Formål:** At praktisere brugen af iterative prompts til problemløsning.

1. **Prompt 1:** _“Hvad er de største udfordringer ved fjernarbejde?”_
2. **Prompt 2:** _“For hver udfordring, foreslå en mulig løsning.”_
3. **Prompt 3:** _“Vælg den mest praktiske løsning, og lav en 3-trins implementeringsplan.”_
4. **Øvelse:** Diskutér, hvordan Chain Prompting fører til et mere struktureret løsningsforslag end én lang prompt.