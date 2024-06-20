---
{"dg-publish":true,"permalink":"/content/rust/language-basics/data-types/scalar/","title":"Scalar","tags":["Rust"]}
---

> [!tldr] 
> Rust har fire primære scalar typer: **integers**, **floating-point numbers**, **bools**, og **characters**. Derudover har Rust sammensatte typer som **tuples** og **arrays**, der kan gruppere flere værdier sammen. Integers kan være signerede eller usignerede og varierer i størrelse. Floating-point numbers inkluderer `f32` og `f64`. Boolean typen specificeres som `bool` og har værdierne `true` og `false`. Character typen er `char` og kan repræsentere Unicode karakterer. Tuples kan gruppere forskellige typer, mens arrays skal have elementer af samme type.

> [!summary] 
> Scalar typer i Rust repræsenterer en enkelt værdi og inkluderer fire hovedtyper: **integers**, **floating-point numbers**, **booleans** og **characters**. Integers kan være signerede (`i8`, `i16`, `i32`, `i64`, `i128`, `isize`) eller usignerede (`u8`, `u16`, `u32`, `u64`, `u128`, `usize`) og varierer i størrelse. Floating-point numbers (`f32`, `f64`) bruges til tal med decimaler. Boolean typen (`bool`) har to værdier: `true` og `false`. Character typen (`char`) kan repræsentere Unicode karakterer. Rust har også to sammensatte typer: tuples, der kan indeholde forskellige typer, og arrays, der indeholder elementer af samme type og har fast længde.

Scalar typer repræsenterer en enkelt værdi. Rust har 4 primær scalar typer:
1. integers
2. Floating-point
3. Bool
4. Characters

# Integer Types
en integer er et tal uden decimal. fx `u32` indikerer at en [[content/Rust/Language Basics/Variables\|variabel]] er associeret med et usigneret heltal.
Følgende tabel viser en oversigt over int typer i rust:

| Længde  | Signed  | Unsigned |
| ------- | ------- | -------- |
| 8-bit   | `i8`    | `u8`     |
| 16-bit  | `i16`   | `u16`    |
| 32-bit  | `i32`   | `u32`    |
| 64-bit  | `i64`   | `u64`    |
| 128-bit | `i128`  | `u128`   |
| arch    | `isize` | `usize`  |
## Signed vs Unsigned
Hver variant kan enten være signerede eller usignerede og har en eksplicit størrelse. Signerede og usignerede refererer til, om det er **muligt for tallet at være negativt** – med andre ord, om tallet skal have et fortegn (*signeret*), eller om det kun nogensinde vil være positivt og derfor kan repræsenteres uden et fortegn (*usigneret*). 
Det er som at skrive tal på papir: når fortegnet er vigtigt, vises et tal med et plustegn eller et minustegn; men når det er sikkert at antage, at tallet er positivt, vises det uden fortegn. 

Desuden afhænger typerne `isize` og `usize` af arkitekturen på den computer, dit program kører på, hvilket i tabellen betegnes som "arch": 64 bits, hvis du bruger en 64-bit arkitektur, og 32 bits, hvis du bruger en 32-bit arkitektur.

# Floating-point
Rust har også to primitive typer til floating point numbers, som er tal med decimaler. Rust's flydende typer er `f32` og `f64`, som henholdsvis er 32 bit og 64 bit store. Standardtypen er `f64`, fordi det på moderne CPU'er er omtrent lige så hurtigt som `f32`, men er i stand til at levere højere præcision. Alle flydende typer er [[content/Rust/Language Basics/Data Types/Scalar#Signed vs Unsigned\|signed]].
```rust
fn main() {
    let x = 2.0; // f64

    let y: f32 = 3.0; // f32
}
```

## Numeriske Operationer

Rust understøtter de grundlæggende matematiske operationer, du ville forvente for alle taltyper: addition, subtraktion, multiplikation, division og rest. Heltalsdivision afkortes mod nul til nærmeste heltal. 
Følgende kode viser, hvordan du bruger hver numerisk operation i en `let`-erklæring:
```rust
fn main() {
    // addition
    let sum = 5 + 10;

    // subtraction
    let difference = 95.5 - 4.3;

    // multiplication
    let product = 4 * 30;

    // division
    let quotient = 56.7 / 32.2;
    let truncated = -5 / 3; // Results in -1

    // remainder
    let remainder = 43 % 5;
}
```

# Bool
Som i de fleste andre programmeringssprog har en Booleansk type i Rust to mulige værdier: `true` og `false`. Booleans er en byte i størrelse. Den Booleanske type i Rust specificeres ved hjælp af `bool`. For eksempel:

```rust
fn main() {
    let t = true;

    let f: bool = false; // with explicit type annotation
}
```

# Character Type
Rust's `char` type er den mest primitive alfabet type. Her er nogle eksempler:
```rust
fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // with explicit type annotation
    let heart_eyed_cat = '😻';
}
```

# Compound Typer
Sammensatte typer kan gruppere flere værdier til én type. Rust har to primitive sammensatte typer: tuples og arrays.

## Tuple-Typen

En tuple er en generel måde at gruppere en række værdier med forskellige typer i én sammensat type. Tuples har en fast længde: når de først er erklæret, kan de ikke vokse eller skrumpe i størrelse.

Vi opretter en tuple ved at skrive en kommasepareret liste af værdier inde i parenteser. Hver position i tuplen har en type, og typerne af de forskellige værdier i tuplen behøver ikke være de samme. Vi har tilføjet valgfrie typeannoteringer i dette eksempel:
```rust
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```
Dette program opretter først en tuple og binder den til [[content/Rust/Language Basics/Variables\|variablen]] `tup`. Derefter bruger det et mønster med `let` til at tage `tup` og opdele den i tre separate variabler, `x`, `y` og `z`. Dette kaldes destrukturering, fordi det bryder den enkelte tuple ned i tre dele. 
Til sidst udskriver programmet værdien af `y`, som er 6.4.

Vi kan også få adgang til *et element* i tuplen direkte ved at bruge et punktum (.) efterfulgt af indekset for den værdi, vi ønsker at få adgang til. For eksempel:
```rust
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

# Array Typen

En anden måde at have en samling af flere værdier på er med et array. I modsætning til en tuple skal hvert element i et array have samme type. I modsætning til arrays i nogle andre sprog har arrays i Rust en fast længde.

Vi skriver værdierne i et array som en kommasepareret liste inde i firkantede parenteser:
```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
}
```


| Kilder                                                             | Beskrivelse     |
| ------------------------------------------------------------------ | --------------- |
| [The Book](https://doc.rust-lang.org/book/ch03-02-data-types.html) | Om Scalar Types |


