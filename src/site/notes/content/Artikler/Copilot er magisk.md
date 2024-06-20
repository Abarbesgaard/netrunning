---
{"dg-publish":true,"permalink":"/content/artikler/copilot-er-magisk/","tags":["Artikel"]}
---


Efter at jeg installerede GitHub Copilot, opstod der en bemærkelsesværdig forandring. Enhver lille kodebid, jeg forsøgte at skrive, blev pludselig mødt af en strøm af intelligente forslag fra Copilot; Intellisense#.

Tidligere var jeg nødt til at tænke grundigt over hver eneste kodeblok, men nu tillod Copilot mig at skrive komplette metoder uden den samme grad af anstrengelse. Mine tanker og ideer kunne blive omsat til kode på rekordtid. Alt, hvad der krævedes, var et enkelt tryk på tabulatortasten, og så var jeg videre til næste metode.

> _Tab! Ny metode! Tab! Ny Klasse! Stop med at tænke! Tab! Ny Klasse! Ik' Tænk! Tab! Tab! TAB!_

Copilot var ren magi for en studerende, som mig. Jeg følte mig som en fantastisk programmør og kunne lynhurtigt få lavet kode, som sten sikkert var super godt for det kom jo fra sort kasse trænet på over 175 billioner parametre, Tilgner.

> _Tab! Ny metode! Tab! Ny Klasse!_ _Tab! Tab! TAB!_

[![Dette eksempel er fra https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/](https://cskarp2.files.wordpress.com/2024/04/copilot-example.gif?w=600)](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)

Som du forhåbentlig kan fornemme, er der en anelse ironi og sarkasme indlejret i det ovenstående.

Efter cirka 3 måneders brug fornemmede jeg, at jeg begyndte at læne mig for meget op ad den sorte kasse. Jeg ventede på dens svar, og når det kom fra dybet, fortsatte jeg.

> _Skriv indledende kode - **pause** - Copilot Magic - tab - fortsæt_

Hvor jeg før skriv kode som

```
public string FunMethod(){
// masser af super fantastisk kode
}
```

Skrev jeg i stedet:

```
public str
```

Copilot tog styringen derfra. Jeg er godt klar over at jeg kan undlade at benytte mig af forslaget fra Copilot men tab-tasten er nu lokkende når en løsning bliver præsenteret umiddelbart.

## Copilot Pausen

For nylig så jeg en video kaldet "Why I'm No Longer Using Copilot"[Dreams of Code], som støttede min beslutning om ikke at benytte Copilot; i hvert fald ikke som studerende.

I denne video snakker manden bag youtube kanalen "Dreams of Code" om begrebet "==Copliot Pause==", og her var det som om at brikkerne faldt på plads for mig. Det var præcis hvad jeg oplevede. Som nævnt tidligere var det ren magi at vente og se hvad Copilot spyttede ud af ny magisk kode; som jeg kun knap nok forstod 10% af. Det var storartet at se hvordan en løsning kunne se ud. Men det var ikke _min løsning_. Det var ikke mig der var kommet frem til den.Ved at Copilot overtog kodningen fuldstændig føltes det som om, jeg mistede forbindelsen til den kreative proces, den personlige investering i min egen kode og ikke mindst logikken bag.

Den seneste forskning præsenteret af [Harding] og hans kolleger belyser en bekymrende udvikling vedrørende vedligeholdelse og kvalitet af kode, der er genereret med hjælp fra AI sammenlignet med kode, der er håndskrevet af mennesker. Specifikt viser undersøgelsen, blandt andet, at GitHub Copilot ofte afviger fra principperne om DRY (Don't Repeat Yourself).

I forskningsartiklen Coding on Copilot står der at GitHub hævder, at kode skrives "55% hurtigere" med Copilot, men det rejser spørgsmålet om kvaliteten af den producerede kode. Ifølge Robert Martin, forfatteren til _"Clean Code: A Handbook of Agile Software Craftsmanship"_, bruger kode 10 gange mere tid på at blive læst end på at blive skrevet.

Derfor kan det, at skrive dårlig kode hurtigere, medføre betydelige udfordringer for dem, der senere skal læse og vedligeholde den. Harding forstætter med at pointere at er afgørende at huske, at hastigheden af kodeproduktion ikke må gå på kompromis med kvaliteten af koden, da en hurtigere skriveproces kan føre til langvarige problemer for dem, der skal arbejde med koden i fremtiden.

## **Anbefalinger til studerende**

Personligt, vil jeg **ikke** anbefale at man, som studerende, benytter sig af en Ai-pair programmer. Jeg indrømmer gerne at det er sjovt at lege med - men jeg blev ikke en bedre programmør.

Jeg foretrækker at skrive 300 linjers kode, selvom den måske er håbløs, fordi jeg forstår den fuldt ud og kan forklare præcis, hvorfor den er så håbløs. Det er, for mig, bedre end at få genereret 30_000 linjers kode, der er perfekt udført, men hvor jeg ikke har nogen forståelse for den bagvedliggende logik.

Jeg forstår det som at være studerende at man går på jagt efter læring, blive frustreret og finde løsninger. En AI-assisteret pair programmer, som Github Copilot, selvom den kan være fristende med sin hurtighed og effektivitet, kan let føre til en _passiv_ tilgang til kodning, hvor man blot accepterer de foreslåede løsninger uden at forstå baggrunden eller processen bag dem.

Dette kan i sidste ende begrænse ens evne til at _udvikle dybdegående forståelse_ og _kritisk tænkning_ inden for kodning. Derfor er det vigtigt for studerende at være opmærksomme på de potentielle faldgruber ved at stole for meget på AI-assisteret kodning.

## Copilot alternativ

Knofedt. Jeg ser det som en del af læringen at skrive dårlig kode, se at det er dårlig kode også komme med bud på hvordan koden kan forbedres. I min optik er dårlig kode en gylden mulighed for at lære. At granske ens tidligere kode og skære ansigt i væmmelse er en af de mest givende oplevelser for en programmør.  
Dette signalerer ikke blot en opnået indsigt, men også muligheden for at optimere koden til en mere effektiv løsning.  
Hvis du vil vide mere om refaktorering kan du læse mere [her](https://cskarp2.wordpress.com/2024/03/20/hva-fanden-er-refaktorering/), om hvornår og hvordan man skal gøre det.

## Kildehenvisninger

Harding, W., & Kloster, M. (2024). Coding on Copilot: 2023 Data Shows Downward Pressure on Code Quality. Alloy.dev Research. Published January 16, 2024.

Tilgner, Aidan. "A Deep Dive Into GitHub Copilot: How GitHub Copilot Works Under the Hood." _Better Programming_, November 10, 2021. Kan findes her: [https://betterprogramming.pub/ai-review-github-copilot-d43afde51a5a](https://betterprogramming.pub/ai-review-github-copilot-d43afde51a5a).

Dreams of Code. "Why I'm No Longer Using Copilot." _Dreams of Code_, YouTube video, 30 March 2024. Accessed April 7, 2024.
