---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-11-04-truselsmodel/","created":"2024-11-04T06:29:49.315+01:00"}
---


![Vita_Microservice_Diagram.png](/img/user/Excalidraw/Vita_Microservice_Diagram.png)

I sidste uge lavede jeg denne ovenstående model der tillader en bruger i vores system at oprette en video (indsætte et link til youtube video) og gemme den. Samt blive notificeret herom.

Jeg har allerede taget lidt forhold regler i forhold til load balancing samt autentifikation og autorisation. 

I det tænkte senarie er dette sat op, lige nu i #APIGateway .

Nu vil jeg se på hvad [[Main/Noter/OWASP\|OWASP]]til sårbarhederne for et umiddelbart simpelt system, som ovenstående. 
I 2023 lavede de en opdatering af det trusselsbillede som udviklere står overfor i dag. 
Se hvad de indebærer her: [OWASP Top 10 API Security Risks - 2023](https://owasp.org/API-Security/editions/2023/en/0x11-t10/)

I vores diagram, er der lige nu kun er **meget** basal sikkerhed: Auth og Load balancing.

> [!TODO] note 
> Igen dette er et tænkt eksempel

Jeg vil nu gennemgå det første punkt fra OWASP API top 10 med fokus på vores API. 

*Klik ind på følgende overskrifter for at se hvordan jeg forholder mig til hver punkt*

## 1 
![2023 Broken Object Level Authorization.png](/img/user/2023%20Broken%20Object%20Level%20Authorization.png)
## [[Main/Noter/Vita/Vita Broken Object level Authorization\|Broken Object Level Authorization]]
## 2
## [[Main/Noter/Vita/Vita Broken Authentication\|Broken Authentication]]

## 3
## [[Main/Noter/Vita/Vita Broken Object Property Level Authorization\|Broken Object Property Level Authorization]]
## 4
## [[Main/Noter/Vita/Vita Unrestricted Resource Consumption\|Unrestricted Resource Consumption]]
## 5
## [[Main/Noter/Vita/Vita Broken Function Level Authorization\|Broken Function Level Authorization]]
## 6
## [[Main/Noter/Vita/Vita Unrestricted Access to Sensitive Business Flows\|Unrestricted Access to Sensitive Business Flows]]
## 7
## 8
## 9
## 10
