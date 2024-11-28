---
{"dg-publish":true,"permalink":"/main/artikler/microservices/hvorfor-er-en-message-broker-vigtig-i-microserivces/","tags":["Microservices","MessageBrokers","SoftwareArchitecture"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-11-27T14:38:38.610+01:00"}
---

[[Main/Noter/Emner/Backend/Microservice\|Microservices-arkitektur]] har revolutioneret måden, vi bygger og skalerer applikationer på. Ved at bryde en [[Main/Noter/Monolitiske Applikationer\|monolitisk applikation]] ned i små, *uafhængige services* kan teams opnå større fleksibilitet, skalerbarhed og vedligeholdelse. 

Men med denne arkitektur opstår også nye udfordringer, især når det gælder kommunikation mellem de forskellige services. Her spiller en [[Main/Noter/Message Brokers\|message broker]] en afgørende rolle.

---

#### Hvad er en Message Broker?

![Pasted image 20241127145828.png](/img/user/Pasted%20image%2020241127145828.png)
*Billedet er fra [tsh](https://tsh.io/blog/message-broker/)*

En message broker er et softwaremodul, der gør det muligt for [[Main/Noter/Emner/Backend/Microservice\|microservices]] at kommunikere med hinanden via beskeder. Det fungerer som en mellemmand, der modtager beskeder fra én service og leverer dem til en eller flere modtagere. Eksempler på populære [[Main/Noter/Message Brokers\|message brokers]] inkluderer [[Main/Noter/RabbitMQ\|RabbitMQ]], **Apache Kafka**, **Amazon SQS** og **Azure Service Bus**.

---

#### Udfordringer i Microservices uden en [[Message Brokers|Message Broker]

Uden en message broker kan [[Main/Noter/Emner/Backend/Microservice\|microservices]] kommunikation blive afhængig af *synkrone* HTTP-anmodninger. Dette skaber følgende udfordringer:

1. **Høj kobling mellem services**: Hvis service A afhænger direkte af service B's tilgængelighed, kan fejl i B påvirke A negativt.
2. **Performance-flaskehalse**: Direkte anmodninger mellem services kan føre til øget latenstid og flaskehalse, især ved høj trafik.
3. **Manglende skalerbarhed**: At skalere en service for at håndtere øgede krav kan være vanskeligere uden en central mekanisme til at distribuere arbejdsbyrden.
4. **Fejlhåndtering**: Uden en mellemmand kan det være svært at genlevere beskeder eller håndtere fejl korrekt.

---
#### Hvordan løser en [[Main/Noter/Message Brokers\|Message Broker]] disse udfordringer?

![Pasted image 20241127145901.png](/img/user/Pasted%20image%2020241127145901.png)
*Billedet er fra [Medium](https://betterprogramming.pub/why-do-we-need-message-broker-7382ce0e46c6)*

1. **Asynkron Kommunikation**  
    Med en [[Main/Noter/Message Brokers\|message broker]] kan [[Main/Noter/Emner/Backend/Microservice\|microservices]] kommunikere *asynkront*. Dette betyder, at en service kan sende en besked og fortsætte sit arbejde uden at vente på svar. Dette reducerer latenstid og afhængighed mellem services.
    
2. **[[Loose Coupling\|Løs Kobling]]**  
    Message brokers tillader services at kommunikere uden at kende hinandens detaljer. Dette gør det nemmere at tilføje, ændre eller fjerne services uden at påvirke hele systemet.
    
3. **Fejltolerance og Pålidelighed**  
    [[Main/Noter/Message Brokers\|Message brokers]] har indbyggede mekanismer til fejlhåndtering, såsom køer til genlevering, *dead letter queues* (DLQ) og beskedlagring, der sikrer, at ingen besked går tabt, selv hvis en service er midlertidigt utilgængelig.
    
4. **Skalerbarhed**  
    Ved hjælp af [[Main/Noter/Message Brokers\|message brokers]] kan arbejdsbyrden fordeles på tværs af flere instanser af en service. Dette gør det muligt at skalere dele af systemet uafhængigt af hinanden.
    
5. **Broadcast og Pub/Sub**  
    [[Main/Noter/Message Brokers\|Message brokers]] understøtter forskellige kommunikationsmønstre som **publish/subscribe (pub/sub)**, hvor én besked kan sendes til flere modtagere, og **point-to-point**, hvor en besked leveres til en specifik modtager.
    

---

#### Use Case: Bestilling af Billetter

Forestil dig et system til billetbestilling, hvor tre [[Main/Noter/Emner/Backend/Microservice\|microservices]] samarbejder:

1. **OrdreService**: Modtager en ny ordre fra brugeren.
2. **BetalingsService**: Håndterer betaling for ordren.
3. **NotifikationsService**: Sender en kvittering til brugeren.

Med en [[Main/Noter/Message Brokers\|message broker]] kan denne proces designes *asynkront*:

- **OrdreService** sender en besked til [[Main/Noter/Message Brokers\|message brokeren]] om, at en ny ordre er oprettet.
- **BetalingsService** lytter til denne besked, behandler betalingen og sender en ny besked om betalingsstatus.
- **NotifikationsService** lytter til betalingsstatus og sender en kvittering, når betalingen er bekræftet.

Denne arkitektur sikrer, at hver service kan fungere uafhængigt og genstarte ved fejl uden at forstyrre resten af systemet.

---

#### Hvornår skal man bruge en Message Broker?

En [[Main/Noter/Message Brokers\|message broker]] er især værdifuld i følgende scenarier:

- **Event-drevet arkitektur**: Hvor services reagerer på hændelser.
- **Høj trafik eller komplekse flows**: Når flere services skal samarbejde om en arbejdsbyrde.
- **Skalerbare systemer**: Når visse dele af systemet skal kunne håndtere store datamængder.
- **Upålidelige netværk**: Hvor beskedgenlevering er afgørende.

---

#### Ulemper og Overvejelser

![Pasted image 20241127150243.png](/img/user/Pasted%20image%2020241127150243.png)
*Billedet er fra [IStock](https://www.istockphoto.com/photos/frustrated-man)*

Selvom en [[Main/Noter/Message Brokers\|message broker]] løser mange problemer, er der også ulemper:

- **Kompleksitet**: Det tilføjer en ekstra komponent, der skal overvåges og vedligeholdes.
- **Overhead**: Beskedhåndtering kan introducere ekstra latency og ressourcetræk.
- **Læringskurve**: Det kræver en forståelse af brokermodellen og koncepter som køer, topic routing og genlevering.

> [!note] Segway
> Disse overvejelser hænger tæt sammen med designvalg i softwareudvikling, hvor diskussionen om **locality of behaviour** kontra **clean code** ofte bliver relevant. Jeg har skrevet [[Main/Artikler/LoB vs Clean Code\|denne artikel]], der dykker ned i dette emne og udforsker balancen mellem kodens læsbarhed og dens effektivitet i komplekse systemer – læs den for en dybere indsigt!

---

#### Konklusion

En [[Main/Noter/Message Brokers\|message broker]] er et kraftfuldt værktøj i [[Main/Noter/Emner/Backend/Microservice\|microservices-arkitektur]]. Den løser mange af de udfordringer, der opstår med distribueret kommunikation, og gør det muligt at bygge robuste, skalerbare og fleksible systemer. 

Ved at vælge en [[Main/Noter/Message Brokers\|message broker]], der passer til dine behov, kan du tage det første skridt mod en mere sammenkoblet og pålidelig microservices-arkitektur.

Hvad er dine erfaringer med at bruge [[Main/Noter/Message Brokers\|message brokers]] i [[Main/Noter/Emner/Backend/Microservice\|microservices-arkitektur]]? Har du stået over for nogen af de udfordringer, der nævnes her, eller måske fundet kreative løsninger? 
Del dine tanker i kommentarfeltet – jeg vil gerne høre om både succeser og udfordringer i dit arbejde med [[Main/Noter/Message Brokers\|message brokers]]! 
👇👇👇

## Kilder
- Jackynote, "Message Brokers: Pros, Cons, and Their Crucial Role in Microservices," [Dev.to](https://dev.to/jackynote/message-brokers-pros-cons-and-their-crucial-role-in-microservices-56pi)​
- "HTTP vs. Messaging for Microservices Communications," [DZone](https://dzone.com/articles/http-vs-messaging-for-microservices-communications)​
   
- "REST vs. Message Brokers: Choosing the Right Communication Method," [DZone](https://dzone.com/articles/rest-vs-message-brokers-choosing-the-right-communi)​

- "Comparing REST and Message Brokers: Choosing the Right Communication," [SuperStream.ai](https://superstream.ai/blog/comparing-rest-and-message-brokers-choosing-the-right-communication/)​
- "Message Broker Pattern for Microservices Inter-Service Communication," [Redis.io](https://redis.io/solutions/message-broker-pattern-for-microservices-interservice-communication/)​

- Rhodes, "Microservice Integration Patterns: Point-to-Point vs. Message Brokers," [LinkedIn](https://www.linkedin.com/pulse/microservice-integration-patterns-point-to-point-vs-message-rhodes-7sfoc/)​

## Andre artikler med samme emne
| File                                                            | Title         | Tags                                                                     |
| --------------------------------------------------------------- | ------------- | ------------------------------------------------------------------------ |
| [[Main/Artikler/Microservices/Mono vs Micro\|Mono vs Micro]] | Mono vs Micro | <ul><li>#Monolith</li><li>#Microservices</li><li>#Architecture</li></ul> |

{ .block-language-dataview}
