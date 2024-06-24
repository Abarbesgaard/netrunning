---
{"dg-publish":true,"permalink":"/content/rust/language-basics/shadowing/","title":"Shadowing","hide":true,"tags":["Rust"]}
---

> [!tldr] 
> Shadowing i Rust tillader, at en ny variabel kan erklæres med samme navn som en tidligere variabel, og overskriver den oprindelige værdi i den nye scope.   

> [!summary] 
> Shadowing i Rust gør det muligt at erklære en ny [[content/Rust/Language Basics/Variables\|variabel]] med samme navn som en tidligere variabel. Dette skaber en ny [[content/Rust/Language Basics/Variables\|variabel]], som overskygger den oprindelige [[content/Rust/Language Basics/Variables\|variabel]] inden for den nye scope. Shadowing tillader transformationer af en [[content/Rust/Language Basics/Variables\|variabels]] værdi og type uden at ændre [[content/Rust/Language Basics/Variables\|variabel]] selv. Dette er anderledes end at bruge `mut`, da Shadowing tillader at ændre typen på [[content/Rust/Language Basics/Variables\|variablen]] ved at bruge `let` igen. Dette gør koden mere fleksibel og nemmere at læse, da man undgår behovet for at finde på forskellige navne til [[content/Rust/Language Basics/Variables\|variabler]] af forskellig type.

### Shadowing

Du kan erklære en ny [[content/Rust/Language Basics/Variables\|variabel]] med samme navn som en tidligere [[content/Rust/Language Basics/Variables\|variabel]]. Man siger, at den første variabel er skygget af den anden, hvilket betyder, at den anden variabel er det, kompilatoren vil se, når du bruger variabelnavnet. Effektivt skygger den anden [[content/Rust/Language Basics/Variables\|variabel]] den første, og tager alle brug af [[content/Rust/Language Basics/Variables\|variabelnavnet]] til sig selv, indtil den selv er skygget eller scopet slutter. Vi kan skygge en [[content/Rust/Language Basics/Variables\|variabel]] ved at bruge det samme variabelnavn og gentage brugen af `let`-nøgleordet som følger:

Filnavn: `src/main.rs`

```rust
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("Værdien af x i den indre scope er: {x}");
    }

    println!("Værdien af x er: {x}");
}
```

Dette program binder først `x` til værdien 5. Derefter skaber det en ny [[content/Rust/Language Basics/Variables\|variabel]] `x` ved at gentage `let x =`, tage den oprindelige værdi og lægge 1 til, så værdien af `x` derefter er 6. Derefter, inden for et indre scope oprettet med krøllede parenteser, skygger den tredje `let`-erklæring også `x` og skaber en ny [[content/Rust/Language Basics/Variables\|variabel]], der multiplicerer den tidligere værdi med 2, så `x` får værdien 12. Når det scope slutter, slutter den indre skygning, og `x` vender tilbage til at være 6. Når vi kører dette program, vil det udskrive følgende:
```sh
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
     Running `target/debug/variables`
Værdien af x i den indre scope er: 12
Værdien af x er: 6

```

Skygning er forskellig fra at markere en [[content/Rust/Language Basics/Variables\|variabel]], som `mut`, fordi vi får en kompileringstidfejl, hvis vi ved et uheld forsøger at tildele denne [[content/Rust/Language Basics/Variables\|variabel]] uden at bruge `let`-nøgleordet. Ved at bruge `let` kan vi udføre nogle transformationer på en værdi, men have variablen være uforanderlig efter disse transformationer er fuldført.

Den anden forskel mellem `mut` og skygning er, at fordi vi effektivt opretter en ny [[content/Rust/Language Basics/Variables\|variabel]], når vi bruger `let`-nøgleordet igen, kan vi ændre typen af værdien, men genbruge det samme navn. For eksempel, hvis vores program beder en bruger om at vise, hvor mange mellemrum de ønsker mellem noget tekst ved at indtaste mellemrumstegn, og vi derefter vil gemme denne indtastning som et tal:
```rust
let spaces = "   ";
let spaces = spaces.len();
```
Den første `spaces` [[content/Rust/Language Basics/Variables\|variabel]] er en strengtype, og den anden `spaces` [[content/Rust/Language Basics/Variables\|variabel]] er en taltype. Skygning sparer os således fra at skulle finde på forskellige navne, såsom `spaces_str` og `spaces_num`; i stedet kan vi genbruge det enklere `spaces` navn. Men hvis vi forsøger at bruge `mut` til dette, som vist her, vil vi få en kompileringstidfejl:
```rust
let mut spaces = "   ";
spaces = spaces.len(); // [Denne kode kompilerer ikke!]
```

Fejlen siger, at vi ikke må ændre en [[content/Rust/Language Basics/Variables\|variabels]] type:

```sh
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
error[E0308]: mismatched types
 --> src/main.rs:3:14
  |
2 |     let mut spaces = "   ";
  |                      ----- expected due to this value
3 |     spaces = spaces.len();
  |              ^^^^^^^^^^^^ expected `&str`, found `usize`
  |
help: try removing the method call
  |
3 -     spaces = spaces.len();
3 +     spaces = spaces;
  |

For more information about this error, try `rustc --explain E0308`.
error: could not compile `variables` (bin "variables") due to 1 previous error
```


| Kilder                                                                            | Beskrivelse  |
| --------------------------------------------------------------------------------- | ------------ |
| [The Book](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)) | om Shadowing |



