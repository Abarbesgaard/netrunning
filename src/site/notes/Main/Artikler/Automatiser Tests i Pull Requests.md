---
{"dg-publish":true,"permalink":"/main/artikler/automatiser-tests-i-pull-requests/","tags":["AutomatedTesting","GitHubActions","CICD"],"dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-11-27T10:33:10.380+01:00"}
---


**At sikre kodekvalitet** er afgørende for succes i ethvert udviklingsprojekt. Automatisering af tests som en del af [[Pull Request\|pull request]]-processen er en effektiv måde at fange fejl, sikre stabilitet og spare tid. I denne guide viser jeg, hvordan du opsætter [[GitHub Actions\|GitHub Actions]] til at køre tests automatisk, hver gang du laver en [[Pull Request\|pull request]] (PR).

> [!important] Når vi er færdige, vil du have en workflow, der:
> >[!note] 1
>Kører dine tests automatisk
>
>>[!note] 2
>Blokerer en [[Pull Request\|PR]] fra at blive merged, hvis testene fejler.
>
>>[!note] 3
>Giver dig et solidt grundlag for at *skalere* dit projekt.

---
## Kort om [[GitHub Actions?\|GitHub Actions?]]

[[GitHub Actions\|GitHub Actions]] er en CI/CD-platform indbygget i [[Main/Noter/GitHub\|GitHub]]. Det gør det muligt at opsætte *workflows*, der aktiveres ved *specifikke hændelser*, som f.eks. når en [[Pull Request\|pull request]] oprettes eller en push laves til et bestemt branch.

Med [[GitHub Actions\|GitHub Actions]] kan du:

- Køre tests.
- Bygge og deploye applikationer.
- Automatisere gentagne opgaver i dit udviklingsarbejde.

---
## **Opsætning af en Workflow til Pull Requests**

### Opret en [[YAML\|YAML]]-fil til din workflow

I din projektmappe skal du oprette en ny fil i `.github/workflows`-mappen. Navngiv den f.eks. `test-on-pr.yml`.

```yaml

name: Test on Pull Request  
on:
  workflow_dispatch:
  pull_request:   
		branches:       
		- main       
		- develop  
jobs:   
	  build:
	    runs-on: ubuntu-latest
    
	    steps: 
	    - name: Checkout code   
	      uses: actions/checkout@v3
      
	    - name: Setup .NET
	      uses: actions/setup-dotnet@v3
		  with:
		      dotnet-version: '8.0.x'  # Angiv din .NET-version her
    
	    - name: Restore dependencies
	      run: dotnet restore [Her skal stå stien til din .sln fil]

	    - name: Build
	      run: dotnet build [Her skal stå stien til din .sln fil] --configuration Release --no-restore
	test:
	    runs-on: ubuntu-latest

	    steps:
	    - name: Checkout code
	      uses: actions/checkout@v3
	
	    - name: Setup .NET
	      uses: actions/setup-dotnet@v3
	      with:
	        dotnet-version: '8.0.x'  # Angiv din .NET-version her
	    - name: Test
	      run: dotnet test [Her skal stå stien til din .csproj testfil] 
    
    
```
---
### Forklaring af Workflow-filen
Denne workflow-fil er designet til at automatisere bygning og testning af en .NET-applikation, hver gang en [[Pull Request\|pull request]] laves mod enten `main`- eller `develop`-branchen. Den bruger [[GitHub Actions\|GitHub Actions]] til at udføre følgende trin:
#### Workflow-navn og triggere

```yaml

name: Test on Pull Request 
on: 
	workflow_dispatch:
	pull_request:     
		branches:       
		- main       
		- develop
```
- **`name`**: Angiver navnet på workflowet, så det er let at identificere i [[GitHub Actions\|GitHub Actions]]-grænsefladen.
- **`on`**: Definerer, hvornår workflowet skal køre. Her bliver det trigget, når der laves en pull request mod `main`- eller `develop`-branchen.

---
#### Jobs
Workflowet består af to jobs: `build` og `test`. De er uafhængige af hinanden, hvilket betyder, at de kan køre parallelt.

