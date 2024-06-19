---
{"dg-publish":true,"permalink":"/content/portfolie/debugland/","title":"Debugland","tags":["Portfolie"]}
---


> [!tldr] 
> Jeg har udviklet _Debugland_, et .NET debugging bibliotek, for at imødekomme et behov for dybere forståelse af koden under kørsel. Med dette værktøj kan udviklere nemt spore og analysere nøjagtige tidspunkter for metodekald, variabeltilstande og SQL-kommandoer i realtid, hvilket giver klarhed over koden under eksekvering

| Links                                                                             | Beskrivelse                              |
| --------------------------------------------------------------------------------- | ---------------------------------------- |
| [Dokumentation](https://abarbesgaard.github.io/Debugland/index.html)              | Et Github Pages side med dokumentationen |
| [Github Repository](https://github.com/Abarbesgaard/Debugland?tab=readme-ov-file) | Link til Github repo                     |
| [Nuget.org](https://www.nuget.org/packages/Debugland)                             | link til Nuget.org                       |

## Debugland: Et .NET Debugging Bibliotek

_Debugland_ er et debugging bibliotek til .NET, som er tilgængeligt på GitHub. Det tilbyder en række metoder til at spore udførelsen af metoder, timing, udførelse af SQL-kommandoer, variabeldeklarationer og kontrolstrømsudtalelser inden for en .NET-applikation. Ved at bruge Debugland kan udviklere få værdifuld indsigt i deres kodes opførsel og identificere potentielle problemer under udvikling og testning.

Siden er sat op med DocFX, som hiver XML kommentarerne direkte over på siden.

**Installation af Debugland NuGet Pakken:**

1. Åbn din projekts NuGet Package Manager.
2. Søg efter “Debugland” og vælg den passende pakke til dit projekts rammeværk (.NET Framework, .NET Core osv.).
3. Klik på “Installer” for at tilføje pakken til dit projekt.

**Tilføj en Reference til Debugland Namespace:**

I din projekts kodefil, tilføj en reference til Debugland Namespace ved hjælp af følgende linje:

C#

```csharp
using Debugger = Debugland.Debugger;
```

AI-generated code. Review and use carefully. .

**Begynd at Bruge Debuglands Metoder:**

Nu kan du begynde at bruge Debuglands metoder i hele din kodebase for at spore forskellige aspekter af din applikations udførelse. For eksempel:

```csharp
Debugger.MethodInitiated("MyMethodName");
// Din metodelogik her
string myVariable = "En værdi";
Debugger.Variable("myVariable", myVariable);

using (var reader = ...)
{
    Debugger.ReaderInitiated();
    // Brug læseren
    Debugger.ReaderTerminated();
}
Debugger.MethodTerminated("MyMethodName");
```




