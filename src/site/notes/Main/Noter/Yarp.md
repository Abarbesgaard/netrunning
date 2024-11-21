---
{"dg-publish":true,"permalink":"/main/noter/yarp/","created":"2024-11-21T10:09:47.392+01:00"}
---

> [!important] Hvad er YARP
> YARP (Yet Another Reverse Proxy) er et open-source bibliotek udviklet af Microsoft til at implementere reverse proxy-funktionalitet i .NET-applikationer [1](https://www.partech.nl/en/publications/2022/03/what-is-yarp) [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59). Det er designet til at være meget fleksibelt og tilpasningsdygtigt, så udviklere kan bygge skræddersyede reverse proxies ved hjælp af .NET-teknologier [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).

![Pasted image 20241121101048.png](/img/user/98_Images/Pasted%20image%2020241121101048.png)
*Billedet er fra [Kinsta](https://kinsta.com/blog/reverse-proxy/)*
## Hovedfunktioner

- **Høj ydeevne**: YARP er bygget oven på ASP.NET Core og udnytter dets højtydende netværksstack [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).
- **Udvidelsesmuligheder**: Det er nemt at tilføje eller erstatte moduler for at implementere kerneproxy-funktionaliteter [1](https://www.partech.nl/en/publications/2022/03/what-is-yarp).
- **Dynamisk konfiguration**: Understøtter dynamiske opdateringer af ruter og klynger, hvilket er nyttigt i moderne mikroservice-arkitekturer [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).
- **Protokolunderstøttelse**: YARP understøtter almindelige webprotokoller som HTTP, HTTPS og WebSockets [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).
- **Load balancing**: Giver mulighed for at konfigurere forskellige load balancing-strategier [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).

## Anvendelsesområder

YARP kan bruges som:

1. [[Main/Noter/API-Gateway\|API-gateway]] i [[Main/Noter/Emner/Backend/Microservice\|mikroservice-arkitekturer]]
2. Load balancer til at fordele trafik på tværs af flere servere
3. Routing-værktøj til at dirigere anmodninger baseret på stier, headers eller andre kriterier
4. Sikkerhedsproxy til at beskytte backend-tjenester mod direkte adgang [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59)

YARP adskiller sig fra andre reverse proxies ved at være *specifikt designet til .NET-økosystemet* og er mere et framework end en selvstændig proxyserver [2](https://dev.to/hossien014/what-is-yarp-vs-nginx-4m59).