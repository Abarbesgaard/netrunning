---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-11-01-it-sikkerhed/","hide":true,"created":"2024-11-01T10:03:33.362+01:00"}
---

Ud fra følgende [[Main/Noter/use case indsæt video\|use case]] vil jeg forsøge at finde de domæner den berør og se hvad der er af sikkerhedsudfordringer ved denne.
### Use Case opsummering:
Brugeren logger ind ved at indtaste deres **brugernavn** og **adgangskode**, hvorefter systemet validerer oplysningerne og bekræfter login. Når brugeren er logget ind, vælger de at indsætte en video, hvor de indtaster nødvendige oplysninger som titel og beskrivelse samt uploader videofilen. Efter uploaden gemmer systemet videoen og viser en bekræftelse til brugeren. 
Hvis brugeren indtaster ugyldige login-oplysninger, kan de modtage en fejlmeddelelse, og der er også mulighed for at nulstille adgangskoden, samt håndtere eventuelle fejl under videoindsendelsen, som kan kræve en ny forsøgsindsendelse.

Følgende domæner kan udledes ud fra følgende usecase:
### 1. **Brugeradministration (User Management)**

- **Funktioner:** Håndtering af brugeroplysninger, registrering, login, autentificering og autorisering.
- **Microservice:** **User Service** - Denne service kan håndtere alt vedrørende brugerkonti, inklusive oprettelse af nye brugere, login-processer og adgangskodehåndtering.

### 2. **Videoadministration (Video Management)**

- **Funktioner:** Upload, lagring, behandling og visning af videoer.
- **Microservice:** **Video Service** - Denne service kan håndtere videoindsendelse, gemme videoer i databasen eller cloud-lagring og generere metadata relateret til videoerne (f.eks. titel, beskrivelse).

### 3. **Metadata- og Indholdsadministration (Metadata and Content Management)**

- **Funktioner:** Håndtering af videooplysninger, som titel, beskrivelse og kategorisering.
- **Microservice:** **Content Service** - Denne service kan være ansvarlig for at gemme og administrere metadata om videoer samt muligheden for at redigere disse oplysninger.

### 4. **Sikkerhed (Security)**

- **Funktioner:** Implementering af sikkerhedsforanstaltninger som tofaktorgodkendelse og session management.
- **Microservice:** **Auth Service** - En dedikeret service til at håndtere autentificering, adgangskontrol og sikkerhedspolitikker for brugere.

### 5. **Notifikation (Notification)**

- **Funktioner:** Informere brugeren om status ved videoindsættelse, succes eller fejl.
- **Microservice:** **Notification Service** - Denne service kan sende beskeder til brugeren om, at videoen er blevet uploadet korrekt eller informere dem om fejl under indsendelsen.

### 6. **Fejl- og Logningshåndtering (Error and Logging Management)**

- **Funktioner:** Håndtering af fejlmeddelelser og systemlogs.
- **Microservice:** **Logging Service** - En service til at indsamle og analysere logdata, hvilket kan hjælpe med fejlfindings- og overvågningsopgaver.

### 7. **API Gateway**

- **Funktioner:** Centraliseret adgang til forskellige microservices.
- **Microservice:** **API Gateway** - En service, der fungerer som et indgangspunkt for alle klientanmodninger, der ruter til de respektive microservices og håndterer forespørgsler.

Dette vil udmunde i følgende diagram:
![Vita_Microservice_Diagram.png](/img/user/Excalidraw/Vita_Microservice_Diagram.png)

### Læringsmål i spil
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§1\|Microservice viden: §1]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§2\|Microservice viden: §2]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§5\|Microservice kompetencer: §7]]

[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§3\| It-Sikkerhed: viden §3]]
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§5\| It-Sikkerhed: færdigheder §5]]
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§5\| It-Sikkerhed: kompetencer §5]]
