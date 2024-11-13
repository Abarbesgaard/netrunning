---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-11-12-truselsmodel/","created":"2024-11-12T08:20:03.871+01:00"}
---

## "I gamle dage"

Den tilgang jeg har læst meget om i forhold til en traditionel monolittisk applikation er:
 
 > the walled garden (Markeret med en rød linje)
 
 ```plantuml
 rectangle "The wall" #Line:Red;Line.Bold {
 package APP
 }
 ```

Alt der skulle snakke med appen ude fra skulle igennem muren først. Men når man så var forbi muren var der dømt "fri leg".

Dette er efterhånden en saga blot.

Fordet første kan appen nu være distribueret hvilket gør at muren som dækkede **hele** vejen rundt om **hele** appen nu kun indeholder en del af appen.

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

## Nye tilgange 
I en *distribueret app* som vi har lavet i vores [[Main/4. Semester/VitaHus/Projekt VitaHus\|projekt]] løste vi denne nye udfordring med følgende tiltag

Vi startede med at gå væk fra konceptet om en "Walled Garden" og i stedet bevæge os mod en mere moderne tilgang.

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
1. Vi implementerede *Authentication* og *Authorization* i [[Main/Noter/API-Gateway\|gateway]]
2. Vi udliciterede ansvaret for bruger oprettelse og administration af dette til [[Main/Noter/Supabase\|Supabase]].

## Authentication og Authorization
Vi sørgede for at når der kom et kald til vores [[Main/Noter/API-Gateway\|gateway]]så skulle det være autoriseret for at kunne benytte sig af vores endpoints. 
I forhold til [OWASP API top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/) så rammer denne tilgang flere af punkterne i top 10'en.
Blandt andet:
[[Main/Noter/Vita/Vita Broken Authentication\|Broken Authentication]]
[[Main/Noter/Vita/Vita Broken Function Level Authorization\|Broken Function Level Authorization]]
[[Main/Noter/Vita/Vita Broken Object level Authorization\|Broken Object level Authorization]]

### Forbedringer
Der hvor vi kunne gøre det bedre var at præcisere endnu mere i forhold til hvad det er for data som den specifikke bruger skal have rettighed til når de laver et kald.
Er det nok som almindelig bruger at have adgang til dto'er?

Dette vil gøre at vi levede bedre op til [OWASP API top 10](https://owasp.org/API-Security/editions/2023/en/0x11-t10/).

## Supabase
I starten af vores [[Main/4. Semester/VitaHus/Projekt VitaHus\|projekt]]brugte vi [[Main/Noter/Auth0\|Auth0]], til at holde styr på Auth-delen af vores projekt. Vi fandt dog ud af at [[Main/Noter/Auth0\|Auth0]]er brugbart hvis man ønsker at appen skal kunne tilgå på en anden måde en vi ønskede.
Derfor skiftede vi til at benytte [[Main/Noter/Supabase\|Supabase]]i stedet. 
Vores Frontend team implementerede en reroute i vores front  der fik lavet en [[Main/Noter/JWT token\|JWT token]]hos [[Main/Noter/Supabase\|Supabase]]som vi så brugte til at verificere brugeren i vores[[Main/Noter/API-Gateway\|gateway]].

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
Ud fra ovenstående kan man argumentere for at vi har benyttet os af princippet **Zero trust**. Dette er mere held end en faktisk overvejelse.

## Tanker og Refleksioner
Meget af det jeg har læst om it sikkerhed i og omkring microservices har været meget omfattende. 
Dette bakkes op i bogen af Building Microservices af Sam Newman. Han udtrykker det på følgende måde:

> Overlad det du kan overlade - til andre.

Med dette mener han at microservices er sådan et bæst at arbejde med at hvis man selv skulle lave alt fra bunden vil det hurtigt kunne blive alt for stor og ikke mindst **dyr** en mundfuld.
### Gateway
For eksempel med den [[Main/Noter/API-Gateway\|gateway]] jeg har opsat til projektet, er meget funktionel og sikkerhedsmæssigt skrabet. Så hvorfor ikke benytte sig af nogen der har lavet en super løsning allerede?

> [!Note] Gateways
> Kong
> Amazon API gateway
> Azure
> Google Cloud

Ovenstående har allerede gode løsninger der kan tage hånd om flere af de udfordringer vi allerede er stødt på i vores app, rent sikkerhedsmæssigt.

Ved at udlicitere ansvaret for den del af vores app til en ekstern provider vi vi hurtigere kunne komme frem til den **værdi** som vores kunde har efterspurgt.

### IT-Sikkerhed fra start
Vi brugte feature driven design fra start og forsøgt så hurtigt som muligt at få skabt en MVP i forhold til at få skabt den **værdi** som kunden ønskede.

> Set fra et sikkerhedsperspektiv, er dette ikke optimalt. 

Men i forhold til min læring vidste jeg ikke bedre. Jeg startede med at lære om microservice arkitektur og havde i denne sammenhæng ikke fokus på sikkerheden i systemet. 

Sikkerheds aspektet kom først senere og da det kom var der store dele af systemet der skulle laves om. 

