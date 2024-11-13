---
{"dg-publish":true,"permalink":"/opsummering-af-4-semester/","created":"2024-11-06T08:44:04.025+01:00"}
---

## Opsummering af læringsforløb - 4. semester

Denne opsummering gennemgår mit læringsforløb på 4. semester af datamatikeruddannelsen, fra begyndelsen af august til slutningen af november, med et særligt fokus på **microservices** og **it-sikkerhed**. 

Den indledende interesse for mere konventionelle sikkerhedstemaer udviklede sig til en dybere forståelse af, hvordan sikkerhed kan indlejres i microservices-arkitektur.
## Indledning
I starten af semesteret havde jeg en noget forenklet tilgang til it-sikkerhed. Som mange andre begyndte jeg med forestillingen om, at sikkerhed primært handler om trusselsmodeller som **DDoS-angreb** og **penetrationstest**. 

Mine oprindelige læringsmål fokuserede på ekstern sikkerhed og trusselshåndtering, men gennem semesteret opdagede jeg, at it-sikkerhed i en microservices-arkitektur indebærer en bredere tilgang. 

Sikkerheden bliver en del af både arkitekturen og udviklingsprocessen, med fokus på autentifikation, autorisation og beskyttelse af interne [[Main/Noter/API\|API'er]]. Dette skifte blev centralt for mit videre arbejde og min forståelse af sikkerhed som en kontinuerlig praksis.

## Diagram: Læringsforløb

![It-sikkerhed_Læringsforløb.png](/img/user/Excalidraw/It-sikkerhed_L%C3%A6ringsforl%C3%B8b.png)

Diagrammet viser min læringsrejse i it-sikkerhed, hvor fokus starter bredt i uge 33-34, markeret med en rød bjælke. Fra uge 35-42 bliver arbejdet gradvist mere specialiseret med fokus på [[Main/Noter/API\|API]]-sikkerhed og interne protokoller, illustreret med de blå sektioner. Mod slutningen, uge 43-48, er læringen mere målrettet mod specifikke sikkerhedsemner.

## Refleksion over ændringer i forståelse af It-sikkerhed

### Før og efter-billede

**Før:**
Min forståelse af it-sikkerhed centrerede sig om *netværksangreb* og *penetrationstest*, og jeg antog, at beskyttelse hovedsageligt handlede om forsvar mod eksterne trusler som DDoS-angreb og hackerangreb.

**Efter:**
Jeg opdagede, at it-sikkerhed også handler om beskyttelse mod interne fejl og menneskelige fejl, som kan opstå under udvikling og implementering. 

>Især i en microservices-arkitektur er sikkerhed ikke et sidste trin, men snarere et integreret aspekt af designet. 

Jeg har derfor fokuseret på at beskytte [[Main/Noter/API\|API'er]] mod autorisationsfejl, gennemføre rate limiting og anvende moderne sikkerhedsløsninger som [[Main/Noter/JWT token\|JWT]], der beskytter mod misbrug og dataeksponering i [[Main/Noter/API\|API'er]]

## Udvikling af læringsmål og hvordan de er opnået

Jeg opnåede mine læringsmål ved at dykke ned i *distributed systems*, *Microservices* og _eventual consistency_, hvilket har været særligt relevant i microservices-arkitekturen. 

Implementeringen af [[Main/Noter/RabbitMQ\|RabbitMQ]] som [[Main/Noter/Message Brokers\|message broker]] for asynkron kommunikation har givet mig erfaring med [at sikre systemets konsistens over tid](https://en.wikipedia.org/wiki/Eventual_consistency). Dette har givet mig en praktisk forståelse af, hvordan microservices kan kommunikere og opretholde dataintegritet, selv under forsinkelser.


## Proces og Refleksion

Jeg brugte [[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] aktivt til at strukturere mit arbejde og reflektere over læringsprocessen. Mit oprindelige fokus var inspireret af [[Main/Noter/Getting things done\|Getting Things Done (GTD)-metoden]], men denne viste sig for bred til de konkrete mål og milepæle, som jeg ønskede at nå i forbindelse med sikkerhed og microservices. Derfor skiftede jeg til [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-mål]], hvilket skabte en klarere ramme for både ambitioner og tidsplan.
![Pasted image 20241112130322.png](/img/user/Pasted%20image%2020241112130322.png)

**Refleksion:** Efter hvert sprint evaluerede jeg, hvilke dele af processen der fungerede optimalt, og hvilke der kunne forbedres. [[Main/Noter/Getting things done\|GTD-metoden]] viste sig mindre velegnet til min målsætning, hvilket førte til overgangen til [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-mål]] som et mere fokuseret værktøj.

**Abstrakt Begrebsdannelse:** Refleksionerne førte til en justering af læringsmålene. [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-målene]] gjorde mine mål specifikke og målbare, hvilket hjalp mig til at opnå bedre overblik og mere præcise fremskridt.

**Aktiv Eksperimenteren:** Med [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-målene]] som fundament eksperimenterede jeg med konkrete løsninger i [[Main/Noter/API-Gateway\|API-gateway'en]], og kunne gennem denne strukturerede tilgang opnå kontinuerlig fremdrift.

[[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] blev således en integreret del af *min proces* og har hjulpet mig med at forfine og fokusere på realistiske læringsmål. Denne strukturerede fremgangsmåde gav mig en målrettet udvikling gennem hele semesteret.
### Smart mål
![Pasted image 20241112130348.png](/img/user/Pasted%20image%2020241112130348.png)

### Eksempel

I starten af 4. semester hvor jeg havde fokus på at benytte mig af [[Main/Noter/Getting things done\|GTD metoden]], fik jeg afsluttet rigtig mange "opgaver". Jeg benyttede mig af et systemet som hed [Task Warrior](https://taskwarrior.org/) til at strukturere dette.

En konkret opgave kunne se sådan ud:

> Læs om Microservice Arkitektur

Jeg fløj gennem de opgaver jeg havde sat mig for at få afsluttet, men noget føltes *off*.

Jeg fik afsluttet de opgaver jeg satte mig for, men lærte jeg  egenlig også noget?

Jeg vil nu tage dig med i processen hvordan sådan en "opgave" kunne forløbe i [[Main/Noter/Getting things done\|GTD]] og på samme måde med [[Main/Noter/Systemudvikling/Smart_Mål\|et smart mål]]efter. Så du kan se den process jeg gennemgik i løbet af 4. semester

#### GTD
>Læs om Microservice Arkitektur

**Kan det handles på?**
ja det kan det. 
**Kræver det flere trin?**
Ja, denne vil kræve flere trin. Da den er ret vag defineret. Så det skulle ind i et projekt. Herefter skulle det indeles i flere trin som hver i sær lever op til [[Main/Noter/Getting things done\|GTD]].
**Tager det mindre end to minutter**
Nej - hvis det gjorde skulle man gøre det med det samme.
**kan det udelegeres?**
Nej
**Planlæg**
Jeg vil gøre det den og den dato

#### Smart mål
> Læs om Microservice Arkitektur

**Specifikt**
Jeg vil gerne opnå viden om arkitekturen i microservices.

**Målbart**
Når jeg har læst om dette vil jeg have en brugbar viden om Microservice arkitektur.

**Attraktivt**
Jeg syntes emnet er utrolig interessant for min udvikling som programmør. 
*Hvis det her var muligt at komme med et endnu mere konkret element der kunne gøre det attraktivt skal det være her i stedet*

**Realistisk**
Ja, jeg vil godt kunne opnå viden inden for emnet.

**Tidsbestemt**
Jeg vil gøre det nu / Jeg sætter tid af man kl 8:45 - 9:45 til at gøre det


Følgende er mine refleksioner om hvordan [[Main/Noter/Getting things done\|GTD]] og [[Main/Noter/Systemudvikling/Smart_Mål\|Smart mål]] virkede for mig.

[[Main/Noter/Getting things done\|GTD]] blev hurtigt en metode til at få lavet en hulens masse ting. Når det er sagt er det også det den er lavet til. For mig var det *inbox'en* i denne metode det som virkede bedst. Det at have et sted hvor man kunne *læsse* alle tanker og ideer af var noget jeg endte med at gøre brug af i smart mål.
[[Main/Noter/Getting things done\|GTD]] ligger også op til at man er i et team, ved at den har et trin hvor man skal, hvis man kan, udelegere ansvaret for opgaven. At have dette trin hver gang jeg skulle igennem når jeg lavede en opgave blev hurtigt trivielt.

[[Main/Noter/Systemudvikling/Smart_Mål\|Smart mål]] blev metoden jeg forsøgte at skifte [[Main/Noter/Getting things done\|GTD]] ud med. Det som lokkede mig ved denne metode var at jeg ikke skulle ind dele/ opdele min opgave når jeg havde en.
Det var bare at gå i gang, og hvis der skulle opstå flere "opgaver" løbende smed jeg dem ind i min *inbox* som jeg har for vane at gennemgå hver morgen.

Et andet godt element var at "[time boxe](https://clockify.me/timeboxing)" opgaverne. Lidt det samme som i [[Main/Noter/Getting things done\|GTD]], dog valgte jeg at gøre mere ud af dette aspekt i [[Main/Noter/Systemudvikling/Smart_Mål\|Smart mål-metoden]]. 

---
Neden under er her en liste over de uger jeg har indført i læringsplanen.
[[Main/4. Semester/Læringsplan/33_34\|Uge 33 - 34]]
[[Main/4. Semester/Læringsplan/35_36\|Uge 35 - 36]]
[[Main/4. Semester/Læringsplan/37_38\|Uge 37 - 38]]
[[Main/4. Semester/Læringsplan/39_40\|Uge 39 - 40]]
[[Main/4. Semester/Læringsplan/41_42\|Uge 41 - 42]]
[[Main/4. Semester/Læringsplan/43_44\|Uge 43 - 44]]
