---
{"dg-publish":true,"permalink":"/main/noter/litteratur/noter/microservice-security/","title":"Microservice Security","created":"2024-09-06T08:19:23.241+02:00"}
---

Troværdighed: 5
Relevans: 5

Til at lave noterne har jeg brugt metoden [[Main/Noter/Ressourcer/PathGPT/LearnGPT\|LearnGPT]].

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

## Noter om Issuing Identity Tokens med OIDC

### Baggrund: OAuth 2.0 og dets Begrænsninger

- **OAuth 2.0 Fokus**: Autorisation, ikke identifikation eller autentifikation
af brugere.
- **Begrænsning**: Mangler standard for brugeridentifikation og -autentifikation.

### Introduktion til OpenID Connect (OIDC)

- **Formål**: Tilføje et identitetslag til OAuth 2.0 for at adressere
ovennævnte begrænsninger.
- **Komponenter**:
  - **Authentication Request**: Indleder brugerautentifikation.
  - **ID Token**: Indeholder brugeridentitet og autentifikationsdetaljer.
  - **UserInfo Endpoint**: Returnerer brugerinformation baseret på access token.
  
### Arkitektur og Anvendelsesområder

- **Standalone Identity Provider**:
  - Kan anvendes af flere klientapplikationer.
  - Reducerer behovet for, at hver applikation udvikler egne autentifikationssystemer.
- **Eksempler**: LinkedIn, Google, Facebook – Sign in with-knapper.
- **Enterprise Brug**: Central autentifikation for en virksomheds applikationssuite.

### OIDC's Rolle i Autorisationsflowet

- **OIDC Tilføjelser til OAuth**:
  - Tilføjelse af `openid` scope til auth request.
  - Tilføjelse af ID Token ved token-udveksling.
- **Autentifikationsflow**:
  1. **Initial Redirect**: Klient sender bruger til identitetsudbyderen.
  2. **Autentifikation og Samtykke**: Bruger logger ind og giver samtykke.
  3. **Kodeudveksling**: Klient modtager ID Token og Access Token.
- **ID Token**:
  - Format: JWT (Jot) med kryptografisk signatur (HS256).
  - Indeholder claims om autentifikationsevent, tokenudsteder, bruger og udløb.

### Verifikation og Anvendelse af Tokens

- **ID Token Verifikation**: Signatur valideres for at sikre integritet.
- **Brug af Tokens**:
  - **ID Token**: Bruges kun af klienten til brugeridentifikation.
  - **Access Token**: Bruges af mikroservices til at hente brugerinfo via
  UserInfo endpoint.

### OpenID Connect Playground

- **Værktøj**: Auth0's OpenID Connect Playground demonstrerer OIDC i praksis.
- **Funktion**: Simulerer auth flow og viser detaljeret tokenudveksling og verifikation.

## Vigtigste Pointer

- **OIDC Udfylder OAuth 2.0's Mangler**: Tilføjer brugeridentifikation og
autentifikation til en ellers autorisationsfokuseret standard.
- **Modulært og Centraliseret Design**: Tillader flere applikationer at bruge
samme identitetsudbyder, hvilket reducerer udviklingsbyrden.
- **Struktureret Token Administration**: ID Token leverer sikker og verificerbar
brugerinformation, mens Access Tokens muliggør datatilgang i mikroservices.
- **Relevans for Moderne Applikationer**: Anvendt bredt i både offentlige og
private systemer for at forbedre sikkerhed og brugeroplevelse.

## Noter om Token Validation

### Introduktion til Token Validation

- **Tokens**: Følsomme informationer, der giver adgang til mikroservices via en API.
- **Klientens ansvar**: Holder og sender token til resource serveren ved hver anmodning.
- **Resource Serverens ansvar**: Skal validere token for at forhindre adgang med
stjålne eller manipulerede tokens.

### Token Valideringsprocessen

- **Reference Tokens**:
  - Skal introspekteres ved autorisationsserveren for at verificere gyldighed.
  - **OAuth 2.0 Token Introspection Standard**: Beskriver processen.
  - **API Gateway**: Bør centralisere introspektion for effektivitet.
  - **Krav til Autorisationsserveren**: Skal kunne håndtere belastning via
  clustering og caching.

