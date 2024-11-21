---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-11-12-truselsmodel/","created":"2024-11-12T08:20:03.871+01:00"}
---

## "I gamle dage"

Den sikkerhedsmæssige tilgang jeg har læst meget om i forhold til en traditionel monolittisk applikation er:
 
 > [the walled garden](https://www.techtarget.com/searchsecurity/definition/walled-garden) (Markeret med en rød linje)
 
 ```plantuml
 rectangle "The wall" #Line:Red;Line.Bold {
 package APP
 }
 ```


![Walled garden.png](/img/user/98_Images/Walled%20garden.png)
*Billedet er fra [propertylistings](https://propertylistings.ft.com/propertynews/united-kingdom/7284-wall-encompassing-a-short-history-of-the-walled-garden.html)*

Alt ekstern kommunikation med appen skulle først passere en sikkerhedsmur. Når denne var krydset, blev al trafik derefter betragtet som *pålidelig*, hvilket tillod *fri adgang internt* i systemet.

> Dette er efterhånden en saga blot.

For det første kan appen nu være [[Main/Noter/Distribuerede systemer\|distribueret]] hvilket gør at muren, som før dækkede **hele** vejen rundt om **hele** appen, nu kun indeholder en del af appen.

```plantuml
title Distribueret app
agent front1
agent front2
rectangle "The wall" #Line:Red;Line.Bold {
	agent API
}
front1 -- API
front2 -- API

```

*The walled garden* er ikke længere en brugbar metode
## En Ny tilgang
I en [[Main/Noter/Distribuerede systemer\|distribueret app]], som vi har lavet i vores [[Main/4. Semester/VitaHus/Projekt VitaHus\|projekt]] løste vi denne nye udfordring med følgende tiltag. 

> [!info] Arkitektur
> Vores app skulle både have en *App*, til telefonen, og en *hjemmeside*. Dermed var en [[Main/Noter/API\|API]] et godt valg, da den vil løse vores distribueringsproblematik.

Vi vidste allerede til at starte med grundet at vi skulle have et [[Main/Noter/Distribuerede systemer\|distribueret system]] at noget af sikkerheden vil ligge i en eventuel [[Main/Noter/API\|API]] og/eller en [[Main/Noter/API-Gateway\|API-Gateway]]
### Gateway
Vi benyttede os af en [[Main/Noter/API-Gateway\|API-Gateway]]for at skabe en fælles kontaktflade for de kald der opstod til den bagvedliggende [[Main/Noter/API\|API]] (og måske på sigt flere [[Main/Noter/API\|API'er]])

```plantuml
title Distribueret app
agent front1
agent front2
rectangle #Line:Red;Line.Bold {
	agent Gateway
}
rectangle #Line:Red;Line.Bold{
	agent API
}
front1 -- Gateway
front2 -- Gateway
Gateway - API

```

I vores [[Main/Noter/API-Gateway\|gateway]] gjorde vi følgende tiltag for at styrke sikkerheden i vores backend:
1. Vi implementerede en default  *Authentication* og *Authorization* i [[Main/Noter/API-Gateway\|gateway]]
2. Vi udliciterede ansvaret for bruger oprettelse og administration af dette til [[Main/Noter/Supabase\|Supabase]]. Vi vil senere bruge den [[Main/Noter/JWT token\|JWT token]] , som [[Main/Noter/Supabase\|Supabase]] laver, til at bekræfte brugerne gennem vores system.

#### Fordele ved Gateway'en
Fordelene ved at have en [[Main/Noter/API-Gateway\|gateway]] i vores projekt gør at vi kunne have et fælles sted hvor al trafikken ind i vores [[Main/Noter/API\|API]] kunne autoriseres. 

Vi vil kunne *load balance* vores strøm af trafik gennem systemet.

Vi vil kunne lave *bedre monitorering.*
#### Ulemperne ved Gateway'en
Der vil opstå et *single point of failure*.

Der vil opstå *øget kompleksitet*.

Den vil kunne *øge latency* og *sænke ydeevnen*.

*Versionering* kan blive en udfordring.

#### Refleksioner om gateway
Vi valgte at lave vores gateway selv. Til dels fordi at jeg skulle lære hvordan den bruges og opsættes. 
Et argument, og et godt et, kan være at udeligere ansvaret for dette til en tredjepart, her kommer store spillere ind som AWS, GOOGLE etc. på banen. Disse udbydere har services der kan lave en gateway løsning bedre end vi kan.

Men de er dog stadig lavet af mennesker(for nu), så i overvejelsen af hvilken tredjepart man indgår samarbejde med kan man overveje følgende:
- Hvordan leverer de sikkerheden i deres løsning?
- Hvilke muligheder er der for Autorisation og autentificering?
- Hvad er prismodellen?
- Er der funktioner som fx load balancing og caching?
- Bliver man bundet til udbyderen?

## Hvad ligger kunden værdi på?
Inden jeg går videre med implementeringen er det vigtigt at man som udvikler kan oplyse kunden om det *sikkerhedsudfordringer* som en app, som de ønsker, står over for.

Til dette kan man gøre brug af en risiko analyse:
![Pasted image 20241113081958.png](/img/user/98_Images/Pasted%20image%2020241113081958.png)
[*kilde: risikoanalyse fra center for ledelse*](https://www.cfl.dk/artikler/risikoanalyse)

> [!important] Pointe 
> Her vil man som udvikler kunne præsentere kunden for en stuktureret tilgang til hvordan sikkerheden i appen er truet allerede inden der er reel kode implementeret.

I vores tilfælde bruger vi som sådan ikke personfølsom data i vores [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]], men i tilfælde af at dette blev nødvendig vil en sikkerhedstrussel som dette emne sagtens kunne ende i det røde felt.

Dette vil dermed skabe en *prioritering* i forhold til hvad det er som skal sikres først i udviklingen af systemet og give kunden et *struktureret overblik* over sikkerheden/sårbarhederne i deres system inden koden er skrevet.

Dette vil gøre 3 ting:
1. Kunden vil føle sig sikker i forhold til samarbejdet med os som programmører.
2. Kunden vil kunne fokusere på det der giver værdi for dem.
3. Det vil være betydeligt billigere at udvikle appen.
## Authentication og Authorization
Vi sørgede for at når der kom et kald til vores [[Main/Noter/API-Gateway\|gateway]]så skulle det være autoriseret for at kunne benytte sig af vores endpoints. 
I forhold til [OWASP API top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/) så rammer denne tilgang flere af punkterne i top 10'en.
Blandt andet:
[[Main/Noter/Vita/Broken Authentication\|Broken Authentication]]
[[Main/Noter/Vita/Broken Function Level Authorization\|Broken Function Level Authorization]]
[[Main/Noter/Vita/Broken Object level Authorization\|Broken Object level Authorization]]

### Forbedringer
Der hvor vi kunne gøre det bedre var at præcisere endnu mere i forhold til hvad det er for data som den specifikke bruger skal have rettighed til når de laver et kald.
Det er en dialog som vi som udviklere skal tage tidligt i processes. Hvis dette ikke bliver gjort er der større tilbøjelighed til at gå med en *default* løsning for at få det til at fungere.

> Er det nok som almindelig bruger at have adgang til dto'er?

Dette vil gøre at vi levede bedre op til [OWASP API top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/).

## Supabase
I starten af vores [[Main/4. Semester/VitaHus/Projekt VitaHus\|projekt]]brugte vi [[Main/Noter/Auth0\|Auth0]], til at holde styr på Auth-delen af vores projekt. Vi fandt dog ud af at [[Main/Noter/Auth0\|Auth0]]er brugbart hvis man ønsker at appen skal kunne tilgå på en anden måde en vi ønskede.
Derfor skiftede vi til at benytte [[Main/Noter/Supabase\|Supabase]]i stedet. 
Vores Frontend team implementerede en route i vores front der fik lavet en [[Main/Noter/JWT token\|JWT token]]hos [[Main/Noter/Supabase\|Supabase]]som vi så brugte til at verificere brugeren i vores[[Main/Noter/API-Gateway\|gateway]].

```plantuml
actor user
participant front
participant gateway
participant api
participant Supabase

user -> front : Logger ind
front -> Supabase : bruger logger ind
Supabase -> front : JWT token retur
user -> front : Vis mig alle brugere, med JWT token
front -> gateway : vis all brugere, med JWT Token
gateway -> gateway : JWT claims bekræftes
gateway -> api : vis alle brugere, med JTW token
api -> api : Claims bekræftes
api -> user : data
```

Ud fra ovenstående kan man argumentere for at vi har benyttet os af princippet **[[Main/Noter/Zero Trust\|Zero Trust]]**. 

> [!INFORMATION] Hvad er [[Main/Noter/Zero Trust\|Zero Trust]]?
En sikkerhedsmodel, der går ud fra, at ingen brugere eller enheder kan stoles på – uanset om de befinder sig inden for eller uden for netværksperimeteren.

For vores vedkomne er dette mere held end en faktisk overvejelse.

## Tanker og Refleksioner
Meget af det jeg har læst om it sikkerhed i og omkring [[Main/Noter/Emner/Backend/Microservice\|microservices]] har været meget omfattende. 
Dette bakkes op i bogen af [Building Microservices af Sam Newman.](https://www.saxo.com/dk/building-microservices_sam-newman_paperback_9781492034025) Han udtrykker det på følgende måde for at lette byrden for programmører:

> Overlad det du kan overlade - til andre.

Med dette mener han at [[Main/Noter/Emner/Backend/Microservice\|microservices]] er sådan et bæst at arbejde med at hvis man selv skulle lave alt fra bunden vil det hurtigt kunne blive alt for *stor* og ikke mindst **dyr** en mundfuld.
### Gateway
Den [[Main/Noter/API-Gateway\|gateway]] jeg har opsat til projektet, implementeret med [[Main/Noter/Yarp\|Yarp]], er meget funktionel og sikkerhedsmæssigt utilstrækkelig. Så hvorfor ikke benytte sig af nogen der har lavet en løsning allerede?

> [!Note] Mulige tredjeparts udbydere
> Kong
> Amazon API gateway
> Azure
> Google Cloud

Ovenstående har allerede gode løsninger der kan tage hånd om flere af de udfordringer vi allerede er stødt på i vores app, rent sikkerhedsmæssigt.

Ved at udlicitere ansvaret for den del af vores app til en ekstern provider vi vi hurtigere kunne komme frem til den **værdi** som vores kunde har efterspurgt.

Vi vil hurtigere kunne levere en *MVP* som leverer den **værdi** som kunden har bedt om, og ikke mindst er mere sikker.

### IT-Sikkerhed fra start
Vi brugte *feature driven design* fra start og forsøgt så hurtigt som muligt at få skabt en *MVP* i forhold til at få skabt den **værdi** som kunden ønskede.

> Set fra et sikkerhedsperspektiv, er dette ikke optimalt. 

Men i forhold til min læring vidste jeg ikke bedre. Jeg startede med at lære om [[Main/Noter/Emner/Backend/Microservice\|microservice arkitektur]] og havde i denne sammenhæng ikke fokus på sikkerheden i systemet. 

Sikkerheds aspektet kom først senere, og da det kom var der store dele af systemet der skulle laves om. 


