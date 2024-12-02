---
{"dg-publish":true,"permalink":"/main/noter/pull-request/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2024-11-27T12:09:50.930+01:00"}
---

> [!important] Hvad er en Pull Request
> En pull request (PR) er en central mekanisme i softwareudvikling, der bruges til at foreslå og integrere kodeændringer i et projekt. 


![Pasted image 20241127121033.png](/img/user/Main/Images/Pasted%20image%2020241127121033.png)
*Billedet er fra [Medium](https://medium.com/@urna.hybesis/pull-request-workflow-with-git-6-steps-guide-3858e30b5fa4)*
## Definition og formål

En pull request er en anmodning om at få ændringer fra én gren (branch) fusioneret ind i en anden gren i et softwareprojekt, typisk fra en funktionsgren til hovedgrenen [1](https://linearb.io/blog/what-is-a-pull-request) [3](https://www.pullrequest.com/blog/pull-requests-101/). Det er en måde, hvorpå udviklere kan:

- Initiere processen med at integrere nye kodeændringer i projektets hovedlager (repository)
- Anmode om gennemgang af deres kode, før den integreres
- Samarbejde om kodeudvikling og kvalitetssikring

## Nøgleelementer i en pull request

En pull request består af flere komponenter:

- **Kildegrenen**: Den gren, der indeholder de nye ændringer
- **Målgrenen**: Den gren, som ændringerne skal fusioneres ind i (ofte hovedgrenen)
- **Diff**: En oversigt over ændringerne mellem kilde- og målgrenen
- **Gennemgang**: En proces, hvor andre teammedlemmer kan kommentere og godkende ændringerne [4](https://graphite.dev/guides/what-is-a-pull-request)

## Processen for en pull request

1. **Oprettelse af en gren**: Udvikleren opretter en ny gren til at arbejde på ændringer
2. **Lave ændringer og commit**: Kodeændringer udføres og committes
3. **Push ændringer**: Ændringerne pushes til det fjerne repository
4. **Åbne pull request**: Udvikleren opretter en pull request via repositoryets webgrænseflade
5. **Gennemgang og diskussion**: Teammedlemmer gennemgår ændringerne og giver feedback
6. **Godkendelse og fusion**: Efter godkendelse fusioneres ændringerne ind i målgrenen
7. **Lukning og oprydning**: Pull requesten lukkes, og kildebrachen slettes ofte [4](https://graphite.dev/guides/what-is-a-pull-request)

## Fordele ved at bruge pull requests

- Fremmer samarbejde og videndeling i teamet
- Forbedrer kodekvaliteten gennem peer review
- Bidrager til bedre sikkerhed og overholdelse af standarder
- Giver en dokumenteret historik over ændringer i projektet [4](https://graphite.dev/guides/what-is-a-pull-request)

Pull requests er et vigtigt værktøj til at opretholde høj kodekvalitet og effektivt samarbejde i softwareudviklingsprojekter.