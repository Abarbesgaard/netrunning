---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-02-microservice/","hide":true,"created":"2024-10-02T09:21:54.218+02:00"}
---


Dette er det første indlæg i det nye format.

I forhold til [[Main/4. Semester/VitaHus/Projekt VitaHus\|Projekt VitaHus]].

Jeg har truffet den beslutning ikke at gøre det til en #Microservice, da projektets størrelse ikke udgør en stor nok belastning til at kunne berettige den #Arkitektur. Dog har jeg valgt at benytte en #APIGateway, men mere om det senere.

Mine overvejelser har taget udgangspunkt i det domæne og de brugere som skal bruge systemet. 

Den belastning som vil komme på systemet fra omkring 20 brugere. Vil ikke udgøre det store. En #Monolit, som jeg på nuværende tidpunkt har implementeret, vil sagtens kunne løse denne udfordring.

På nuværende tidspunkt er systemet sat op på den måde som er illustreret i billedet neden for:

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data
## Text Elements
Front 
API
Gateway 
Service 
Database 


</div></div>


Der er en #APIGateway, som vil håndtere alle indgående kald from kommer fra fronten. Denne gateway vil håndtere #Autorisation og #Autentifikation, samt lede trafikken hen til rette service. 
