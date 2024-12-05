---
{"dg-publish":true,"permalink":"/main/ai/prompt-hacking/prompt-leaking/","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-05T08:06:44.706+01:00"}
---

## Nøglepunkter

> [!note] Definition
> Prompt-leak sker, når en model afslører sine interne instruktioner, normalt som resultat af, at brugere manipulerer input for at udtrække den originale prompt.

> [!note] Risici
> Lækage af prompts kan afsløre følsomme oplysninger og intellektuel ejendom, hvilket underminerer fortrolighed og virksomheders integritet.

### Anbefaling
Jeg vil anbefale at se [denne videos](https://www.youtube.com/watch?v=LWiMwhDZ9as) sidste 5 kapitler(fra 4:43:12 og frem), her viser han hvordan man kan få ChatGPT til at leake information,
### **Hvad er prompt-lækage?**

Prompt-lækage er en form for prompt-injektion, hvor modellen opfordres til at afsløre sin egen prompt.

Som vist i eksempel **billede 1** (Perez & Ribeiro, 2022) manipulerer angriberen brugerinput for at forsøge at få prompten returneret. Dette adskiller sig fra målkapring (almindelig prompt-injektion), hvor angriberen ændrer brugerinput for at generere ondsindede instruktioner.

![Pasted image 20241205081157.png](/img/user/Pasted%20image%2020241205081157.png)
*Billedet er fra [Learn Prompting](https://learnprompting.org/docs/prompt_hacking/leaking)

## Hvorfor er det vigtigt?
Prompt-lækage kan være problematisk, når virksomheder ønsker at holde deres prompts hemmelige. For eksempel kan et uddannelsesfirma bruge prompten _"Forklar dette til mig, som om jeg er 5 år gammel"_ til at forklare komplekse emner. Hvis denne prompt lækkes, kan andre bruge den uden at gå gennem firmaet.

### **Konklusion**

Prompt-leak er vigtigt at forstå, fordi utilsigtet afsløring af følsomme prompts udgør en **kritisk sårbarhed** i AI-systemer. Efterhånden som flere virksomheder anvender sprogbaserede modeller, bliver det afgørende at adressere prompt-leak for at beskytte intellektuel ejendom og fortrolige data.

## Kilder
> [!source]- Promp Leaking
> Tilgængelig på: [learnprompting](https://learnprompting.org/docs/prompt_hacking/leaking)

> [!source]- Prompt Leaking  
> Tilgængelig på: [promptingguide.ai](https://www.promptingguide.ai/prompts/adversarial-prompting/prompt-leaking)

> [!source]- Prompt Leak  
> Tilgængelig på: [prompt.security](https://www.prompt.security/vulnerabilities/prompt-leak)

> [!source]- YouTube Video: Understanding Prompt Leaking  
> Tilgængelig på: [YouTube](https://www.youtube.com/watch?v=7Njh2Xrd8Dw)