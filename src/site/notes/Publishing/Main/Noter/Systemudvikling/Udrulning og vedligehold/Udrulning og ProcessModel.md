---
{"dg-publish":true,"permalink":"/publishing/main/noter/systemudvikling/udrulning-og-vedligehold/udrulning-og-process-model/","title":"Udrulning og Processmodel","hide":true,"tags":["systemudvikling","Udrulning"],"created":"2024-09-20T10:05:41.530+02:00"}
---

> [!tldr]
> Valg af cutover-strategi bør matche den anvendte procesmodel for at sikre en
smidig overgang. Vandfaldsmodellen passer bedst til Big Bang, mens agile og
iterative modeller egner sig til faseopdelt, parallel og modulært cutover.
Inkremental udvikling harmonerer med modulært og gradvis cutover samt
Strangler Fig Pattern.

## Procesmodel

Der er en betydelig sammenhæng mellem dit valg af **udrulnings strategi** og
den **procesmodel**, du har anvendt til systemudvikling. Forskellige
procesmodeller kan påvirke, hvilken [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Valg Af Cutover Strategi\|udrulnings strategi]]
der er mest passende og effektiv. Her er nogle tanker om, hvordan
forskellige procesmodeller kan kobles med udrulningsstrategier:

### Vandfaldsmodellen

- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Big Bang Cutover\|Big Bang udrulning]]: Passer godt til
vandfaldsmodellen, da hele systemet typisk er fuldt udviklet og
testet før overgangen. Hele organisationen kan skifte til det
nye system på én gang.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Pilot Cutover\|Pilot udrulning]]: Kan også anvendes,
især hvis systemet er kritisk og en gradvis implementering ønskes
efter endt udvikling.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Faseopdelt Cutover\|Faseopdelt udrulning]]: Er mindre
almindelig, men kan bruges hvis forskellige moduler eller dele af
systemet implementeres i separate vandfaldsprojekter.

### Agil Udvikling

- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Faseopdelt Cutover\|Faseopdelt udrulning]]: Passer godt til agile
metoder, da systemet udvikles og implementeres i små, håndterbare dele
over tid.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Parallel Cutover\|Parallel udrulning]]: Kan bruges til at sikre, at
nye funktionaliteter gradvist implementeres og testes, mens det gamle system
stadig kører.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Strangler Fig Pattern\|Strangler Fig Pattern]]: Ideelt for agil, da
det tillader kontinuerlig forbedring og udskiftning af dele af det gamle system
over tid.

### Iterativ Udvikling

- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Faseopdelt Cutover\|Faseopdelt udrulning]]:Meget velegnet til
iterativ udvikling, hvor hver iteration kan afslutte med implementeringen
af en ny funktionalitet.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Pilot Cutover\|Pilot udrulning]]: Kan anvendes i tidligere
iterationer for at teste systemet i et kontrolleret miljø før bredere
implementering.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Wave Cutover\|Wave udrulning]]: Hver iteration kan introducere
nye bølger af funktionalitet til forskellige dele af organisationen.

### Inkremental Udvikling

- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Modulært Cutover\|Modulært udrulning]]: Passer godt til
inkremental udvikling, da hver inkrement kan implementeres som et
separat modul.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Gradvis Cutover\|Gradvis (Incremental) udrulning]]: Direkte
sammenhæng, da systemet introduceres trinvis parallelt med den
inkrementelle udviklingsproces.
- [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Strangler Fig Pattern\|Strangler Fig udrulning]]: Kan også anvendes,
hvor nye inkrementer gradvist erstatter dele af det gamle system.

## Sammenfatning

Valget af **udrulning** strategi bør være i tråd med din anvendte
**procesmodel** for at sikre en glidende overgang og minimal forstyrrelse.
**Vandfaldsmodellen**, med sin lineære tilgang, passer bedst til mere
engangs- og omfattende udrulning strategier som
[[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Big Bang Cutover\|Big Bang]].
Agile og iterativ udvikling, der værdsætter fleksibilitet og gradvis
forbedring, passer bedre til [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Faseopdelt Cutover\|Faseopdelt]],
[[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Parallel Cutover\|Parallel ]] og
[[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Modulært Cutover\|Modulært udrulning]], hvor systemet kan
udvikles og implementeres i små, håndterbare dele.

Inkremental udvikling, med sin gradvise udvidelse af systemfunktionalitet,
harmonerer godt med strategier som modulært og gradvis udrulning cutover,
samt [[Publishing/Main/Noter/Systemudvikling/Udrulning og vedligehold/Cutover#Strangler Fig Pattern\|Strangler Fig Pattern]], der tillader
kontinuerlig forbedring.

[Rise articuale](https://rise.articulate.com/share/l6jaM5QkUIYZIMlwdvLsi3JEE9bY7BWI#/lessons/nwOQZZowwKqRkyOi1l0nyZiLawKLHeVZ)
