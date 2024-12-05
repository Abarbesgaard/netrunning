---
{"dg-publish":true,"permalink":"/main/artikler/the-power-of-ten/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowFileTree":"false","dgEnableSearch":"false","created":"2024-12-05T10:29:43.859+01:00"}
---

Mange softwareprojekter bruger kodningsretningslinjer, som beskriver, hvordan koden skal struktureres, og hvilke funktioner der bør undgås. Der er dog ikke enighed om, hvad der udgør en god standard, og mange retningslinjer er for lange og komplekse. 

Ofte er det svært at sikre, at reglerne følges, især for store projekter. For at gøre retningslinjerne effektive, bør de være enkle og klare, med højst ti regler, der kan kontrolleres automatisk. Dette kan forbedre pålideligheden af kritisk software, især når strengere regler er nødvendige for at sikre sikkerheden.
## 1. Regel
Begræns al kode til meget enkle kontrolstrukturer – brug ikke `goto`-sætninger, `setjmp` eller `longjmp`-konstruktioner, og direkte eller indirekte rekursion.

I C# betyder dette, at man bør undgå at bruge `goto` til at springe rundt i koden, undgå rekursiv funktionalitet, og bruge enkle kontrolstrukturer som if, while, for, osv.

### Eksempler
#### Med GoTo
```csharp
public void ExampleWithGoto()
{
    int x = 0;
    start:
    if (x < 5)
    {
        Console.WriteLine(x);
        x++;
        goto start;  // Brug af goto er No-No
    }
}

```

#### Uden GoTo
```csharp
public void ExampleWithoutGoto()
{
    int x = 0;
    while (x < 5)
    {
        Console.WriteLine(x);
        x++;
    }
}

```

Du bør undgå at bruge `goto`, da det kan gøre koden sværere at følge og vedligeholde. Brug i stedet simple løkker og betingelser, som er nemmere at forstå og kontrollere.
## 2. Regel
Alle løkker skal have en fast øvre grænse. Det skal være muligt for et kontrolværktøj at bevise statisk, at en forudbestemt øvre grænse for antallet af iterationer i en løkke ikke kan overskrides. 
Hvis løkkens grænse ikke kan bevises statisk, betragtes reglen som brudt.

I C# betyder dette, at du altid skal definere en fast grænse for antallet af iterationer i en løkke, så det er muligt at kontrollere på forhånd, hvor mange gange løkken vil køre.

### Uden øvre grænse
```csharp
public void ExampleWithoutFixedBound()
{
    int x = 0;
    while (x != -1)  
    {
        Console.WriteLine(x);
        x = GetNextValue();  
    }
}

```
I dette tilfælde kan vi ikke vide på forhånd, hvor mange gange løkken vil køre, fordi `GetNextValue()` kan returnere vilkårlige værdier.

### Med Øvre Grænse
```csharp
public void ExampleWithFixedBound()
{
    for (int i = 0; i < 10; i++)  // Fast øvre grænse for iterationer
    {
        Console.WriteLine(i);
    }
}

```

I dette tilfælde er det klart, at løkken *kun kører 10 gange*, hvilket gør det muligt for et værktøj at bekræfte, at grænsen ikke overskrides.
## 3. Regel 
Do not use dynamic memory allocation after initialization.

I C# betyder dette, at du bør undgå at allokere hukommelse dynamisk (som ved `new` eller brug af datastrukturer, der ændrer størrelse under kørsel) efter den oprindelige opsætning af objektet eller variablen. Formålet er at sikre, at hukommelsen, der bruges af programmet, forbliver forudsigelig og nem at håndtere.

### Dynamisk hukommelsestildeling efter initialisering
```csharp
public void ExampleWithDynamicMemory()
{
    List<int> numbers = new List<int>();  // Initialisering
    numbers.Add(1);  
    numbers.Add(2);  
}
```
Her bruger vi `List<T>`, som dynamisk allokerer hukommelse, hver gang vi tilføjer et nyt element. Dette er et eksempel på dynamisk hukommelsestildeling efter initialisering.
### Uden dynamisk hukommelsestildeling
```csharp
public void ExampleWithoutDynamicMemory()
{
    int[] numbers = new int[10];
    numbers[0] = 1;
    numbers[1] = 2;
}
```
I dette tilfælde har vi en statisk array, hvor størrelsen er kendt og ikke ændres under programkørsel. Der er ingen dynamisk hukommelsestildeling efter initialisering.

## 4. Regel
Ingen funktion bør være længere end det, der kan printes på et enkelt ark papir i et standard referencformat, hvor hver erklæring og hver statement optager én linje. Typisk betyder dette ikke mere end omkring 60 linjer kode pr. funktion.