- **Strukturerede Tokens**:
  - Beskyttes via JSON Object Signing and Encryption (JOSE) specifikationer.
  - **JOSE Specifikationer**: Fire standarder, der sikrer token integritet og
  fortrolighed gennem signering og kryptering.
  - **JWT (JSON Web Token)**: Grundstrukturen i JOSE, som specificerer, hvordan
  token er opbygget.

### JWT Signering og Verifikation

- **JSON Web Signature (JWS)**: Beskriver, hvordan en JWT signatur oprettes.
  - **Signeringsproces**:
    - Header og payload Base64 URL-enkodes og sammenkædes.
    - En nøgle bruges til at beregne signaturen, som derefter føjes til JWT.
  - **HS256 Algoritme**: Symmetrisk signeringsalgoritme (samme nøgle til
  signering og verifikation).
  
- **Eksempel på JWT Verifikation**:
  - **Forkert Nøgle**: Meddeler ugyldig signatur.
  - **Korrekt Nøgle**: Bekræfter gyldig signatur.
  
- **RS256 Algoritme**:
  - Kræver offentlig og privat nøglepar for signering og verifikation.
  - **JSON Web Key Set (JWKS)**: Offentlige nøgler tilgængelige via endpoint
  til verifikation af tokens.
  
### Praktisk Anvendelse af JWT Verifikation

- **JWT.io Værktøj**: Muliggør encoding, decoding, og verifikation af JWT’er.
- **Auth0 Eksempel**: Viser hvordan en JWKS kan bruges til at verificere en
token's signatur.

## Konklusion, token validering

### Vigtigste Pointer, token validering

- **Tokens kræver nøje validering**: Forhindrer uautoriseret adgang og sikrer integritet.
- **Reference Tokens vs. Strukturerede Tokens**: Validering afhænger af
token-type; introspektion for reference tokens, signering for strukturerede tokens.
- **JOSE Specifikationer**: Kritiske for sikker tokenadministration, især ved
brug af JWT'er.
- **Værktøjer og Algoritmer**: JWT.io og standardalgoritmer som HS256 og RS256
er centrale for token signering og validering.
- **Offentlige Nøglesæt**: Gør det muligt for klienter at verificere
signaturer uden direkte adgang til privat nøgle.

## Noter om Tokenvedligeholdelse og Beskyttelse

### Tokenvedligeholdelse

- **Token Livscyklus**:
  - Tokens bruges typisk indtil deres udløbsdato.
  - Ved udløb kan de ikke længere bruges til adgang til mikroservices.
  
- **Udløbsdato**:
  - **Expires In Claim**: Sættes på access token for at angive udløbsdato.
  - **Kortvarige Tokens**: Generelt anbefales det at holde access tokens
  kortvarige for at begrænse skader ved kompromittering.

- **Refresh Tokens**:
  - Giver mulighed for at få en ny access token uden brugerens deltagelse.
  - Nyttigt når brugeren er offline.
  - **Rotation**: For at mindske risikoen ved stjålne refresh tokens, kan nye
  refresh tokens udstedes hver gang en ny access token opnås.

### Token Revokation

- **Problemer med Token Revokation**:
  - Hvis tokens ikke er godt beskyttede og kompromitteres, skal de revokeres.
  - **Opbevaring**: Tokens skal være persistent for at kunne revokeres effektivt.
  - **Revokation**: Kan ske naturligt ved logout eller når en klient bliver afregistreret.

- **Token Revokationsspecifikation**:
  - Udvider OAuth med et endpoint til token revokation.
  - Efter revokation kan token ikke længere anvendes.

### Generelle Best Practices

- **Transport**:
  - Alle OAuth-relaterede kald skal ske over TLS for at beskytte credentials og
  tokens mod kompromittering.
  - **Ingen Klartekst**: Transport af information bør ikke ske i klartekst.

- **Beskyttelse**:
  - Tokens bør beskyttes som passwords.
  - **Client ID og Client Secret**: Skal også beskyttes.

- **Udløbsdatoer**:
  - Sørg for at inkludere en udløbsdato på alle access tokens.
  - Hold udløbsdatoen kort for at begrænse adgangstiden.

- **Sensible Information**:
  - Undgå at inkludere meget følsom information i token payload, der er
  udenfor din kontrol.
  - Brug sikre mønstre for at få adgang til følsomme oplysninger fra mikroservices.

## Konklusion, token vedligeholdelse og beskyttelse

### Vigtigste Pointer, token vedligeholdelse og beskyttelse

