---
{"dg-publish":true,"permalink":"/main/noter/rabbit-mq/","created":"2024-10-11T10:48:12.506+02:00"}
---

![rabbitmq.png](/img/user/rabbitmq.png)
RabbitMQ er en meget anvendt **meddelelsesbroker**, der letter kommunikationen mellem applikationer ved at håndtere transmissionen af meddelelser gennem køer. Det fungerer efter princippet om **meddelelseskøer**, hvilket gør det muligt for applikationer at sende og modtage meddelelser asynkront, hvilket forbedrer effektiviteten og skalerbarheden i softwarearkitekturer.

## Nøglebegreber

### Message Broker 
RabbitMQ fungerer som en mellemmand for meddelelser, ligesom et posthus, der modtager, opbevarer og videresender meddelelser. Det gør det muligt for producenter (applikationer, der sender meddelelser) at kommunikere med forbrugere (applikationer, der modtager meddelelser) uden at skulle kende hinandens detaljer, hvilket fremmer lav kobling mellem komponenter. 

### Queues
En kø i RabbitMQ er en ordnet samling af meddelelser, der følger en **FIFO (First In, First Out)** metode. Meddelelser opbevares i køen, indtil de behandles af forbrugere. Dette muliggør effektiv belastningsbalancering og opgavefordeling blandt flere forbrugere. **3. Producenter og Forbrugere:**

- **Producenter:** Applikationer, der opretter og sender meddelelser til RabbitMQ-brokeren.
- **Forbrugere:** Applikationer, der opretter forbindelse til brokeren for at hente og behandle meddelelser fra køen.

### Exchanges 
Exchanges modtager meddelelser fra producenter og ruter dem til en eller flere køer baseret på definerede regler. Rute mekanismen bestemmes af rute nøgler og binding konfigurationer. **5. AMQP Protokol:**  
RabbitMQ bruger **Advanced Message Queuing Protocol (AMQP)**, som er en åben standard for meddelelsesorienteret middleware. Denne protokol sikrer pålidelig levering af meddelelser mellem producenter og forbrugere.

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