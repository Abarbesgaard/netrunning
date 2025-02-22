---
{"dg-publish":true,"permalink":"/publishing/main/artikler/lo-b-vs-clean-code/","title":"LoB vs Clean Code","tags":["Objektorienteret_Programmering","Software_Design","Clean_Code","Locality_of_Behaviour"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-08-11T08:05:48.254+02:00"}
---

Se hvad jeg ellers har skrevet [[Publishing/Main/Artikler/Artikler jeg har skrevet\|her]]

---
## Hvad er du mest til?
> [!question] Spørgsmål 1
>At have små funktioner i din kode som implementerer andre små funktioner,
som tilsammen skaber én adfærd?

> [!question] spørgsmål 2
> At have en funktion med én adfærd, uden mange små funktioner der opdeler
denne adfærd?

Dette spørgsmål vil jeg prøve at komme med forskellige synsvinkler på der
belyser gode argumenter for og i mod henholdsvis **Locality of Behaviour
principle(LoB)** og **Clean Code principle**.

## Hvad er LoB principle?

LoB er defineret ved:
> [!Quote] Carson Gross
> Adfærden i en enhed af kode bør være så åbenlys som muligt. Ved blot at
se på denne enhed af kode skal man kunne forstå hele adfærden.

Princippet søger at gøre det lettere for udviklere at forstå og vedligeholde
kode ved at sikre, at adfærden af et kode element er så tydeligt og let at
forstå, som muligt.

### Dårlig LoB

Her er et eksempel på kode der ikke lever op til *LoB pricippet*:

I én fil vi kalder **File1.cs** ligger:

```C#
public class ButtonHandler
{
    public void HandleButtonClick()
    {
        // Håndterer knappens klik
        var dataFetcher = new DataFetcher();
        var data = dataFetcher.FetchData();
        var dataProcessor = new DataProcessor();
        dataProcessor.ProcessData(data);
        var dataRenderer = new DataRenderer();
        dataRenderer.RenderData(data);
    }
}
```

I en anden fil vi kalder **file2.cs** ligger:

```c#
public class DataFetcher
{
    public string FetchData()
    {
        // Simulerer hentning af data fra en ekstern kilde
        return "Data fra ekstern kilde";
    }
}

public class DataProcessor
{
    public void ProcessData(string data)
    {
        // Simulerer behandling af data
        Console.WriteLine("Behandler data: " + data);
    }
}

public class DataRenderer
{
    public void RenderData(string data)
    {
        // Simulerer rendering af data
        Console.WriteLine("Viser data: " + data);
    }
}
```

### God LoB

Her vil nu komme et eksempel på hvordan en god LoB kunne se ud. Alt adfærden
vil være samlet i én fil.

```C#
public class ButtonHandler
{
    public void HandleButtonClick()
    {
        // Håndterer knappens klik
        FetchAndProcessData();
        RenderData();
    }

    private string FetchData()
    {
        // Simulerer hentning af data fra en ekstern kilde
        return "Data fra ekstern kilde";
    }

    private void ProcessData(string data)
    {
        // Simulerer behandling af data
        Console.WriteLine("Behandler data: " + data);
    }

    private void RenderData()
    {
        // Simulerer rendering af data
        Console.WriteLine("Viser data: " + FetchData());
    }
}
```

### Fordele ved LoB

 Der er flere fordele ved at følge Locality of Behaviour (LoB):

- Forbedret vedligeholdelighed
- Øget produktivitet
- Bedre kodekvalitet
- Øget forståelse
- Reduceret afhængighed
### Ulemper ved LoB

Selv om det kan lyde lovende med at gøre det væsentlig lettere at læse koden
er det stadig nogle udfordringer ved at holde sig hovedsagtligt til LoB:

- Kompleksitet i nogle tilfælde.
- Mulig duplication af kode.
- Overtrædelse af andre principper.
- Sværere integration med tredjepartsbiblioteker
- Potentiel ydeevneforringelse

## Hvad er Clean Code?

I en artikkel på medium  kommer de med referencen:  

> The first rule of functions is that they should be small. The second rule of
> functions is that *they should be smaller than that*. This is not an assertion
> that I can justify “ Make the smallest you can do. A function should not have
> two business rules and should only produce one result. Each function should tell
> a story and serve a purpose: Do something or respond to the caller code
>
> – Uncle Bob

Så for at opsummere skal dine funktioner være små

### Dårlig Clean Code

```C#
public class Calc
{
    public double a;
    public double b;
    
    public double c;

    public void DoCalculation()
    {
        double x = a + b * c;
        double y = a * b - c;
        double z = a / b + c;
        
        double result = x + y * z;
        
        Console.WriteLine("Resultat: " + result);
    }
}
```

### God Clean Code

```C#
public class Calculator
{
    private double operand1;
    private double operand2;
    private double result;

    public Calculator(double operand1, double operand2)
    {
        this.operand1 = operand1;
        this.operand2 = operand2;
    }

    public double Add()
    {
        result = operand1 + operand2;
        return result;
    }

    public double Subtract()
    {
        result = operand1 - operand2;
        return result;
    }

    public double Multiply()
    {
        result = operand1 * operand2;
        return result;
    }

    public double Divide()
    {
        if (operand2 == 0)
        {
            throw new ArgumentException("Division by zero is not allowed.");
        }
        
        result = operand1 / operand2;
        return result;
    }

    public void PrintResult()
    {
        Console.WriteLine("Resultat: " + result);
    }
}
```

### Fordele ved Clean Code

- Øget læsbarhed
- Forbedret vedligeholdelighed
- Øget produktivitet
- Bedre samarbejde

### Ulemper ved Clean Code

- Tidskrævende
- Over-engineering
- Sværere at lære
- Modstand fra andre udviklere
- Mulig overdreven abstraktion

## Sammenligning

I en artikel[Fowler] om funktioners længde fremhæves vigtigheden af at skrive
kortfattede funktioner i softwareudvikling. Martin Fowler argumenterer for,
at en funktion bør være kort nok til, at dens formål straks er åbenlyst,
og at læseren ikke behøver at dykke ned i dens implementering for at
forstå dens formål.

Både Locality of Behaviour (LoB) og Clean Code deler begge det Fowlers mål
om at gøre kode mere forståelig, vedligeholdelig og robust. Men der kan
opstå situationer, hvor de to principper kan støde sammen eller være i
konflikt:

1. **Abstraktion vs. Tydelighed:** Clean Code lægger vægt på at abstrahere
kompleksitet og skjule unødvendige detaljer bag velnavngivne metoder og
klasser. Dette kan undertiden føre til, at adfærden af en enhed af kode
ikke er så åbenlys som LoB kræver. Der kan her opstå en konflikt mellem at
gøre koden abstrakt og generisk (Clean Code) og at gøre adfærden tydelig
og åbenlys (LoB).
2. **Kodeopdeling:** Clean Code opfordrer til opdeling af kode i mindre,
selvstændige enheder, såsom metoder og klasser, for at øge vedligeholdeligheden
og genbrugeligheden. Men dette kan føre til situationer, hvor adfærden af en
enhed af kode er spredt over flere filer eller klasser, hvilket kan gøre det
sværere at opnå god LoB.
3. **Balance mellem abstraktion og detaljer:** Clean Code kan nogle gange føre
til overdreven abstraktion, hvor detaljer bliver skjult bag metoder eller klasser.
Dette kan være en fordel for vedligeholdelse og læsbarhed, men det kan også
gøre det svært at forstå den fulde adfærd af koden, hvilket kan modarbejde
LoB-princippet.
4. **Prioritering af principper:** I nogle tilfælde kan udviklere stå over
for en afvejning mellem LoB og Clean Code. For eksempel kan det være nødvendigt
at vælge mellem at skabe en mere abstrakt og generel løsning (Clean Code) og
at gøre adfærden af koden mere åbenlys og forståelig (LoB).

### **Udfordringer ved implementering og balance af LoB og Clean Code-principper**

Implementering og balance af LoB og Clean Code-principper kan præsentere visse udfordringer:

- **Abstraktion vs. Tydelighed:** Der kan opstå en konflikt mellem at gøre
koden abstrakt og generisk (Clean Code) og at gøre adfærden tydelig og åbenlys (LoB).
- **Kodeopdeling:** Clean Code-opdeling af kode i mindre, selvstændige enheder
kan gøre det sværere at opnå god LoB, da adfærden af koden kan blive spredt
over flere filer eller klasser.
- **Balance mellem abstraktion og detaljer:** Der kan være en udfordring i at
finde den rette balance mellem at skjule unødvendige detaljer bag abstraktioner
og samtidig bevare tilstrækkelig tydelighed og åbenlyshed i adfærden af koden.

I sidste ende handler det om at finde en passende balance mellem LoB og Clean
Code-principper afhængigt af projektets behov og krav.

## Opsummering

Her er en kort opsummering af de vigtigste punkter, der blev diskuteret:

- Det er vigtigt at finde en *balance* mellem Locality of Behaviour (LoB) og
Clean Code-principper i software design.
- Begge principper forsøger at nu frem til at vedligeholdelse og læsbarhed er
afgørende for at skabe velstruktureret og let forståelig kode på hver deres måde.
- Udviklere opfordres til at vægte adfærdens åbenlyshed og kodekvalitet for
at sikre, at deres software er robust, vedligeholdbart og pålideligt.

Ved at kombinere principperne for LoB og Clean Code kan udviklere skabe
softwareløsninger, der ikke kun er teknisk avancerede, men også let forståelige
og lette at vedligeholde.

## Litteratur

Gross, Carson. “Locality of Behaviour (LoB).” *htmx*, Maj 29, 2020.
[https://htmx.org/essays/locality-of-behaviour](https://htmx.org/essays/locality-of-behaviour)

Fowler, M. (2016, 30. November). Function Length [Online]. Tilgængelig:
[https://martinfowler.com/bliki/FunctionLength.html](https://martinfowler.com/bliki/FunctionLength.html)
Martin, R. C. (2008). Clean Code: A Handbook of Agile Software Craftsmanship.
Prentice Hall.

Alkan, S. (2022, November 3). Clean Code Chapter 3: Functions. Medium.
[https://medium.com/@seydialkan/clean-code-chapter-3-functions-bfde27c1983a](https://medium.com/@seydialkan/clean-code-chapter-3-functions-bfde27c1983a)

## Andre artikler med samme emne
| File | Title | Tags |
| ---- | ----- | ---- |

{ .block-language-dataview}