- **Token Livscyklus**: Kortvarige tokens og refresh tokens med rotation er
anbefalede for at sikre kontrol.
- **Revokation**: Tokens skal opbevares og kunne revokeres effektivt ved kompromittering.
- **Sikker Transport**: Brug TLS for alle token-relaterede kommunikationer for
at forhindre kompromittering.
- **Token Beskyttelse**: Behandle tokens som passwords og beskyt dem nøje.
- **Expiration Management**: Inkluder udløbsdatoer og begræns adgangsperioden.
- **Sensitiv Information**: Undgå at inkludere følsomme data i tokens; brug
sikre mønstre til at håndtere denne information.

## Noter om mTLS (Mutual TLS) for Microservices

### Zero Trust Prinsippet

- **Mikroservices** bør ikke stole på eksterne parter som standard.
- **Defense in Depth**: Mikroservices bør være deres egne tillidsgrænser.
- **Zero Trust**: Mikroservices skal verificere identiteten af enhver kaldende
part og informationens integritet.

### Digital Certifikater

- **Digital Certifikat**: Indeholder information om en enhed, en offentlig
nøgle og information om den udstedende certifikatmyndighed (CA).
- **TLS (Transport Layer Security)**: Bruges til at etablere en krypteret
kommunikationskanal ved hjælp af et certifikat og en krypteringsnøgle.
- **One-Way Authentication**: Kun klienten verificerer serverens identitet via
dens certifikat.

### Mutual TLS (mTLS)

- **mTLS**: Både klient og server autentificerer hinanden ved at udveksle
digitale certifikater udstedt af en fælles betroet certifikatmyndighed.
- **Fordele ved mTLS**:
  - Tillader tjenester at identificere og bekræfte hinandens identitet, inden
  de kommunikerer.
  - Forstærker sikkerheden mellem API gateway og mikroservice-deployments.
  - Forhindrer angribere i at kalde mikroservices uden et betroet digitalt certifikat.

### Udfordringer ved mTLS

- **Certifikatstyring**:
  - Provisionering af certifikater skal automatiseres, især i dynamiske
  miljøer med containeriserede mikroservices.
  - **Certifikatrotation**: Skal også automatiseres på grund af den høje
  forekomst af mikroservice-instanser.
- **Løsninger**:
  - Container orkestratorer og service mesh-løsninger kan håndtere
  mTLS-konfiguration og styring automatisk.

### Anbefalinger, mTLS

- Implementering af mTLS tilføjer et ekstra sikkerhedslag, som er både
effektivt og nødvendigt.
- Hvis du vælger at stole på netværket uden mTLS, risikerer du at
kompromittere mikroservices-sikkerheden.

## Konklusion, mTLS

### Vigtigste Pointer, mTLS

- **Zero Trust**: Implementer mikroservices som deres egne tillidsgrænser for
at styrke sikkerheden.
- **mTLS**: Giver tovejsautentificering mellem mikroservices, hvilket skaber en
mere sikker kommunikationskanal.
- **Automatisering**: Automatiser certifikatstyring og rotation for at håndtere
mTLS i dynamiske miljøer.
- **Sikkerhedspraksis**: Vælg mTLS frem for at stole på netværket alene for
at forhindre sikkerhedsbrud.

## Noter om Sikring af Øst-Vest Trafik i Microservices

### Mikroservices og Øst-Vest Trafik

- **Enkelt Ansvars-Princippet**: Microservices er designet til at udføre en
specifik opgave godt.
- **Øst-Vest Trafik**: Trafik mellem microservices inden for en klynge, hvilket
skaber nye sikkerhedskrav.
- **Identificering og Adgangsstyring**: Vigtigt for at beskytte brugeridentitet
og sikre korrekt adgangskontrol inden for klyngen.

### Anti-Pattern: Delte Adgangstokener

- **Delte Tokener**: Brug af et enkelt adgangstoken med fælles scope til flere tjenester.
- **Problemer**:
  - Skaber **distribueret monolit**, hvor scopes skal være ens på tværs af tjenester.
  - **Brud på mindste privilegium**: Token kan bruges direkte af klienten eller
  ressourceejeren til at tilgå følsomme tjenester.

### Forbedret Strategi: Client Credentials Grant

- **Nyt Token**: Ordretjenesten anmoder om et nyt adgangstoken med kun det
nødvendige scope til betalingstjenesten.
- **Fordele**:
  - Decouplerer scopes mellem ordretjenesten og betalingstjenesten.
  - Forhindrer klienten i at få forhøjet adgang.

