---
{"dg-publish":true,"permalink":"/main/4-semester/litteratur/noter/microservice-fundamentals/","title":"Microservice Fundamentals","hide":true,"created":"2024-08-16T13:21:57.196+02:00"}
---

Troværdighed: 4
Relevans: 5

## Historien om service-baserede arkitekturer

Historien om service-baserede arkitekturer begynder med de traditionelle
monolitiske applikationer, som typisk var bygget i tre-lags arkitekturer.

Disse monolitter var stærkt koblede, hvilket gjorde ændringer svære og
langsomme at implementere. Efterhånden som problemerne med monolitter blev
tydeligere, skiftede fokus til service-orienteret arkitektur (SOA), hvor
applikationer blev opdelt i mindre moduler. SOA introducerede dog nye
udfordringer, især på grund af brugen af SOAP, som ikke passede godt med
HTTP, og kompleksiteten i aggregeringslaget, hvor logik ofte blev tilføjet.

Over tid blev microservices populære, fordi de tilbyder en mere agil og
skalerbar løsning, især i en cloud-baseret verden. Men microservices har
også deres egne udfordringer. Deres popularitet skyldes, at de passer
godt til moderne web- og webservice-udvikling, især når HTTP og REST er
i centrum. Samlet set handler det om at lære af tidligere arkitekturmodeller
for at skabe bedre løsninger i fremtiden.

## Monolitten

Monolitiske applikationer bliver ofte kritiseret i diskussioner om
microservices, men det er ikke altid helt retfærdigt. Monolitter kan
typisk opdeles i to typer:

**Store enkeltfil-deployments**: I Java-verdenen blev applikationer ofte
pakket som én stor fil, der indeholdt alt fra dataadgang til
webapplikationer og forretningslogik. Dette førte til, at både relaterede
og ikke-relaterede komponenter blev deployet samlet, hvilket gjorde
systemerne tunge og svære at vedligeholde.

**Kodegenbrug**: Udviklere har ofte genbrugt eksisterende komponenter, selvom
de ikke var designet til det aktuelle formål. Dette skaber stramt koblede
systemer, hvor en ændring i én komponent kan påvirke andre uforudsigeligt,
hvilket gør koden skrøbelig og svær at arbejde med.

Disse problemer påvirker også leveringen af software. Fordi alt er så tæt
koblet, kræver selv små ændringer omfattende testning og lange
deployment-processer, hvilket forsinker udgivelser og reducerer agilitet.
Skalerbarhed er også et problem, da hele applikationen skal skaleres,
selvom kun en enkelt funktion har brug for det.

Disse udfordringer har gjort monolitter **mindre populære** blandt udviklere,
især i forhold til mere fleksible og skalerbare løsninger som microservices.

## Service-orienteret arkitektur (SOA)

Forfatteren har arbejdet meget med SOAP-tjenester, SOA-platforme og
servicebusser, hvilket præger vedkommendes holdning til disse teknologier.
SOAP som kommunikationsmekanisme er ikke grundlæggende dårlig, og
forfatteren har opnået mange resultater med det. Selvom mange kritiserer
XML for at være for omfattende, mener forfatteren, at dens "verbositet"
har værdi, især i forhold til validering. Det stærkeste aspekt ved SOAP
er dog WSDL (Web Services Description Language), som giver en robust
kontrakt og fungerer som en dokumentationslag—aftaler, som ofte bliver
undervurderet.

### Fordele ved SOAP

Stærk kontrakt: WSDL er et af SOAP's største aktiver, da det giver klare,
validerbare kontrakter og fungerer som dokumentation.
XML-validering: Selvom XML kan virke tungt, tilføjer det en værdifuld
valideringsfunktion.

### Ulemper ved SOAP

Begrænset fejlhåndtering: SOAP tilbyder kun to responser—enten "OK" (200)
eller "Fault" (500). Denne manglende nuancering er problematisk i komplekse
systemer, hvor mere detaljeret fejlhåndtering er nødvendig.
Overflødig indpakning: SOAP-omslaget er ofte spild af plads og kunne
håndteres mere effektivt.

### Problemer med SOA

SOA lovede meget ved at tilbyde veldefinerede kontrakter og en fælles
protokol til systemkommunikation. Mange problemer med monolitter blev løst
ved at opdele systemerne i tjenester, som kunne udvikles og implementeres
separat. Udfordringerne opstod dog især med Business Process Orchestration
(BPO). Når forretningsbrugere begyndte at sammenkoble tjenester, blev det
lige så komplekst og uhåndterbart som traditionel kode. Dette skabte:

