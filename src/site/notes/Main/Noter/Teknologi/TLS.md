---
{"dg-publish":true,"permalink":"/main/noter/teknologi/tls/","created":"2024-11-11T13:14:12.920+01:00"}
---

```plantuml
autonumber "[000]"
participant Client

participant Server
== TCP Handshake ==
Client ->(10) Server : TCP SYN
Client (10)<- Server : TCP SYN + ACK
Client ->(10) Server : TCP ACK
... Connection Established ...
== Certificate Check ==
Client ->(10) Server : Client Hello
Client (10)<- Server : Server Hello
Client (10)<- Server : Certificate
Client (10)<- Server : Server Hello Done
== Key Exchange ==
Client ->(10) Server : Client Key Exchange 
note across: session key bliver encrypted med Server public key 
Client ->(10) Server : Change Cipher Spec
note across: Session key bliver decrypted med Server Private key
Client (10)<- Server : Change Cipher Spec
Client (10)<- Server : Finished
== Data Transmission ==
Client ->(10) Server:  Encrypted Data
... Session Key ...
Client (10)<- Server: Encrypted Data
```

### TCP Handshake

001: **Client -> Server: TCP SYN**  
Klienten sender en **SYN**-pakke for at initiere en **TCP**-forbindelse til serveren.
   
002: **Server <- Client: TCP SYN + ACK**  
Serveren svarer med både en **SYN** (for at anerkende forbindelsen) og en **ACK** (for at bekræfte modtagelsen af klientens SYN-pakke).
   
003: **Client -> Server: TCP ACK**  
Klienten sender en **ACK**-pakke tilbage for at fuldende den trevejs TCP-handshake. 

***Forbindelsen er nu etableret.***
   

### Certificate Check

004: **Client -> Server: Client Hello**  
Klienten sender en `Client Hello` for at starte *SSL/TLS handshake*, inklusive oplysninger om understøttede *krypteringsprotokoller*.
   
005: **Server <- Client: Server Hello**  
Serveren svarer med et `Server Hello`, som vælger en krypteringsmetode baseret på klientens muligheder.
   
006: **Server <- Client: Certificate**  
Serveren sender sit **SSL/TLS-certifikat** til klienten, som indeholder serverens *offentlige nøgle* og *identitetsoplysninger*.
   
007: **Server <- Client: Server Hello Done**  
Serveren indikerer, at den er færdig med sin del af handshake og venter på klientens respons.
   

### Key Exchange

008: **Client -> Server: Client Key Exchange**  
Klienten sender en hemmelig nøgle (session key) til serveren krypteret med serverens offentlige nøgle.
   
009: **Client -> Server: Change Cipher Spec**  
Klienten indikerer, at den vil begynde at bruge *den nye krypteringsalgoritme* og **session key** til al efterfølgende kommunikation.

010: **Client -> Server: Finished**  
Klienten sender en `Finished`-meddelelse som en verifikation af, at den har gennemført handshake korrekt.
   
011: **Server <- Client: Change Cipher Spec**  
Serveren skifter også til den nye *krypteringsalgoritme og session key.*

012: **Server <- Client: Finished**  
Serveren bekræfter, at den har modtaget klientens handshake-meddelelser og at handshake er fuldført.
   

### Data Transmission

013: **Client -> Server: Encrypted Data**  
Klienten sender krypterede data til serveren ved hjælp af session key. Begge parter har nu etableret en sikker kommunikationskanal.

014: **Server <- Client: Encrypted Data**  
Serveren sender krypterede data tilbage til klienten.