### Udfordringer med Identitetsoplysning

- **Manglende Brugeridentitet**: Betalingstjenesten har ingen information om
brugerens identitet uden det oprindelige token.
- **Risiko**: Hvis ordretjenesten kompromitteres, kan angriberen foretage
betalinger uden tilladelse.

### Løsning: JWT med Brugerclaims

- **JWT Claims**: Inkluderer brugerclaims i en ny adgangstoken, der sendes fra
ordretjenesten til betalingstjenesten.
- **Verifikation**: Betalingstjenesten kan verificere tokenens integritet og
identificere brugeren, før betalingen autoriseres.

### Sikkerhedsmønster: Reference Token og Structured Token

- **Reference Token**: Klienten får udstedt en reference token, der bruges til
at tilgå microservices.
- **Token Udveksling**: Ved API-gatewayen udveksles reference token med en JWT,
der indeholder brugerclaims.
- **Fordele**:
  - Beskytter brugerens information ved ikke at sende strukturerede tokens til klienten.
  - JWT bruges kun internt mellem microservices for at opretholde en sikker brugeridentitet.

### Anbefalinger for Sikker Øst-Vest Trafik

- Undgå sammenflettede scopes eller claims, der kan føre til tæt kobling mellem microservices.
- Brug strukturerede tokens og sikre kommunikation for at opretholde
brugerkontekst uden at lagre tilstand mellem tjenester.

## Konklusion, sikring af øst-vest trafik

### Vigtigste Pointer, sikring af øst-vest trafik

- **Undgå delte adgangstokener** for at forhindre sikkerhedsbrud og opretholde
mindste privilegium.
- **Brug JWT med brugerclaims** for at sikre korrekt identifikation og
adgangsstyring mellem microservices.
- **Implementer reference tokens og strukturerede tokens** for at beskytte
brugerens oplysninger og styrke sikkerheden.
- **Sørg for at decouplere services** for at undgå en distribueret monolit og
bevare fleksibilitet og sikkerhed.

## Monitoring and Logging i Microservices Arkitekturer

### Vigtigheden af Overvågning og Logning

- Overvågning af systemaktiviteter er afgørende, især fra et sikkerhedsperspektiv.
- Logs giver synlighed og kan advare om mistænkelig adfærd, hvilket hjælper
med at opdage igangværende angreb.
- Ved gode logningsmetoder kan man identificere angrebsvektorer, omfanget af
angrebet og potentielt angriberen.
- Logs kan bruges til at etablere revisionsspor for følsomme operationer, der
kan udnyttes af insider-trusler.

### Udfordringer ved Microservices

- Microservices introducerer unikke udfordringer, da følsomme operationer nu
foregår over flere distribuerede komponenter.
- Logning bliver fragmenteret på tværs af flere tjenester, hvilket kan føre
til uoverensstemmelser mellem forskellige teams’ logningsstrategier.

### Tracing i Microservices

- Tracing er vigtigt for at overvinde logningsudfordringer i microservices-arkitekturer.
- En korrelations-ID tilknyttet hver anmodning kan bruges til at spore en
begivenhed, der distribueres over flere microservices.
- Når hver microservice inkluderer korrelations-ID'et i deres logs, kan
begivenheden rekonstrueres senere for at understøtte sikkerhedsanalyser eller fejlfinding.

### Anbefalede Logningsstrategier

- Et fælles logningsformat bør etableres på tværs af teams, der bygger microservices.
- Logs bør inkludere oplysninger om: tidspunkt for begivenheden, involverede
personer, begivenhedstype, og hvilken kode der blev aktiveret.
- Brug af en standard logningsramme og konfigurationsfil anbefales, især hvis
der bruges det samme sprog på tværs af microservices.

### Logning af Mislykkede Aktiviteter

- Teams bør også logge mislykkede forsøg såsom autorisationsfejl, fejl i
HTTP-koder, og ugyldige endpoints.
- Disse fejl kan indikere forsøg på angreb eller scanningsaktiviteter.

### Centralisering af Logs

- Alle logs bør sendes til en central vært, hvor de kan indsamles og aggregeres.
- Centralisering gør det muligt at få et samlet overblik over aktiviteter i
det distribuerede system.
- Der findes både open-source og kommercielle værktøjer til dette formål, fx
Elastic Stack.