**Øget kobling**: Systemerne blev tæt forbundne, hvilket gjorde dem
skrøbelige og svære at vedligeholde.
**Kompleksitet**: Koblinger blev en del af kodebasen, men skjult for
udviklerne, hvilket førte til spaghetti-kode.
**Manglende agilitet**: SOA’s kompleksitet og deployment-udfordringer
begrænsede den fleksibilitet, der oprindeligt var målet.

### Konklusion

Selvom SOA havde et enormt potentiale, førte kompleksiteten og de skjulte
koblinger til, at det faldt i unåde. Til sidst blev det nemmere at
håndtere monolitter end de fragmenterede og dyre SOA-implementeringer.

## Microservices: The new kid on the block

Microservices-arkitekturer er relativt nye, men de bygger på mange af
de samme koncepter som SOA og andre service-baserede arkitekturer.
Som med alle softwareudviklingsmønstre er der ingen universalløsning,
og dette er en central pointe i diskussionen om microservices.

### Hvad er microservices?

Microservices handler om at nedbryde systemet i mindre, mere diskrete
enheder. Ligesom god kodepraksis fokuserer på modularisering og
afkobling, anvender microservices dette princip på hele systemet.

Størrelsen på en microservice er ikke fastsat; det handler om at gøre
dem passende til deres brugsscenarier. Kommunikation mellem tjenester
sker ofte via REST, hvilket gør det muligt at bygge systemet med
forskellige programmeringssprog, så længe de understøtter fælles
kommunikationsprotokoller.

### Fordele ved microservices

#### Fleksibilitet

Hver enhed af arbejde kan kaldes fra en hvilken som
helst anden enhed, hvilket giver stor fleksibilitet.

#### Agilitet og skalering

Microservices gør det nemt at skalere og distribuere systemer globalt.

### Hvorfor er microservices populære?

Microservices er billige at implementere, ofte ved brug af open-source
software på standardhardware. Dette adskiller dem fra SOA, som var dyrt
og komplekst. Den fortsatte interesse i microservices skyldes deres evne
til at øge agilitet og støtte global distribution, hvilket har sikret
deres popularitet både i store virksomheder og startups.

### Konklusion, udfordringer og perspektiver

Selvom microservices har mange fordele, kommer de også med omkostninger, som vi
vil udforske nærmere.

## Microservices: Solver of problems but not the silver bullet

Enhver arkitekturbeslutning indebærer kompromiser. Der findes ingen
universalløsning, der løser alle brugsscenarier, og selv inden for en
bestemt arkitektur findes der kompromiser, der skal tages. Forfatteren
understreger, at der er omkostninger ved at skifte til en
microservices-arkitektur, og det er vigtigt at vurdere, om fordelene opvejer
disse omkostninger. Hvis en microservices-arkitektur ikke passer til
organisationens behov, bør man ikke tvinge det igennem.

### Udfordringer ved microservices

#### Øget kompleksiteten

Overgangen fra et monolitisk system til microservices kan
øge kompleksiteten betydeligt. Dette gælder især, hvis organisationen har
komplekse processer omkring softwareudvikling og deployment. Håndtering af mange
små services i stedet for få store komponenter kan blive tids- og ressourcekrævende.

#### Distributionsafgift

En microservices-arkitektur fører til en betydelig stigning
i netværkskommunikation mellem tjenesterne. Dette øger den samlede latenstid
og risikoen for netværksbelastning, hvilket kan medføre store forsinkelser
og flaskehalse i systemet.

#### Reduceret pålidelighed

Flere bevægelige dele i systemet øger risikoen for fejl.
Hvis en microservice fejler, kan det påvirke flere klientkald og dermed
systemets overordnede pålidelighed.

Forfatteren anbefaler, at organisationer nøje overvejer disse udfordringer,
før de implementerer microservices. Det er vigtigt at finde en balance mellem
fordelene ved microservices og de risici, der følger med, for at opnå succes.

Målet er at træffe informerede beslutninger, der maksimerer fordele og
minimerer risici.

## Microservices and cloud native

Når vi taler om microservices, er det ofte i forbindelse med cloud native
arkitekturer, men de to begreber er ikke identiske. Her er en kort oversigt
over deres forhold og forskelle:

### Cloud Native Arkitekturer

#### Definition, Cloud Native

Cloud native arkitekturer er designet til at køre i forskellige typer
af cloud-infrastrukturer (offentlig, privat eller hybrid) og følger
ofte 12-faktor eller 15-faktor metoderne.

#### Egenskaber, Cloud Native

Øget oppetid, skalerbarhed, og distribution. Cloud native systemer kan
være en del af en enkelt datacenter eller globalt distribueret.

### Microservices

#### Definition, Microservices

Microservices er en arkitektur, hvor applikationen opdeles i små,
uafhængige tjenester.

#### Relation til Cloud Native

Microservices passer godt til cloud native arkitekturer, da de
nemt kan implementeres og skaleres i cloud-miljøer. Men, microservices
kan også eksistere uden en cloud-native kontekst.

### Forskel og Sammenhæng

#### Forskel, Cloud Native vs. Microservices

Microservices fokuserer på hvordan applikationen er opdelt i
tjenester, mens cloud native handler om hvordan applikationen
er designet til at køre i forskellige cloud-miljøer.

#### Sammenhæng, cloud native og microservices

Mange microservices-implementeringer er designet til at køre på
cloud-native platforme, men det er muligt at have cloud-native
applikationer uden microservices og omvendt.

### Praktiske Overvejelser

#### Migration

En af de største udfordringer ved at flytte microservices til
cloud native miljøer er håndtering af filsystemer, som ofte kræver
migration til tjenester som Amazon S3.

Forfatteren vil i det følgende fokusere på microservices, men vil
inkludere tips til at overgå fra traditionelle systemer til cloud native løsninger.

## Microservices: The Core Concepts

### Hvad gør en Microservice til en Microservice?

Kommunikation mellem Tjenester

#### Protokoller

I en microservices-arkitektur kommunikerer tjenester primært via HTTP, ofte ved
hjælp af REST. Alternativer inkluderer gRPC og GraphQL for frontend, samt
event-baserede kommunikationsmetoder.

#### Fordele

Standardisering af kommunikationsmetoder gør det muligt for teams at bygge
og konsumere tjenester på en ensartet måde, hvilket er særligt nyttigt for
store organisationer som Amazon eller Netflix.

### Størrelse vs. Funktionalitet

#### Størrelse

Der er ingen fast størrelse for en microservice. Det er ikke størrelsen,
men snarere hvordan en service fungerer, der er vigtig.

#### Operationer

En microservice bør fokusere på en veldefineret domæne med lidt eller ingen
tværgående operationer. Dette svarer til objekt-orienteret programmering,
hvor en klasse håndterer en bestemt type opgave.

### Domæne-Driven Design

#### Domæner

Microservices bør operere på et veldefineret domæne, hvilket betyder at
tjenesterne arbejder på et sammenhængende sæt af funktioner og data. Dette
kan omfatte CRUD-operationer på domæneobjekter eller håndtering af
forretningsprocesser på tværs af domæner.

### Udfordringer og Eksperimentering

#### For Fint eller For Groft

Det er en almindelig fejl at lave tjenester enten
for fine-grained eller for coarse-grained. Oftest ender man med at bygge for
fine-grained tjenester, hvilket kan føre til høj latency.

#### Refaktorering

Forfatteren anbefaler at eksperimentere og være villig til at refaktorere
tjenester, da mindre tjenester kan bygges, testes, deployeres og opstartes
hurtigere, hvilket fremmer hurtigere læring og fejlretning.

I dette kursus vil forfatteren opfordre til at eksperimentere med størrelsen og
strukturen af microservices for at finde den bedste balance og forbedre
systemets effektivitet.

## Netværkstrafik og Kommunikation i Microservices

### Kommunikationsstrategi

#### HTTP og REST

I en microservices-arkitektur kommunikerer alle tjenester over HTTP, hvor
REST er den primære metode. Dette muliggør, at tjenester kan udvikles i
forskellige programmeringssprog og rammer, så længe de understøtter
RESTful-tjenester.

#### Protokol-Aware Heterogeneous Interoperability

Denne tilgang gør det muligt for tjenester at kommunikere effektivt i en
blandet miljø uden behov for specielle kommunikationsteknologier. Dette
skaber stor fleksibilitet i, hvordan tjenester bygges og anvendes.

### Fordele ved HTTP/REST

#### Fleksibilitet og Agilitet