Denne regel handler om at holde funktionerne korte og overskuelige, så de er nemmere at forstå og vedligeholde. Hvis en funktion er for lang, kan det blive svært at følge, hvad den gør, og det kan føre til fejl.

### Funktion med mere end 60 linjer kode
```csharp
public void LongFunction()
{
    int a = 10;
    int b = 20;
    int c = a + b;
    Console.WriteLine(c);
    // Mange flere linjer kode
    a = a * b;
    b = a - c;
    c = a + b;
    // ... (måske op til 1 milliard linjers kode)
    a = a + b;
    b = a * c;
    c = a - b;
    Console.WriteLine(a);
    Console.WriteLine(b);
    Console.WriteLine(c);
    // Funktionen bliver for den svage programmør svær at følge
}

```
Denne funktion har mange linjer kode, hvilket gør den svær at læse og vedligeholde. Den bryder reglen om at holde funktionerne korte.
### Funktion med maks. 60 linjer kode
```csharp
public void ShortFunction()
{
    int a = 10;
    int b = 20;
    int c = a + b;
    Console.WriteLine(c);
}
```
Denne funktion er kort og præcis og holder sig inden for den anbefalede grænse på 60 linjer. Den gør kun én ting og er let at forstå.

### 5. Regel
*Assertion Density*  i koden bør i gennemsnit være *mindst to*  pr. funktion. Assertions bruges til at kontrollere for anomalier, som aldrig bør opstå under normale kørsels forhold. Assertions skal altid være fri for "side effekter" og defineres som boolske tests. Når en assertion fejler, skal der tages en eksplicit håndteringshandling, f.eks. ved at returnere en fejlsituation til den kaldende funktion, der udfører den fejlede assertion. 


Denne regel hjælper med at sikre, at koden effektivt opdager og håndterer fejl, samtidig med at den ikke indeholder unødvendige eller ubrugelige assertioner.
### Rigtig dårlig assertion
```csharp
public void FunctionWithFewAssertions()
{
    int a = 10;
    int b = 20;
    Console.WriteLine(a + b);

    Assert.IsTrue(a > 0);  // En enkelt assertion, men det er ikke nok
}
```
Denne funktion har kun én assertion, og den er ikke nok til at opfylde reglen om mindst to assertioner. Desuden kan assertionen `Assert.IsTrue(a > 0)` muligvis aldrig fejle, da `a` altid er større end 0 i denne funktion.

### God Assertion
```Csharp
public void FunctionWithAssertions()
{
    int a = 10;
    int b = 20;
    
    Assert.IsTrue(a > 0);  // Første nyttige assertion
    Assert.IsTrue(b < 30);  // Anden nyttige assertion

    Console.WriteLine(a + b);
}
```
Denne funktion indeholder to nyttige assertions, der kontrollerer betingelser, som bør være sande under normale omstændigheder. Begge assertions er relevante for funktionen og vil opdage fejl, hvis de fejler.

## 6. Regel
Dataobjekter skal erklæres på det mindste mulige scope-niveau.

Denne regel betyder, at variabler og objekter kun skal være synlige inden for det mindste område, hvor de er nødvendige. Ved at begrænse scope af dataobjekter reduceres risikoen for utilsigtede ændringer af data og forbedrer koden ved at gøre den mere overskuelig og lettere at vedligeholde.
### Variabel erklæret globalt, men kun brugt lokalt
```csharp
public void Example()
{
    int number = 5;  // Erklæres på for højt niveau

    // Flere kodelinjer, men number er kun nødvendig her
    Console.WriteLine(number);
}

```
Her er `number` erklæret på et for højt niveau (på metode-niveau), selvom den kun er nødvendig i én del af funktionen. Det er bedre at begrænse dens synlighed til kun det nødvendige scope.
### Variabel erklæret på det mindste nødvendige scope
```csharp
public void Example()
{
    if (true)
    {
        int number = 5;  // Erklæres på det mindste niveau, hvor den er nødvendig
        Console.WriteLine(number);
    }
}
```
Her er `number` kun erklæret inden for den blok, hvor den faktisk bruges. Dette minimerer dens synlighed og sikrer, at den ikke utilsigtet ændres andre steder i funktionen.

## 7. Regel
Returværdien af ikke-void funktioner skal kontrolleres af hver kaldende funktion, og gyldigheden af parametre skal kontrolleres i hver funktion.

Denne regel understreger vigtigheden af at validere både de input, der modtages af funktionerne, og de resultater, der returneres. Dette hjælper med at fange fejl tidligt og sikre, at funktionerne altid arbejder med gyldige data og returnerer forventede resultater.

