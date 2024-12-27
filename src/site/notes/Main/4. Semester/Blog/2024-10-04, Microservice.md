---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-04-microservice/","hide":true,"created":"2024-10-04T10:03:11.700+02:00"}
---

Dette er det første spade stik på  vejen til at gøre [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]] til en #Microservice e arkitektur.

Alt hvad jeg har læst indtil videre har på det kraftigste udtrykket, at et skift til en sådan arkitektur kan bringe flere fordele med sig men også rigtig mange udfordringer, som man skal forhold sig til som udvikler/firma.

## Refleksioner
Dette afsnit kan hurtigt blive enormt når det kommer til de overvejelser man bør gøre sig ved et skift til #Microservices . Derfor vil jeg skrive om det løbende i takt med at jeg rammer de forskellige elementer. 

Følgende er ikke en rækkefølge som overvejelserne skal gøres i men et udtryk for de overvejelser man bør gøre sig:

### Hvordan skal man dele Vita hus op?
Det første jeg vil have fokus på er at få delt vores nuværende #Monolit op, men at gøre dette kan allerede bringe en del spørgsmål med sig:

- Skal man skille #Monolitten ad i de controllere der allerede er defineret?
- Skal man skille den ad i #Domæner 
- Er der intern Coupling i #Monolitten som vi ikke har taget højde for?

## Opdel med et mål
Det implementere en #Microservice skal være et bevist valg i følge Sam Newman (Forfatteren til bogen Building Microservices). Et citat fra bogen lyder:

> Microservices aren’t easy. Try the simple stuff first.

Med dette in mente er jeg glad for at vore monolit ikke er kæmpe stor.
I følge forfatteren er det rigtige at gøre at gå til sådan et projekt med `domain driven design`, og at gøre det i små bidder. 
I følge Martin Fowler:

> If you do a big-bang rewrite, the only thing you’re guaranteed of is a big bang.

Et skift til Microservice, skal være velbegrundet og gennemtænkt. Det skal opvejes fordele og ulemper. 

## Fra monolit til microservice

Nu leger jeg med tanken om at [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]]får rigtig meget med vind og brugerne strømmer til deres produkt. 
Et skift til microservice er ikke kun det rigtige valg men også en nødvendighed for at kunne håndtere alle de kald til deres nuværende #Monolit. Hvis ikke de skifter vil deres brugere få en dårlig oplevelse med produktet og skifte til en anden løsning.

Så...

På nuværende tidpunkt ser Monolitten sådan ud:

![Vitahus, monolit.png](/img/user/Excalidraw/Vitahus,%20monolit.png)

Når den skal deles op er der som sagt flere måde at gøre det på:
1. Data først
2. Kode først

I følgende eksempel vi jeg tage udgangspunkt i at vores funktionalitet med at gemme Videoer bliver taget ud først fra Monolitten
### Data først
Hvis valget bliver data først vil dette diagram vise fremgangsmåde:
![Vitahus, monolit dataførst.png](/img/user/Excalidraw/Vitahus,%20monolit%20dataf%C3%B8rst.png)


### Kode først
Hvis valget bliver kode først vil dette diagram vise fremgangsmåde:
![Vitahus, monolit Kode først.png](/img/user/Excalidraw/Vitahus,%20monolit%20Kode%20f%C3%B8rst.png)

Der er også andre metoder så som [[Main/Noter/Programmering/Strangler fig pattern\|Strangler fig pattern]], [[Main/Noter/Programmering/Parallel Run\|Parallel Run]] og [[Main/Noter/Programmering/Feature Toggle\|Feature Toggle]]. Men disse er uden for scope, da vores system ikke er så stort endnu og det er et tænkt scenarie.

Og med dette in mente vil jeg starte dette projekt med - kode først.


## Læringsmål i spil
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§1\| Microservices: Viden §1]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§2\| Microservices: Viden §2]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§6\| Microservices: Færdigheder §6]]
