---
{"dg-publish":true,"permalink":"/content/portfolie/towninator-som-cli/forlob/ons-26-jun/","title":"Ons 26. jun.","tags":["Rust","Towninator"]}
---

Research inden projektet startede tog udgangspunkt i "[the book](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html?search=if)", som virkelig er en god dokumentation.
Yderligere brugte jeg CharGPT til at se hvordan man kan "oversætte" OOP over i en Rust kontekst.

Sådan som projektet, ser ud nu:
```
src/ 
│ 
├── main.rs 
├── town/ 
│ ├── mod.rs 
│ ├── townfolk.rs 
│ └── utilities.rs
```

Måden jeg er kommet frem til dette har været lidt knudret(og er stensikkert helt forkert :D ).

MEN
Jeg forsøgte mig med en *objekt orienteret tilgang* da jeg kommer fra .NET universet med C#, som hovedsprog. 
Det viste sig dog at være, lad mig sige, en interessant tilgang til at bruge Rust. Det jeg fandt frem til der kunne være i den retning, altså OOP, var at lave `struct`'s, som en langs objekter; uden rigtig at være det.

Min Town `struct` ser, lidt opsummeret, sådan ud:
```rust
pub struct Town{
	pub name: String,
    pub crime: u32,
    pub culture: u32,
    ...
}
```

Sådan som jeg forstår en `struct` nu er at det er at der er noget der minder om tuples. På den måde at de kan indeholde variabler af forskellige typer.
Herefter bliver den implementeret, da der umiddelbart skal genereres tilfældige værdier til variablerne.
```rust
impl Town {
    pub fn new() -> Self {
        let mut rng = rand::thread_rng();
        let name = utilities::city_name_generator();
        let crime = rng.gen_range(1..=5);
        let culture = rng.gen_range(1..=5);
        let education = rng.gen_range(1..=5);
        ...
        Town {
            name: name.to_string(),
            crime,
            culture,
            education,
            ...
        }

}
```
Til sidst oprettes der så et nyt, objekt - tror jeg, som repræsenterer Town.

Dette ser umiddelbart ud til at virke efter hensigten.