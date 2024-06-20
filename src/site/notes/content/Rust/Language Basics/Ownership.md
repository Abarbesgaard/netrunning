---
{"dg-publish":true,"permalink":"/content/rust/language-basics/ownership/"}
---

> [!tldr] 
> Ownership i Rust dikterer, hvordan hukommelse håndteres uden kørselsoverhead. Det bruger et strengt system, hvor hver værdi har en enkelt ejer, hvilket sikrer sikker og effektiv kode.

> [!summary] 
> Ownership i Rust definerer, hvordan hukommelse håndteres: hver værdi har en unik ejer, der sikrer sikkerhed og effektivitet. Overtrædelse af ownership-regler forhindrer kompilering, men påvirker ikke kørselshastigheden.

Ownership er et sæt regler, der styrer, hvordan et Rust-program håndterer hukommelse. Alle programmer skal administrere, hvordan de bruger computerens hukommelse, mens de kører. Nogle sprog har garbage collection, som regelmæssigt søger efter hukommelse, der ikke længere bruges, mens programmet kører; i andre sprog skal programmøren eksplicit allokere og frigive hukommelsen. 

Rust bruger en tredje tilgang: hukommelse administreres gennem et system af ownership med et sæt regler, som compileren tjekker. Hvis nogen af reglerne overtrædes, vil programmet ikke kompilere. Ingen af ownership-funktionerne vil gøre dit program langsommere, mens det kører.

Fordi ownership er et nyt koncept for mange programmører, tager det lidt tid at vænne sig til. Den gode nyhed er, at jo mere erfaring du får med Rust og reglerne i ownership-systemet, jo lettere vil det være for dig naturligt at udvikle kode, der er sikker og effektiv. 

## Ownership regler
Reglerne for ownership. 
1. Hver værdi i Rust har en `owner`.
2. Der kan kun være én `Owner` ad gangen.
3. Når `Owner` går ud af scope, vil værdien blive frigivet.

## [[content/Rust/Language Basics/Variables\|Variable]] scope
Som det første eksempel på ownership, vil vi se på scope af nogle [[content/Rust/Language Basics/Variables\|variabler]]. Et scope er det område inden for et program, hvor en enhed er gyldig. Betragt følgende [[content/Rust/Language Basics/Variables\|variabel]]:
```rust
let s = "hello";
```
[[content/Rust/Language Basics/Variables\|Variablen]] `s` henviser til en *string literal*, hvor værdien af strengen er Hard Coded i vores programmet. [[content/Rust/Language Basics/Variables\|Variablen]] er gyldig fra det punkt, hvor den er deklareret, indtil slutningen af det aktuelle scope. 
```rust
{                      // s er ikke gyldig her, den er endnu ikke deklareret
    let s = "hello";   // s er gyldig fra dette punkt og fremefter

    // gør noget med s
}                      // dette omfang er nu slut, og s er ikke længere gyldig

```

Med andre ord er der to vigtige tidspunkter her:

- Når `s` kommer i scope, er den gyldig.
- Den forbliver gyldig, indtil den går ud af scope.

På dette tidspunkt er forholdet mellem scope og hvornår [[content/Rust/Language Basics/Variables\|variabler]] er gyldige, lignende det i andre programmeringssprog.


| Kilder                                                                 | Beskrivelse |
| ---------------------------------------------------------------------- | ----------- |
| [The Book](https://chatgpt.com/c/2658fb64-4089-404f-9437-213bf70c2b60) | Ownership   |