### Automatiseret Overvågning

- Efter central logning kan automatiseret overvågning identificere og advare
udviklere om mistænkelig adfærd.
- Advarsler kan fokusere på trafik, der fejler pga. mutual TLS, ugyldige
adgangstokens, eller overdreven trafik, som kan indikere en angribers forsøg
på at sonde systemet.

### Værdi af Logs i Sikkerhed

- Logs er uvurderlige ikke kun for fejlfinding men også for sikkerhed.
- Monolitiske logningsstrategier fungerer ikke godt i microservices-arkitekturer.
- Implementering af de rigtige strategier giver et holistisk billede af
systemets sikkerhedsposition.

## Konklusion, overvågning og logning

### Vigtigste Pointer, overvågning og logning

- **Overvågning og logning** i microservices er kritiske for sikkerheden og
kræver specielle tilgange.
- **Tracing og korrelations-ID'er** hjælper med at samle begivenheder på
tværs af microservices.
- **Standardiserede logningsstrategier** og centralisering af logs er
essentielle for effektiv overvågning.
- **Automatiserede overvågningssystemer** kan hurtigt identificere og
rapportere mistænkelig adfærd.
- **Holistisk logningsstrategi** er nødvendig for at få en fuld forståelse af
systemets sikkerhed og performance.

## Service Mesh i Microservices Arkitekturer

### Introduktion til Service Mesh

- En service mesh hjælper med at håndtere kompleksiteten af
service-til-service kommunikation i et microservices-baseret system.
- Microservices skal køre i containere (Docker er standard) og være udrullet i
et container orkestrationssystem som Kubernetes.
- Service mesh etablerer et netværk af sidecar proxies ved siden af
containerne, som håndterer trafikken mellem microservices.

### Funktionalitet og Fordele ved Service Mesh

- **Sidecar proxies**: Disse interceptorer håndterer trafik og anvender
sikkerhedsforanstaltninger som mutual TLS, adgangspolitikker,
og audit logs.
- Efterhånden som flere instanser af en microservice udrulles, udrulles
tilsvarende proxies, hvilket skaber et sammenhængende mesh-netværk.
- **Transparens**: Service mesh er gennemsigtigt for microservices, da proxies
kører i samme pod som microservices, hvilket muliggør centraliseret styring.

### Istio som Eksempel

- **Arkitektur**: Istio består af en data plane og en control plane.
  - **Data plane**: Indeholder de proxies, som microservices bruger til at kommunikere.
  - **Control plane**: Håndterer og distribuerer politikker og konfigurationer
  til proxies via en komponent kaldet Pilot.
- **Sikkerhedspolitikker**: Politikker kan definere autorisationsroller, fra
generelle kommunikationsregler til specifikke krav som JOT-tokens.
- **Tracing og Logging**: Istio understøtter tracing og logging, der forbedrer
overvågningsmulighederne for microservices, f.eks. gennem request ID og trace
ID headers.
- **Mutual TLS**: Istio leverer mutual TLS nemt med minimal konfiguration via
Citadel, som også kan håndtere certifikater og nøglerotation i Kubernetes pods.

### Fordele ved Service Mesh

- Øger sikkerheden og gør administration af service-til-service kommunikation
mere håndterbar.
- Tilbyder funktioner som mutual TLS, tracing, og logning, hvilket forbedrer
observabiliteten og sikkerheden i microservices-arkitekturer.
- Forventet at spille en større rolle i fremtiden, da teknologien er
forholdsvis ny og stadig udvikles.

## Konklusion, service mesh

## Vigtigste Pointer, service mesh

- **Service mesh** er en kraftfuld løsning til at håndtere kompleksiteten i
microservices-kommunikation.
- **Istio** er et eksempel på en service mesh, der tilbyder avanceret
sikkerhed, tracing, og automatiserede funktioner som mutual TLS.
- **Sidecar proxies** gør det muligt at anvende sikkerhedspolitikker og loggin
g uden ændringer i selve microservices.
- **Fremtidspotentiale**: Service meshes forventes at blive endnu mere
integrerede i microservices-arkitekturer som teknologien udvikler sig.

## Throttling og Rate Limiting i Microservices Arkitekturer

### Vigtigheden af Throttling og Rate Limiting

