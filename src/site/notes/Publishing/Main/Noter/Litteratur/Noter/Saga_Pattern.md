---
{"dg-publish":true,"permalink":"/publishing/main/noter/litteratur/noter/saga-pattern/","title":"Saga Pattern","tags":["læringsmål","systemudvikling","projektarbejde","programmering"],"created":"2024-09-06T08:17:28.852+02:00"}
---


## Problem

Hvordan implementerer man transaktioner, der spænder over flere tjenester, når
hver tjeneste har sin egen database?

## Løsning

Implementér transaktioner som **sagas**. En saga er en sekvens af lokale
transaktioner, hvor hver transaktion:

1. Opdaterer sin database.
2. Udsender en besked eller hændelse for at udløse den næste lokale
transaktion i sagaen.

Hvis en lokal transaktion fejler, udfører sagaen kompenserende transaktioner
for at rulle ændringer tilbage.

## Koordineringsmetoder

### 1. Choreography

- **Beskrivelse**: Tjenester kommunikerer via domænehændelser uden en central
koordinator.
- **Eksempel**:
  1. **Order Service** modtager `POST /orders` og opretter en ordre i PENDING-tilstand.
  2. Udsender `Order Created` hændelse.
  3. **Customer Service** forsøger at reservere kredit og sender
  `Credit Reserved` eller `Insufficient Credit` hændelse.
  4. **Order Service** godkender eller afviser ordren baseret på kreditreservations-resultatet.

- **Fordele**:
  - Decentraliseret kontrol.
  - Mindre kompleksitet med en central koordinator.

- **Ulemper**:
  - Sværere at administrere og fejlfinde.
  - Kræver robust hændelseshåndtering.

### 2. Orchestration

- **Beskrivelse**: En central orchestrator styrer sagaens flow og sender
kommandoer til tjenesterne.
- **Eksempel**:
  1. **Order Service** modtager `POST /orders` og opretter en orchestrator.
  2. Orchestrator opretter ordre i PENDING-tilstand.
  3. Sender `Reserve Credit` kommando til **Customer Service**.
  4. **Customer Service** sender svar tilbage (success eller failure).
  5. Orchestrator godkender eller afviser ordren baseret på svar.

- **Fordele**:
  - Centraliseret kontrol.
  - Klar sekvens af handlinger.

- **Ulemper**:
  - Potentielt enkelt fejlpunkt.
  - Kræver vedligeholdelse af orchestratorens logik.

## Håndtering af Resultater

### Metoder

1. **Øjeblikkelig Svar**: Tjenesten svarer, når sagaen er afsluttet.
2. **Polling**: Klienten modtager `orderID` og tjekker status periodisk.
3. **Hændelsesmeddelelse**: Klienten modtager `orderID` og en hændelse
(f.eks. via WebSocket) når sagaen er afsluttet.

### Overvejelser

- **Øjeblikkelig Svar**: God til kortvarige sagaer, men kan være kompleks.
- **Polling**: Enkel, men kan føre til ekstra belastning.
- **Hændelsesmeddelelse**: Effektiv for langvarige sagaer, kræver realtids-hændelseshåndtering.

## Fordele ved Sagas

- Opretholder datakonsistens uden distribuerede transaktioner.
- Tillader komplekse distribuerede arbejdsforløb.

## Ulemper ved Sagas

- Manglende automatisk rollback; kræver design af kompenserende transaktioner.
- Manglende isolation kan føre til dataanomalier; kræver ekstra designovervejelser.

## Problemer at Adressere

- **Pålidelighed**: Atomisk opdatering af database og meddelelser.
- **Klientinteraktion**: Vælg passende metode for at bestemme sagaens resultat.