Udviklingsteams kan vælge det sprog og den ramme, der er mest passende for
dem, og eksponere deres tjenester via HTTP. Dette reducerer læringskurven
for andre teams, der bruger tjenesterne og øger hastigheden af udviklingen.

#### Hurtigere Levering

Da alle moderne rammer understøtter REST, kan teams levere og forbruge
tjenester hurtigt uden at skulle tilpasse sig komplekse
kommunikationsprotokoller som SOAP.

### Udfordringer ved Kommunikation

#### Orkestrering

Med den frihed, som microservices tilbyder, er orkestrering afgørende.
Uden klare begrænsninger på, hvilke tjenester der kan kalde hinanden, kan
systemet blive sårbart over for fejlkald og systemsvigt.

#### Versionering og API-Opdateringer

Manglende kontrol over, hvilke tjenester der kan opdatere eller kalde
hinanden, kræver en solid versioneringsstrategi. Hvis en API opdateres,
skal du sikre, at eksisterende tjenester ikke bliver brudt. Implementering
af kontraktstest og passive API-regler kan hjælpe med at håndtere dette.

### Anbefalinger

#### Versioneringsstrategi

Udvikl og vedligehold en klar versioneringsstrategi for dine API'er.

#### Kontraktstest

Brug kontraktstest for at sikre, at ændringer i en tjeneste ikke bryder
andre tjenester.

#### Passivitet

Implementer passive API-regler for at undgå systemfejl ved API-opdateringer.

Ved at forstå og håndtere disse kommunikationsudfordringer kan du forbedre
robustheden og effektiviteten af din microservices-arkitektur.

## Distribution og Skalering i Microservices

### Distribution

#### Global Distribution

Microservices-arkitekturen tillader, men kræver ikke, global distribution af tjenester.
Selvom det er muligt at flytte tjenester over hele verden, kan dette medføre høje
omkostninger og øget latens.

#### Fordele ved Distribution

Muligheden for global distribution betyder, at du kan placere tjenester nærmere
brugerne for høj tilgængelighed og lavere latenstid uden at gøre hele systemet
globalt tilgængeligt. Dette er særligt nyttigt for virksomheder med både
kundeorienterede og interne applikationer.

#### Forberedelse til Fremtiden

Ved at designe en system af microservices, der er i stand til global distribution
fra starten, forbereder du din virksomhed til fremtidig vækst og ekspansion.

### Skalering

#### Uafhængig Skalering

I en microservices-arkitektur kan hver tjeneste skaleres individuelt. Hvis en
bestemt tjeneste oplever høj belastning, kan du øge antallet af instanser af
denne tjeneste uden at påvirke resten af systemet.

### Horisonal og Vertikal Skalering

#### Horisonal Skalering

Øg antallet af instanser af en microservice for at håndtere øget belastning.
Dette kræver normalt ingen ændringer uden for selve tjenesten, især hvis et
API-proxy-lag er på plads.

#### Vertikal Skalering

Forøg ressourcerne til en eksisterende instans. Begge metoder kan anvendes
for at håndtere trafikstigninger eller -fald.

#### Elastisk Skalering

Microservices-arkitekturen muliggør elastisk skalering, hvor systemet kan
tilpasse sig ændringer i trafikvolumen. Dette står i kontrast til traditionelle
monolitiske systemer, der ofte bygges til at håndtere den højeste forventede
belastning og kan have svært ved at skalere fleksibelt.

### Omkostninger og Udfordringer

#### Pris og Komplekse Overvejelser

Mens distribution og skalering er nogle af de mest værdifulde fordele ved
microservices-arkitekturen, kommer de med omkostninger. Det er vigtigt at være
opmærksom på disse omkostninger, som vil blive uddybet i kommende materiale.

Microservices-arkitekturen tilbyder kraftfulde muligheder for skalering og
distribution, men det er vigtigt at forstå og forberede sig på de omkostninger
og kompleksiteter, der følger med.

## Risikoen ved Latency og Gridlock

### Latency

Microservices-arkitekturen forbedrer skalerbarheden og distributionen af
systemet, men det kommer med omkostninger, især relateret til latency.

