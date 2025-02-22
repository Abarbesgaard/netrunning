---
{"dg-publish":true,"permalink":"/publishing/main/noter/programmering/zero-trust/","created":"2024-11-15T10:23:17.679+01:00"}
---

> [!important] Opsummering 
> Zero Trust er en sikkerhedsmodel og -strategi, der bygger på princippet om aldrig at stole på nogen eller noget som standard, hverken inden for eller uden for organisationens netværk. Her er de vigtigste aspekter af Zero Trust:

![Pasted image 20241115102445.png](/img/user/Resource/98_Images/Pasted%20image%2020241115102445.png)
*Billedet er fra [Mad devs](https://maddevs.io/blog/what-is-zero-trust-network-architecture/)*

## Kilder
1. [CloudFlare](https://www.cloudflare.com/learning/security/glossary/what-is-zero-trust/)
2. [Google](https://cloud.google.com/learn/what-is-zero-trust)
3. [Microsoft](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview?WT_mc_id=academic-0000-abartolo)
## Grundlæggende koncept

Zero Trust-modellen er baseret på idéen om, at ingen enhed, bruger eller netværk automatisk bør betragtes som pålidelig. Mottoet er "Never trust - always verify" [1](https://cloud.google.com/learn/what-is-zero-trust)[4](https://en.wikipedia.org/wiki/Zero_trust_security_model).

## Nøgleprincipper

1. **Eksplicit verifikation**: Alle brugere, enheder og komponenter skal autentificeres og autoriseres baseret på *alle tilgængelige datapunkter* [2](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview?WT_mc_id=academic-0000-abartolo).
2. **Least Privilege adgang**: Brugere får kun adgang til de ressourcer, de har brug for, når de har brug for dem (Just-In-Time og Just-Enough-Access) [2](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview?WT_mc_id=academic-0000-abartolo).
3. **Antag brud**: Systemet designes med antagelsen om, at der allerede er sket et sikkerhedsbrud [2](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview?WT_mc_id=academic-0000-abartolo).

## Implementering

Zero Trust implementeres gennem:

- Streng identitetsverifikation
- Kontinuerlig validering af enheders integritet
- Mikrosegmentering af netværket
- Kryptering af data både i transit og i hvile
- Anvendelse af princippet om mindst privilegeret adgang

## Fordele

- **Øget sikkerhed**: Reducerer risikoen for databrud og lateral bevægelse i netværket [3](https://www.cloudflare.com/learning/security/glossary/what-is-zero-trust/).
- **Bedre synlighed**: Giver bedre indsigt i trafik og aktiviteter på tværs af netværket [1](https://cloud.google.com/learn/what-is-zero-trust).
- **Tilpasningsevne**: Egnet til moderne, komplekse IT-miljøer med cloud-tjenester og mobil arbejdskraft [4](https://en.wikipedia.org/wiki/Zero_trust_security_model).

## Udfordringer

Implementering af Zero Trust kan være *kompleks* og kræve betydelige ændringer i eksisterende infrastruktur og processer. Det kan også medføre øgede omkostninger og potentielt påvirke brugeroplevelsen, hvis det ikke implementeres korrekt.

## Konklusion

Zero Trust er ikke blot et produkt eller en teknologi, men *en omfattende tilgang til sikkerhed*. Det kræver en fundamental ændring i tankegangen omkring netværkssikkerhed, hvor *tillid aldrig tages for givet,* men konstant skal optjenes gennem verifikation og kontekstbaseret adgangskontrol.