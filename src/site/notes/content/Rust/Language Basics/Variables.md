---
{"dg-publish":true,"permalink":"/content/rust/language-basics/variables/","title":"Variables","tags":["Rust"]}
---


> [!tldr] 
> Variabler i Rust er som standard [[content/Rust/Language Basics/Muteability\|uforanderlige]]. Brug `mut` for at gøre dem [[content/Rust/Language Basics/Muteability\|foranderlige]].

> [!summary] 
> Rust's variabler er [[content/Rust/Language Basics/Muteability\|uforanderlige]] som standard, hvilket hjælper med at forhindre bugs og gør koden mere sikker og lettere at forstå. Du kan dog gøre en variabel [[content/Rust/Language Basics/Muteability\|foranderlig]] ved at bruge `mut`, hvilket tillader ændring af dens værdi. 

**Variabler** som standard [[content/Rust/Language Basics/Muteability\|uforanderlige]] (**immutable**) i Rust. Dette er en af de mange måder, hvorpå Rust opfordrer dig til at skrive din kode på en måde, der drager fordel af sikkerheden og concurrency, som Rust tilbyder. 
Du har dog stadig mulighed for at gøre dine variabler [[content/Rust/Language Basics/Muteability\|foranderlige]]. 

Når en variabel er *uforanderlig*, kan du **ikke ændre** værdien, når den først er bundet til et navn. For at illustrere dette, skal du oprette et nyt projekt kaldet `variables` i din projektmappe ved at bruge `cargo new variables`.

Derefter skal du i din nye `variables`-mappe åbne `src/main.rs` og erstatte koden med følgende kode, som ikke vil kunne kompilere endnu:
```rust
fn main() { 
	let x = 5; 
	println!("Værdien af x er: {}", x); 
	x = 6; println!("Værdien af x er: {}", x); 
}
```

Gem og kør programmet ved hjælp af `cargo run`. Du bør modtage en fejlmeddelelse vedrørende en `immutability error`, som vist i denne output:
```sh
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
error[E0384]: cannot assign twice to immutable variable `x`
 --> src/main.rs:4:5
  |
2 |     let x = 5;
  |         -
  |         |
  |         first assignment to `x`
  |         help: consider making this binding mutable: `mut x`
3 |     println!("The value of x is: {x}");
4 |     x = 6;
  |     ^^^^^ cannot assign twice to immutable variable

For more information about this error, try `rustc --explain E0384`.
error: could not compile `variables` (bin "variables") due to 1 previous error
```

Dette eksempel viser, hvordan `compiler` hjælper dig med at finde fejl i dine programmer. Kompilatorfejl kan være frustrerende, men de betyder egentlig kun, at dit program ikke sikkert gør, hvad du vil have det til at gøre endnu; de betyder ikke, at du ikke er en god programmør! 

Du modtog fejlmeddelelsen "cannot assign twice to immutable variable `x`", fordi du forsøgte at tildele en ny værdi til den uforanderlige variabel `x`.

Det er vigtigt, at vi får fejl ved kompileringstidspunktet, når vi forsøger at ændre en værdi, der er udpeget som uforanderlig, fordi denne situation kan føre til bugs. Hvis en del af vores kode arbejder ud fra antagelsen om, at en værdi aldrig vil ændre sig, og en anden del af vores kode ændrer den værdi, er det muligt, at den første del af koden ikke vil gøre, hvad den var designet til at gøre. 
Årsagen til denne slags bug kan være svær at finde efterfølgende, især når den anden del af koden kun nogle gange ændrer værdien. Rust-kompilatoren garanterer, at når du siger, at en værdi ikke vil ændre sig, så vil den virkelig ikke ændre sig, så du behøver ikke selv at holde styr på det. 

Men *foranderlighed*(*mutability*) kan være meget nyttig og kan gøre koden mere bekvem at skrive. Selvom variabler som standard er uforanderlige, kan du gøre dem foranderlige ved at tilføje `mut` foran variabelnavnet.

Tilføjelse af `mut` angiver også hensigten til fremtidige læsere af koden ved at vise, at andre dele af koden vil ændre denne variabels værdi.

For eksempel, lad os ændre `src/main.rs` til følgende:

Filnavn: `src/main.rs`
```rust
fn main() {
    let mut x = 5;
    println!("Værdien af x er: {x}");
    x = 6;
    println!("Værdien af x er: {x}");
}

```

Når vi nu kører programmet, får vi dette:
```sh
$ cargo run
   Compiling variables v0.1.0 (file:///projects/variables)
    Finished dev [unoptimized + debuginfo] target(s) in 0.30s
     Running `target/debug/variables`
Værdien af x er: 5
Værdien af x er: 6

```
Vi har lov til at ændre den værdi, der er bundet til `x` fra 5 til 6, når `mut` bruges. 
I sidste ende er det op til dig at beslutte, om du vil bruge foranderlighed eller ej, og det afhænger af, hvad du synes er klarest i den pågældende situation.

| Kilder                                                                            | Beskrivelse  |
| --------------------------------------------------------------------------------- | ------------ |
| [The Book](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)) | om variabler |