- Når en API får øget anvendelse, er det vigtigt at opretholde ydelsen og
stabiliteten for klienterne.
- API'er bygger ofte på en række microservices, der skal forblive stabile,
selv når trafikken stiger.
- Skalering er den første strategi, når efterspørgslen overstiger
kapaciteten, men har sine begrænsninger (fx omkostninger og
ressourcer).

### Udfordringer med Skalering

- **Auto-skalering**: Effektivt men begrænset af omkostninger og tilgængelige ressourcer.
- I tilfælde som denial of service-angreb er skalering ikke ønskværdigt.

### Throttling som Strategi

- Throttling er en metode til at begrænse API-forbrug for at forhindre overbelastning.
- Tanken er, at det er bedre at nægte noget trafik for at bevare
systemstabiliteten end at lade systemet kollapse.

### Grundlæggende Throttling Strategier

- **Universel cap**: En simpel metode, der anvender et generelt loft på
samtidige anmodninger.
  - Ulemper: Kan tillade en enkelt klient at udnytte kapaciteten urimeligt.
- **Kvote og rate limit**: Bedre strategi, hvor hver klient har en individuel
kvote og rate limit.
  - **Kvote**: Antal tilladte kald over en længere periode (fx dag eller måned).
  - **Rate limit**: Forhindrer burst af samtidige kald på kort tid.

### Differentiering af Throttling Strategier

- Nogle klienter kan have højere rate limits og kvoter end andre
(fx first-party klienter vs. third-party).
- Admin-værktøjer kan undtages fra throttling for at sikre, at problemer kan
løses hurtigt.
- Monetiserede API'er tilbyder forskellige tiers, hvor forbrugere kan købe
større kvoter eller højere rate limits.

### Granulær Throttling

- Kvoter kan håndhæves på mere granulære niveauer, såsom per slutbruger,
for at sikre retfærdig fordeling af ressourcer.
  - JOT-claims kan bruges til at identificere slutbruger og klient.
- **Operation-specifik throttling**: Forskellige operationer på en API kan have
forskellige throttling-limits afhængigt af deres ressourceforbrug.

### Sikkerhed og Tilgængelighed

- Tilgængelighed er en ofte overset del af sikkerhed, især når det er
legitime brugere, der bringer en tjeneste ned.
- Flere teknikker er tilgængelige til throttling for at holde microservices tilgængelige.

## Konklusion, throttling og rate limiting

### Vigtigste Pointer, throttling og rate limiting

- **Throttling og rate limiting** er essentielle for at opretholde stabiliteten
og tilgængeligheden af microservices under høj belastning.
- **Universel cap** kan være ineffektiv, mens **individuelle kvoter og rate
limits** giver bedre kontrol og retfærdighed.
- **Granulær throttling** tillader ressourceallokering på slutbrugerniveau og
pr. operation, hvilket sikrer optimal udnyttelse af systemressourcer.
- **Tilgængelighed** er kritisk, og passende throttling-strategier kan
forhindre systemnedbrud, selv under ekstreme forhold.

## Sikkerhed i Container Runtime i Microservices Arkitekturer

### Vigtigheden af Containersikkerhed

- Microservice-arkitekturer kræver et fleksibelt miljø for hurtige og stabile
udrulninger, hvilket gør containere (især Docker) til et populært valg.
- Containere introducerer nye angrebsflader og vektorer, som kræver
specifikke sikkerhedsforanstaltninger.

### Sikring af Host og Container Runtime

- **Host Sikkerhed**:
  - Begræns direkte adgang til hosten, især ved brug af container
  orchestrators som Kubernetes.
  - Brug en minimal og container-specifik OS-distribution, fx Fedora CoreOS, for
  at reducere angrebsfladen.
  - Hardening af hosten bør følge de samme strategier som andre virtuelle maskiner.

- **Runtime Sikkerhedskonfigurationer**:
  - Konfigurer containere til at køre med mindst mulige rettigheder.
  - Start med at droppe alle kernekapaciteter og tilføj kun de nødvendige.
  - Brug `no-new-privileges` flaget for at forhindre, at processer i containeren
  får nye rettigheder.
  - Undgå at bruge `privileged` flaget, da det giver omfattende adgang, der kan
  misbruges til angreb på hosten.
  - Angiv altid en specifik bruger, når containeren kører; hvis ikke, kører
  containeren som root, hvilket giver fuld adgang til hosten ved en container-flugt.
  - Brug et skrivebeskyttet filsystem og volumener for at minimere skaderne ved
  en eventuel kompromittering.

