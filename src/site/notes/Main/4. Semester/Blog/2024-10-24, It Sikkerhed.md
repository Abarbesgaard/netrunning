---
{"dg-publish":true,"permalink":"/main/4-semester/blog/2024-10-24-it-sikkerhed/","created":"2024-10-24T09:12:56.365+02:00"}
---


En fejl som mange godt kan falde i med It-Sikkerhed omkring microservices er at antage at blot fordi hoveddøren er låst med 4 forskellige typer af låse, overvåget at CCTV og vagthunde står klar. 
Er det ikke noget værd hvis vinduet bag huset står åbent.

I bogen **building microservices** af [[Main/Noter/Sam Newman\|Sam Newman]], kommer han ind på hvilke foranstaltninger man kan gøre sig i forhold til at skabe et sikkert microservice arkitektur.

Han fremlægger  følgende punkter som opmærksomhedpunkter, som han kalder `core principles` der vil hjælpe i arbejdet med sikkerhed i Microservices.

1. Princippet om `Least Privilege`
2. `Defence in Depth`
3. `Automation`
4. Sikkerhed implementeret i `CI/CD`

## Least Privilege
Dette princip bunder den adgang, som en bruger, skal have til systemet. Her siger [[Main/Noter/Sam Newman\|han]] at bruger kun skal adgang til det de som minimum skal bruge for at opfylde deres mål gennem systemet.
Hvis en microservice kun har `read-only` adgang til en database, vil en ondsindet aktør kun have `read-only` adgang og kun til denne database.

## Defence in depth
Dette princip handler om at man ikke blot skal sikre sin hoveddør mod angreb men også sikre resten af huset.
Gør microservices paranoide. Dette kan godt sænke hastigheden, men til gengæld vil services være mere sikker.

## Automation
En STOR DEL af microservices arkitektur er **Automation**. Uden dette vil du ikke kunne arbejde med dette. 
Automation fjerne den meneskelige interaktion med de fleste ting i Services og sikrer en ens behandling af services.

## Sikkerhed implementeret i CI/CD

Sikkerhed bliver ofte betragtet som en eftertanke i softwareudvikling, hvilket kan føre til betydelige restruktureringer senere. Tidligere har aspekter som test, brugervenlighed og drift også været silo-opdelte og først adresseret, når det meste af koden var færdig. Ligesom vi har integreret test og DevOps tidligere i leveringsprocessen, bør sikkerhed også trækkes fremad. 
Udviklere skal have en generel forståelse for sikkerhed, specialister skal indgå i delivery-teams, og værktøjer skal forbedres for at understøtte sikkerhed i softwaren. 
Værktøjer som **ZAP** fra OWASP kan simulere angreb, mens andre værktøjer som **Snyk** og **Brakeman** hjælper med at finde sårbarheder i kode og tredjepartsafhængigheder. Dog skal systemets sikkerhed forstås på et bredere niveau, da disse værktøjer kun adresserer lokale problemer.