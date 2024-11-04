---
{"dg-publish":true,"permalink":"/main/noter/jwt-token/","created":"2024-11-04T09:36:53.983+01:00"}
---

Et JWT (JSON Web Token) er et kompakt, URL-venligt tokenformat, der bruges til sikker overførsel af oplysninger mellem to parter. JWT består af tre dele: header, payload og signature.

- **Header** indeholder metadata om tokenet, som typisk angiver algoritmen, der bruges til signaturen.
- **Payload** indeholder selve dataen (claims), som kan være information om brugeren, autorisationsniveauer, og andre brugerdefinerede data.
- **Signature** bruges til at bekræfte, at tokenet ikke er blevet ændret undervejs og er baseret på header, payload, og en hemmelig nøgle eller et privat certifikat.

JWT bruges ofte til autentificering og autorisation i webapplikationer og API'er, hvor serveren kan validere brugerens identitet uden at gemme sessioner.