- **Latency Problematik**: Hver serviceopkald i en microservices-arkitektur er en
netværksanrop, som medfører forbindelse opsætning, nedrivning og wire latency.
Selvom latency for en enkelt opkald kan synes ubetydelig, kan det blive kritisk,
når systemet bliver komplekst og flere opkald skal håndteres samtidigt.
- **Øget Risiko ved Høj Belastning**: Når trafikken stiger og tjenesterne bliver
mere belastede, stiger risikoen for øget latency. Dette kan føre til gridlock,
hvor ventetiden bliver uudholdelig, og kan føre til systemfejl.

### Gridlock

- **Cirkulære Opkald**: I en ren microservices-arkitektur kan enhver service kalde
enhver anden service, hvilket kan føre til cirkulære opkald. Dette kan hurtigt
forværre latency, især når mange tjenester er afhængige af en service i en
cirkulær opkaldsstak.
- **Håndtering af Gridlock**: For at håndtere latency og gridlock effektivt,
er det vigtigt at implementere mønstre som circuit breaker. Dette mønster
gør det muligt at bryde forbindelsen til en fejlfungerende service og udløse
en standard adfærd, der ikke inkluderer den problematiske service.

### Praktiske Løsninger

- **Circuit Breaker**: Brug af et circuit breaker mønster hjælper med at undgå total
systemfejl ved at begrænse virkningen af latency. Eksempler inkluderer
Netflix's Hystrix, som tillader systemet at fortsætte med en reduceret
funktionalitet, selvom nogle tjenester er nede.
- **Timeout Logik**: Implementer stærk timeout logik for at forhindre gridlock
og sikre, at systemet ikke bliver fuldstændig ude af funktion.

At forstå og implementere løsninger til latency og gridlock er essentielt
for at sikre systemets stabilitet og ydeevne i en microservices-arkitektur.

## Bounded Context

Når du planlægger at opdele dit system i mikroservices, kan Domain-Driven
Design (DDD) være en nyttig strategi. En central del af DDD er at definere
**bounded contexts** for effektiv dekomponering af et stort system til
individuelle tjenester.

### Bounded Contexts og Microservices

- **Formål med Bounded Context**: Bounded contexts hjælper med at identificere
grænserne for forskellige domæner i dit system og anvende denne viden til at opdele
tjenester. Dette kan forhindre problemer med enten for fine eller for grove
opdelinger af tjenester.

- **Undgå Fejl**: Tidlige fejl ved migrering fra monolitiske systemer til microservices
skyldes ofte dårligt valg af granularitet. Ved at anvende DDD kan du finde en
passende balance for dine tjenester.

### Analyse af Domæner

- **Data-Domæner vs. Brugs-Cases**: Det er ikke nok at opdele baseret på data-domæner
alene. Analyser trafikmønstre og brugstilfælde for at forstå, hvordan domæner
interagerer.

- **Eksempel**: Hvis du har et kundedomæne og et brugerdomain, og alle kald til
brugerdomain også rammer kundedomænet, kan det indikere, at de måske bør samles
i en enkelt bounded context. Men, hvis brugerdomain har særlige sikkerhedskrav,
kan det være grund til at adskille dem.

### Fordele ved Bounded Contexts

- **Reducere Latency**: Ved at definere klare bounded contexts kan du reducere antallet
af kryds-domæne opkald og dermed minimere latency.

- **Forbedre Kontrakter**: Klare grænser gør det lettere for forbrugere af dine
tjenester at finde de rette tjenester og forbedrer systemets samlede sundhed.

- **Øge Agilitet**: En veldefineret bounded context forbedrer både systemets ydeevne
og udviklingsprocessens hastighed.

Implementering af en stærk bounded context-struktur forbedrer både systemets
effektivitet og udviklingsteamets agilitet.

## Data Domains as a Service Boundary

Når du arbejder med mikroservices, er det vigtigt at overveje, hvordan du
håndterer dataadgangslagene. Dette kan være en kompleks proces, især når
du flytter fra en monolitisk database til en mikroservices-arkitektur.

### Udfordringer med Data Domæner

- **Transaktionsgrænser**: At fjerne transaktionsgrænser i en eksisterende
database kan være svært. Distributed transactions er ofte en smertefuld
løsning i mikroservices, så det er bedre at undgå dem.
  
- **Decomponering**: At opdele en monolitisk database i mindre systemer er en
af de sværeste opgaver. Der er to primære strategier for dette:

  1. **Database Først**: Opdel den eksisterende database i mindre databaser og
  byg tjenesterne derefter. Denne metode kan være hurtigere, men risikerer
  fejl, som kan være vanskelige at rette.
  
  2. **Service Først**: Start med at bygge tjenesterne og lad dem tilslutte sig
  den monolitiske database. Dette giver dig mulighed for at observere trafikmønstre
  og definere dine dataområder bedre. Når du har en klarere forståelse, kan du
  begynde at opdele databaserne.

