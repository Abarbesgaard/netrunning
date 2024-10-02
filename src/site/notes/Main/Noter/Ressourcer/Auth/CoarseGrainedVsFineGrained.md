---
{"dg-publish":true,"permalink":"/main/noter/ressourcer/auth/coarse-grained-vs-fine-grained/","title":"Coase vs Fine-Grained Authorization","tags":["læringsmål","systemudvikling","projektarbejde","programmering"],"created":"2024-09-03T14:31:15.984+02:00"}
---

## Opsummering af "Coarse-Grained vs. Fine-Grained Authorization: Which to Use?"

### Hvad er Coarse-Grained Authorization (CGA)?

- **Definition**: CGA baserer sig på én enkelt attribut (f.eks. brugerroller)
for at bestemme adgang.
- **Fordele**: Enkel at implementere, lave omkostninger, let at administrere.
- **Ulemper**: Manglende fleksibilitet, risiko for "role explosion", kan være
for simpel til komplekse systemer.

### Hvad er Fine-Grained Authorization (FGA)?

- **Definition**: FGA anvender en kombination af flere detaljerede attributter
for mere præcis adgangskontrol.
- **Fordele**: Tilbyder større fleksibilitet, bedre sikkerhed og tilpasning,
forhindrer "role explosion".
- **Ulemper**: Kompleks opsætning, højere ressourcetræk, vanskelig at vedligeholde.

### Sammenligning af CGA og FGA

- **Nøjagtighed**: CGA kan føre til manglende eller overdreven adgang; FGA
tilpasser adgang præcist.
- **Brugervenlighed**: CGA er nemmere at bruge; FGA kræver mere omhu i opsætning.
- **Vedligeholdelse**: CGA er nemmere at vedligeholde; FGA kræver større
opmærksomhed på detaljer.
- **Skalérbarhed**: CGA kan føre til "role explosion"; FGA skalerer bedre, men
kræver flere ressourcer.
- **Sikkerhed**: CGA kan føre til sikkerhedsproblemer ved "attribute bloat";
FGA giver bedre kontrol og transparens.

### Hvilken tilgang er bedst?

- **Valg af metode** afhænger af virksomhedens størrelse og kompleksitet.
- **Kombination** af CGA og FGA kan være mest effektivt, især ved brug af RBAC
til grundlæggende kontrol og ABAC/ReBAC til mere komplekse behov.