### Returværdi ikke kontrolleret
```csharp
public int Divide(int a, int b)
{
    return a / b;
}

public void Example()
{
    int result = Divide(10, 0);  // Deling med 0 – returværdi bliver ikke kontrolleret
    Console.WriteLine(result);
}
```
Her kaldes `Divide`-funktionen uden at kontrollere returværdien. Hvis `b` er 0, vil der opstå en undtagelse, men den håndteres ikke, og der er ingen kontrol af returværdien.
### Returværdi kontrolleret
```Csharp
public int Divide(int a, int b)
{
    if (b == 0) 
    {
        Console.WriteLine("Error: Division by zero");
        return -1; 
    }
    return a / b;
}

public void Example()
{
    int result = Divide(10, 0);
    if (result == -1)  
    {
        Console.WriteLine("Invalid operation");
    }
    else
    {
        Console.WriteLine(result);
    }
}
```
I dette eksempel bliver returværdien fra `Divide`-funktionen kontrolleret. Hvis der er en fejl (f.eks. division med 0), håndteres fejlen korrekt, og den kaldende funktion reagerer passende.

## 8. Regel
Brugen af preprosessor skal begrænses til inkludering af headerfiler og enkle makrodefinitioner. Token-pasting, variable argumentlister (ellipsis), og rekursive makroopkald er ikke tilladt. Alle makroer skal ekspandere til komplette syntaktiske enheder. Brugen af betingede kompilationsdirektiver er ofte tvivlsom, men kan ikke altid undgås. Det betyder, at der sjældent bør være behov for mere end én eller to betingede kompilationsdirektiver, selv i store softwareudviklingsprojekter, ud over den standardkode, der forhindrer multipel inkludering af den samme headerfil. Hver brug af betingede kompilationsdirektiver bør markeres af et værktøjsbaseret checker og begrundes i koden.
(kristus denne var jeg usikker på)

Denne regel sikrer, at præprocessorens funktionalitet bruges på en enkel og effektiv måde, uden at det bliver kompliceret eller svært at vedligeholde.

### Brug af betinget kompilering uden grund
```csharp
#define DEBUG

#ifdef DEBUG
    Console.WriteLine("Debugging");
#endif

#ifdef TEST_MODE
    Console.WriteLine("Test mode");
#endif
```

Brugen af betinget kompilering her kan være problematisk, da det kan føre til kodestykker, der kun er relevante under bestemte betingelser, hvilket gør koden sværere at forstå og vedligeholde. Der bør sjældent være mere end én eller to betingede kompilationsdirektiver.

### Standard makro til beskyttelse mod flere inkluderinger
```csharp
#ifndef HEADER_FILE_H
#define HEADER_FILE_H

// Headerfilens indhold

#endif
```
Dette er et simpelt og gyldigt brug af preprosessor til at forhindre flere inkludering i headerfiler. Dette er den mest typiske anvendelse af præprocessor, som er både effektiv og vedligeholdelsesvenlig.

## 9. Regel
Brugen af pointers bør begrænses. Specifikt må der ikke være mere end én niveau af dereferencering. Pointer-dereferencering må ikke skjules i makrodefinitioner eller i typedef-erklæringer. Funktionspointers er ikke tilladt.

Denne regel sigter mod at gøre koden mere sikker og lettere at forstå ved at minimere kompleksiteten, der opstår ved brugen af pointers. Mange niveauer af pointer-dereferencering og funktionalitet som funktionspointers kan gøre koden vanskelig at vedligeholde og fejlfinde.

```c
#include <stdio.h>

#define DEREF_PTR(ptr) *ptr

int main() {
    int a = 5;
    int *ptr = &a;  // Opretter en pointer, der peger på 'a'
    
    // Brug af makroen til at dereferere pointeren og udskrive værdien
    printf("%d\n", DEREF_PTR(ptr));  // Skjuler pointer-dereferencering med makro
    
    return 0;
}

```

**Forklaring:**

- `int *ptr = &a;` opretter en pointer, der peger på variablen `a`.
- `DEREF_PTR(ptr)` er en makro, der derefererer pointeren og giver værdien af `a` (som er 5).
- `printf("%d\n", DEREF_PTR(ptr));` udskriver værdien, som pointeren peger på.

## 10. Regel
Al kode skal kompileres fra den første dag af udviklingen med alle kompilatoradvarsler aktiveret på kompilatorens mest pedantiske indstilling. Al kode skal kunne kompileres med disse indstillinger uden nogen advarsler. Al kode skal tjekkes dagligt med mindst én, men helst flere, moderne statiske kildekodeanalyseværktøjer og bør bestå analyserne uden nogen advarsler.

#treatwarningsaserrors
## Det' Kilder
>[!source]- The Power of 10
> Tilgængelig på: [website](https://www.syv.ai/prompting-guide)