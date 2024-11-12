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



