---
{"dg-publish":true,"permalink":"/content/rust/language-basics/constants/","title":"Constants","hide":true,"tags":["Rust"]}
---

> [!tldr] 
> Konstanter i Rust er altid [[content/Rust/Language Basics/Muteability\|uforanderlige]] og erklæres med `const`. De skal have typeannotering og kan ikke ændres ved runtime.

> [!summary] 
> Konstanter i Rust, erklæret med `const`, er altid uforanderlige og kræver typeannotering. De kan deklareres i ethvert scope og er nyttige for værdier, der bruges mange steder i koden. Konstanter skal sættes til et konstant udtryk og kan ikke ændres ved runtime. At bruge konstanter gør koden mere forståelig og nemmere at vedligeholde, da de giver en centraliseret måde at ændre værdier på, hvis det bliver nødvendigt.

Ligesom uforanderlige [[content/Rust/Language Basics/Variables\|variabler]] er `constants` værdier, der er bundet til et navn og ikke må ændres, men der er nogle få forskelle mellem konstanter og variabler. 

For det første er det **ikke tilladt** at bruge `mut` med konstanter. Konstanter er ikke bare [[content/Rust/Language Basics/Muteability\|uforanderlige]] som standard – de er altid [[content/Rust/Language Basics/Muteability\|uforanderlige]]. Du erklærer konstanter ved hjælp af `const`-nøgleordet i stedet for `let`-nøgleordet, og typen af værdien skal annoteres. 

Konstanter kan erklæres i ethvert scope, inklusive det globale scope, hvilket gør dem nyttige for værdier, som mange dele af koden skal kende til.

Den sidste forskel er, at konstanter kun kan sættes til en konstant udtryk, ikke resultatet af en værdi, der kun kan beregnes ved runtime.

Her er et eksempel på en konstant erklæring:

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

Konstantens navn er `THREE_HOURS_IN_SECONDS`, og dens værdi er sat til resultatet af at multiplicere 60 (antallet af sekunder i et minut) med 60 (antallet af minutter i en time) med 3 (antallet af timer, vi ønsker at tælle i dette program). 

Rust's navngivningskonvention for konstanter er at bruge **store bogstaver** med **understregninger** mellem ord. Kompilatoren er i stand til at evaluere et begrænset sæt operationer ved kompileringstidspunktet, hvilket lader os vælge at skrive denne værdi på en måde, der er lettere at forstå og verificere, i stedet for at sætte denne konstant til værdien 10.800. Se Rust Reference's sektion om konstant evaluering for mere information om, hvilke operationer der kan bruges, når man erklærer konstanter.

Konstanter er gyldige for hele den tid, et program kører, inden for det scope, hvori de blev erklæret. Denne egenskab gør konstanter nyttige for værdier i dit applikationsdomæne, som flere dele af programmet måske skal kende til, såsom det maksimale antal point, som en spiller af et spil må tjene, eller lysets hastighed.

Navngivning af hardcoded værdier, der bruges gennem hele dit program som konstanter, er nyttigt til at formidle betydningen af den værdi til fremtidige vedligeholdere af koden. Det hjælper også at have kun ét sted i din kode, som du skal ændre, hvis den hårdkodede værdi skal opdateres i fremtiden.

| Kilder                                                                            | Beskrivelse  |
| --------------------------------------------------------------------------------- | ------------ |
| [The Book](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)) | om variabler |

