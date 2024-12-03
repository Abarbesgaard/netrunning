---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/zero-shot-prompting/","tags":["⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T11:44:48.999+01:00"}
---

> [!important] Sværhedsgrad
> ⭐

[[Main/Noter/Large language model\|Store sprogmodeller]] som [GPT-3.5 Turbo](https://openai.com/index/gpt-3-5-turbo-fine-tuning-and-api-updates/), [GPT-4](https://openai.com/index/gpt-4/) og [Claude 3](https://www.anthropic.com/news/claude-3-family) er i dag trænet til at følge instruktioner og er blevet trænet på store mængder data. 

Denne store trænings mængde gør modellerne i stand til at udføre visse opgaver uden forudgående eksempler – det kaldes "**zero-shot**" prompting. 

> [!important] Hvad er Zero-Shot
> Zero-shot prompting betyder, at prompten, du bruger til at interagere med modellen, ikke indeholder eksempler eller demonstrationer. Den giver simpelthen instruktionen om, hvad modellen skal gøre, uden at der er brugt yderligere eksempler til at lede modellen.

Vi prøvede et par zero-shot eksempler i den forrige sektion. Her er et af de eksempler, vi brugte (tekstklassifikation):

> [!example] eksempel
**Prompt:**
Klassificer teksten som neutral, negativ eller positiv.  
Tekst: "Frodo og hans venner begiver sig ud på en lang rejse for at ødelægge ringen i Mordor."  
Sentiment:
**Output:**
Positiv

Bemærk, at vi i prompten ovenfor ikke gav modellen eksempler på tekst og deres klassifikationer. [[Main/Noter/Large language model\|LLM'en]] forstår allerede, hvad "sentiment" betyder – det er zero-shot funktionaliteten i spil.

Når zero-shot ikke fungerer godt, anbefales det at give modellen demonstrationer eller eksempler i prompten, hvilket fører til "few-shot" prompting. 