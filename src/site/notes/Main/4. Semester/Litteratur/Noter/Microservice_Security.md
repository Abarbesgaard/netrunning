---
{"dg-publish":true,"permalink":"/main/4-semester/litteratur/noter/microservice-security/","title":"Microservice Security","hide":true,"created":"2024-08-19T12:56:07.027+02:00"}
---

Troværdighed: 5
Relevans: 5

[Video](https://www.linkedin.com/learning/microservices-security/microservice-security-challenges?autoSkip=true&resume=false&u=57075649)

## Microservice Arkitektur

Microservice arkitektur repræsenterer et fundamentalt skift i måden, hvorpå
udviklere bygger, driver og sikrer tekniske systemer. Før introduktionen
af microservices blev mange systemer bygget med en **tre-lags arkitektur**
bestående af:

1. **Præsentationslag**: Kører i browseren.
2. **Logiklag**: Kører på serveren.
3. **Databaselag**: Hvor data opbevares.

### Monolitisk Arkitektur

I en monolitisk arkitektur kombineres alle forretningsfunktioner (som
produktkatalog, lager, prissætning, indkøbskurv og levering i en
e-handel applikation) i et enkelt program. Disse funktioner kommunikerer
direkte med hinanden i samme procesrum.

### Microservice Arkitektur, en Kontrast

I modsætning hertil opdeler en microservice arkitektur forretningsfunktionerne
i uafhængige komponenter, der hver kører i deres egen proces. Kommunikation
mellem disse microservices sker over netværket, typisk via HTTP, og adgang til
hver microservices data og funktionalitet sker gennem et veldefineret REST API.

### Fordele ved Microservice Arkitektur

- **Uafhængig udvikling**: Hver service kan udvikles og vedligeholdes af
separate teams, hvilket reducerer behovet for koordinering mellem teams.
- **Uafhængig deployment**: Ændringer i én service kan frigives uden at
påvirke andre tjenester, hvilket eliminerer behovet for store,
koordinerede deployment-events.
- **Skalerbarhed**: Individuelle tjenester kan skaleres horisontalt efter behov,
hvilket optimerer ressourceforbrug.
- **Resiliens**: Microservices kan implementere fejl-tolerancemønstre som
**circuit breaker**-mønsteret, som omdirigerer trafik fra en svigtende
service til en backup eller simpel service for at opretholde systemets
integritet.

### Sikkerhedsaspekter

Microservice arkitektur kræver forskellige sikkerhedsstrategier for at sikre
**fortrolighed**, **integritet** og **tilgængelighed** sammenlignet med en
monolitisk arkitektur.

## Sikkerhedsfundamentaler

Før vi diskuterer sikkerhed i microservices, skal vi se på nogle
grundlæggende sikkerhedskoncepter, der gælder for enhver systemarkitektur
. Når man sikrer et informationssystem, er der tre primære sikkerhedsmål:

1. **Fortrolighed**: Sikrer, at information forbliver privat ved kun at tillade
autoriserede brugere adgang til den.
2. **Integritet**: Sikrer, at information kan stoles på, fordi den ikke er
blevet ændret eller manipuleret.
3. **Tilgængelighed**: Sikrer, at systemer er tilgængelige og kan levere
information til autoriserede brugere, når de har brug for det.

For at opnå disse mål vælges og anvendes forskellige sikkerhedsstrategier
og -kontroller i systemarkitekturen, afhængigt af behovet.

### Adgangskontrol

Adgangskontrol er en sikkerhedsteknik, der beskytter følsomme ressourcer.
Adgangskontrol består af to nøglekomponenter:

- **Autentifikation**: Verificering af en brugers identitet, f.eks. via kodeord
eller token.
- **Autorisation**: Styring af adgang til ressourcer baseret på brugerens rettigheder.

Moderne autorisationsprotokoller som **OAuth** tillader, at adgangsrettigheder
kan delegeres til tredjeparter, hvilket gør det muligt for dem at tilgå
ressourcer på vegne af en bruger.

### Tillid

Tillid er afgørende, da det afgør, i hvilket omfang noget anses for at være
sandt. Systemer skal ofte vurdere, om de kan stole på informationer såsom
brugeridentiteter, adgangsrettigheder, tokens og forretningsdata. Tillid
baseres på faktorer som datakilde, alder og integritetskontroller.

### Angrebsflade

Et systems angrebsflade består af alle de veje, data kan bruges til at komme
ind i eller ud af en applikation, herunder brugergrænseflader, åbne porte,
API'er og databaser. Ved at reducere og forstærke angrebsfladen kan systemets
sikkerhed forbedres.

Disse sikkerhedsmål og -koncepter gælder for enhver arkitektur, men metoderne
til at opnå dem vil variere betydeligt mellem en monolitisk arkitektur og
en microservice-arkitektur. Mange af de strategier, der bruges til at sikre
en monolit, skal gentænkes for at sikre et distribueret system.

## Sikkerhedsudfordringer ved Microservice Arkitektur

Microservice-arkitekturer medfører unikke sikkerhedsudfordringer, som kræver,
at vi gentænker vores tilgang til applikationssikkerhed. Traditionelle
sikkerhedsstrategier, der fungerer i en monolitisk arkitektur, er ikke direkte
overførbare til microservices.

### Monolitisk vs. Microservice Arkitektur

- **Monolitisk Arkitektur**:
  - Færre eksponerede porte, hvilket reducerer angrebsfladen.
  - Indkommende forespørgsler passerer gennem et sikkerhedsfilter, der
  håndterer autentifikation og autorisation.
  - En samlet sikkerhedskontekst oprettes efter autentifikation og bruges
  til autorisation gennem hele systemet.
  - Hele systemet deler det samme tillidsdomæne.

- **Microservice Arkitektur**:
  - Består af uafhængige komponenter, hvor hver service skal eksponere en
  port, hvilket øger angrebsfladen.
  - Angrebsfladen er dynamisk og ændrer sig ved skalering eller introduktion
  af nye services.
  - **North/South Traffic**: Udfordring med at bestemme, hvor autentifikation og
  autorisation skal udføres. Indbygning af autentifikation i hver service er
  ineffektivt, da det ville kræve genautentifikation ved hver forespørgsel
  til en anden service.
  - **East/West Traffic**: Sikring af kommunikation mellem services kræver
  særlige sikkerhedsforanstaltninger for at opretholde fortrolighed og
  integritet, især når trafikken krydser flere tillidsdomæner.
  - Deling af brugeridentitet på tværs af services, mens integriteten
  opretholdes, kræver specialiserede strategier.

### Fordele ved MA

Trods de unikke udfordringer har microservice-arkitekturer også visse fordele:

- **Tilgængelighed**: Fordi services er uafhængige, kan en Denial of Service (DDoS)
angreb kun påvirke en enkelt, ikke-kritisk service, hvilket kan lade resten af
systemet forblive tilgængeligt.
- **Begrænset skadesomfang**: Hvis en service bliver kompromitteret, kan
virkningen begrænses til en mindre del af systemet, hvilket gør det sværere
for en angriber at bevæge sig lateralt.

### Opsummering

For at sikre en microservice-arkitektur er det vigtigt at forstå disse unikke
aspekter af distribuerede systemer og anvende de rette sikkerhedsstrategier
fra starten.

## Distribuerede Adgangsstyringsmønstre i Microservices

Efterhånden som microservices har modnet, er de teknikker, der bruges til at
sikre dem, også blevet forbedret. Inden for sikkerhedsdomæner som identitets-
og adgangsstyring er der opstået generelle mønstre, som er blevet bredt
adopteret. Ved at anvende disse mønstre kan vi abstrahere fra de detaljerede
implementeringer og forstå, hvordan systemet fungerer på et højt niveau.

### Nøglebegreber

- **Klient**: En generel betegnelse for hardware eller software, der anmoder om
en service. Dette kan være en mobil enhed, en single-page applikation, en
backend, en batchproces eller en applikation fra en tredjepart.
- **Token**: Digitale nøgler, der indeholder sikkerhedsoplysninger og bruges
til at få adgang til ressourcer som microservices. Tokens kan variere fra
simple UUID'er til tokens, der indeholder detaljerede oplysninger om identitet
og tilladelser.

### Identitetsservice og Token Validation

- **Identitetsservice**: En distribueret komponent, der håndterer styringen af
identiteter, rettigheder og adgang. Denne service udsteder tokens til
klientapplikationer efter en autentifikationsproces. Klienterne bruger disse
tokens til at påvise deres adgangstilladelser over for microservices.

#### Enkelt og direkte implementering

I simple implementeringer sender microservices tokenet tilbage til
identitetsservicen for at validere dets ægthed, før de giver adgang til
en ressource. Denne metode kan dog føre til overbelastning af
identitetsservicen, hvilket gør den til et flaskehals i systemet, især når
systemet skaleres.

#### Implementering med Reverse Proxy

En løsning på dette problem er at rute trafikken til microservices gennem en
reverse proxy, der validerer tokenet mod identitetsservicen, før den tillader
trafik til microservices. Efter valideringen betragtes trafikken som værende
i et betroet netværk, hvor yderligere validering ikke er nødvendig.
Denne tilgang har dog sine egne sikkerhedsrisici, da implicit tillid til
netværket kan føre til sikkerhedsbrud.

#### Udvidet Token-information

En mere avanceret implementering indebærer, at identitetsservicen tilføjer
yderligere oplysninger om brugerens identitet og tilladelser i tokenet, når
det oprettes. Klienten kan derefter sende disse oplysninger med tokenet til
API-gatewayen og microservices. Microservices bruger de indlejrede identitets-
og tilladelsesoplysninger til at håndhæve adgangspolitikker uden yderligere
kommunikation med identitetsservicen og uden at stole blindt på netværket.

### Opsummering, Token-baserede Strategier

Disse mønstre, kombineret med token-baserede strategier, er de mest anvendte
metoder til identitets- og adgangsstyring i microservice-arkitekturer.
De gør det muligt at balancere sikkerhed, skalerbarhed og ydeevne i
distribuerede systemer.

## Identity and Access Management (IAM) Platforme i Microservice Arkitektur

I en microservice-arkitektur leverer identitetstjenesten to kritiske funktioner:
autentifikation og token-håndtering. Det er generelt ikke anbefalet at udvikle
sine egne sikkerhedsløsninger, men i stedet anvende løsninger fra eksperter.
Heldigvis findes der mange open-source og kommercielle IAM-platforme, der
tilbyder disse funktioner out-of-the-box.

### Centrale Funktioner i IAM Platforme

Når du integrerer microservices med en IAM-platform, er der fire primære
funktioner, som er relevante:

1. **Autentifikation**:
   - Autentifikation er komplekst og nemt at fejle, hvorfor det bør hentes fra
   en IAM-platform.
   - Ledende platforme integrerer sømløst med forskellige typer af
   identitetslagre, som kan være lokale databaser, virksomhedsapplikationer
   eller sociale netværk.
   - IAM-platforme understøtter også multi-faktor autentifikation (MFA) for
   ekstra sikkerhed, hvor brugeren kombinerer deres legitimationsoplysninger
   med f.eks. en engangskode eller biometriske data.

2. **Identitetsstyring**:
   - Identitetsstyring handler om at forstå, hvem eller hvad der har adgang til
   en ressource, og hvilke tilladelser de har.
   - IAM-platforme understøtter avancerede scenarier, herunder delegering af
   adgang, hvor en bruger giver en anden applikation adgang til deres data.

3. **Implementering af Sikkerhedsstandarder**:
   - Platformene implementerer vigtige sikkerhedsstandarder og protokoller som
   OAuth 2.0, OpenID Connect og JSON Web Tokens (JWT).
   - Disse standarder er essentielle for microservices, men bør ikke bygges fra
   bunden, da det kræver stor ekspertise og kan føre til fejl.

4. **Token-håndtering**:
   - Token-håndtering er centralt for at sikre microservices, og mange
   IAM-platforme tilbyder funktioner til at oprette, verificere og administrere
   tokens.
   - Platformene understøtter forskellige token-formater, refresh tokens,
   token-revokering og token-lagring.
   - Tokens oprettes og håndteres af en autorisationsserver, som defineret i
   OAuth 2.0-specifikationen.

### Hosting Konfigurationer

IAM-platforme understøtter forskellige hosting-konfigurationer, herunder
on-premise, cloud og hybrid løsninger, hvilket kan imødekomme de forskellige
behov i microservice-baserede systemer.

### Vigtigheden af IAM Platforme

IAM-platforme er en central del af sikkerheden i mange systemer, herunder
microservices. De sikrer en effektiv og sikker måde at håndtere identitet,
autentifikation og autorisation på tværs af distribuerede systemer.

Når du vælger en IAM-platform, er det vigtigt at foretage en grundig vurdering
af, hvilken løsning der bedst opfylder dine behov.

## API Gateways i Microservice Arkitektur

En API gateway fungerer som en omvendt proxy og er et centralt komponent i mange
microservice-baserede systemer. API gateways tilbyder en række funktioner, der
styrker sikkerheden og håndteringen af trafik, samtidig med at de fungerer som
en enkelt indgangspunkt til microservices.

### Hovedfunktioner i en API Gateway

1. **Omvendt Proxy**:
   - En API gateway fungerer som en omvendt proxy, hvor al trafik til
   microservices passerer igennem. Dette skaber et enkelt indgangspunkt, der
   skjuler detaljerne om de underliggende servere fra klienterne og
   centraliserer funktionaliteten i gatewayen.

2. **Sikkerhedskontrol**:
   - API gatewayen kan verificere klientens token ved at sende det til en
   Identity and Access Management (IAM) platform for validering. Dette sikrer,
   at tokenen er gyldig og ikke udløbet.
   - Gatewayen kan også håndhæve adgangskontrol ved at beskytte specifikke
   ressourcer eller endpoints.
   - Andre sikkerhedspolicies, såsom "spike arrest" og kvotestyring, kan
   begrænse trafikbelastningen og forhindre, at en klient overforbruger
   ressourcer, hvilket øger systemets tilgængelighed.

3. **Synlighed og Overvågning**:
   - API gateways tilbyder synlighed i trafikken, der går ind i systemet,
   hvilket gør det muligt at overvåge og spore denne trafik via dashboards.
   Dette er især nyttigt ved sikkerhedshændelser.

4. **Ekstra Funktioner**:
   - Ud over sikkerhed kan API gateways også inkludere andre funktioner som
   monetization. De kan leveres med udviklerportaler, hvor interne og
   eksterne udviklere kan registrere deres applikationer for at tilgå de
   APIs, som microservices tilbyder.
   - Disse portaler kan integreres med IAM-platforme for at overholde
   OAuth-standarder vedrørende klientregistrering.

### Integration og Overlap

Der kan være overlap mellem funktionerne i en API gateway og en IAM platform,
især når det kommer til OAuth og reverse proxy-funktioner. For mindre systemer
kan det være muligt at opfylde alle behov med et enkelt produkt, afhængigt
af organisationens krav og politikker.

### Hosting Konfigurationer, On-Premise, Cloud og Hybrid

API gateways fås i forskellige hosting-konfigurationer, herunder on-premise,
cloud og hybrid modeller, så de kan tilpasses forskellige organisationsbehov.

### Konklusion

API gateways er essentielle for at sikre microservices og tilbyde
funktionalitet, der ellers ville være upraktisk at udvikle internt.
De integreres ofte med IAM platforme for at sikre en robust og sikker
arkitektur.

## Adgangsscenarier i Microservice Arkitektur

Når du designer sikkerhed til microservices, er det vigtigt at forstå de mange
forskellige adgangsscenarier, som kan påvirke sikkerhedsstrategien.
Adgangen til en microservice sker altid gennem en klient, og klienterne kan
variere betydeligt i deres evne til at sikre deres egne legitimationsoplysninger.

### Typer af Klienter

1. **Offentlige Klienter (Public Clients)**:
   - Disse klienter kan ikke beskytte deres legitimationsoplysninger, da de
   kører i et miljø, som f.eks. en browser, hvor data kan tilgås af en
   angriber. Eksempler inkluderer single-page applications (SPA).

2. **Fortrolige Klienter (Confidential Clients)**:
   - Disse klienter kan beskytte deres legitimationsoplysninger bedre, fordi de
   kører i et betroet domæne, typisk på serversiden. Her er adgangen til deres
   indre mekanismer begrænset til en lille gruppe autoriserede brugere.

### Ejerskab af Klienter

1. **Førsteparts Klienter**:
   - Klienter ejet af den samme organisation, der har bygget microservices. De
   er under samme sikkerhedskontrol og politikker.

2. **Tredjeparts Klienter**:
   - Klienter, som ejes af eksterne parter eller partnere. Disse klienter er
   sværere at sikre, fordi deres sikkerhedspolitikker ikke er under
   organisationens kontrol. Derfor anvendes ofte strengere
   sikkerhedsforanstaltninger for disse klienter.

### Netværksplacering

1. **Interne Klienter**:
   - Klienter placeret inden for virksomhedens firewall og kan drage fordel af
   den begrænsede adgang.

2. **Eksterne Klienter**:
   - Klienter uden for virksomhedens netværk, som er mere udsat for angreb.
   Uanset placering bør der dog ikke slækkes på sikkerhedskontrollerne på grund
   af muligheden for interne trusler eller sideværts bevægelse af angribere,
   hvis netværksperimeteren brydes.

### Avancerede Adgangsscenarier

1. **Menneskelig Slutbruger med Førsteparts Klient**:
   - En menneskelig bruger benytter en webapplikation eller SPA fra samme
   organisation til at få adgang til microservices. IAM-platforme kan ofte
   håndtere denne situation gnidningsløst.

2. **Menneskelig Slutbruger med Tredjeparts Klient**:
   - En bruger giver samtykke til, at en tredjeparts applikation kan få adgang
   til deres ressourcer på en microservice drevet af en anden organisation.
   Dette scenarie kræver avancerede sikkerhedsforanstaltninger for at håndtere
   delegeret adgang.

3. **Maskin-til-Maskin Kommunikation**:
   - I denne situation er der ingen mennesker involveret, og kommunikationen
   sker mellem systemer, ofte ved hjælp af servicekonti. Dette scenarie er
   relativt nemt at sikre.

### Konklusion,   Adgangsscenarier

## Tokens

Microservice-arkitekturer skal understøtte en bred vifte af adgangsscenarier
for at kunne håndtere kravene fra en sammenkoblet verden. Brug af etablerede
sikkerhedsplatforme og standarder, som OAuth, er afgørende for effektivt at
sikre disse forskellige adgangsscenarier.

I en microservice-arkitektur spiller tokens en central rolle i etableringen af
identitet og håndhævelsen af adgangskontrol. Tokens løser de udfordringer,
som et distribueret system medfører, ved at tilbyde en måde, hvorpå en klient
kan opbevare og videregive information om en slutbruger og den adgang, der er
givet til klienten, uden at skulle håndtere brugerens legitimationsoplysninger direkte.

### Typer af Tokens

Tokens kan opdeles i to hovedtyper: reference tokens og strukturerede tokens.

1. **Reference Tokens**:
   - Disse tokens er opake strenge, der ikke indeholder nogen meningsfuld
   information i sig selv. De fungerer som identifikatorer, som kan bruges
   til at slå metadata om tokenet op i en IAM-platformens lagringssystem.

2. **Strukturerede Tokens**:
   - Disse tokens indeholder metadata om autentificeringsbegivenheden og
   slutbrugeren direkte i tokenets payload. Metadataene er organiseret som
   nøgle-værdi-par kaldet claims, som er grupperet i en claim set. JSON Web
   Token (JWT) er en almindelig standard for strukturerede tokens i microservices.

### JSON Web Token (JWT)

JWT består af tre segmenter:

1. **Header**: Indeholder information om, hvordan tokenet er kryptografisk
beskyttet, herunder hvilke algoritmer der er brugt til at signere eller
kryptere det.
2. **Payload (Claim Set)**: Indeholder information om slutbrugeren eller
autentificeringsbegivenheden i form af nøgle-værdi-par.
3. **Signature**: Denne del er kritisk, da den kryptografisk afledes fra
headeren, payloaden og en hemmelig nøgle. Signaturen sikrer, at tokenet
ikke er blevet ændret siden det blev oprettet, hvilket beskytter dets
integritet.

### Anvendelser af Tokens

Tokens anvendes primært i følgende former:

1. **Access Tokens**: Bruges til at få adgang til microservices. De kan være
enten reference eller strukturerede tokens.
2. **Refresh Tokens**: En form for reference token, der giver mulighed for at
udstede et nyt access token, når det nuværende er udløbet.
3. **ID Tokens**: Strukturerede tokens, der bruger JWT-formatet til at levere
autentificeringsinformation om brugeren, som klienten kan bruge.

### Tokens i Microservices

Tokens spiller den rolle, som sessioner plejede at have i monolitiske systemer.
De er afgørende for at mikroservices kan træffe adgangsbeslutninger og etablere
brugeridentitet. På trods af deres store fordele er tokens dog sværere at
administrere, især i distribuerede miljøer. Tokens har en livscyklus, der starter
med udstedelse og slutter med udløb eller tilbagekaldelse, og de fleste aspekter
af denne livscyklus er defineret af etablerede industristandarder som OAuth og JWT.

## OAuth 2.0 Primer

OAuth 2.0 er en autorisationsstandard, der bruger token-baserede metoder til at
sikre adgang til beskyttede ressourcer, såsom microservices. Det er vigtigt at
forstå de grundlæggende roller og flow i OAuth 2.0:

## Roller i OAuth 2.0

1. **Ressourceejer (Resource Owner)**
   - Slutbrugeren, der ejer data eller ressourcer, og som kan give adgang til disse.

2. **Ressourceserver (Resource Server)**
   - Serveren, der hoster API'en og giver adgang til data, hvis en gyldig
   adgangstoken præsenteres.

3. **Autorisationsserver (Authorization Server)**
   - Serveren, der udsteder adgangstokenet til klienten og verificerer tokenets
   gyldighed.

4. **Klient (Client)**
   - Applikationen, der anmoder om adgang til de beskyttede ressourcer på vegne
   af ressourceejeren.

## OAuth 2.0 Flow

OAuth 2.0 beskriver, hvordan en klient kan opnå og bruge en adgangstoken for at
få sikker adgang til beskyttede ressourcer. Tænk på det som et hotelophold:

- **Ressourceejer** er hotellets ejer.
- **Autorisationsserver** er receptionisten, der udsteder nøglekortet (adgangstoken).
- **Klient** er gæsten, der bruger nøglekortet til at få adgang.
- **Ressourceserver** er låsen på døren, der verificerer nøglekortet.

## OAuth 2.0 Grant Types

OAuth 2.0 specificerer forskellige "grant types" eller flows for at få
adgangstokens. Hvert flow består af en sekvens af HTTPS-anmodninger mellem
klienten, ressourceejeren og autorisationsserveren. De vigtigste grant types
inkluderer:

- **Authorization Code Grant**
- **Implicit Grant**
- **Resource Owner Password Credentials Grant**
- **Client Credentials Grant**

## Token Typer

1. **Adgangstoken (Access Token)**
   - Bruges til at få adgang til beskyttede ressourcer.

2. **Opfriskningstoken (Refresh Token)**
   - Bruges til at få en ny adgangstoken, når den nuværende er udløbet.

3. **ID Token**
   - En JSON Web Token (JWT), der giver autentifikationsinformation om brugeren.

## Standarder og Udvidelser

OAuth 2.0 er fleksibel og kan tilpasses gennem udvidelser som:

- **OpenID Connect**
- **JWT (JSON Web Token)**
- **JWS (JSON Web Signature)**

Disse standarder og udvidelser hjælper med at specificere, hvordan man sikkert
håndterer tokens, autentificering og adgangskontrol.

## Udstedelse af Tokens i OAuth 2.0

Når en klient skal have sikker adgang til en microservice, er det første
skridt at blive udstedt en adgangstoken. Denne proces involverer en række
HTTPS-anmodninger mellem ressourceejeren, klientapplikationen og
autorisationsserveren.

## Processen for Udstedelse af Adgangstokens

1. **Autentifikation og Samtykke**
   - **Ressourceejeren** (endbrugeren) autentificerer sig overfor
   autorisationsserveren med deres legitimationsoplysninger.
   - Ressourceejeren giver samtykke til klienten om at få adgang til deres
   beskyttede ressourcer.

2. **Token Udstedelse**
   - Efter autentifikation og samtykke, opretter autorisationsserveren en
   adgangstoken og udsteder den til klienten.
   - Hvis adgangstokenet er en reference-token, skal det gemmes i et
   repository på autorisationsserveren.

## Fordele ved Tokenbaseret Autentifikation

- **Ingen Lagring af Legitimationsoplysninger:** Microservice og klienten skal
ikke opbevare brugerens legitimationsoplysninger. Alt håndteres centralt af autorisationsserveren.
- **Forbedret Sikkerhed:** Forhindrer stjålne legitimationsoplysninger fra
klienten og sikrer informationskonfidentialitet og -integritet.

## OAuth 2.0 Grant Types i Microservices

OAuth 2.0 definerer fire grant types, men her fokuserer vi på de to mest
almindelige til microservices:

### 1. Authorization Code Grant

- **Registrering:** Klienten og dens redirect URI skal registreres hos
autorisationsserveren. Dette gøres ved at udfylde en registreringsformular i udviklerportalen.
- **Flow:**
  - Ressourceejeren besøger klientens hjemmeside, som omdirigerer dem til
  autorisationsserverens autorisations endpoint.
  - Klienten sender en anmodning om et autorisationskode med parametre som
  client ID, redirect URI, scope og state.
  - Hvis ressourceejeren ikke er autentificeret, skal de logge ind.
  - Efter samtykke fra ressourceejeren, sender autorisationsserveren en
  autorisationskode til klientens redirect URI.
  - Klienten sender en HTTP POST-anmodning med autorisationskoden til
  token endpointet for at få en adgangstoken.

### 2. Client Credentials Grant

- **Flow:**
  - Klienten sender sin client ID og client secret til token endpointet,
  sammen med grant type.
  - Autorisationsserveren returnerer en adgangstoken, som kan bruges til at
  få adgang til microservices.

## Implementering

- **IAM Platforms:** Identity and Access Management (IAM) platforme eksponerer
de nødvendige autorisations- og token-endpoints som en del af deres
autorisationsserverimplementeringer. Nogle IAM-platforme bygger oven på disse
flows for at forenkle brugen for førstpartikunder.

Dette giver et overblik over hvordan tokens bliver udstedt og anvendt i
OAuth 2.0, og hvordan processen understøtter sikker adgang til beskyttede ressourcer.
