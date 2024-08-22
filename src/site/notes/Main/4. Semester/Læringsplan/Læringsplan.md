---
{"dg-publish":true,"permalink":"/main/4-semester/laeringsplan/laeringsplan/","title":"Læringsplan U. 33 - 34","tags":["læringsmål","systemudvikling","projektarbejde","programmering"],"created":"2024-08-22T11:08:13.868+02:00"}
---


## Om udformningen af læringsplanen

Følgende læringsplan er udarbejdet i  starten af semesteret, for at skabe et
overblik over de emner som er relevante for semesterprojektet, og opfylde de
[[Main/4. Semester/Læringsmål/Læringsmål\|Læringsmål]], som er sat for semesteret af underviserne.
Men også de personlig mål som jeg selv har sat for [[Main/4. Semester/Læringsmål/Microservices\|Microservices]] og
[[Main/4. Semester/Læringsmål/It-Sikkerhed\|It-Sikkerhed]].

Det store mål for mig i dette semester er at få en dybere forståelse for
hvordan man laver **Microservices**.

Med udgangspunkt i dette [[Main/4. Semester/Emner/Mindmap\|mindmap]] og [[Main/Systemudvikling/Smart_Mål\|smart mål]] har jeg udarbejdet
følgende læringsplan:

Nedenfor ses den læringsplan som jeg har udarbejdet for 4. Semester.

## Læringsplan

### **Uge**: [[Main/4. Semester/Læringsplan/33_34\|33 - 34]]

#### Grundlæggende Research

**Fokus**: Backend, IT-Sikkerhed og grundlæggende forståelse af microservices.
At finde ukendte og ukendte ukendte.

### **Uge**: [[Main/4. Semester/Læringsplan/35_36\|35 - 36]]

- Introduktion til Microservices: Forstå grundprincipperne og fordelene ved
microservices.
- Service-Oriented Architecture (SOA): Undersøg SOAP, WSDL, og hvordan
SOA adskiller sig fra microservices.
- Opgave: Design en simpel microservices-arkitektur og dokumenter forskellene
mellem microservices og SOA.

#### Fine-grained vs. Coarse-grained Microservices

- Fine-grained vs. Coarse-grained: Læs om de to tilgange og deres implikationer
på design.
- Event-Based Communication: Forstå hvordan event-baseret kommunikation
fungerer, og lær om messaging-systemer som RabbitMQ og Kafka.
- Opgave: Implementér en simpel event-baseret kommunikation ved hjælp af
RabbitMQ eller Kafka.

### **Uge**: [[37_38\|37 - 38]]

#### Cloud-baseret Arkitektur og API-Gateway

- Cloud-tjenester: Læs om de grundlæggende tjenester på AWS, Azure, og
Google Cloud.
- Opsætning i Cloud: Deploy en grundlæggende microservice på en af disse
cloud-platforme.
- Opgave: Konfigurer en simpel service på din valgte cloud-platform og
dokumenter processen.

#### Hybrid Arkitektur og API-Gateway

- Hybrid Arkitektur: Forstå hierarkiske og service-baserede modeller.
- API-Gateway: Læs om API-gateways og hvordan de styrer adgang til microservices.
- Opgave: Design en hybrid arkitektur og opsæt en API-gateway ved hjælp af en løsning
som Kong eller NGINX.

### **Uge**: [[39_40\|39 - 40]]

#### Systemeffektivitet

- Skalerbarhed og Redundans: Undersøg hvordan du kan sikre skalerbarhed og redundans.
- Fault-Tolerance og Latency: Læs om fault-tolerance, latency, grid lock, og
timeout logic.
- Opgave: Analysér en eksisterende arkitektur for effektivitet og find måder
at forbedre systemeffektiviteten på.

#### Fejlhåndtering og Transaktionsgrænser

- Fejlhåndtering: Forstå circuit breakers, retry logic, og timeout logic.
- Transaktionsgrænser: Læs om ACID vs BASE og distributed transactions.
- Opgave: Implementér circuit breakers og retry mekanismer. Overvej hvordan du
kan håndtere distributed transactions i dine microservices.

### **Uge**: [[41_43\|41 - 43]]

#### CI/CD og Automation

- CI/CD Pipelines: Læs om Docker, DevOps, og CI/CD processer.
- Automation: Opsæt en CI/CD pipeline ved hjælp af Docker og en CI/CD-platform
som GitHub Actions eller Jenkins.
- Opgave: Implementér en CI/CD pipeline for dine microservices og automatisér
bygning og deployment.

#### Sikkerhed - Secret Management og Secure Pipelines

- Secret Management: Undersøg metoder til secret management med værktøjer som
HashiCorp Vault.
- Secure Pipelines: Læs om sikkerhed i pipelines og hvordan du beskytter dine build-processer.
- Opgave: Implementér secret management med HashiCorp Vault og sikr din CI/CD pipeline.