### Bedste Praksis

- **Minimere Kryds-Domæne Kald**: Prøv at reducere antallet af kald mellem domæner
for at undgå kompleksitet og latens.
  
- **Forstærk Transaktionsgrænser**: Sørg for, at dine transaktioner er godt
defineret og håndteret.

- **Brug af Telemetri**: Implementer gode telemetri- og sporingsmønstre for at
overvåge og optimere dataadgang.

Bygning af stærke data domæner er kritisk for en vellykket mikroservices-arkitektur.
Ved at tage tid til at designe dine data domæner ordentligt, vil du kunne minimere
problemer og sikre en sund systemarkitektur.

## No ACID, Only BASE

Når du arbejder med mikroservices, er det vigtigt at forstå forskellen mellem ACID
og BASE, især når det kommer til transaktioner i distribuerede systemer.

### ACID

Traditionelle systemer sigter efter ACID-kompatible transaktioner, som står for:

- **Atomic**: Transaktionen skal enten fuldføres helt eller ikke fuldføres overhovedet.
- **Consistent**: Alle dataens regler og begrænsninger skal opretholdes.
- **Isolated**: Ingen andre transaktioner kan se eller ændre data, der ikke er
i en konsistent tilstand.
- **Durable**: Når en transaktion er fuldført, skal ændringerne være
permanente og ikke gå tabt.

Disse egenskaber fungerer godt i monolitiske applikationer uden distribution.
I en SOA-model bliver de vanskelige at håndtere, og i en mikroservices-arkitektur
nærmest umulige.

### BASE

I mikroservices-arkitektur stræber vi ofte efter BASE i stedet for ACID:

- **Basically Available**: Systemet er tilgængeligt det meste af tiden.
- **Soft state**: Data kan være midlertidigt inkonsistent.
- **Eventually consistent**: Data vil blive konsistent over tid, men ikke
nødvendigvis med det samme.

I BASE-modellen stræber vi efter eventual consistency i stedet for umiddelbar,
atomisk eller isoleret konsistens. Målet er at opnå en tilstand, hvor data i
alle noder i det distribuerede datasystem til sidst vil være konsistent,
forudsat at data ikke ændres igen.

### Overvejelser

- **ACID vs BASE**: ACID er lettere at arbejde med som udvikler eller arkitekt,
da det giver garantier for dataens tilstand. BASE kræver dog en anden
tilgang til håndtering af systemets konsistens og tilgængelighed.
  
- **Brug af BASE**: Identificer, hvor du virkelig har brug for ACID-transaktioner
og modeller dine domæner og tjenester omkring disse behov. Overvej, om din
opfattelse af behovet for øjeblikkelig konsistens er berettiget, eller om
det kan håndteres med eventual consistency.

- **Eksempler**: I et bank system, hvor du overfører penge fra en konto til en
anden, skal denne operation være atomisk. I andre tilfælde, som ansøgning
om lån, kan eventual consistency være tilstrækkelig.

### Design for Eventual Consistency

Selv om design for eventual consistency kan være komplekst, kan du finde
ressourcer og materialer online til at hjælpe med at tackle disse problemer
i virkeligheden. At stræbe efter eventual consistency, hvor det er muligt,
kan forbedre systemets sundhed som helhed.

## The API Layer

Et API-lag er ofte inkluderet i mikroservices-arkitekturer, og det er der
en god grund til. I en ren mikroservices-arkitektur er et API-lag i bund og
grund en aggregeret proxy for alle dine service-tilbud.

### Funktioner ved API-laget

- **Proxy Interface**: API-laget fungerer som en standardiseret proxygrænseflade,
der eksponerer de service endpoints og API-operationer, som vi konfigurerer
det til at eksponere. Det beskytter den eksterne verden eller dine klienter
fra at kende strukturen, organisationen eller hvilken præcis service der
udstiller en specifik operation.

- **Isolering af Klienter**: API-laget isolerer klienter fra at skulle kende
den direkte IP-adresse og port for de services, de kalder. Dette er især
nyttigt under skaleringsoperationer, hvor API-laget muliggør kald til
mange forskellige endpoints uden at vide, hvilken service der producerer
det specifikke endpoint.

