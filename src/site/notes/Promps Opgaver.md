---
{"dg-publish":true,"permalink":"/promps-opgaver/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-03T10:08:57.061+01:00"}
---

Her er en liste over opgaver. Prøv selv at se om du kan løse dem først før du ser hvordan jeg har svaret.

## Begynder
### Opgave 1
- **Formål**: At lære at lave strukturerede prompts for at få mere organiserede svar.
- **Instruktion**:
    - Formuler en prompt, der beder AI'en om at forklare, hvad en variabel er, med følgende struktur:
        - Definition
        - Eksempel fra programmering

> [!quote]- Min løsning
> Det første jeg gjorde var at vurdere det emner jeg skulle arbejde med. Emnet krævede nok en højre grad af korrekthed end fx en fantasy tekst. Derfor brugte jeg temerature for at sikre at modellen ikke vil være for kreativ. Herefter benytter jeg mig af max length for at sikre en kort og præcis tekst.
> **Prompt**:
> Hvad er en variabel? 
> Når du svarer vil jeg gerne have at du følger denne struktur: 
> 1. definition 
> 2. Eksempel fra programmering 
> temperature 0.2 
> max length 200

> [!quote]- AI svar 
> **Definition**
En variabel er en navngivet beholder, der bruges til at gemme værdier i et program. Variabler gør det muligt at arbejde med data dynamisk, da værdien kan ændres under programmets kørsel. Hver variabel har en type (fx tal, tekst eller boolean), som definerer, hvilken slags data den kan holde.
**Eksempel fra programmering**
I C#:
> ```csharp
int age = 25; // En variabel af typen int, der gemmer alderen som et heltal. 
string name = "Andreas"; // En variabel af typen string, der gemmer et navn.
>```

### Opgave 2
- **Formål**: At lære hvordan man får AI til at generere relevante tags.
- **Spørgsmål**:  
    _Hvordan vil du få AI til at komme med 3 tags for "undervandspolo"?_
    - **Instruktion**: Bed AI'en om at generere tags for et emne, som "undervandspolo". Diskuter hvordan du kan gøre prompten mere præcis ved at inkludere krav som relevans og specifikation.

> [!quote]- Min 1. løsning
> Det første jeg gjorde var at benytte mig af [[Main/Ai/Prompt Teknikker/Prompt Chaining\|Prompt Chaining]] og stille spørgsmålet til GPT om hvad undervandspolo er. 
> Herefter benyttede jeg dette svar i en ny chat og benyttede mig af [[Main/Ai/Prompt Teknikker/Generate knowledge prompting\|Generate knowledge prompting]] for at kunne implementere den generelle viden i den næste chat. 
> Næste trin var at bruge stop sequence og sætte den til `3`. 
> 
> Det var den lange og bøvlede metode, hvorfor ikke få den selv til at gøre dette?
> 
> **Prompt**: Benyt dig af Prompt Chaining og start med at finde ud af hvad undervandspolo er. Herefter skal du benytte dig af Generate knowledge prompting for at kunne bruge denne viden til at gøre følgende. 
> Lav 3 tags til undervandspolo 
> stop sequence 3

> [!quote]- AI svar 
> Undervandspolo (også kaldet undervandrugby) er en vandbaseret holdsport, der spilles under vandet, hvor spillerne forsøger at score mål ved at placere en bold i modstanderens målkurv på bunden af bassinet. Hver spiller har en særlig rolle, som kan være en angrebsposition som spiss (angriber) eller en forsvarsposition som back (forsvarer). Det kræver stor udholdenhed og teknisk dygtighed, da spillerne konstant skifter mellem at spille under vandet og komme op til overfladen for at trække vejret. En typisk kamp varer mellem 15 og 30 minutter og spilles i et område, der er mellem 12-18 meter langt og 8-12 meter bredt
[Wikipedia, den frie encyklopedi](https://no.wikipedia.org/wiki/Undervannsrugby).
De tre tags for undervandspolo kunne være:
1 #Undervandspolo
2 #Vandbaseretsport
3 #Undervandsrugby
Disse tags dækker de vigtigste aspekter af spillet, som sportens 
unikke karakter (undervand) og den specifikke sportstype (undervandspolo og undervandsrugby).
> som du nok kan se kræver min prompt lidt mere arbejde da jeg fik en masse tekst jeg ikke skulle bruge.

> [!quote]- min 2. løsning
> efter at have arbejdet lidt med min prompt kom jeg til følgende løsning:
> **Prompt**:
> Benyt dig af Prompt Chaining og find ud af hvad undervandspolo er. Herefter skal du benytte dig af Generate knowledge prompting for at kunne bruge denne viden til at gøre følgende. 
> Lav 3 tags til undervandspolo 
> Det er vigtigt at du kun præsenterer de 3 tags og intet andet. Alt research du finder ud af skal du undlade fra dit svar. 
> stop sequence 3

> [!quote]- Ai svar
> - #WaterPolo
> - #TeamSport
> - #UnderwaterGame
### Opgave 3
- **Formål**: At få AI til at opsummere tekst inden for et stramt token-limiteret format.
- **Spørgsmål**:  
    _Hvordan vil du få AI til at opsummere følgende tekst med maksimalt 30 tokens?_
    - **Instruktion**: Giv en kort tekst og bed AI'en om at opsummere den i 30 tokens. Diskuter hvordan man kan strukturere prompten for at sikre, at opsummeringen bliver kort og præcis.

> [!quote]- Min løsning

> [!quote]- AI svar 

### Opgave 4
- **Formål**: At få AI til at omformulere tekst på en forståelig og korrekt måde.
- **Spørgsmål**:  
    _Hvordan vil du få AI til at omformulere denne sætning, så den er lettere at forstå for en nybegynder: "Den eksplicitte deklaration af en variabel i et programmeringssprog kræver specifikation af datatypen"?_
    - **Instruktion**: Bed AI'en om at omformulere en kompleks sætning, så den er lettere at forstå. Diskuter hvordan AI'en kan instrueres til at holde sig til en bestemt målgruppe.

> [!quote]- Min løsning

> [!quote]- AI svar 
### Opgave 5
- **Formål**: At få AI til at kategorisere et emne korrekt.
- **Spørgsmål**:  
    _Hvordan vil du få AI til at angive en passende kategori for et emne som "Mars"?_
    - **Instruktion**: Bed AI'en om at identificere og tildele en kategori til et emne, f.eks. "Mars". Diskuter hvordan du kan styre AI til at vælge den mest relevante kategori, fx ved at inkludere information om emnets natur (planet, mytologi, etc.).

> [!quote]- Min løsning

> [!quote]- AI svar 