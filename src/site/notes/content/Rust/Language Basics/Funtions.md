---
{"dg-publish":true,"permalink":"/content/rust/language-basics/funtions/","title":"Scalar","tags":["Rust"]}
---

> [!tldr]
> Content

> [!summary]
> Content

Funktioner er udbredte i Rust-kode. Du har allerede set en af de vigtigste funktioner i sproget: `main`, som er indgangspunktet for mange programmer. Du har også set nøgleordet `fn`, som giver dig mulighed for at erklære nye funktioner.

Rust-kode bruger snake case som den konventionelle stil for funktions- og [[content/Rust/Language Basics/Variables\|variabelnavne]], hvor alle bogstaver er små, og understregninger adskiller ord. Her er et program, der indeholder et eksempel på en funktionsdefinition:

```rust
fn main() {
    println!("Hello, world!");

    another_function();
}

fn another_function() {
    println!("Another function.");
}
```

En funktion i Rust er defineret ved at skrive `fn` efterfulgt af et funktionsnavn og et sæt parenteser. 
De krøllede parenteser`{...}` fortæller compileren, hvor funktionskroppen begynder og slutter.

Enhver funktion kan kaldes, vi har defineret, ved at skrive dens navn efterfulgt af et sæt parenteser. Fordi `another_function` er defineret i programmet, kan den kaldes inde fra hovedfunktionen. Bemærk, at vi definerede `another_function` efter hovedfunktionen i kildeteksten; vi kunne også have defineret den før. Rust er ligeglad med, hvor du definerer dine funktioner, så længe de er defineret et sted i et scope, der kan ses af den kaldende funktion.

### Parameters
Funktioner kan defineres til at have parametre, som er specielle [[content/Rust/Language Basics/Variables\|variabler]], der er en del af en funktions signatur. 
Når en funktion har parametre, kan du give den konkrete værdier for disse parametre. Teknisk set kaldes de konkrete værdier for argumenter, men i almindelig samtale bruger folk ofte ordene parameter og argument ombytteligt, enten for [[content/Rust/Language Basics/Variables\|variablerne]] i en funktions definition eller de konkrete værdier, der sendes ind, når du kalder en funktion.

I denne version af `another_function` tilføjer vi en parameter:
```rust
fn main() {
    another_function(5);
}

fn another_function(x: i32) {
    println!("The value of x is: {x}");
}
```

### Statements og Expressions
Funktionskroppe består af en række udsagn, der eventuelt afsluttes med et udtryk. Indtil nu har de funktioner, vi har dækket, ikke inkluderet et afsluttende udtryk, men du har set et udtryk som en del af et udsagn. 

**Fordi Rust er et udtryksbaseret sprog, er denne forskel vigtig at forstå.** 

Andre sprog har ikke de samme skel, så lad os se på, hvad udsagn og udtryk er, og hvordan deres forskelle påvirker funktionskroppe.

**- Udsagn** er instruktioner, der udfører en handling og ikke returnerer en værdi.
**- Udtryk** evalueres til en resulterende værdi. Lad os se på nogle eksempler.

Oprettelse af en variabel og tildeling af en værdi til den med nøgleordet `let` er et udsagn. I Listing 3-1 er `let y = 6;` et udsagn.
```rust
fn main() {
    let y = 6;
}
```
Funktionsdefinitioner er også udsagn; hele det foregående eksempel er et udsagn i sig selv.

Udsagn returnerer ikke værdier. Derfor kan du ikke tildele et `let`-udsagn til en anden variabel, som følgende kode forsøger at gøre; du vil få en fejl:
```rust
fn main() {
    let x = (let y = 6);
}
```
Hvis ovenstående kode bliver smidt ind i kompileren kommer følgende ud:
```sh
$ cargo run
   Compiling functions v0.1.0 (file:///projects/functions)
error: expected expression, found `let` statement
 --> src/main.rs:2:14
  |
2 |     let x = (let y = 6);
  |              ^^^
  |
  = note: only supported directly in conditions of `if` and `while` expressions

warning: unnecessary parentheses around assigned value
 --> src/main.rs:2:13
  |
2 |     let x = (let y = 6);
  |             ^         ^
  |
  = note: `#[warn(unused_parens)]` on by default
help: remove these parentheses
  |
2 -     let x = (let y = 6);
2 +     let x = let y = 6;
  |

warning: `functions` (bin "functions") generated 1 warning
error: could not compile `functions` (bin "functions") due to 1 previous error; 1 warning emitted
```

### Funktioner med retur værdi
Funktioner kan returnere værdier til den kode, der kalder dem. Men navngiver ikke returværdier, men vi skal erklære deres type efter en pil (->). 
I Rust er returværdien af funktionen synonym med værdien af det sidste udtryk i blokken af funktionskroppen. 
Du kan returnere tidligt fra en funktion ved at bruge nøgleordet `return` og specificere en værdi, men de fleste funktioner returnerer implicit det sidste udtryk. Her er et eksempel på en funktion, der returnerer en værdi:
```rust
fn five() -> i32 {
    5
}

fn main() {
    let x = five();

    println!("The value of x is: {x}");
}
```
