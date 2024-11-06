---
{"dg-publish":true,"permalink":"/main/noter/rabbit-mq/","created":"2024-10-11T10:48:12.506+02:00"}
---

![rabbitmq.png](/img/user/rabbitmq.png)
RabbitMQ er en meget anvendt **Message Broker**, der letter kommunikationen mellem applikationer ved at håndtere transmissionen af meddelelser gennem køer. Det fungerer efter princippet om **Message Queues**, hvilket gør det muligt for applikationer at sende og modtage meddelelser *asynkront*, hvilket forbedrer effektiviteten og skalerbarheden i softwarearkitekturer.

## Nøglebegreber

### Message Broker 
>[!NOTE] *RabbitMQ* fungerer som en mellemmand for meddelelser, ligesom et posthus, der modtager, opbevarer og videresender meddelelser. 

Det gør det muligt for **Producers** (applikationer, der sender meddelelser) at kommunikere med **Consumers** (applikationer, der modtager meddelelser), uden at skulle kende hinandens implementering, hvilket fremmer [lav kopling](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) mellem komponenter. 

### Queues
En *Queue* i RabbitMQ er en ordnet samling af meddelelser, der følger en **FIFO (First In, First Out)** metode. Meddelelser opbevares i køen, indtil de behandles af forbrugere. Dette muliggør effektiv belastningsbalancering og opgavefordeling blandt flere forbrugere. **3. Producenter og Forbrugere:**

- **Producers:** Applikationer, der opretter og sender meddelelser til RabbitMQ-brokeren.
- **Consumers:** Applikationer, der opretter forbindelse til *brokeren* for at hente og behandle meddelelser fra køen.
### Bindings
I **RabbitMQ** refererer "bindings" til forbindelserne mellem udvekslinger (exchanges) og køer (queues). Bindingen bestemmer, hvordan meddelelser, der sendes til en udveksling, dirigere til en eller flere køer baseret på bestemte kriterier.
For at oprette en binding skal en kø være tilknyttet en udveksling med en specifik routing key (eller et mønster, afhængigt af udvekslingens type). Bindingen gør det muligt for udvekslingen at sende meddelelser til køen, når meddelelser, der matcher bindingens kriterier, bliver sendt til udvekslingen.

> [!IMPORTANT] Vigtigt!
> Bindings er en essentiel del af RabbitMQ's fleksible routing-mekanisme, da de giver mulighed for komplekse meddelelsesstrukturer og datadistribution.
### Exchanges 
Exchanges modtager meddelelser fra **Producers** og ruter dem til en eller flere *køer* baseret på definerede regler. Rute mekanismen bestemmes af rute nøgler og binding konfigurationer. 
### AMQP Protokol  
RabbitMQ bruger **Advanced Message Queuing Protocol (AMQP)**, som er en åben standard for meddelelsesorienteret middleware. Denne protokol sikrer pålidelig levering af meddelelser mellem producenter og forbrugere.
### Routing Keys
**Routing keys** i RabbitMQ er en central del af *Message Routing* og bruges til at bestemme, hvordan meddelelser dirigeres fra en *udveksling* (exchange) til en eller flere køer (queues). 

Routing keys er *strenge*, der følger bestemte mønstre og fungerer i forbindelse med bindinger.
#### Nøglepunkter om Routing Keys i RabbitMQ:

1. **Definition**: En routing key er en streng, der sendes sammen med en meddelelse til en udveksling. Den fungerer som en etikette, der hjælper med at identificere, hvor meddelelsen skal sendes.
    
2. **Exchange Typer**:
    - **Direct Exchange**: Meddelelser sendes til køer, hvis bindinger matcher den eksakte routing key.
    - **Fanout Exchange**: Ignorerer routing keys og sender meddelelser til alle bundet køer.
    - **Topic Exchange**: Bruger routing keys med mønstermatching (wildcards) til at sende meddelelser til køer, der matcher et specifikt mønster. For eksempel kan en routing key som `logs.error` dirigere meddelelser til en kø, der er bundet med et mønster, der matcher `logs.*`.
    - **Headers Exchange**: Routing keys ignoreres, og meddelelser dirigeres baseret på header-egenskaber, som kan indeholde flere nøgle-værdi-par.
3. **Bindinger og Routing Keys**: Når en kø oprettes, kan den bindes til en udveksling med en specifik routing key. Denne binding fortæller udvekslingen, at enhver meddelelse, der sendes med en matching routing key, skal leveres til denne kø. For eksempel, hvis en binding er oprettet med routing key `task.process`, vil enhver meddelelse sendt til udvekslingen med den samme routing key blive dirigeret til den bundet kø.
    
4. **Brugsscenarier**: Routing keys bruges ofte til at filtrere meddelelser baseret på type, status eller andre karakteristika, hvilket giver mulighed for fleksible og skalerbare meddelelsesmodeller. For eksempel kan et system, der håndterer forskellige typer hændelser (f.eks. `order.created`, `order.updated`), bruge forskellige routing keys til at dirigere disse hændelser til specifikke behandlingstjenester.
    

Routing keys gør RabbitMQ i stand til at håndtere komplekse meddelelsesruter og tilpasse sig forskellige behov i systemdesign og datadistribution.
## Funktioner

- **Asynkron Kommunikation:** RabbitMQ adskiller meddelelsesproducenter fra forbrugere, så de kan fungere uafhængigt.
- **Belastningsbalancering:** Meddelelser kan distribueres på tværs af flere forbrugere, hvilket muliggør effektiv behandling af opgaver.
- **Holdbarhed og Pålidelighed:** Meddelelser kan gemmes på disk, hvilket sikrer, at de ikke går tabt i tilfælde af fejl i brokeren.
- **Fleksibel Ruting:** Brugen af exchanges og rute nøgler muliggør komplekse rutingscenarier tilpasset applikationsbehov.

## Anvendelsesområder

RabbitMQ er særligt nyttigt i scenarier som:

- **Mikrotjenestearkitektur:** Lettere kommunikation mellem forskellige tjenester.
- **Opgavekøer:** Fordeling af tidskrævende opgaver blandt arbejdende applikationer.
- **Hændelsessstreaming:** Håndtering af realtids begivenhedsdatabehandling.

Sammenfattende fungerer RabbitMQ som en robust løsning til meddelelseskøer, der forbedrer applikationsydelse og pålidelighed ved at muliggøre asynkron kommunikation mellem forskellige systemer.