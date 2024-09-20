---
{"dg-publish":true,"permalink":"/main/teknologi/tcp/","title":"TCP","hide":true,"tags":["Web_Design","Web_Development"],"created":"2024-09-20T10:05:41.514+02:00"}
---

## Kilder

[TCP vs UDP Comparison](https://www.youtube.com/watch?v=uwoD5YsGACg)
[TCP Explained](https://study-ccna.com/tcp-explained/)
[TCP - 3 way handshake](https://www.youtube.com/watch?v=xMtP5ZB3wSk)
[What Is a Three-Way Handshake in TCP?](https://www.youtube.com/watch?v=LyDqA-dAPW4)
[TCP connection walkthrough | Networking tutorial (13 of 13)](https://www.youtube.com/watch?v=F27PLin3TV0)
[TCP: Flow Control and Window Size](https://www.youtube.com/watch?v=4l2_BCr-bhw)

## **Sammenligning af TCP vs. UDP**

**TCP** (Transmission Control Protocol) og **UDP** (User Datagram Protocol) er to
forskellige protokoller, der anvendes i internetkommunikation. Mens begge
disse protokoller har til formål at lette datatransmission, har de
forskellige egenskaber, der gør dem egnede til forskellige anvendelser.

## **TCP Forklaret**

**TCP** er en pålidelig, forbindelsesorienteret protokol, der bruges til at overfør
e data på internettet. Den sikrer pålidelig levering af data ved at etablere en
forbindelse mellem afsenderen og modtageren, opdage og håndtere fejl under
transmission og sikre, at data ankommer i den rigtige rækkefølge.

## **TCP - Trevejshåndtrykket**

Trevejshåndtrykket er en vigtig del af den proces, hvor en TCP-forbindelse
oprettes mellem to enheder. Det indebærer tre trin: Først sender den ene
enhed (klienten) en anmodning om at oprette forbindelse til den anden enhed
(serveren). Derefter svarer serveren med en accept til klientens anmodning.
Endelig sender klienten en bekræftelse tilbage til serveren. Denne proces
etablerer en pålidelig forbindelse mellem de to enheder, før dataoverførslen
begynder.
![3wayhandshake.png](/img/user/Main/Images/3wayhandshake.png)

## **Gennemgang af TCP-forbindelse**

En TCP-forbindelse indebærer flere trin for at overføre data fra en kilde til
en destination. Først etableres en forbindelse mellem klienten og serveren ved
hjælp af trevejshåndtrykket. Derefter sendes data fra klienten til serveren i
separate segmenter, der indeholder en sekvensnummerering for at sikre, at data
ankommer i den rigtige rækkefølge. Serveren sender derefter en kvittering
tilbage til klienten for at bekræfte modtagelsen af hvert segment. Når alle
data er overført, lukker begge parter forbindelsen.

Disse processer og protokoller er afgørende for effektiv datakommunikation på
internettet og spiller en central rolle i opbygningen af pålidelige
netværksapplikationer og -tjenester.
