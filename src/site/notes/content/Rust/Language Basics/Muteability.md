---
{"dg-publish":true,"permalink":"/content/rust/language-basics/muteability/","title":"Muteability","hide":true,"tags":["Rust"]}
---

> [!tldr] 
> Rust har immutable [[content/Rust/Language Basics/Variables\|variabler]] som standard, der ikke kan ændres efter initialisering, og mutable variabler, der kan ændres ved at bruge nøgleordet `mut`.

> [!summary] 
> I Rust er [[content/Rust/Language Basics/Variables\|variabler]] som standard immutable, hvilket betyder, at deres værdier ikke kan ændres efter initialisering. Dette øger sikkerheden og forudsigeligheden i kode. Hvis man ønsker, at en variabel skal kunne ændres, bruges nøgleordet `mut`. Immutable variabler fører til kompilatorfejl ved forsøg på ændring, mens mutable variabler tillader værdiændringer efter initialisering. Dette skaber en klar og sikker måde at håndtere variabler på i Rust.


Mutability i Rust handler om, hvorvidt en variabels værdi kan ændres efter dens initialisering. Rust har en stærk skelnen mellem mutable og immutable variabler for at øge sikkerheden og forudsigeligheden i programmering. Her er en grundlæggende note om mutability i Rust med simple eksempler.

# Mutability i Rust

## Immutatble variabler
Standard i Rust er [[content/Rust/Language Basics/Variables\|variabler]] immutable. Det betyder, at når en variabel er tildelt en værdi, kan denne værdi ikke ændres.
```rust
fn main() {
    let x = 5;
    println!("Værdien af x er: {}", x);

    // Følgende linje vil forårsage en fejl:
    x = 6;
}

```
I dette eksempel er `x` en immutable variabel. Hvis vi forsøger at ændre `x`'s værdi, vil kompilatoren give en fejl.
## Muteable Variabler
Hvis du vil have en variabel, der kan ændres, skal du bruge nøgleordet `mut`.
```rust
fn main() {
    let mut y = 5;
    println!("Den oprindelige værdi af y er: {}", y);
    
    y = 6;
    println!("Den ændrede værdi af y er: {}", y);
}
```

Her er `y` en mutable variabel. Vi kan ændre dens værdi efter initialiseringen uden fejl.

| Kilder                                                                           | Beskrivelse                          |
| -------------------------------------------------------------------------------- | ------------------------------------ |
| [The Book](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html) | Rust Book - Variables and Mutability |


