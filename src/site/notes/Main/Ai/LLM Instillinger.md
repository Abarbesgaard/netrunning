---
{"dg-publish":true,"permalink":"/main/ai/llm-instillinger/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T09:25:06.682+01:00"}
---

## Parametre i prompt engineering

Når du designer og tester *prompts*, interagerer du typisk med [[Main/Noter/Large language model\|LLM'er]] via en [[Main/Noter/API\|API]]. Her kan du justere nogle parametre for at opnå forskellige resultater. 

Justeringen kræver eksperimenter for at finde de rette indstillinger, der passer til dine behov. Her er en forklaring på de mest almindelige parametre:

---

### temperatur

- **Hvad det gør**: Bestemmer, hvor deterministisk eller kreativ modellen er.
- **Lave værdier**: Giver mere *præcise* og *forudsigelige* svar, da modellen vælger *det mest sandsynlige næste ord*. Ideelt til faktabaserede opgaver.
- **Høje værdier**: Giver mere *tilfældige* og *kreative* svar, f.eks. til poesi eller historiefortælling.
- **Anvendelse**: Brug lave værdier til faktabaserede spørgsmål og høje værdier til kreative opgaver.

> [!example] lav temperatur
> **Prompt**: Beskriv en kat. temperature 0.2.
> **Output**: En kat er et lille, pelsklædt pattedyr med fire ben, lange knurhår og skarpe kløer. Den er et populært kæledyr, kendt for sin uafhængighed og jagtinstinkt.

> [!example] høj temperatur
> **Prompt**: Beskriv en kat. temperature 0.8.
> **Output**: En kat er en mystisk skabning med øjne som smeltet rav og en gang som silke gennem natten. Den spinder historier i mørket og gemmer hemmeligheder i sin pels.

---

### top_p 

- **Hvad det gør**: Kontrollerer, hvor mange mulige ord modellen kan vælge imellem, baseret på sandsynlighedsmasse.
- **Lave værdier**: Begrænser valget til de mest sandsynlige ord, hvilket *giver mere præcise svar*.
- **Høje værdier**: Giver adgang til mindre sandsynlige ord, hvilket *skaber mere varierede og kreative svar*.
- **Anbefaling**: Justér enten _temperature_ **eller** _top_p_, men ikke begge samtidig. [kilde](https://genai.stackexchange.com/questions/1850/why-isnt-it-generally-recommended-to-alter-both-the-temperature-and-top-p-whe)

> [!example] lav top_p
> **Prompt**: Beskriv en kat. top_p 0.2.
> **Output**: En stjerne er en gigantisk kugle af brændende gas, primært bestående af hydrogen og helium. Den producerer energi gennem kernefusion og udsender lys.

> [!example] høj top_p
> **Prompt**: Beskriv en kat. top_p 0.8.
> **Output**: En stjerne er som en glitrende fyrtårn i universets mørke, en danser af lys, født af kosmiske kræfter, der synger tidens evige sang..

---

### max length

- **Hvad det gør**: Angiver det maksimale antal tokens, modellen kan generere.
- **Hvorfor det er vigtigt**: Hjælper med at undgå for lange eller irrelevante svar og reducerer omkostninger.


> [!example] kort max length
> **Prompt**: Forklar fotosyntese. max length 50.
> **Output**: Fotosyntese er en proces, hvor planter bruger lysenergi til at omdanne kuldioxid og vand til glukose og ilt.

> [!example] Lang max length
> **Prompt**: Beskriv en kat. max length 200.
> **Output**: Fotosyntese er en biokemisk proces, hvor planter, alger og nogle bakterier bruger sollys til at syntetisere føde. Processen foregår i kloroplasterne, hvor klorofyl optager lysenergi, som driver omdannelsen af kuldioxid og vand til glukose og ilt. Denne proces er vigtig for livet på Jorden, da den både producerer ilt, som vi indånder, og energi, der lagres i glukosen, som er en vigtig energikilde for levende organismer.


---

### stop sequence

- **Hvad det gør**: Stopper modellen fra at generere flere tokens, når en bestemt sekvens dukker op.
- **Anvendelse**: Brug det til at kontrollere struktur og længde, f.eks. at begrænse en liste til 10 punkter ved at sætte "11" som stop-sekvens.



> [!example] Ingen stop sequence
> **Prompt**: Lav en liste over fordelene ved regelmæssig motion.
> **Output**: 
> - Forbedrer konditionen.
> - Styrker musklerne.
> - Reducerer stress.
> - Øger energi.
> - Forbedrer søvnkvaliteten.
> - Fremmer vægttab.
> - Øger mental skarphed.
> - Forbedrer humøret.
> - Styrker immunsystemet.
> - Forbedrer kredsløbet.
> - Reducerer risikoen for kroniske sygdomme.
> - Hjælper med at opbygge selvtillid.

> [!example] stop sequence 3
> **Prompt**: Lav en liste over fordelene ved regelmæssig motion. stop sequence 3
> **Output**: 
> - Forbedrer konditionen.
> - Styrker musklerne.
> - Reducerer stress.

---
### Frequency Penalty

- **Hvad det gør**: Pålægger en straf for at bruge ord, der allerede er blevet brugt i prompten eller svaret.
- **Effekt**: Reducerer gentagelser, så svarene bliver mere varierede.

> [!example] uden frequency penalty
> **Prompt**: Beskriv fordelene ved at læse bøger.
> **Output**: Læsning af bøger har mange fordele. Det udvider din viden, forbedrer koncentrationsevnen og hjælper med at udvide dit ordforråd. Bøger giver også en mulighed for at slappe af og reducere stress, samtidig med at de stimulerer din fantasi og kreativitet.

> [!example] frequency penalty 0.5
> **Prompt**: Beskriv fordelene ved at læse bøger. frequency penalty 0.5.
> **Output**: At læse bøger tilbyder mange gevinster. Det øger din viden, forbedrer opmærksomheden og udvider dit ordforråd. Bøger giver dig også mulighed for at slappe af og mindske stress, samtidig med at de fremmer din fantasi og kreative tanker.




---

### Presence Penalty

- **Hvad det gør**: Pålægger en fast straf for gentagne ord, uanset hvor ofte de optræder.
- **Effekt**: Forhindrer, at modellen gentager de samme sætninger for ofte.
- **Anbefaling**: Justér enten _frequency penalty_ **eller** _presence penalty_, men ikke begge samtidig.

> [!example] uden presence penalty
> **Prompt**: Beskriv fordelene ved at træne regelmæssigt.
> **Output**: At træne regelmæssigt er godt for din krop. Det hjælper med at opbygge muskler, forbedre kredsløbet og øge energiniveauet. Træning forbedrer også din mentale sundhed og hjælper med at reducere stress.

> [!example] frequency penalty 0.5
> **Prompt**: Beskriv fordelene ved at træne regelmæssigt. presence penalty 0.5.
> **Output**: Regelmæssig træning giver mange fordele. Det styrker musklerne, forbedrer blodcirkulationen og øger energiniveauet. Derudover har træning en positiv indvirkning på din mentale sundhed og hjælper med at lindre stress.

