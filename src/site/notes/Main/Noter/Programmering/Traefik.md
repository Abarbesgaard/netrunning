---
{"dg-publish":true,"permalink":"/main/noter/programmering/traefik/","created":"2024-11-19T08:27:25.986+01:00"}
---

## Kilder
> [!important] Opsummering
> Traefik er en moderne open source [[Main/Noter/Programmering/API-Gateway\|reverse proxy]] og ingress controller, der forenkler og automatiserer håndteringen af [[Main/Noter/Emner/Backend/Microservice\|microservices]]



![traefik example.png](/img/user/Resource/98_Images/traefik%20example.png)
*Billedet er fra [traefik](https://traefik.io/traefik/)*
## Hovedfunktioner

- **Dynamisk konfiguration**: Traefik opdager automatisk ændringer i infrastrukturen og opdaterer routingreglerne i realtid uden manuel konfiguration [1](https://doc.traefik.io/traefik/getting-started/concepts/) [3](https://traefik.io/traefik/).
- **Automatisk service discovery**: Traefik integrerer med forskellige cluster-teknologier som [Kubernetes](https://kubernetes.io/), [Docker Swarm](https://docs.docker.com/engine/swarm/) og [AWS](https://aws.amazon.com/) for at opdage services automatisk [1](https://doc.traefik.io/traefik/getting-started/concepts/) [2](https://doc.traefik.io/traefik/).
- **Edge router**: Fungerer som indgangspunkt til platformen og håndterer al indkommende trafik baseret på definerede regler [1](https://doc.traefik.io/traefik/getting-started/concepts/).

## Centrale koncepter

- **EntryPoints**: Definerer netværksindgangspunkterne til Traefik [1](https://doc.traefik.io/traefik/getting-started/concepts/).
- **Routers**: Forbinder indkommende requests med de relevante [[Main/Noter/Emner/Backend/Microservice\|services]] [1](https://doc.traefik.io/traefik/getting-started/concepts/).
- **Middlewares**: Kan modificere requests eller responses før de sendes til  [[Main/Noter/Emner/Backend/Microservice\|services]] [1](https://doc.traefik.io/traefik/getting-started/concepts/).
- **[[Main/Noter/Emner/Backend/Microservice\|Services]]**: Konfigurerer hvordan Traefik når de faktiske services der skal håndtere requests [1](https://doc.traefik.io/traefik/getting-started/concepts/).

## Fordele

- Simplificerer og automatiserer routing og load balancing af  [[Main/Noter/Emner/Backend/Microservice\|services]] [3](https://traefik.io/traefik/).
- Understøtter alle større protokoller og tilbyder et rigt sæt af middlewares [3](https://traefik.io/traefik/).
- Nem at operere, men kan håndtere store, komplekse deployments på tværs af forskellige miljøer [3](https://traefik.io/traefik/).
- Indbygget support for SSL-terminering og automatisk certifikatgenerering via Let's Encrypt [3](https://traefik.io/traefik/).

Traefik er designet til at være enkel at bruge, men samtidig kraftfuld nok til at håndtere komplekse scenarier i moderne cloud-native arkitekturer [2](https://doc.traefik.io/traefik/) [3](https://traefik.io/traefik/).