---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/prompt-chaining/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T08:51:11.343+01:00"}
---

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
