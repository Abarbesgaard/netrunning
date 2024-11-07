---
{"dg-publish":true,"permalink":"/opsummering-af-4-semester/","created":"2024-11-06T08:44:04.025+01:00"}
---

# Opsummering af læringsforløb - 4. semester

Denne side opsummerer mit læringsforløb fra starten af august til slutningen af november, på 4. semester på datamatiker online. Jeg valgte at fokusere på microservices og it-sikkerhed.

## Indledning

I starten af [[Main/4. Semester/Læringsplan/33_34\|august]] var jeg overbevist om, at it-sikkerhed for mig ville handle om emner som DDoS, penetrationstest, white/black hat, etc. Dette afspejlede sig i mine [[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål\|læringsmål]], som initialt fokuserede på viden og færdigheder indenfor disse emner. Men i løbet af semesteret har jeg opdaget nye, spændende emner og udvidet min forståelse af it-sikkerhed, især i relation til microservices og API-sikkerhed.

## Diagram: Læringsforløb

![It-sikkerhed_Læringsforløb.png](/img/user/Excalidraw/It-sikkerhed_L%C3%A6ringsforl%C3%B8b.png)

Den store røde bjælke i [[Main/4. Semester/Læringsplan/33_34\|uge 33 - 34]] markerer starten på projektet, hvor alt virkede interessant. Jeg havde oprindeligt meget bredt fokus, men hurtigt fandt jeg ud af, at it-sikkerhed i høj grad også handler om design og arkitektur – særligt med hensyn til, hvordan man håndterer *autentifikation*, *autorisation* og *beskyttelse* af API'er i en microservice-arkitektur.

## Refleksion over ændringer i forståelse af It-sikkerhed

### Før og efter-billede

**Før:**
Jeg havde en grundlæggende forståelse af it-sikkerhed baseret på netværksangreb og penetrationstest. Jeg troede, at it-sikkerhed primært handlede om at beskytte eller angrive mod eksterne trusler som DDoS-angreb og hackerangreb.

**Efter:**
Jeg indså, at it-sikkerhed i høj grad handler om at sikre applikationer mod interne fejl og menneskelige fejl, som kan opstå under *udvikling* og *implementering*. 
Det var vigtigt, for mig, at forstå, hvordan sikkerhed *skal integreres i hele applikationen*, ikke kun som et sidste skridt. Jeg har lært meget om hvordan man beskytter APIs mod *autorisationsfejl*, *rate limiting*, og hvordan man bruger moderne sikkerhedsløsninger som OAuth2 og JWT.

## Konkretisering af læringsmål og hvordan de er opnået

### Opnåelse af læringsmål

I løbet af semesteret har jeg opnået mine mål om at få en dybere forståelse af distributed systems og eventuel konsistens, især i forbindelse med microservices-arkitektur. Et vigtigt element har været arbejdet med [[Main/Noter/RabbitMQ\|RabbitMQ]] til asynkrone beskeder og eventuel konsistens. 
Jeg har implementeret [[Main/Noter/RabbitMQ\|RabbitMQ]] til at håndtere kommunikation mellem microservices, hvilket har givet mig et praktisk indblik i, hvordan man kan sikre, at systemet fungerer korrekt, selv når der er forsinkelser eller uoverensstemmelser mellem services.

Jeg har arbejdet med at designe et system, hvor data kan blive opdateret på tværs af flere services uden at kræve øjeblikkelig konsistens. I stedet har systemet implementeret *eventual consistency*, hvilket betyder, at data i systemet vil blive synkroniseret over tid og ikke nødvendigvis med det samme. Jeg har anvendt RabbitMQ til at sikre, at opdateringer og ændringer sendes som beskeder mellem systemerne, hvilket tillader microservices at arbejde uafhængigt og samtidig opretholde dataintegritet over tid.

### Justering af læringsmål

Jeg justerede mine læringsmål undervejs og indså, at det ikke kun handler om at beskytte mod eksterne angreb, men også om at sikre funktioner, der kan udnyttes af en angriber via API'erne. Jeg har lært vigtigheden af at implementere grundig funktionel autorisation for at sikre, at brugere kun har adgang til de funktioner, de er autoriseret til.

## Refleksion over udviklingsperioder

### Uge 33-34: Projektstart og planlægning

Denne periode var fokuseret på at få projektet sat op og vælge emner. Jeg definerede mine mål og begyndte at forstå de basale principper omkring microservices og it-sikkerhed.

### Uge 37-38: Microservices og API-sikkerhed

Jeg dykkede ned i API-sikkerhed og begyndte at implementere rate limiting i YARP og OAuth2 til API-gatewayen. Jeg lærte også om API-sårbarheder som Broken Function Level Authorization og hvordan man beskytter API'er mod uautoriseret adgang.

### Uge 39-40: Sikkerhedsdesign og implementering

I denne periode arbejdede jeg intensivt med sikkerhed i forbindelse med de funktionelle krav i microservices. Jeg lærte at integrere rate limiting og authorization checks effektivt i API-endpoints for at forhindre misbrug og forhindre unødvendig belastning af systemet.

### Uge 41-42: Evaluering og implementering af avancerede sikkerhedsforanstaltninger

Jeg fokuserede på at implementere ekstra sikkerhedsforanstaltninger som TLS i RabbitMQ og trusselsmodellering. Jeg lærte at identificere potentielle sårbarheder i systemet og planlægge passende modforanstaltninger.

## Feedback og refleksioner

Jeg har modtaget værdifuld feedback, især i forbindelse med **sikkerhed** ved **API-udvikling**. Jeg fik at vide, at det var vigtigt at overveje *rate limiting* og *API-gateways* som en måde at forhindre, at uautoriserede brugere får adgang til følsomme data. Jeg har taget denne feedback til mig og arbejdet med at integrere de anbefalede løsninger i min kode.

## Fremtidig anvendelse og overføringsværdi

De færdigheder, jeg har opnået i dette semester, vil have stor værdi i fremtidige projekter. Jeg ser mig selv bruge de teknologier og koncepter, jeg har lært om, især inden for API-sikkerhed og rate limiting, til at udvikle robuste, sikre applikationer. Jeg vil fortsat arbejde på at styrke mine færdigheder inden for trusselsmodellering og sikre applikationer mod både interne og eksterne trusler.

## Afslutning

Dette semester har været meget lærerigt, og jeg føler mig meget mere sikker på mine evner til at udvikle sikre microservices og API'er. Jeg ser frem til at implementere de teknologier og metoder, jeg har lært, i fremtidige projekter og udfordringer.

### Mine vigtigste læringer:

- Betydningen af funktionel autorisation og rate limiting i en microservice-arkitektur
- Hvordan man integrerer OAuth2 og JWT korrekt
- Vigtigheden af at forstå både eksterne og interne trusler i relation til sikkerhed
