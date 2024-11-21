---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-11-microservice/","hide":true,"created":"2024-10-11T10:53:03.237+02:00"}
---


De sidste par dage har jeg set på hvordan en Message Broker, som fx [[Main/Noter/RabbitMQ\|RabbitMQ]] , fungerer i forhold til microservices.


## Overvejelser og refleksioner

Umiddelbart vidste jeg intet om hvordan en #MessageBroker fungerer -  eller i det hele taget hvad den er.

Så jeg startede med at gå ind på [RabbitMq's hjemmeside](https://www.rabbitmq.com/tutorials/tutorial-one-dotnet), hvor de blandt andet har en hel fantastisk dokumentation, men også har en super tutorial for .net.

Jeg lavede denne for at forstå hvordan man sætter en producer og en consumer op.

Da jeg var færdig med tutorial'en, gik jeg i gang med at prøve på mit eget projekt. 

Her har jeg på skrivende tidspunkt opsat det på følgende måde:

![Vitahus, simplyfied mq.png](/img/user/Excalidraw/Vitahus,%20simplyfied%20mq.png)

Front: react - sender en request til en af de srvices jeg har på nuværende tidspunkt. Disse sender så beskeden videre til min #MessageBroker [[Main/Noter/RabbitMQ\|RabbitMQ]] som "lagrer" beskeden i en [[Main/Noter/RabbitMQ#Queues\|queue]], som vil blive "tømt" når der er en consumer der modtager en besked om at der er en Message klar til behandling.
Denne bliver så behandlet og sendt til den rette database i dette tilfælde MongoDB.

## Næste Skridt
Det næste vil være at få sat en gateway op til at lave en fælles kontaktflade til de kald der kommer til systemet.



