---
{"dg-publish":true,"permalink":"/main/noter/programmering/message-brokers/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-11-13T08:04:32.981+01:00"}
---


> [!important] Hvad er en message broker?
> En message broker er en softwarekomponent, der fungerer som mellemmand i kommunikationen mellem forskellige applikationer, systemer og tjenester [1](https://en.wikipedia.org/wiki/Message_broker) [2](https://www.ibm.com/topics/message-brokers). Den oversætter beskeder mellem afsenderens og modtagerens protokoller, hvilket muliggør udveksling af information mellem applikationer, selv hvis de er skrevet i forskellige programmeringssprog eller implementeret på forskellige platforme [2](https://www.ibm.com/topics/message-brokers).

![Pasted image 20241114114132.png](/img/user/98_Images/Pasted%20image%2020241114114132.png)

## Formål
Hovedformålet med en message broker er at:

1. Validere, gemme og route beskeder til en eller flere destinationer [1](https://en.wikipedia.org/wiki/Message_broker)
2. Transformere beskeder til alternative formater [1](https://en.wikipedia.org/wiki/Message_broker)
3. Håndtere asynkron kommunikation, så afsendere ikke behøver at vente på svar fra modtagere [2](https://www.ibm.com/topics/message-brokers)
4. Sikre pålidelig levering af beskeder, ofte ved hjælp af message queues [2](https://www.ibm.com/topics/message-brokers)

## Patterns
Message brokers understøtter typisk to grundlæggende kommunikationsmønstre:

**Point-to-point messaging**: En besked sendes fra en afsender til en specifik modtager [3](https://www.bigtech.coach/system-components/what-is-a-message-broker)
![Pasted image 20241122081320.png](/img/user/Main/Images/Pasted%20image%2020241122081320.png)

**Publish/subscribe (pub/sub)**: En afsender publicerer beskeder til et emne, og brokeren distribuerer dem til alle abonnenter på det pågældende emne [3](https://www.bigtech.coach/system-components/what-is-a-message-broker)

![Pasted image 20241122081520.png](/img/user/Main/Images/Pasted%20image%2020241122081520.png)
*Billedet er fra [AWS](https://aws.amazon.com/what-is/pub-sub-messaging/)*

Ved at bruge en **message broker** kan man opnå løs kobling mellem tjenester i et system, hvilket gør det lettere at *skalere*, *refaktorere* og *implementere* individuelle komponenter uafhængigt af hinanden [3](https://www.bigtech.coach/system-components/what-is-a-message-broker).