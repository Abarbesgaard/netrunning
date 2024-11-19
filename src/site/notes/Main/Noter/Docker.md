---
{"dg-publish":true,"permalink":"/main/noter/docker/","created":"2024-11-05T09:22:27.784+01:00"}
---

> [!important] Hvad er Docker?
> Docker er en open source-platform, der gør det muligt at opbygge, distribuere og køre software i containere. 


![Docker_ong.png](/img/user/Docker_ong.png)

## Hvad er Docker?

Docker er en containeriseringsteknologi, der tillader udvikling, distribution og kørsel af applikationer i isolerede miljøer kaldet **containere** [1](https://cybermonkey.dk/cyberpedia/docker-hvad-er-det-hvordan-virker-det-og-hvorfor-b) [2](https://opensource.dk/hvad-er-docker/). 

En container indeholder alt det nødvendige for at køre en applikation, herunder *kode*, *biblioteker*, *systemværktøjer* og *afhængigheder* [2](https://opensource.dk/hvad-er-docker/).

![Docker example 2.png](/img/user/Docker%20example%202.png)
*Billedet er fra [Docker](https://www.docker.com/resources/what-container/)*
## Hvordan fungerer Docker?

Docker bruger en klient-server-arkitektur med følgende hovedkomponenter:

- **Docker Engine**: Består af Docker Daemon, Docker API og Docker CLI. Dette håndterer opbygning og kørsel af containere [3](https://kinsta.com/dk/videnbase/hvad-er-docker/).
- **Docker-images**: Skabeloner der indeholder alt nødvendigt for at køre en applikation [2](https://opensource.dk/hvad-er-docker/).
- **Docker-containere**: Kørende instanser af Docker-billeder [1](https://cybermonkey.dk/cyberpedia/docker-hvad-er-det-hvordan-virker-det-og-hvorfor-b).

Docker Hub fungerer som et centralt lager for Docker-images, hvor udviklere kan dele og hente billeder [2](https://opensource.dk/hvad-er-docker/).

## Fordele ved Docker

- **Portabilitet**: Containere kan køre på enhver maskine med Docker installeret, uanset operativsystem [2](https://opensource.dk/hvad-er-docker/).
- **Effektivitet**: Containere deler operativsystemets kerne, hvilket gør dem mere ressourceeffektive end virtuelle maskiner [3](https://kinsta.com/dk/videnbase/hvad-er-docker/).
- **Skalerbarhed**: Det er nemt at skalere applikationer op eller ned ved at tilføje eller fjerne containere [2](https://opensource.dk/hvad-er-docker/).
- **Isolering**: Containere kører isoleret fra hinanden, hvilket øger sikkerheden [3](https://kinsta.com/dk/videnbase/hvad-er-docker/).

![Works on my machine.png](/img/user/Works%20on%20my%20machine.png)
*Billedet er fra [Activestate](https://www.activestate.com/blog/how-to-eliminate-works-on-my-machine-issues/)*
## Anvendelsesområder

Docker bruges primært af udviklere og DevOps-teams til at:

- Udvikle og teste applikationer i konsistente miljøer [4](https://prohoster.info/da/blog/administrirovanie/ponimaya-docker).
- Implementere applikationer hurtigt og effektivt [4](https://prohoster.info/da/blog/administrirovanie/ponimaya-docker).
- Standardisere udviklingsprocesser og infrastruktur [1](https://cybermonkey.dk/cyberpedia/docker-hvad-er-det-hvordan-virker-det-og-hvorfor-b).

![Docker example 1.png](/img/user/Docker%20example%201.png)
*Billedet fra [dbconvert](https://dbconvert.com/blog/building-docker-images-for-dbconvert-tools/)*

> [!info] opsummering
> Docker har revolutioneret softwareudvikling og -implementering ved at gøre det nemmere at bygge, distribuere og køre applikationer på en konsistent og effektiv måde på tværs af forskellige miljøer.

