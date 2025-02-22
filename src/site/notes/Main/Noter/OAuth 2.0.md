---
{"dg-publish":true,"permalink":"/main/noter/o-auth-2-0/","created":"2024-11-21T09:55:57.894+01:00"}
---

> [!important] Hvad er OAuth 2.0
> OAuth 2.0 er en **autorisationsprotokol**, der giver tredjepartsapplikationer begrænset adgang til brugerdata på andre tjenester uden at kende brugerens adgangskode [1](https://auth0.com/intro-to-iam/what-is-oauth-2) [5](https://itconfidence.dk/encyclopedia/oauth/) [6](https://cybermonkey.dk/cyberpedia/oauth-2-0-en-moderne-standard-for-sikker-adgang).


![Pasted image 20241121095748.png](/img/user/Resource/98_Images/Pasted%20image%2020241121095748.png)
*Billedet er fra [Prismatic](https://prismatic.io/docs/getting-started/oauth2/what-is-oauth2/)*

Den erstattede OAuth 1.0 i 2012 og er nu industristandarden for online autorisation [1](https://auth0.com/intro-to-iam/what-is-oauth-2).
Hovedprincipperne for OAuth 2.0 inkluderer:

1. Det er en autorisationsprotokol, ikke en autentiseringsprotokol [1](https://auth0.com/intro-to-iam/what-is-oauth-2).
2. Den bruger adgangstokens til at give adgang til ressourcer [1](https://auth0.com/intro-to-iam/what-is-oauth-2).
3. Den definerer forskellige roller som klient, ressourceejer, autorisationsserver og ressourceserver [1](https://auth0.com/intro-to-iam/what-is-oauth-2).
4. Den bruger "scopes" til at specificere præcis hvilke ressourcer der gives adgang til [1](https://auth0.com/intro-to-iam/what-is-oauth-2).

**OAuth 2.0** fungerer ved at klienten (f.eks. en mobilapp eller hjemmeside) anmoder om autorisation fra autorisationsserveren. Efter godkendelse udstedes et *adgangstoken*, som klienten kan bruge til at få adgang til beskyttede ressourcer på ressourceserveren [1](https://auth0.com/intro-to-iam/what-is-oauth-2).

Protokollen er designet til at være fleksibel og kan bruges af forskellige typer applikationer, herunder webapplikationer, mobilapps og desktopapplikationer [2](https://oauth.net/2/).