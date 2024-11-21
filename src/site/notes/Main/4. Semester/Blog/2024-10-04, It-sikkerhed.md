---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-04-it-sikkerhed/","hide":true,"created":"2024-10-04T08:20:18.569+02:00"}
---

I forhold til IT sikkerhed har jeg gået lidt rundt om den varme grød og ikke rigtig vidst hvordan jeg skulle starte på det projekt. 

Jeg forsøgte mig med at lave en traditionel vinkel på #ItSikkerhed - Cyber Security. Men dette føltes ikke som den sti jeg gerne vil ned ad. 

Så jeg er istedet gået i den retning der har hovedsageligt med sikkerheden i systemet at gøre og ikke så meget det at "hacke" sig ind i systemet

Det at kunne svare på spørgsmålet:

> Hvor meget skal til for at gøre en API/Microservice så sikker som muligt?

Syntes jeg lyder mere interessant.

Dette betyder dog en lettere omskrivelse af mine læringsmål så de i højere grad vil deje sig om dette emne.

I forhold til [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]] , så har jeg haft denne nye tilgang til projektet.

Jeg har taget tilgangen [[Main/Noter/Defence in Depth\|Defence in Depth]] til mig og integreret en umiddelbar #Autentifikation når man rammer vores gateway. Men også hver gang en HTTP get metode benyttes i en controller vil de bekræfte den JWT token der er kommet ind samt de rettigheder denne token bærer med sig.
Dette diagram viser et overblik over flowet:
![It Sikkerhed, Gateway flow.png](/img/user/Excalidraw/It%20Sikkerhed,%20Gateway%20flow.png)

### Læringsmål i spil
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§1\| It-Sikkerhed: Viden §1]]
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§4\| It-Sikkerhed: Viden §4]]
[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§5\| It-Sikkerhed: Viden §5]]

[[Main/4. Semester/Læringsmål/It-Sikkerhedslæringsmål#§8\| It-Sikkerhed: Færdigheder §8]]