##### Job: Build
```yaml
jobs:   
	  build:
	    runs-on: ubuntu-latest
    
	    steps: 
	    - name: Checkout code   
	      uses: actions/checkout@v3
      
	    - name: Setup .NET
	      uses: actions/setup-dotnet@v3
		  with:
		      dotnet-version: '8.0.x'  # Angiv din .NET-version her
    
	    - name: Restore dependencies
	      run: dotnet restore [Her skal stå stien til din .sln fil]

	    - name: Build
	      run: dotnet build [Her skal stå stien til din .sln fil] --configuration Release --no-restore
```

- **`runs-on`**: Angiver den virtuelle maskine, som jobben skal køre på. Her er det `ubuntu-latest`.
- **`steps`**: En liste over handlinger, der udføres i rækkefølge:
    - **`Checkout code`**: Henter koden fra repository'et.
    - **`Setup .NET`**: Installerer .NET SDK, her version `8.0.x`.
    - **`Restore dependencies`**: Kører `dotnet restore` for at hente alle nødvendige NuGet-pakker. Du skal angive stien til din `.sln`-fil.
    - **`Build`**: Kompilerer projektet med `dotnet build`. Der bruges `--configuration Release` for at bygge i produktionsmode, og `--no-restore` undgår at gendanne afhængigheder igen, da det allerede er gjort.

---
##### **Job: Test**

```yaml
test:
	    runs-on: ubuntu-latest

	    steps:
	    - name: Checkout code
	      uses: actions/checkout@v3
	
	    - name: Setup .NET
	      uses: actions/setup-dotnet@v3
	      with:
	        dotnet-version: '8.0.x'  # Angiv din .NET-version her
	    - name: Test
	      run: dotnet test [Her skal stå stien til din .csproj testfil] 
    
```

- **`runs-on`**: Bruger samme virtuelle maskine som build-jobbet (`ubuntu-latest`).
- **`steps`**: Handlingerne i test-jobbet:
    - **`Checkout code`**: Henter koden, præcis som i build-jobbet.
    - **`Setup .NET`**: Installerer den ønskede version af .NET SDK.
    - **`Test`**: Kører tests med `dotnet test`. Du skal angive stien til din `.csproj`-testprojektfil for at sikre, at de korrekte tests køres.

---
### **Tilpasning af Stier**

De steder, hvor der står `[Her skal stå stien til din .sln fil]` eller `[Her skal stå stien til din .csproj testfil]`, skal du tilpasse det til din projektstruktur. Eksempler:

Hvis din løsning hedder `MyApp.sln` og ligger i rodmappen:
```bash
dotnet restore MyApp.sln 
dotnet build MyApp.sln
```

Hvis dit testprojekt hedder `MyApp.Tests.csproj` og ligger i `tests`-mappen:
```bash
dotnet test tests/MyApp.Tests/MyApp.Tests.csproj
```

---
### **Fordele ved denne Struktur**

- **Modularitet:** Build og test er separate jobs, hvilket gør workflows nemmere at debugge og vedligeholde.
- **Parallellitet:** Du kan konfigurere workflows til at køre jobs samtidigt for at spare tid.
- **Fleksibilitet:** Nem at udvide med flere trin, som f.eks. kodeanalyse, deploy eller integrationstests.

Ved at bruge dette workflow kan du automatisere dine builds og tests, hvilket sparer tid og sikrer høj kodekvalitet. Det er nemt at tilpasse yderligere trin som *code coverage*, *linting* eller *integrationstests* for at styrke din **CI/CD-proces**.

**Hvad tænker du?**  
Har du erfaring med [[GitHub Actions\|GitHub Actions]], eller mangler der noget i denne guide? Del dine tanker, forslag og spørgsmål i kommentarerne – lad os starte en diskussion om bedste praksis for test-automatisering! 🚀

## Kilder
> [!source]- Github Actions
> Tilgængelig på: [github](https://docs.github.com/en/actions/writing-workflows/quickstart)

> [!source]- Build your first GitHub Actions workflow
> Tilgængelig på: [youtube](https://www.youtube.com/watch?v=47zYGHwXPmE)

## Andre artikler med samme emne
| File | Title | Tags |
| ---- | ----- | ---- |

{ .block-language-dataview}
