---
{"dg-publish":true,"permalink":"/publishing/main/noter/programmering/rabbit-mq/","created":"2024-10-11T10:48:12.506+02:00"}
---

![rabbitmq.png](/img/user/Resource/98_Images/rabbitmq.png)

> [!important] En message broker
> RabbitMQ er en meget anvendt **[[Publishing/Main/Noter/Programmering/Message Brokers\|Message Broker]]**, der letter kommunikationen mellem applikationer ved at håndtere transmissionen af meddelelser gennem køer. Det fungerer efter princippet om **Message Queues**, hvilket gør det muligt for applikationer at sende og modtage meddelelser *asynkront*, hvilket forbedrer effektiviteten og skalerbarheden i softwarearkitekturer.

![Pasted image 20241120062650.png](/img/user/Resource/98_Images/Pasted%20image%2020241120062650.png)
*Billedet fra [CloudAMQP](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html)*
## Nøglebegreber

### Message Broker 
>[!NOTE] *RabbitMQ* fungerer som en mellemmand for meddelelser, ligesom et posthus, der modtager, opbevarer og videresender meddelelser. 

Det gør det muligt for **Producers** (applikationer, der sender meddelelser) at kommunikere med **Consumers** (applikationer, der modtager meddelelser), uden at skulle kende hinandens implementering, hvilket fremmer [lav kopling](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) mellem komponenter. 

### Queues
![Pasted image 20241120062845.png](/img/user/Resource/98_Images/Pasted%20image%2020241120062845.png)
*Billedet fra [Medium](https://binodmahto.medium.com/different-exchange-types-in-rabbitmq-cfd1c263e3c2)*
En *Queue* i RabbitMQ er en ordnet samling af meddelelser, der følger en **FIFO (First In, First Out)** metode. Meddelelser opbevares i køen, indtil de behandles af forbrugere. Dette muliggør effektiv belastningsbalancering og opgavefordeling blandt flere forbrugere. 

- **Producers:** Applikationer, der opretter og sender meddelelser til RabbitMQ-brokeren.
- **Consumers:** Applikationer, der opretter forbindelse til *brokeren* for at hente og behandle meddelelser fra [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|køen]].
### Bindings
![Pasted image 20241120080418.png](/img/user/Resource/98_Images/Pasted%20image%2020241120080418.png)
*Billedet fra [CloudAMQP](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html)*

I **RabbitMQ** refererer **bindings** til forbindelserne mellem [[Publishing/Main/Noter/Programmering/RabbitMQ#Exchanges\|Exchanges]] og [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]]. Bindingen bestemmer, hvordan meddelelser, der sendes til en udveksling, dirigere til en eller flere [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]]baseret på bestemte kriterier.

For at oprette en **binding** skal en [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queue]] være tilknyttet en udveksling med en specifik [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing key]] (eller et mønster, afhængigt af udvekslingens type). Bindingen gør det muligt for udvekslingen at sende meddelelser til [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queue]], når meddelelser, der matcher bindingens kriterier, bliver sendt til [[Publishing/Main/Noter/Programmering/RabbitMQ#Exchanges\|exchange]].

> [!IMPORTANT] Vigtigt!
> **Bindings** er en essentiel del af RabbitMQ's fleksible routing-mekanisme, da de giver mulighed for komplekse meddelelsesstrukturer og datadistribution.
### Exchanges 
![Pasted image 20241120063059.png](/img/user/Resource/98_Images/Pasted%20image%2020241120063059.png)

> [!important] Opsummering
> Exchanges modtager meddelelser fra **Producers** og ruter dem til en eller flere [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]] baseret på definerede regler. Rute mekanismen bestemmes af [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing key]] og binding konfigurationer. 