### Sikkerhedsværktøjer og Automatisering

- **Docker Bench**:
  - Et værktøj, der hjælper med at sikre korrekt konfiguration af containere
  ved at scanne for afvigelser fra industristandarder.
- **Automatisering og Standardisering**:
  - Sikring af containersikkerhed skal standardiseres og automatiseres for at
  reducere risici og forbedre sikkerheden i hele organisationen.

## Konklusion, containers

## Vigtigste Pointer, containers

- Containersikkerhed er kritisk i microservice-arkitekturer for at beskytte mod
nye angrebsvektorer.
- Hostens angrebsflade bør minimeres ved at bruge en minimal OS-distribution og

## Sikkerhed i Containere: Fokus på Billedsikkerhed

### Vigtigheden af Billedsikkerhed

- Sikkerhed i containerbaserede microservices omfatter ikke kun
runtime-konfigurationer, men også hvordan billeder bygges og hentes.
- Et containerbillede oprettes fra en Dockerfile, som indeholder instruktioner
til at tilføje og konfigurere microservicen.
- Dockerfiles kan sammenlignes med kildekode for et miljø, og containerbilleder
ligner kompilerede objekter.

### Sikring af Base Images

- **Brug af officielle base images**:
  - Det er afgørende, at base images stammer fra officielle, pålidelige
  kilder, som Microsoft, Red Hat eller officielle Linux-distributioner.
  - Brug af uofficielle eller upålidelige base images kan føre til
  forsyningskædeangreb, hvor ondsindet kode bliver indført i miljøet.

### Styring af Image Registries

- Mange organisationer opretholder deres egne billedregistre for at kontrollere,
hvilke images der kan trækkes og bruges i deres miljø.
- Kun godkendte og sikkerhedsscannede billeder tillades i disse registries, og
udviklere kan kun tilføje billeder via godkendte CI/CD pipelines.

### Hold Billeder Opdateret

- **Sårbarheder og CVEs**:
  - Et billede, der tidligere var sikkert, kan senere blive sårbart, når nye
  CVEs (Common Vulnerabilities and Exposures) opdages.
  - Udbydere af officielle billeder opdaterer dem rutinemæssigt for at lukke
  kritiske sårbarheder, hvilket kræver, at brugerne følger med og sørger for
  at bruge den nyeste version.
  
## Scanning og Automatisering

- **Automatiserede sikkerhedsscanninger**:
  - Regelmæssig scanning af billedregistrene med værktøjer som Snyk kan
  identificere potentielle sårbarheder og sikre, at de nyeste sikre billeder
  bruges.
  - Opdatering af containerne kræver ofte genopbygning af billeder med den
  nyeste base image-version og genudrulning.

## Konklusion, billedsikkerhed

- Billedsikkerhed er en kritisk del af en sikker containerstrategi. Officielle
og opdaterede base images samt automatiserede sikkerhedsscanninger er
essentielle for at minimere risikoen for sårbarheder i containerbaserede
microservices.

## Sikker Håndtering af Secrets i Microservices

### Problemer med Traditionel Secret Håndtering

- Microservices kræver opbevaring af følsomme oplysninger såsom
klientlegitimation, databaseadgangskoder og SSL-certifikater.
- Uhensigtsmæssige teknikker som at gemme secrets i egenskabsfiler, hårdkodede
strenge, Docker-filer, containerbilleder eller miljøvariabler kan føre til kompromittering.
- Med adgang til kildekontrol, billedregistre eller værtsmaskiner kan disse
secrets nemt udsættes.

### Løsninger Med Container Orchestrators

- **Indbyggede Secret Management Funktioner**:
  - Kubernetes, OpenShift og andre container orchestrators tilbyder sikre
  metoder til at håndtere secrets.
  - Secrets kan injiceres i en container som miljøvariabler eller monteres i en
  fil via et volumen. Montering af en fil via et volumen er den mest sikre metode.
  - Disse metoder sikrer, at secrets ikke indbages i containerbilleder, hvilket
  forbedrer sikkerheden betydeligt.

### Begrænsninger ved Container Orchestrators

- Orchestrators som Kubernetes kan effektivt håndtere secrets inden for en
microservice-klynge, men kan ikke dele secrets på tværs af forskellige klynger
eller udenfor.
- Dette begrænser deres anvendelighed i organisationer, der har behov for at
administrere secrets på tværs af flere systemer eller miljøer.

