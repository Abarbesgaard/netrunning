---
{"dg-publish":true,"permalink":"/main/noter/programmering/jwt-token/","created":"2024-11-04T09:36:53.983+01:00"}
---

> [!important] hvad er et JWT token?
> JWT (JSON Web Token) er en åben standard til sikker overførsel af information mellem forskellige systemer som signerede JSON-objekter [1](https://workos.com/blog/json-web-tokens) [3](https://en.wikipedia.org/wiki/JSON_Web_Token).


![Pasted image 20241121092639.png](/img/user/Resource/98_Images/Pasted%20image%2020241121092639.png)
*Billedet er fra [SuperTokens](https://supertokens.com/blog/what-is-jwt)*
## Dele i et JWT Token
Et JWT består af tre dele:

1. **Header**: Indeholder information om tokentypen og den anvendte signeringsalgoritme.
2. **Payload**: Indeholder claims eller JSON-objektet med den information, der skal overføres.
3. **Signatur**: En kryptografisk genereret streng, der bruges til at verificere tokenets integritet [2](https://supertokens.com/blog/what-is-jwt) [3](https://en.wikipedia.org/wiki/JSON_Web_Token).

JWTs bruges primært til:

- **Autentificering**: Efter login inkluderes JWT'en i efterfølgende forespørgsler for at give adgang til beskyttede ressourcer [4](https://jwt.io/introduction).
- **Informationsudveksling**: JWT'er muliggør sikker overførsel af information mellem parter, da de kan signeres og verificeres [4](https://jwt.io/introduction).

JWTs er selvstændige og *stateless*, hvilket betyder, at al nødvendig information er indeholdt i selve tokenet. Dette eliminerer behovet for at gemme sessionsdata på serveren og muliggør effektiv autentificering på tværs af [[Main/Noter/Programmering/Distribuerede systemer\|distribuerede systemer]] [2](https://supertokens.com/blog/what-is-jwt).