#### Exchange Typer
##### Direct Exchange 
Meddelelser sendes til [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]], hvis [[Publishing/Main/Noter/Programmering/RabbitMQ#Bindings\|bindinger]] matcher den eksakte [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing key]].
![Pasted image 20241120080729.png](/img/user/Resource/98_Images/Pasted%20image%2020241120080729.png)
*Billedet er fra [Medium](https://medium.com/@erdogancayir/direct-exchange-rabbitmq-d35860757d2d)*
##### Fanout Exchange
Ignorerer [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing key]] og sender meddelelser til alle bundet [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]].
![Pasted image 20241120080829.png](/img/user/Resource/98_Images/Pasted%20image%2020241120080829.png)
*Billedet er fra [RabbitMQ](https://www.rabbitmq.com/tutorials/amqp-concepts)*
##### Topic Exchange
Bruger [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing keys]] med mønstermatching (wildcards) til at sende meddelelser til [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]], der matcher et specifikt mønster. For eksempel kan en [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing key]] som `logs.error` dirigere meddelelser til en [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queue]], der er bundet med et mønster, der matcher `logs.*`.
![Pasted image 20241120080959.png](/img/user/Resource/98_Images/Pasted%20image%2020241120080959.png)
*Billedet er fra [lostechies](https://lostechies.com/derekgreer/2012/03/28/rabbitmq-for-windows-exchange-types/)*
##### Headers Exchange
[[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing keys]] ignoreres, og meddelelser dirigeres baseret på header-egenskaber, som kan indeholde flere nøgle-værdi-par.
![Pasted image 20241120081038.png](/img/user/Resource/98_Images/Pasted%20image%2020241120081038.png)
*Billedet er fra [javainuse](https://www.javainuse.com/messaging/rabbitmq/exchange)*
### AMQP Protokol  
RabbitMQ bruger **Advanced Message Queuing Protocol (AMQP)**, som er en åben standard for meddelelsesorienteret middleware. Denne protokol sikrer pålidelig levering af meddelelser mellem producenter og forbrugere.
### Routing Keys
**Routing keys** i RabbitMQ er en central del af *Message Routing* og bruges til at bestemme, hvordan meddelelser dirigeres fra en [[Publishing/Main/Noter/Programmering/RabbitMQ#Exchanges\|exchange]] til en eller flere [[Publishing/Main/Noter/Programmering/RabbitMQ#Queues\|queues]]. 

Routing keys er *strenge*, der følger bestemte mønstre og fungerer i forbindelse med bindinger.
#### Nøglepunkter om Routing Keys i RabbitMQ:
![Pasted image 20241120063240.png](/img/user/Resource/98_Images/Pasted%20image%2020241120063240.png)
*Billedet fra [CloudAMQP](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html)*

[[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|Routing keys]] gør RabbitMQ i stand til at håndtere komplekse meddelelsesruter og tilpasse sig forskellige behov i systemdesign og datadistribution.
## Funktioner

- **Asynkron Kommunikation:** RabbitMQ adskiller meddelelsesproducenter fra forbrugere, så de kan fungere uafhængigt.
- **Belastningsbalancering:** Meddelelser kan distribueres på tværs af flere consumers, hvilket muliggør effektiv behandling af opgaver.
- **Holdbarhed og Pålidelighed:** Meddelelser kan gemmes på disk, hvilket sikrer, at de ikke går tabt i tilfælde af fejl i [[Publishing/Main/Noter/Programmering/Message Brokers\|brokeren]].
- **Fleksibel Ruting:** Brugen af [[Publishing/Main/Noter/Programmering/RabbitMQ#Exchanges\|exchanges]] og [[Publishing/Main/Noter/Programmering/RabbitMQ#Routing Keys\|routing keys]] muliggør komplekse rutingscenarier tilpasset applikationsbehov.

## Anvendelsesområder

RabbitMQ er særligt nyttigt i scenarier som:

- **[[Publishing/Main/Noter/Emner/Backend/Microservice\|Microservice Arkitektur]]:** Lettere kommunikation mellem forskellige tjenester.
- **Messagequeues:** Fordeling af tidskrævende opgaver blandt arbejdende applikationer.
- **Hændelsessstreaming:** Håndtering af realtids begivenhedsdatabehandling.

Sammenfattende fungerer **RabbitMQ** som en robust løsning, der forbedrer applikationsydelse og pålidelighed ved at muliggøre *asynkron kommunikation* mellem forskellige systemer.

## Kilder
[RabbitMQ dokumentation](https://www.rabbitmq.com/)