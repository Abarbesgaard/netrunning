---
{"dg-publish":true,"permalink":"/main/noter/api-gateway/","created":"2024-11-11T10:19:56.138+01:00"}
---

## Hvad er en Reverse Proxy/API Gateway?
![Reverse proxy.png](/img/user/Reverse%20proxy.png)

> [!important] Opsummering 
> En **reverse proxy** eller **API Gateway** er en server, der står mellem en klient og en række servere, og som fungerer som en mellemmand for at håndtere, omdirigere eller filtrere anmodninger til forskellige backend-tjenester. I stedet for at klienterne interagerer direkte med serverne, kommunikerer de kun med API Gateway'en, som derefter videresender anmodningerne til den rigtige tjeneste og returnerer svaret til klienten.

Disse løsninger bruges i stor stil i moderne applikationsarkitekturer, især i microservices-arkitekturer, hvor de hjælper med at administrere kompleksiteten ved at håndtere mange små tjenester.

### Hvordan virker en Reverse Proxy/API Gateway?

En *reverse proxy/API Gateway* fungerer som **et enkelt indgangspunkt** for alle anmodninger, der skal rettes til forskellige backend-tjenester. Når en anmodning kommer fra en klient (f.eks. en webbrowser eller mobilapp), modtager API Gateway'en anmodningen og beslutter, hvilken backend-tjeneste der skal håndtere den. Derefter videresender den anmodningen til den valgte service og returnerer resultatet til klienten.

Udover at dirigere trafik, kan API Gateway'er også tilbyde ekstra funktionalitet som **autentificering**, **rate limiting**, **load balancing**, **logging**, **sikkerhed** og **caching**.

### Typer af Reverse Proxies/API Gateways

1. **Reverse Proxy**: En simpel form for API Gateway, der videresender anmodninger til backend-servere. Den håndterer ikke nødvendigvis kompleks logik som autentificering eller rate limiting, men fungerer som et mellemled for trafikstyring.
    
2. **API Gateway**: En mere avanceret løsning, der tilbyder et komplet sæt af funktioner som autentificering, [[Main/Noter/API\|API]]-rateregulering, load balancing, og caching. Den fungerer som et enkelt adgangspunkt for alle [[Main/Noter/API\|API]]-anmodninger, og hjælper med at abstrahere og forenkle kommunikationen mellem frontend og backend.

### Eksempler på brug af en Reverse Proxy/API Gateway

- **Autentificering og autorisation**: En API Gateway kan håndtere login og autentificering via OAuth2, JWT eller en anden protokol og sikre, at kun autoriserede brugere har adgang til de relevante [[Main/Noter/API\|API'er]].
    
- **Load balancing**: API Gateway'en kan sprede anmodninger mellem flere servere eller instanser af en tjeneste for at sikre høj tilgængelighed og belastningsfordeling.
    
- **Rate limiting**: For at forhindre overbelastning kan API Gateway'en begrænse antallet af anmodninger fra en given bruger eller IP-adresse over en bestemt tidsperiode.
    
- **Caching**: API Gateway'en kan cache ofte anmodede data for at reducere belastningen på backend-tjenesterne og forbedre svartiderne.
    
- **Logging og monitoring**: API Gateway'en kan fungere som et sted at opsamle logfiler og overvågningsdata for at få indsigt i systemets sundhed og præstation.
    

### Eksempler på Reverse Proxy/API Gateway-teknologier

1. **NGINX**: [NGINX](https://nginx.org/en/) er en populær reverse proxy, der ofte bruges som API Gateway i moderne applikationer. Den er kendt for sin høje ydeevne og evne til at håndtere store mængder trafik.
    
2. **Kong**: [Kong](https://konghq.com/products/kong-gateway) er en open-source API Gateway, der tilbyder avancerede funktioner som autentificering, rate limiting, logging og monitoring, og den kan nemt integreres med microservices-arkitekturer.
    
3. **Traefik**: [[Traefik\|Traefik]] er en moderne reverse proxy og load balancer, der er meget populær i Docker- og Kubernetes-miljøer. Den er dynamisk og automatisk opdager tjenester i et containerbaseret miljø.
    
4. **AWS API Gateway**: [AWS API Gateway](https://aws.amazon.com/api-gateway/) er en fuldt administreret service, der giver udviklere mulighed for at oprette, administrere og sikre [[Main/Noter/API\|API'er]] i cloudmiljøer.

![Pasted image 20241119082400.png](/img/user/Pasted%20image%2020241119082400.png)
*Billede fra [blog.treblle](https://blog.treblle.com/what-is-an-api-gateway-and-when-do-i-need-one/)*
### Fordele ved at bruge en Reverse Proxy/API Gateway

- **Centraliseret kontrol**: API Gateway'en giver et enkelt sted at administrere og kontrollere adgangen til forskellige mikroservices.
- **Skalering og load balancing**: Den kan hjælpe med at håndtere trafikbelastning og sikre høj tilgængelighed ved at distribuere anmodninger til flere servere.
- **Forbedret sikkerhed**: API Gateway'er kan tilbyde funktioner som autentificering, kryptering og rate limiting, som beskytter backend-tjenester mod misbrug og angreb.
- **Simplificering af frontend-arkitektur**: I stedet for at kommunikere direkte med flere backend-tjenester, kan frontend-applikationer kommunikere med en enkelt API Gateway, hvilket forenkler arkitekturen og gør det lettere at udvikle og vedligeholde.

## Konklusion

En **Reverse Proxy/API Gateway** er et essentielt element i moderne applikationer, især i[[Main/Noter/Emner/Backend/Microservice\|mikroservice-arkitekturer]] . Det hjælper med at abstrahere backend-tjenesterne, forbedre sikkerheden og ydeevnen, samt give centraliseret kontrol over [[Main/Noter/API\|API-trafik]]. Ved at implementere en API Gateway kan du sikre, at applikationen forbliver *skalerbar*, *fleksibel* og *sikker*, samtidig med at den tilbyder en effektiv måde at styre kommunikation mellem frontend og backend på.