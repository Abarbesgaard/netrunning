---
{"dg-publish":true,"permalink":"/main/artikler/microservices/horisontal-vs-vertikal-skalering/","tags":["Microservice","skalering"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"true","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-11-28T08:49:31.897+01:00"}
---


> [!important] Information om skalering
> Skalering er en essentiel del af enhver moderne applikation, især når man arbejder med [[Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]] som [[Main/Noter/Emner/Backend/Microservice\|microservices]]. 


![Pasted image 20241128085307.png](/img/user/Main/Images/Pasted%20image%2020241128085307.png)
*Billedet er fra [medium](https://medium.com/javarevisited/difference-between-horizontal-scalability-vs-vertical-scalability-67455efc91c)*

Når man taler om skalering, refererer man ofte til to hovedmetoder: **horisontal skalering** og **vertikal skalering**. Begge metoder har deres *fordele* og *ulemper*, og det er vigtigt at forstå forskellen og hvornår man bør vælge den ene frem for den anden.

---
### **Hvad er Vertikal Skalering?**

Vertikal skalering, også kaldet **skalering op**, indebærer at opgradere de ressourcer, der allerede findes på en enkelt server eller instans. Det betyder, at du øger serverens kapacitet ved at tilføje flere CPU-kerner, mere RAM, større lagerplads eller kraftigere netværksforbindelser.

![Pasted image 20241128085417.png](/img/user/Main/Images/Pasted%20image%2020241128085417.png)
*Billedet er fra [Medium](https://sumeetpanchal-21.medium.com/scaling-strategies-vertical-scaling-horizontal-scaling-and-hybrid-designs-fc42a63af0cb)*
#### **Fordele ved vertikal skalering:**

- **Enkel implementering:** Du behøver ikke at ændre noget i applikationen. Hvis du allerede har en applikation, der kører på én server, kan du simpelthen opgradere serveren til en kraftigere version.
- **Lavere kompleksitet:** Der er færre bevægelige dele, og du behøver ikke at bekymre dig om load balancing eller synkronisering mellem flere servere.

#### **Ulemper ved vertikal skalering:**

- **Begrænset skalerbarhed:** Der er en øvre grænse for, hvor meget du kan opgradere en enkelt server. Uanset hvor kraftig en server bliver, vil der komme et punkt, hvor det ikke længere er muligt at opgradere den uden at skulle investere i en helt ny infrastruktur.
- **Single point of failure:** Hvis den ene server fejler, går hele applikationen ned. Dette er en stor risiko for kritiske systemer.

---

### **Hvad er Horisontal Skalering?**

Horisontal skalering, også kaldet **skalering ud**, indebærer at tilføje flere servere (eller instanser) til din applikation i stedet for at opgradere en enkelt server. I stedet for at gøre én server kraftigere, distribuerer du arbejdsbelastningen mellem flere servere.

![Pasted image 20241128085532.png](/img/user/Main/Images/Pasted%20image%2020241128085532.png)
*Billedet er fra [gartsolutions](https://gartsolutions.com/cloud-scalability-horizontal-vs-vertical-scaling-of-it-infrastructures/)*
#### **Fordele ved horisontal skalering:**

- **Ubegrænset skalerbarhed:** Der er næsten ingen grænse for, hvor mange servere du kan tilføje, hvilket giver meget stor fleksibilitet til at håndtere trafiktoppe.
- **Fejltolerance:** Fordi applikationen kører på flere instanser, vil systemet fortsætte med at fungere, selv hvis en enkelt server fejler. Dette skaber en mere robust og pålidelig løsning.

#### **Ulemper ved horisontal skalering:**

- **Øget kompleksitet:** Du skal håndtere l*oad balancing*, *synkronisering* og *eventuelle problemer med konsistens* mellem serverne. Det kræver ofte specialiserede værktøjer som [Kubernetes](https://kubernetes.io/) eller [Docker Swarm](https://docs.docker.com/engine/swarm/) til at håndtere disse udfordringer.
- **Netværksflaskehalse:** Kommunikationen mellem servere kan skabe flaskehalse, hvilket kan påvirke applikationens ydeevne, især når der er store mængder data, der skal synkroniseres.

---

### **Hvornår skal man vælge vertikal skalering?**

Vertikal skalering er ofte den første løsning, mange vælger, især i følgende scenarier:
> [!note] Begrænset trafik
> Hvis applikationen ikke har meget trafik og kører på et begrænset budget, kan det være lettere og billigere at opgradere én server.

> [!note] Enkel applikation
> Hvis applikationen ikke er kompleks og ikke kræver høj tilgængelighed, kan vertikal skalering være den nemmeste løsning. Du slipper for at håndtere det ekstra arbejde, der følger med horisontal skalering.

> [!note] Korte skaleringsbehov
> Hvis du forventer, at trafikken vil være høj i en kort periode (fx i forbindelse med et engangsarrangement eller lancering), kan vertikal skalering være en hurtig løsning for midlertidig høj ydeevne.


---

### **Hvornår skal man vælge horisontal skalering?**

Horisontal skalering er normalt den foretrukne løsning, når du har behov for stor skalerbarhed og høj tilgængelighed, især i de følgende tilfælde:

> [!note] Høj trafik og voksende applikationer
> Når applikationen forventes at håndtere stor trafik over tid, vil horisontal skalering give den nødvendige fleksibilitet til at håndtere en konstant vækst uden at være begrænset af en enkelt server.

> [!note] Distribuerede systemer
> Hvis du arbejder med microservices eller distribuerede systemer, hvor hver service kører på sin egen instans, er horisontal skalering næsten uundgåelig.

> [!note] Høj tilgængelighed og redundans
> Horisontal skalering gør det muligt at opbygge redundans, så applikationen fortsætter med at fungere, selv hvis en server fejler. Dette er afgørende for systemer, der skal være tilgængelige 24/7.

---

### **Hvordan vælger man mellem horisontal og vertikal skalering?**

Valget mellem horisontal og vertikal skalering afhænger af flere faktorer:

> [!important] Trafikmængde
> Hvis du har høj trafik eller forventer at vokse hurtigt, vil horisontal skalering sandsynligvis være den bedste løsning. Vertikal skalering kan dog være en hurtigere løsning for mindre applikationer med lavere trafik.tal skalering være mere økonomisk, da du kan tilføje flere instanser efter behov.

> [!important] Kompleksitet
> Vertikal skalering er enklere at implementere og kræver færre teknologiske løsninger. Horisontal skalering kræver derimod load balancing, synkronisering og mere sofistikerede systemer.

> [!important] Skalering af tjeneste
> Hvis du arbejder med [[Main/Noter/Emner/Backend/Microservice\|microservices]] eller [[Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]], vil horisontal skalering være den naturlige vej at gå, da du ofte har brug for flere instanser af hver service.

---

### **Konklusion**

Både vertikal og horisontal skalering har deres fordele og anvendelsesområder. Vertikal skalering kan være ideel til små applikationer med begrænset trafik, mens horisontal skalering er den bedste løsning for store, voksende systemer, der kræver høj tilgængelighed og robusthed. Når du arbejder med microservices og distribuerede systemer, vil horisontal skalering ofte være den foretrukne løsning på grund af dens fleksibilitet og skalerbarhed.

## Hvad gør du?
Jeg vil gerne høre din mening! Hvilken skaleringsmetode bruger du i dine projekter, og hvilke udfordringer har du mødt undervejs? Del dine tanker og spørgsmål i kommentarerne nedenfor – lad os starte en diskussion og lære af hinandens erfaringer.

## Andre artikler med samme emne
| File                                                                                                                                        | Title                                               | Tags                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [[Main/Artikler/Microservices/Hvorfor er en message broker vigtig i Microserivces\|Hvorfor er en message broker vigtig i Microserivces]] | Hvorfor er en message broker vigtig i Microserivces | <ul><li>#Microservices</li><li>#MessageBrokers</li><li>#SoftwareArchitecture</li></ul> |
| [[Main/Artikler/Microservices/Mono vs Micro\|Mono vs Micro]]                                                                             | Mono vs Micro                                       | <ul><li>#Monolith</li><li>#Microservices</li><li>#Architecture</li></ul>               |

{ .block-language-dataview}

## Kilder
- **[Multishoring Blog - Horizontal vs Vertical Scaling](https://multishoring.com/blog/horizontal-vs-vertical-scaling/)**  
    En artikel, der forklarer de grundlæggende forskelle mellem horisontal og vertikal skalering, og hvornår hver metode bør anvendes i et system.
    
- **[DigitalOcean - Horizontal Scaling vs Vertical Scaling](https://www.digitalocean.com/resources/articles/horizontal-scaling-vs-vertical-scaling)**  
    DigitalOcean giver en detaljeret sammenligning af horisontal og vertikal skalering og deres anvendelser i cloud computing, herunder fordele og ulemper ved begge tilgange.
    
- **[Cockroach Labs Blog - Vertical Scaling vs Horizontal Scaling](https://www.cockroachlabs.com/blog/vertical-scaling-vs-horizontal-scaling/)**  
    Cockroach Labs diskuterer forskellene mellem vertikal og horisontal skalering, og hvordan de påvirker databaser og distribuerede systemer.
    
- **[CloudZero Blog - Horizontal vs Vertical Scaling](https://www.cloudzero.com/blog/horizontal-vs-vertical-scaling/)**  
    En artikel, der fokuserer på omkostningerne og præstationsfordelene ved horisontal og vertikal skalering, især i relation til cloud-infrastrukturer og -applikationer.
    
- **[Dgraph - Vertical Scale](https://dgraph.io/blog/post/vertical-scale/)**  
    Dgraph's blog omhandler vertikal skalering, med fokus på, hvordan det påvirker databaser og hvordan Dgraph håndterer skalerbarhed.
    
- **[Nops Blog - Horizontal vs Vertical Scaling](https://www.nops.io/blog/horizontal-vs-vertical-scaling/)**  
    Denne artikel giver en oversigt over horisontal og vertikal skalering, der fokuserer på, hvordan de kan implementeres i mikroservice-arkitektur.
    
- **[Azure Cloud Computing Dictionary - Scaling Out vs Scaling Up](https://azure.microsoft.com/da-dk/resources/cloud-computing-dictionary/scaling-out-vs-scaling-up)**  
    Microsoft Azure giver en præcis definition af de to skaleringsmetoder, "scaling out" og "scaling up", og deres anvendelse i cloud computing-arkitekturer.

