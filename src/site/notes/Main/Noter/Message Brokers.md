---
{"dg-publish":true,"permalink":"/main/noter/message-brokers/","created":"2024-11-13T08:04:32.981+01:00"}
---


En message broker er en softwarekomponent, der faciliterer asynkron kommunikation mellem forskellige systemkomponenter eller mikroservices ved at videresende beskeder mellem dem. 

Message brokers kan hjælpe med at øge skalerbarheden, pålideligheden og fleksibiliteten i distribuerede systemer. De agerer som mellemled, hvor beskeder kan modtages, gemmes og videresendes, hvilket skaber en form for _decoupling_, så de kommunikerende systemer ikke behøver at være direkte forbundet eller kende hinandens detaljer.

De vigtigste arkitektoniske mønstre, som message brokers ofte implementerer, inkluderer:

1. **Publisher-Subscriber**: Her kan beskeder sendes til mange modtagere via en enkelt kanal, hvor hver subscriber kun modtager de beskeder, som matcher deres abonnementskriterier. Dette mønster er nyttigt i systemer, hvor mange services skal reagere på samme begivenhed.
    
2. **Point-to-Point**: Her sendes en besked fra en producent til en specifik kø, og kun én modtager forbruger beskeden. Dette bruges typisk til at fordele arbejdsopgaver mellem flere services, fx kø for arbejdsfordeling eller opgaveudførsel.
    
3. **Event-Driven Architecture (EDA)**: Message brokers kan understøtte event-baserede systemer, hvor services reagerer på hændelser i stedet for at afhænge af synkrone kald. Dette mønster muliggør løst koblede services, hvor ændringer i en service ikke nødvendigvis kræver tilpasning i andre services.
    
4. **Routing og Filtrering**: Nogle message brokers understøtter mønstre som routing, hvor beskeder distribueres baseret på indhold eller metadata, og filtrering, hvor kun bestemte services modtager relevante beskeder.
    

Message brokers som [[Main/Noter/RabbitMQ\|RabbitMQ]], Apache Kafka og NATS benytter sig af disse mønstre til at skabe fleksible, skalerbare systemer, der kan håndtere kompleks kommunikation på tværs af applikationer.