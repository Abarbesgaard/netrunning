---
{"dg-publish":true,"permalink":"/opsummering-af-4-semester/","created":"2024-11-06T08:44:04.025+01:00"}
---

# Opsummering af læringsforløb - 4. semester

Denne opsummering gennemgår mit læringsforløb på 4. semester af datamatikeruddannelsen, fra begyndelsen af august til slutningen af november, med et særligt fokus på **microservices** og **it-sikkerhed**. 
Den indledende interesse for mere konventionelle sikkerhedstemaer udviklede sig til en dybere forståelse af, hvordan sikkerhed kan indlejres i microservices-arkitektur.
## Indledning
I starten af semesteret havde jeg en noget forenklet tilgang til it-sikkerhed. Som mange andre begyndte jeg med forestillingen om, at sikkerhed primært handler om trusselsmodeller som DDoS-angreb og penetrationstest. 

Mine oprindelige læringsmål fokuserede på ekstern sikkerhed og trusselshåndtering, men gennem semesteret opdagede jeg, at it-sikkerhed i en microservices-arkitektur indebærer en bredere tilgang. 

Sikkerheden bliver en del af både arkitekturen og udviklingsprocessen, med fokus på autentifikation, autorisation og beskyttelse af interne API'er. Dette skifte blev centralt for mit videre arbejde og min forståelse af sikkerhed som en kontinuerlig praksis.

## Diagram: Læringsforløb

![It-sikkerhed_Læringsforløb.png](/img/user/Excalidraw/It-sikkerhed_L%C3%A6ringsforl%C3%B8b.png)

Diagrammet nedenfor illustrerer min læringsrejse, hvor det brede fokus i starten af semesteret gradvist blev indsnævret til et mere målrettet arbejde med API-beskyttelse og interne sikkerhedsprotokoller. Uge 33-34 er markeret med en fremtrædende rød bjælke for at symbolisere projektets start og mit oprindelige brede fokus, som senere blev justeret.

## Refleksion over ændringer i forståelse af It-sikkerhed

### Før og efter-billede

**Før:**
Min forståelse af it-sikkerhed centrerede sig om *netværksangreb* og *penetrationstest*, og jeg antog, at beskyttelse hovedsageligt handlede om forsvar mod eksterne trusler som DDoS-angreb og hackerangreb.

**Efter:**
Jeg opdagede, at it-sikkerhed også handler om beskyttelse mod interne fejl og menneskelige fejl, som kan opstå under udvikling og implementering. 

>Især i en microservices-arkitektur er sikkerhed ikke et sidste trin, men snarere et integreret aspekt af designet. 

Jeg har derfor fokuseret på at beskytte API'er mod autorisationsfejl, gennemføre rate limiting og anvende moderne sikkerhedsløsninger som JWT, der beskytter mod misbrug og dataeksponering i API'er.

## Udvikling af Læringsmål og Hvordan De Er Opnået

Jeg opnåede mine læringsmål ved at dykke ned i *distributed systems* og _eventual consistency_, hvilket har været særligt relevant i microservices-arkitekturen. 

Implementeringen af RabbitMQ som message queue for asynkron kommunikation har givet mig erfaring med at sikre systemets konsistens over tid. Dette har givet mig en praktisk forståelse af, hvordan microservices kan kommunikere og opretholde dataintegritet, selv under forsinkelser.


## Proces og Refleksion

Jeg brugte **Kolbs læringscirkel** aktivt til at strukturere mit arbejde og reflektere over læringsprocessen. Mit oprindelige fokus var inspireret af _Getting Things Done (GTD)_-metoden, men denne viste sig for bred til de konkrete mål og milepæle, som jeg ønskede at nå i forbindelse med sikkerhed og microservices. Derfor skiftede jeg til [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-mål]], hvilket skabte en klarere ramme for både ambitioner og tidsplan.
![Pasted image 20241112130322.png](/img/user/Pasted%20image%2020241112130322.png)

