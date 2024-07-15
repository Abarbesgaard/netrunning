---
{"dg-publish":true,"permalink":"/content/portfolie/towninator-som-cli/forlob/man-15-juli/","tags":["CSharp","Towninator"]}
---

Jeg har taget mig den frihed at konvertere hele projektet tilbage til kendt land - #CSharp. Dette var noget af en berigelse da jeg også er ved at lære lazyvim at kende. 

Dette har dog medført et ordenligt boost i kreativitet og produktivitet.

Jeg har fået lavet mit program så det kan generere kort som dette:
```
♣ ⌂ ∩ ♣ ⌂ n ♣ ∩ ♣ ♣ . . ♣ . . ♠ n ⁿ ♠ n 
∩ ∩ ⌠ ♠ ⁿ ∩ ⌂ . . ♣ ♣ ♣ ⌠ ♣ ⁿ ∩ ∩ . ♣ ⌠ 
ⁿ ♣ ♣ . ⁿ ⁿ ⌂ ⌂ ♠ ♠ ♠ ♠ ♣ ⁿ ⁿ . ≈ ≈ ♠ ▲ 
♣ ♠ ♣ ♣ ⁿ ⁿ ♠ ♣ ♠ ♣ ♣ ♣ ♠ ∩ . . . ⌠ ♠ ∩ 
⌂ ♠ ♠ ♠ . . . ♠ ♣ ♠ ♣ ♠ ♠ n ⌂ ⁿ ♠ ♣ ♣ . 
. ♠ ♠ ♠ ⁿ . ⁿ ⁿ ♣ ♣ ♣ ♣ ♣ ♣ ⁿ ⌂ ♠ ♠ ♣ ⌠ 
♣ ⌂ ♣ ♣ ⁿ . ⁿ ⌂ ⌂ ♣ ♠ ♠ ♠ ♣ ♣ ⌂ ⌂ ♣ ♠ ♣ 
⌠ ▲ ⌂ ≈ ⁿ . . ⌂ ⌂ . ♠ ♣ ♣ ♠ ♠ ⌂ ⌂ n . ⌂ 
⌂ ♣ n ⌂ . ⁿ . ⌂ ⌂ n ♣ ♣ ♠ ♣ ♠ ♠ ⌂ ⌂ . ⁿ 
♣ ♠ ♣ ♣ ⌂ ♣ ♣ ⌂ ⌂ ♣ ♣ ♣ ♠ ♠ ♠ ♠ ⌂ ⌂ . ⁿ 
ⁿ ♣ ♣ ♣ ♣ ⌂ ⌂ ⌂ ⌂ . + ♣ ♣ ♠ ♣ ⌂ ⌂ ⌂ ⁿ . 
ⁿ ♠ ♣ ♠ ♠ ⌂ ⌂ ⌂ n ⁿ ♠ ♠ ♠ ♣ ♣ ⌂ ⌂ ⌂ ♣ ⁿ 
♣ ♣ ♣ ♠ ♠ ♠ ♠ ∩ ⁿ . . ♠ ♣ ♠ ♣ ⌂ ⌂ ⌂ ♣ n 
. ♣ ♠ ♠ ♣ ♣ . . ⁿ . . ♠ ♠ ♣ ♣ ⌠ ⁿ ⌂ ⌂ n 
. ♣ ♠ ♠ ♠ ♣ ⁿ . ⁿ . ⁿ . ♠ ♠ ♣ . . ⁿ ⌂ ⌂ 
♠ ♣ ♣ ♠ ♠ ♠ . . ⁿ . ⁿ ⌂ ♠ ♠ ♣ . . . ⁿ . 
▲ . ♣ ♠ ♠ ♠ ⁿ . ⁿ ⁿ ⁿ ≈ ♣ ♠ ⁿ . ⁿ ⁿ . ⁿ 
. ♠ ♣ ♣ ♠ ♠ ⁿ . ⁿ . ⌂ ♠ ♠ ♣ ♣ ⁿ . . ⁿ n 
♣ ♠ ♠ ♣ ♣ ♠ . ⁿ . . ⁿ ⌂ ♣ ♠ ♣ ♣ . ⁿ ⁿ ♠ 
∩ ∩ ⌂ ♠ ⌂ n ⁿ ⁿ . ⁿ ∩ . ⁿ ♣ n ⁿ ♠ ♠ ∩ . 
```

I midten af koret ses den by det hele vil dreje sig om - `+` 
Der kommer også en beskrivelse hvis man bruger kommandoen `-t`, som kan se sådan ud:
*Welcome to the town of Beöing* 
*Nestled within a vast forest, paths leading deeper into nature's embrace. East of town: surrounded by majestic redwoods reaching for the sky. West of town: with its gentle terrain providing a sense of calm and serenity. North of town: where townsfolk and forest creatures mingle in a serene glade. South of town: in a tranquil grove surrounded by ancient oaks.*

Så alt er genereret ved kommantoden `-t` og jeg forestiller mig at denne vil man gøre brug af når man vil starte en ny by. 
Alle beskrivelserne er genereret automatisk alt efter hvilke tiles der er Nord, Syd, Øst og Vest fra byen.
 

