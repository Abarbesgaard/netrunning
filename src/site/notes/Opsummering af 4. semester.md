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

>[!important] Især i en microservices-arkitektur er sikkerhed ikke et sidste trin, men snarere et integreret aspekt af designet. 

Jeg har derfor fokuseret på at beskytte [[Main/Noter/API\|API'er]] mod autorisationsfejl, gennemføre rate limiting og anvende moderne sikkerhedsløsninger som [[Main/Noter/JWT token\|JWT]], der beskytter mod misbrug og dataeksponering i [[Main/Noter/API\|API'er]]

## Udvikling af læringsmål og hvordan de er opnået

Jeg opnåede mine læringsmål ved at dykke ned i *distributed systems*, *Microservices* og _eventual consistency_, hvilket har været særligt relevant i microservices-arkitekturen. 

Implementeringen af [[Main/Noter/RabbitMQ\|RabbitMQ]] som [[Main/Noter/Message Brokers\|message broker]] for asynkron kommunikation har givet mig erfaring med [at sikre systemets konsistens over tid](https://en.wikipedia.org/wiki/Eventual_consistency). Dette har givet mig en praktisk forståelse af, hvordan microservices kan kommunikere og opretholde dataintegritet, selv under forsinkelser.


## Proces og Refleksion

Jeg brugte [[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] aktivt til at strukturere mit arbejde og reflektere over læringsprocessen. Mit oprindelige fokus var inspireret af [[Main/Noter/Getting things done\|Getting Things Done (GTD)-metoden]], men denne viste sig for bred til de konkrete mål og milepæle, som jeg ønskede at nå i forbindelse med sikkerhed og microservices. 

> [!note] Metoden hang ikke godt nok sammen med mine læringsplaner.

![Pasted image 20241112130322.png](/img/user/Pasted%20image%2020241112130322.png)

Derfor skiftede jeg til [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-mål]], hvilket skabte en klarere ramme for både ambitioner og tidsplan.

**Refleksion:** Efter hvert sprint evaluerede jeg, hvilke dele af processen der fungerede optimalt, og hvilke der kunne forbedres. [[Main/Noter/Getting things done\|GTD-metoden]] viste sig *mindre velegnet* til min målsætning, hvilket førte til overgangen til [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-mål]] som et mere fokuseret værktøj.

**Abstrakt Begrebsdannelse:** Refleksionerne førte til en justering af læringsmålene. [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-målene]] gjorde mine mål specifikke og målbare, hvilket hjalp mig til at opnå bedre overblik og mere præcise fremskridt.

**Aktiv Eksperimenteren:** Med [[Main/Noter/Systemudvikling/Smart_Mål\|SMART-målene]] som fundament eksperimenterede jeg for eksempel med konkrete løsninger i [[Main/Noter/API-Gateway\|API-gateway'en]], og kunne gennem denne strukturerede tilgang opnå kontinuerlig fremdrift.

[[Main/Noter/Systemudvikling/Kolbs Læringscirkel\|Kolbs Læringscirkel]] blev således en integreret del af *min proces* og har hjulpet mig med at forfine og fokusere på realistiske læringsmål. Denne strukturerede fremgangsmåde gav mig en målrettet udvikling gennem hele semesteret.
### Smart mål
![Pasted image 20241114063041.png](/img/user/Pasted%20image%2020241114063041.png)

### Eksempel

I starten af 4. semester hvor jeg havde fokus på at benytte mig af [[Main/Noter/Getting things done\|GTD metoden]], samt benytte mig af læringsplaner. Dette resulterede i at jeg fik afsluttet rigtig mange "opgaver". Jeg benyttede mig af et systemet som hed [Task Warrior](https://taskwarrior.org/) til at strukturere dette.

Jeg fløj gennem de opgaver jeg havde sat mig for at få afsluttet, men noget føltes *off*.

#### Udfordringen
Jeg manglede et overordnet mål med min læring ud over min læringsplan og den mængde af opgaver jeg løst. Jeg manglede **sporbarheden** fra mine læringsmål ned i mine opgaver jeg lavede hver dag.

#### implementering af [[Main/Noter/Systemudvikling/Smart_Mål\|SMART mål]]
Implementeringen af [[Main/Noter/Systemudvikling/Smart_Mål\|SMART mål]] betød for mig at der nu var **sporbarhed** fra de overordnede mål - helt ned til de daglige todo's jeg havde sat mig for.

Mit overordnede mål *blev præciseret* til at at være:

> [!important] Få et 7-tal til eksamen den 18. December

##### [[Main/Noter/Systemudvikling/Smart_Mål#Specifikt\|S]]
Mit mål er [[Main/Noter/Systemudvikling/Smart_Mål#Specifikt\|specifikt]] på den måde at hvis der fx havde stået: "*jeg vil være den bedste datamatiker i hele verden*" ville dette være alt for bredt.
##### [[Main/Noter/Systemudvikling/Smart_Mål#Målbart\|M]]
Det er [[Main/Noter/Systemudvikling/Smart_Mål#Målbart\|målbart]] da det er tydeligt efter eksaminationen at jeg har fået over eller under 7.

##### [[Main/Noter/Systemudvikling/Smart_Mål#Attraktivt\|A]]
Det er [[Main/Noter/Systemudvikling/Smart_Mål#Attraktivt\|attraktivt]] da en karakter som 7 vil gøre mig faglig stolt.

##### [[Main/Noter/Systemudvikling/Smart_Mål#Realistisk\|R]]
Det er [[Main/Noter/Systemudvikling/Smart_Mål#Realistisk\|realistisk]] da jeg før har fået karakterer i  dette niveau.

##### [[Main/Noter/Systemudvikling/Smart_Mål#Tidsbestemt\|T]]
Det er [[Main/Noter/Systemudvikling/Smart_Mål#Tidsbestemt\|tidsbestemt]] da der er en meget præcis dato for eksaminationen

#### Hvad så nu?
Nu hvor mit [[Opsummering af 4. semester#implementering af Smart_Mål SMART mål\|overordnede mål]] var sat på plads som et [[Main/Noter/Systemudvikling/Smart_Mål\|SMART mål]] kunne jeg nu begynde at dele min vej op i delmål for at nå mine læringsmål for hhv. [[Main/4. Semester/Læringsmål/Microservices læringsmål\|microservices]]og [[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål\|It-Sikkerhed]].

Jeg fik brudt det ned i del mål som helt lav praktisk mundede ud i de opgaver jeg har på min todo liste hver dag til dette er redskabet [Todoist](https://todoist.com/) blevet brugt.

Når opgaverne er bundet sammen med det overordnede mål bliver det utroligt motiverende at få lavet dem. Kontra de opgaver som [[Main/Noter/Getting things done\|Getting things done]] metoden bragte på banen, som var opgaver der blot skulle udføres.

---
Nedenunder er her en liste over de uger jeg har indført i læringsplanen.
[[Main/4. Semester/Læringsplan/33_34\|Uge 33 - 34]]
[[Main/4. Semester/Læringsplan/35_36\|Uge 35 - 36]]
[[Main/4. Semester/Læringsplan/37_38\|Uge 37 - 38]]
[[Main/4. Semester/Læringsplan/39_40\|Uge 39 - 40]]
[[Main/4. Semester/Læringsplan/41_42\|Uge 41 - 42]]
[[Main/4. Semester/Læringsplan/43_44\|Uge 43 - 44]]