**Refleksion:** Efter hvert sprint evaluerede jeg, hvilke dele af processen der fungerede optimalt, og hvilke der kunne forbedres. GTD-metoden viste sig mindre velegnet til min målsætning, hvilket førte til overgangen til SMART-mål som et mere fokuseret værktøj.

**Abstrakt Begrebsdannelse:** Refleksionerne førte til en justering af læringsmålene. SMART-målene gjorde mine mål specifikke og målbare, hvilket hjalp mig til at opnå bedre overblik og mere præcise fremskridt.

**Aktiv Eksperimenteren:** Med [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-målene]] som fundament eksperimenterede jeg med konkrete løsninger, såsom rate limiting og OAuth2 i API-gatewayen, og kunne gennem denne strukturerede tilgang opnå kontinuerlig fremdrift.

Kolbs læringscirkel blev således en integreret del af min proces og har hjulpet mig med at forfine og fokusere på realistiske læringsmål. Denne strukturerede fremgangsmåde gav mig en målrettet udvikling gennem hele semesteret.
### Smart mål
![Pasted image 20241112130348.png](/img/user/Pasted%20image%2020241112130348.png)

### Eksempel

I starten af 4. semester hvor jeg havde fokus på at benytte mig af GTD metoden, fik jeg lavet rigtig mange "opgaver". Jeg benyttede mig af et systemet som hed Task Warrior til at strukturere dette.

En konkret opgave kunne se sådan ud:

> Læs om Microservice Arkitektur

Jeg vil nu tage dig med i processen hvordan sådan en "opgave" kunne forløbe i GTD og på samme måde med et smart mål efter.

#### GTD
>Læs om Microservice Arkitektur

**Kan det handles på?**
ja det kan det. 
**Kræver det flere trin?**
Ja, denne vil kræve flere trin. Da den er ret vag defineret. Så det skulle ind i et projekt. Herefter skulle det indeles i flere trin som hver i sær lever op til GTD.
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
Jeg vil gøre det nu/ Jeg sætter tid af man kl 8:45 - 9:45 til at gøre det


Følgende er mine refleksioner om hvordan GTD og Smart mål virkede for mig.

**GTD** blev hurtigt en metode til at få lavet en hulens masse ting. Når det er sagt er det også det den er lavet til. For mig var det *inbox'en* i denne metode det som virkede bedst. Det at have et sted hvor man kunne *læsse* alle tanker og ideer af var noget jeg endte med at gøre brug af i smart mål.
**GTD** ligger også op til at man er i et team, ved at den har et trin hvor man skal, hvis man kan, udelegere ansvaret for opgaven. At have dette trin hver gang jeg skulle igennem når jeg lavede en opgave blev hurtigt trivielt.

**Smart mål** blev derfor metoden jeg forsøgte at skifte **GTD** ud med. Det som lokkede mig ved denne metode var at jeg ikke skulle ind dele/ opdele min opgave når jeg havde en.
Det var bare at gå i gang, og hvis der skulle opstå flere "opgaver" løbende smed jeg dem ind i min *inbox* som jeg har for vane at gennemgå hver morgen.
Et andet godt element var at "time boxe" opgaverne. Lidt det samme som i *GTD*, dog valgte jeg at gøre mere ud af dette aspekt i Smart mål-metoden

---
Neden under er her en liste over de uger jeg har indført i læringsplanen.
[[Main/4. Semester/Læringsplan/33_34\|Uge 33 - 34]]
[[Main/4. Semester/Læringsplan/35_36\|Uge 35 - 36]]
[[Main/4. Semester/Læringsplan/37_38\|Uge 37 - 38]]
[[Main/4. Semester/Læringsplan/39_40\|Uge 39 - 40]]
[[Main/4. Semester/Læringsplan/41_42\|Uge 41 - 42]]
[[Main/4. Semester/Læringsplan/43_44\|Uge 43 - 44]]
