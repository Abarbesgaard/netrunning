---
{"dg-publish":true,"permalink":"/content/rust/language-basics/string/","title":"String","hide":true,"tags":["Rust"]}
---

> [!tldr] 
> `String` i Rust er en dynamisk ændringsbar strengtype, der allokerer data på heap'en og tillader håndtering af variabel længde tekst. [[content/Rust/Language Basics/Ownership\|Ownership konceptet]] sikrer sikker og effektiv hukommelsesstyring.

> [!summary] 
> `String` i Rust adskiller sig fra statiske `string literals` ved at tillade dynamisk ændring og variabel længde. Den allokerer hukommelse på heap'en og anvender [[content/Rust/Language Basics/Ownership\|Ownership konceptet]] til automatisk at styre hukommelsesoprydning og levetid. Dette sikrer, at der ikke opstår typiske problemer som hukommelseslækager, som ses i andre sprog.

En `String` i Rust repræsenterer en type streng, som kan vokse og ændre sig dynamisk. Denne evne adskiller den fra `string literal`, som er faste og uforanderlige ved kompileringstidspunktet. `String`-typen allokerer sine data på heap'en i stedet for på stakken. Dette gør det muligt at håndtere tekststrenge af varierende længde og opbevare dem, selv når deres størrelse ikke er kendt på forhånd.

[[content/Rust/Language Basics/Ownership\|Ownership konceptet]] i Rust er kernen i, hvordan `String` håndteres. Når du opretter en `String`, bliver du ejer af den tilknyttede hukommelsesallokering på heap'en. Når ejerskabet af en `String` overføres eller kopieres til en anden variabel eller funktion, håndterer Rust automatisk levetiden og oprydningen af den allokerede hukommelse. Dette sikrer, at der ikke opstår hukommelseslækager eller udefineret adfærd, som ofte ses i andre programmeringssprog.

For eksempel kan du oprette en `String` [[content/Rust/Language Basics/Variables\|variabel]] ved at konvertere en strenglitteral ved hjælp af `from`-metoden:
```rust
fn main() {
	let s = String::from("hello");
}
```

Den dobbelte kolon `::` operatør tillader os at placere funktionen `from` under String typen i stedet for at bruge en slags navn som fx "string_from". 

Denne type streng kan ændres:
```rust
let mut s = String::from("hello");

    s.push_str(", world!"); // push_str() appends a literal to a String

    println!("{s}"); // This will print `hello, world!`
```


| Kilder                                                                    | Beskrivelse |
| ------------------------------------------------------------------------- | ----------- |
| [The Book](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html) | Om string   |


