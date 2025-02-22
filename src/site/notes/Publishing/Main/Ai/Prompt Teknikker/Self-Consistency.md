---
{"dg-publish":true,"permalink":"/publishing/main/ai/prompt-teknikker/self-consistency/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-04T08:25:04.341+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐⭐⭐

### **Hvad er Self-Consistency i prompt engineering?**

Self-Consistency handler om at sikre, at et AI-modellen giver konsistente, pålidelige og gennemtænkte svar. Det gør vi ved at "spørge modellen flere gange" om det samme og derefter vælge det bedste svar ud fra, hvad der går mest igen eller virker mest logisk.

### **Hvordan fungerer det?**

Forestil dig, at du spørger en gruppe mennesker om, hvad der er det bedste måltid til middag. Hvis flertallet siger "pizza", er det nok et godt valg. Det samme gælder her:

1. Du skriver din prompt (spørgsmål eller opgave).
2. Modellen giver flere svar (ofte ved at blive kørt flere gange).
3. Du samler svarene og finder det svar, der enten gentager sig mest eller virker mest gennemtænkt.

### **Hvorfor er det smart?**

- **Kvalitetssikring**: Når vi spørger modellen flere gange, undgår vi "skæve" svar.
- **Bedre logik**: Modellen har flere chancer for at komme med kreative og logiske løsninger.

### **Et simpelt eksempel**

Du spørger AI'en:  
_Hvad kan jeg lave af en banan til dessert?_

Hvis du kører Self-Consistency, får du måske disse svar:

1. Lav en banansplit. 
2. Bag en banankage. 
3. Lav en smoothie. 
4. Lav en banansplit. 
5. Lav en banansplit. 

Her vælger vi "banansplit", fordi det går igen flest gange og derfor sandsynligvis er det bedste svar.

## Øvelser 
> [!note]- prompt brugt til at lave øvelserne
> Du er prompting ekspert og skal lave 5 bud på øvelser til self-consistencyPrompting. Øvelserne skal være til for at gøre forståelsen for self-consistency prompring lettere at forstå. Kom med 5 bud


### Øvelse 1: **Find det bedste svar ved gentagelse**

**Mål:** Forstå hvordan Self-Consistency hjælper med at finde det mest konsistente svar.

**Opgave:**

- Stil modellen et simpelt spørgsmål, f.eks. "Hvad er de bedste øvelser for at styrke ryggen?"
- Kør prompten 5 gange og få 5 forskellige svar.
- Vurder hvilke svar der gentager sig eller virker mest konsistente, og vælg det bedste.
- Diskuter, hvorfor det valgte svar virker mest pålideligt.

**Formål:** Øvelsen lærer deltagerne at se, hvordan gentagelse og konsistens i svarene kan pege på den bedste løsning.

---

### Øvelse 2: **Sammenlign flere forslag**

**Mål:** Forstå hvordan man vælger det mest gennemtænkte svar ud fra flere muligheder.

**Opgave:**

- Stil modellen et spørgsmål som "Hvordan kan jeg forbedre min produktivitet på arbejdet?"
- Kør prompten 3 gange og få 3 forskellige svar.
- Vurder om svarene er ensartede, eller om de har forskellige perspektiver.
- Vælg det svar, der giver mest mening på baggrund af din erfaring.
- Diskuter i grupper, hvorfor du valgte det svar, der virker mest konsistent.

**Formål:** Øvelsen viser, hvordan man kan bruge flere svar til at finde et sammenhængende og brugbart resultat.

---

### Øvelse 3: **Vurder variationer i svar**

**Mål:** Lære at håndtere forskellige meninger og vælge det mest relevante svar.

**Opgave:**

- Stil modellen et spørgsmål som "Hvilken film er bedst til en familiefest?"
- Kør prompten 4 gange og få 4 forskellige svar.
- Vurder variationerne i svarene: Er de meget forskellige, eller er der nogle gentagelser?
- Vælg det svar, der lyder mest passende for din situation, og forklar hvorfor du valgte det.

**Formål:** Øvelsen hjælper deltagerne med at identificere, hvordan selv små variationer kan påvirke, hvilket svar der er det bedste.

---

### Øvelse 4: **Brug Self-Consistency til beslutningstagning**

**Mål:** Forstå hvordan Self-Consistency kan hjælpe med at træffe beslutninger.

**Opgave:**

- Stil modellen et beslutningsspørgsmål, f.eks. "Skal jeg tage toget eller flyve til min ferie?"
- Kør prompten 3-4 gange og få forskellige forslag med fordele og ulemper.
- Vurder hvilke forslag der er mest konsistente, og brug disse til at træffe en informeret beslutning.
- Diskuter med en partner, hvordan Self-Consistency hjalp dig med at træffe dit valg.

**Formål:** Øvelsen lærer deltagerne at bruge flere svar til at træffe velovervejede beslutninger.

---

### Øvelse 5: **Test mod en kendt løsning**

**Mål:** Forstå hvordan Self-Consistency kan hjælpe med at finde den mest pålidelige løsning.

**Opgave:**

- Stil modellen et teknisk spørgsmål som "Hvordan opretter jeg en database i MongoDB?"
- Kør prompten 3-5 gange og få forskellige trin-for-trin-vejledninger.
- Sammenlign svarene med din egen viden om, hvordan man opretter en database i MongoDB.
- Vurder, hvilket svar der er mest præcist og konsistent med de bedste praksisser.
- Diskuter i grupper, hvordan Self-Consistency kan hjælpe med at forbedre nøjagtigheden af de løsninger, der gives.

**Formål:** Øvelsen viser, hvordan man kan bruge flere svar til at vurdere præcision og finde den mest pålidelige løsning.