---
{"dg-publish":true,"permalink":"/main/noter/programmering/strangler-fig-pattern/","created":"2024-10-07T08:16:42.230+02:00"}
---

![Strangler fig pattern.png](/img/user/Resource/98_Images/Strangler%20fig%20pattern.png)
Strangler fig-mønsteret er et softwarearkitekturkoncept, der blev introduceret af Martin Fowler. Det beskriver en metode til gradvist at erstatte gamle systemer med nye ved at indføre nye funktioner, mens de eksisterende stadig er i drift. Navnet stammer fra strangler fig-planten, som vokser omkring et værts træ og til sidst erstatter det.

## Nøgleelementer

- **Gradvis Erstatning**: Mønsteret tillader udviklere at opdele et monolitisk system i mindre sektioner, som kan opdateres én ad gangen. Dette reducerer risikoen for fejl og gør det lettere at håndtere ændringer[5](https://deviq.com/design-patterns/strangler-fig-pattern/)[7](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig).
- **Facade Design**: En facade bruges til at intercept requests til det gamle system og dirigere dem enten til den gamle eller den nye service. Dette gør det muligt for brugerne at interagere med systemet uden at bemærke ændringerne[1](https://en.wikipedia.org/wiki/Strangler_fig_pattern)[3](https://docs.aws.amazon.com/prescriptive-guidance/latest/modernization-aspnet-web-services/fig-pattern.html)[7](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig).
- **Logging og Overvågning**: Under overgangen kan logging implementeres for at overvåge brugen af den gamle kode, hvilket hjælper med at identificere, hvilke dele der skal prioriteres i migreringen[1](https://en.wikipedia.org/wiki/Strangler_fig_pattern).

## Anvendelsesområder

Strangler fig-mønsteret er særligt nyttigt ved:

- **Modernisering af Legacy-systemer**: Det muliggør en langsom og kontrolleret overgang fra ældre teknologier til moderne løsninger, hvilket er ideelt for store og komplekse systemer[1](https://en.wikipedia.org/wiki/Strangler_fig_pattern)[3](https://docs.aws.amazon.com/prescriptive-guidance/latest/modernization-aspnet-web-services/fig-pattern.html).
- **Overgang til Mikrotjenester**: Mønsteret kan anvendes til at migrere monolitiske applikationer til en mikrotjenestearkitektur, hvilket giver mulighed for bedre skalerbarhed og vedligeholdelse[5](https://deviq.com/design-patterns/strangler-fig-pattern/).

## Fordele og Ulemper

**Fordele**:

- Reducerer risikoen ved store systemændringer.
- Muliggør kontinuerlig forbedring og hurtigere implementering af nye funktioner.

**Ulemper**:

- Kan føre til kompleksitet ved at skulle håndtere både gamle og nye systemer samtidigt.
- Kræver omhyggelig planlægning for at undgå flaskehalse i facaden[5](https://deviq.com/design-patterns/strangler-fig-pattern/)[7](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig).

Strangler fig-mønsteret tilbyder en effektiv tilgang til softwaremodernisering ved at kombinere gradualisme med strategisk planlægning.