### Eksterne Secrets Management Løsninger

- **Vault fra HashiCorp**:
  - Vault er en populær platform til secrets management, som tilbyder
  forskellige strategier til sikker opbevaring og adgang til secrets,
  herunder API-nøgler, adgangskoder og certifikater.
  - Vault tilbyder en API til at hente secrets, og en Vault Agent, der
  integreres tæt med container orchestrators via en Sidecar-model.
  - Vault Agenten automatiserer håndtering af secrets og eliminerer behovet for
  at skrive kode, der manuelt henter secrets via HTTP-kald.

### Dynamiske Secrets

- **Dynamiske Credentials**:
  - Vault kan generere dynamiske credentials, som roteres automatisk, hvilket
  forbedrer sikkerheden, da stjålne credentials hurtigt bliver ubrugelige.
  - **Leases**: Vault kan udstede kortvarige credentials hver gang en klient
  anmoder om adgang til en beskyttet ressource, hvilket yderligere øger sikkerheden.

## Anbefalinger

- Overvej at bruge en tredjepartsløsning som Vault for effektiv secrets
management i dynamiske miljøer som microservices.
- Hvis en ekstern løsning ikke er mulig, brug i det mindste de indbyggede
muligheder, som container orchestrators tilbyder, for at sikre, at secrets
håndteres på en sikker måde.

## Konklusion, secrets management

- Effektiv secrets management er afgørende for at beskytte microservices mod
sikkerhedsbrud. Container orchestrators tilbyder grundlæggende, men sikre
metoder, mens tredjepartsløsninger som Vault giver avancerede funktioner til
håndtering af secrets i dynamiske og distribuerede miljøer.

## Secure Pipelines

### DevOps Pipelines

- DevOps pipelines muliggør hurtig levering ved hjælp af microservices.
- Pipeline fungerer som en funktion:
  - Input: Kodecommits fra udviklere.
  - Output: Container med software, der matcher commit'en.
- CI (Continuous Integration) del:
  - Bygger og tester softwaren.
- CD (Continuous Deployment) del:
  - Pakker containeren og distribuerer den til container runtime via orchestrator.

### Automatiserede Sikkerhedskontroller

- Mulighed for at integrere automatiserede sikkerhedskontroller.
- Sikkerhedskontroller fungerer som porte, der forhindrer sårbar kode i at
blive distribueret.
- Det er bedst at opdage og rette sikkerhedsvulnerabiliteter tidligt i processen.

### Statisk Kodeanalyse

- Kodeanalyseværktøjer på udviklerarbejdsstationer som første forsvarslinje.
- Advarer udviklere om sikkerhedsproblemer før kode kommer til repository.
- Kodeanalyse bør også køres på CI-build og fejle byggeriet ved sikkerhedsbrud.

### Kildekode Repository

- Adgang bør begrænses til reelle bidragsydere.
- Pull request model for at begrænse, hvem der kan committe kode til release branches.
- Værktøjer som Sneak kan inkorporere sikkerhedsscanninger direkte i pull requests.

### Tredjeparts Biblioteker

- Tredjeparts biblioteker bør komme fra en betroet artifact repository.
- Artefakter skal gennemgå en række enhedstests og integrationstests.

### Interaktive Sikkerhedstests

- Test under eksekvering af koden for at finde sikkerhedsproblemer.
- Yderligere feedback om tekniske sårbarheder.

### Registreringsscanner

- Bruges i artifact repository for at opdage nye sårbarheder i containeren.
- Adgang til artifact repository bør være strengt kontrolleret.

### Deployment og Kontrol

- CI pipeline afsluttes, og CD pipeline udløser deployment til lavere miljøer.
- Strenge kontrolmekanismer for version af artefaktet.
- Artefakter skal være gennemgået gennem tidligere sikkerhedskontroller før produktionsrelease.

## Konklusion, secure pipelines

- DevOps pipelines muliggør hurtigere udvikling, men kræver integrerede
sikkerhedskontroller for at forhindre sårbarheder.
- Automatiserede værktøjer til statisk og interaktiv sikkerhedsanalyse er afgørende.
- Adgang til repositories og artefakt-lagre skal være strengt kontrolleret.
- Kontrolmekanismer skal sikre, at artefakter er testet og godkendt før
deployment til produktion.
