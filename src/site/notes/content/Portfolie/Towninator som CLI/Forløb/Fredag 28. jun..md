---
{"dg-publish":true,"permalink":"/content/portfolie/towninator-som-cli/forlob/fredag-28-jun/","title":"Fredag 28. jun.","tags":["Rust","Towninator"]}
---


Så lige nu ser min struktur sådan ud:
```
src/ 
│ 
├── controller/ 
├── model/ 
│ ├── repository/ 
│ ├── town_utilities/ 
│ └── townsfolk_utilities/
├── view/
├── main.rs
```

Det er lidt af hver inde i hver mappe.

grunden til denne struktur er at få skabt overblik over systemet. på nuværende tidspunkt mangler der en controller og det er den som skal laves næste gang.

Jeg tænker at jeg vil vise min `main.rs` som den ser ud på nuværende tidspunkt.

```rust
mod model;
mod view;
use crate::view::town_details::TownDetails;
// Assuming `town.rs` or `mod.rs` exists in the same directory
use clap::{command, Arg, Command};
use model::town::Town; // Ensure Town is imported if necessary

fn main() {

    let _match_result = command!()
    .subcommand(
            Command::new("find-villager")
            .arg(
                Arg::new("villager")
                    .short('v')
                    .long("villager")
                    .help("Show a specific villager")
                )
    )
    .subcommand(
            Command::new("generate")
            .arg(
                Arg::new("hamlet")
                    .short('g')
                    .long("generate")
                    .help("Generate a new town")
    )
    )
    .about("\nWelcome to the towninator, this simualtion of a hamlet that lives and breathes while you code")
    .get_matches();
    
    match _match_result.subcommand() {
        Some(("generate", _sub_m)) => {
            let my_town = Town::new();
            println!("{}", my_town.details());
        }
    _ => println!("No valid subcommand was used."),
    }
}
```
Ovenstående kode tager udgangspunkt i at man skal kunne bruge programmet gennem en CLI. Til dette bruger jeg Rust::Clap som tillader dette.