- **Håndtering af Ændringer**: Uanset om du refaktorerer en monolit eller
bygger nye service-tilbud, vil implementeringen af et API-lag minimere
ændringer for klienterne i forhold til underliggende ændringer i kodebasen.
Hvis hver service eksponeres gennem et API-proxy-lag, kan du opdele eller
aggregere services og blot ændre proxy-konfigurationen for at matche
udviklingsoperationerne.

- **Versionering**: API-laget kan også hjælpe med versionering af operationer.
Selvom der er flere måder at håndtere versionændringer på, kan API-laget
dirigere til en ældre version af en service uden at tvinge en klient til
at ændre noget, selvom deploymentsmodellen ændres.

### Vigtighed af API-laget

Selvom API-laget ofte betragtes som valgfrit, er det en af de mest kritiske
komponenter, hvis du ønsker at reducere den samlede påvirkning af overgangen
til denne arkitekturmodel. Overvej at implementere et API-lag for at opnå
de nævnte fordele.

## Asynchronous Communications

En af de bedste strategier til at reducere latenstid i et mikroservices-baseret
system er at undgå en ren synkron kommunikationsmodel. At udnytte
begivenhedsdrevet asynkron kommunikation er en fremragende måde at forbedre
systemets sundhed samt støtte langsigtede mål om at flytte store mængder data
over lange afstande på en relativt rettidig måde.

### Udfordringer med Asynkron Kommunikation

- **Kompleksitet**: Asynkron kommunikation er ikke let. Du skal investere
betydelig tid i at sikre, at dine kommunikationer når deres destination og
bliver behandlet i overensstemmelse med forudbestemte tolerancer. At lære, hvordan
man passende håndterer og reagerer på fejlforhold er kritisk for at holde
systemet kørende.

- **Event-Drevet Mikroservices**: Når man taler om asynkron kommunikation i en
mikroservices-arkitektur, henvises der ofte til event-drevne mikroservices som
en metode til at støtte eventual konsistens af data. I denne model lægger services
en besked i en asynkron beskedbroker eller et midlertidigt datalager, og derefter
driver events fra denne tilstandændring. De efterfølgende event-processorer vil
behandle dataene og til sidst få dataene opbevaret i deres endelige datalager.
Mutationer vil derefter ske gennem enten distribuerede datapatterns eller
efterfølgende eventbehandling.

- **Stream Data Platforms**: En stærk model for store systemer med mange operationer
er en stream data platform. I en stream data platform skrives events til en central
beskedbroker. Disse events udløser lytteoperationer, der tager handling på dataen,
hvis den er relevant. Events kan udløse operationer, der formaterer dataen,
forårsager andre downstream events eller forskellige andre aktiviteter. Stream
data platforms kan være meget nyttige i store distribuerede systemer, fordi events
ofte udløser flere operationer, ikke bare én. Ved at udnytte en sådan platform kan
du udføre mere arbejde med mindre samlet stress på systemet, hvilket forbedrer den
samlede ydeevne, især i aktiviteter som logning, revision, sikkerhed eller
andre data-inspektioner.

### Overgang til Asynkrone Processer

- **Fejlbehandling**: Overgangen fra ren synkron operation til asynkron behandling
kan være en af de mest oversete mønstre. Selvom vi ofte ønsker øjeblikkelig
feedback, er det ikke altid nødvendigt. Mange gange kan vi blot udsætte behandlingen
til at finde sted asynkront. Når vi gør dette, reducerer vi latenstidens
begrænsninger på funktioner, der skal udføres i realtid.

- **Fejltilstande**: Når du skifter til asynkrone operationer, skal du sørge for
korrekt håndtering af fejltillstande og genopretning fra dem. Hvis beskeder ikke
kan behandles af nogen grund, kan du ikke blot ignorere dem. Dead letter queues
skal overvåges, og der skal handles for at behandle beskederne, selvom rettelsen
er manuel.

Data skal rutinemæssigt overvåges for korrekthed på en automatiseret måde,
og ydeevnen skal vurderes for at sikre, at Message Broker's ikke bliver forsinket.

### Anbefaling

Forfatteren opfordrer til at tage tid i dit systemdesign og undersøge, hvordan
udnyttelse af asynkron kommunikation kan hjælpe dit team med at opnå reduceret
latenstid og øget gennemløb.
