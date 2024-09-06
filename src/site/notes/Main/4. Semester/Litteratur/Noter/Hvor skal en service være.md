---
{"dg-publish":true,"permalink":"/main/4-semester/litteratur/noter/hvor-skal-en-service-vaere/","title":"Hvor skal en service være?","created":"2024-09-06T08:19:23.237+02:00"}
---


## Noter om Microservices Architecture, The Hard Parts: Service Granularity

1. **Mikroservices definition**:
   - En [[Main/4. Semester/Emner/Backend/Microservice\|microservice]] er en separat, enkeltstående
   softwareenhed, der har ét formål og kan implementeres uafhængigt.
   - En stor fordel er teamautonomi, hvor teams selv bestemmer, hvornår de vil
   frigive funktioner uden at skulle koordinere med andre teams.

2. **Udfordring med servicegranularitet**:
   - Det er ofte svært at afgøre, hvor stor eller lille en
   [[Main/4. Semester/Emner/Backend/Microservice\|microservice]] skal være.
   - For små services kan resultere i for meget inter-service kommunikation,
   hvilket skaber kobling og præstationsproblemer.
   - For store services kan føre til samme problemer som
   monolitiske arkitekturer.

3. **Eksempel: Notifikationsservice**:
   - Et team skal implementere en notifikationsservice, der sender beskeder via
   e-mail, SMS og in-app.
   - Der er to mulige løsninger:
     1. En samlet, grovkornet notifikationsservice.
     2. Flere små, fintkornede [[Main/4. Semester/Emner/Backend/Microservice\|microservice]]  én for hver type besked.

4. **Beslutningsfaktorer for servicegranularitet**:
   - **Funktionalitet**:
     - [[Main/4. Semester/Emner/Backend/Microservice\|Microservices]] bør have ét enkelt formål og være meget sammenhængende.
     - Diskussioner om forretningskontekst kan hjælpe med at forstå, om en
     samlet eller opdelt tilgang er bedst.
   - **Skalérbarhed**:
     - Nogle funktioner har forskellige krav til skalering, og det kan
     derfor være nødvendigt at opdele en service for at spare ressourcer
     og forbedre brugeroplevelsen.
   - **Fejltolerance**:
     - Hvis én del af en mikroservice fejler, skal resten fortsætte med at
     fungere. En opdelt service øger fejltolerance.
   - **Kodevolatilitet**:
     - Hvis nogle dele af en service ændrer sig hyppigere end andre, kan det
     være en fordel at opdele servicen for at reducere testomfanget og
     øge systemstabiliteten.
   - **Udvidelsesmuligheder**:
     - Hvis der forventes at skulle tilføjes flere funktioner i fremtiden, kan
     det være bedre at opdele servicen fra starten for at gøre fremtidige
     tilføjelser lettere og mere pålidelige.

5. **Konklusion**:
   - Der er ingen enkel løsning på, hvordan man fastsætter granulariteten
   af mikroservices. Beslutninger bør baseres på funktionalitet, skalering,
   fejltolerance, kodevolatilitet og udvidelsesmuligheder.
