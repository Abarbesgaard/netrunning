---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-02-microservice/","dgEnableSearch":true,"created":"2024-10-02T09:21:54.218+02:00"}
---


Dette er det første indlæg i det nye format.

I forhold til [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]].

Jeg har truffet den beslutning ikke at gøre vores afleverede produkt til en #Microservice, da projektets størrelse ikke udgør en berettigelse til at implementere den #Arkitektur. Dog har jeg valgt at benytte en #APIGateway, men mere om det senere.

## Overvejelser og Reflektioner
Mine overvejelser har taget udgangspunkt i det domæne og de brugere som skal bruge systemet. 

Den belastning som vil komme på systemet fra omkring *20 brugere*. Vil ikke udgøre det store. En #Monolit, som jeg på nuværende tidpunkt har implementeret, vil sagtens kunne løse denne udfordring.

På nuværende tidspunkt er systemet sat op på den måde, som er illustreret i billedet neden for:
![Vitahus, overblik.png](/img/user/Excalidraw/Vitahus,%20overblik.png) 

## API Gateway
Jeg har lavet en #APIGateway, som vil håndtere alle indgående kald from kommer fra fronten. Denne gateway vil håndtere #Autorisation og #Autentifikation, samt lede trafikken hen til rette service. 

> Og siden der kun er én service vil dette ikke være den store udfordring.

### Hvorfor lave en Gateway?
En grund til at lave en #APIGateway var, at lave 1 interface, som front skulle forholde sig til.

En anden grund var, at flytte alt #Autorisation og #Autentifikation væk fra service'en. Så ville services kun stå for at bekræfte det JWT token som kommer ind i systemet.

## Service'en
Hvis vi kigger ind i den store service kasse ser den sådan ud:
![Vitahus, Big_Service.png](/img/user/Excalidraw/Vitahus,%20Big_Service.png)

Den består lige nu af 3 controllers, hhv: en **Video**-, en **Activity**- og en **Identity** Controller.

Den som stikker ud her, er *Identity Controlleren*, som vi bruger til at bekræfte det JWT token der er kommet ind i systemet via vores #APIGateway. 

De to andre 'controllere' bruges til at behandle den data der kommer ind i systemet via den front der bliver lagt på.

Det data der kommer fra Controllerene rammer først en generisk service og derefter en generisk repository.

Grunden til at de er generiske er at det gør det væsentlig lettere at lave nye ændringer i systemet, da det egentlig "kun" er modellen, en controller og dto'er man skal forholde sig til. Men også at det ikke på nuværende tidspunkt har været nødvendigt at lave komplekse behandlinger af det data der kommer ind i systemet. 

> "Any fool can write code that a computer can understand. Good programmers write code that humans can understand."

— _Martin Fowler, Refactoring_


## Læringsmål i spil
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§1\|Microservices: Viden §1]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§2\|Microservices: Viden §2]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§3\|Microservices: Viden §3]]

[[Main/4. Semester/Læringsmål/Microservices læringsmål#§5\|Microservice: Færdighed §5]]
[[Main/4. Semester/Læringsmål/Microservices læringsmål#§6\|Microservice: Færdighed §6]]

[[Main/4. Semester/Læringsmål/Microservices læringsmål#§9\|Microservice: Kompetencer §9]]

