---
{"dg-publish":true,"permalink":"/main/noter/emner/backend/microservice/","title":"Microservice","hide":true,"tags":["Backend","Microservice","Projektarbejde"],"created":"2024-09-05T09:15:05.478+02:00"}
---

![Microservice.png](/img/user/Main/Images/Microservice.png)

**Microservices** er en arkitektur, hvor en applikation opdeles i mindre,
selvstændige services, der hver især har en specifik funktion.

Disse services er løst koblede og kan udvikles, implementeres og skaleres
uafhængigt af hinanden. Kommunikation mellem microservices sker typisk
via REST API'er, message brokers eller service mesh.

## Fordele

- Nem opdatering og tilføjelse af funktioner
- Individuel skalering af komponenter
- Fremmer agil udvikling med tværfunktionelle teams

## Udfordringer

- Øget kompleksitet i styring og overvågning
- Kræver DevOps og container-baserede værktøjer som Docker og Kubernetes
- Risiko for overkomplicering ved for mange eller små services
- Microservices anbefales kun, når en monolitisk applikation bliver for kompleks.

## Kilder

[[Main/Noter/Litteratur/Noter/Microservices_Explained\|Microservices Explained - Youtube]]
[[Main/Noter/Litteratur/Noter/What_Are_Microservices_IBM\|What Are Microservices - IBM]]