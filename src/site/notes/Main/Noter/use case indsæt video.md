---
{"dg-publish":true,"permalink":"/main/noter/use-case-indsaet-video/","created":"2024-11-01T10:04:48.239+01:00"}
---

---
### Use Case: Indsæt Video

**Use Case ID:** UC-001  
**Use Case Navn:** Indsæt Video  
**Aktør:** Bruger

#### Beskrivelse

Brugeren logger ind på applikationen og indsætter en video.

#### Forudsætninger

- Brugeren har en konto i applikationen.
- Brugeren har adgang til internettet.
- Applikationen er tilgængelig og fungerer korrekt.

#### Postbetingelser

- Videoen er gemt i applikationen og kan tilgås af brugeren og eventuelt andre brugere, afhængig af applikationens delingsindstillinger.

#### Hovedscenarie

1. **Bruger åbner applikationen.**
    
    - Applikationen præsenterer en login-skærm.
2. **Bruger indtaster login-oplysninger.**
    
    - Bruger indtaster brugernavn og adgangskode.
3. **Bruger klikker på 'Log ind'-knappen.**
    
    - Systemet validerer login-oplysningerne.
4. **Systemet bekræfter login.**
    
    - Brugeren bliver sendt til hovedskærmen i applikationen.
5. **Bruger vælger 'Indsæt video'-mulighed.**
    
    - Applikationen viser en formular for videoindsendelse.
6. **Bruger indtaster videooplysninger.**
    
    - Brugeren angiver titel, beskrivelse og uploader videofilen.
7. **Bruger klikker på 'Indsend video'-knappen.**
    
    - Systemet uploader videoen og gemmer oplysningerne i databasen.
8. **Systemet bekræfter videoindsendelse.**
    
    - Applikationen viser en besked om, at videoen er blevet indsat.

#### Alternative Scenarier

- **A1:** Bruger indtaster ugyldige login-oplysninger.
    - Systemet viser en fejlmeddelelse og beder brugeren om at prøve igen.
- **A2:** Bruger vælger at nulstille adgangskoden.
    - Systemet sender en nulstillingslink til brugerens registrerede e-mail.
- **A3:** Videoindsendelsen fejler (f.eks. på grund af netværksproblemer).
    - Systemet viser en fejlmeddelelse, og brugeren får mulighed for at prøve igen.

### Noter

- Overvej at inkludere sikkerhedsfunktioner, som f.eks. tofaktorgodkendelse, for at forbedre sikkerheden under login-processen.
- For videoindsendelsen kan der implementeres krav til videofilens format og størrelse.