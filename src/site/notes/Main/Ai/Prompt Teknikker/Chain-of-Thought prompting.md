---
{"dg-publish":true,"permalink":"/main/ai/prompt-teknikker/chain-of-thought-prompting/","tags":["⭐⭐⭐"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-02T17:10:35.163+01:00"}
---

> [!important] Sværhedsgrad
> ⭐⭐⭐

Chain-of-thought (CoT) prompting muliggør for modellen at lave komplekse ræsonnement. Det fungerer ved at modellen ikke kun genererer et endeligt svar, men også de mellemtrin, der fører til konklusionen. 

Dette gør det muligt for modellen at forstå og håndtere mere komplekse opgaver, der kræver mere logik, før den giver et svar.

CoT prompting kan kombineres med [[Main/Ai/Prompt Teknikker/Few-shot prompting\|Few-shot prompting]] for at opnå bedre resultater på mere komplekse opgaver, hvor det er nødvendigt at gøre processen tydelig og dele den op i forståelige trin. 

Denne tilgang hjælper modellen med at forstå, hvordan man løser et problem trin for trin, hvilket kan forbedre præstationen, *især* i situationer, der involverer matematiske beregninger, logik og andre komplekse beslutningstagning.

**Eksempel:**  
Hvis vi tager eksemplet med at finde ud af, om de ulige tal i en gruppe summerer til et lige tal, kan CoT prompting hjælpe modellen med at vise sine mellemtrin:

> [!example] eksempel
De ulige tal i denne gruppe lægges sammen til et lige tal: 4, 8, 9, 15, 12, 2, 1. 
S: Hvis man lægger alle de ulige tal sammen (9, 15, 1) giver det 25. Svaret er Falsk. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 17, 10, 19, 4, 8, 12, 24. 
S: Hvis man lægger alle de ulige tal sammen (17, 19) giver det 36. Svaret er Sandt. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 16, 11, 14, 4, 8, 13, 24. 
S: Hvis man lægger alle de ulige tal sammen (11, 13) giver det 24. Svaret er Sandt. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 17, 9, 10, 12, 13, 4, 2. 
S: Hvis man lægger alle de ulige tal sammen (17, 9, 13) giver det 39. Svaret er Falsk. 
De ulige tal i denne gruppe lægges sammen til et lige tal: 15, 32, 5, 13, 82, 7, 1. 
S: 
**Output:** 
Hvis man lægger alle de ulige tal sammen (15, 5, 13, 7, 1) giver det 41. Svaret er Falsk.

Ved at inkludere disse mellemtrin får modellen ikke kun mulighed for at forstå processen, men også at give et korrekt og begrundet svar. Denne metode er især nyttig, *når opgaven er kompleks*, og der er behov for en logisk progression for at nå frem til den rigtige løsning.

### Kode eksempel
Jeg forsøgte mig med at lave et kode eksempel med C#.
> [!Example] prompt
> lav nu C# kode ud fra følgende: 
> Step 1: Definér, hvad et primtal er. Et primtal er et tal, der kun kan deles med 1 og sig selv, og som er større end 1. 
> Step 2: Tjek om 29 er større end 1. 29 er større end 1, så det er muligt, at det er et primtal. Step 3: Prøv at dele 29 med alle tal fra 2 op til kvadratroden af 29. Vi skal kun teste deling med tal op til kvadratroden af 29, fordi hvis 29 kan deles med et tal større end kvadratroden, vil det også kunne deles med et mindre tal. 
> Step 4: Tjek om 29 kan deles med nogen af disse tal. Vi tester divisionen for 2, 3, 4, 5, 6. 
> 29 % 2 == 1 (kan ikke deles med 2) 
> 29 % 3 == 2 (kan ikke deles med 3) 
> 29 % 4 == 1 (kan ikke deles med 4) 
> 29 % 5 == 4 (kan ikke deles med 5) 
> 29 % 6 == 5 (kan ikke deles med 6) 
> Step 5: Da 29 ikke kan deles med nogen af tallene fra 2 til kvadratroden af 29, er 29 et primtal. 
> Step 6: Konklusion: 29 er et primtal.

### Output
```csharp
using System;

class Program
{
    static void Main()
    {
        int number = 29;
        
        // Step 1: Check if the number is greater than 1
        if (number > 1)
        {
            bool isPrime = true;

            // Step 3: Check divisibility up to the square root of the number
            int limit = (int)Math.Sqrt(number);

            for (int i = 2; i <= limit; i++)
            {
                // Step 4: Test if the number is divisible by any number from 2 to the square root of the number
                if (number % i == 0)
                {
                    isPrime = false;
                    break;
                }
            }

            // Step 5: Conclusion
            if (isPrime)
            {
                Console.WriteLine($"{number} is a prime number.");
            }
            else
            {
                Console.WriteLine($"{number} is not a prime number.");
            }
        }
        else
        {
            Console.WriteLine($"{number} is not a prime number.");
        }
    }
}

```