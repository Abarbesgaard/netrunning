---
{"dg-publish":true,"permalink":"/main/noter/ressourcer/api/tutorial/api-trin-3/","title":"Trin 3","tags":["ressource","API","Web Api","Tutorial"],"created":"2024-08-16T10:49:13.398+02:00"}
---


## 3. Trin

Nu hvor du har oprettet programmet og installeret nuget pakken, kan du prøve at
køre programmet.

Hvis dit program ikke selv starter en browser så skal du gøre det manuelt.
Programmet starter din API på en lokal host, så du kan åbne en browser og
skrive:

`https://localhost:5255/weatherforecast`

Porten som min API kører på kan være en anden end din så vær opmærksom på det.

## Swagger

Når du har åbnet din browser og skrevet
`https://localhost:5255/weatherforecast`.
Vil du se en side som denne:

![Swagger_API.png](/img/user/Main/Images/Swagger_API.png)

Hvis du kører `GET` metoden vil ud få JSON tilbage der minder om dette:

```JSON
[
  {
    "date": "2020-12-28T00:00:00",
    "temperatureC": -16,
    "temperatureF": 3,
    "summary": "Freezing"
  },
  {
    "date": "2020-12-29T00:00:00",
    "temperatureC": -16,
    "temperatureF": 3,
    "summary": "Freezing"
  },
  {
    "date": "2020-12-30T00:00:00",
    "temperatureC": -16,
    "temperatureF": 3,
    "summary": "Freezing"
  },
  {
    "date": "2020-12-31T00:00:00",
    "temperatureC": -16,
    "temperatureF": 3,
    "summary": "Freezing"
  },
  {
    "date": "2021-01-01T00:00:00",
    "temperatureC": -16,
    "temperatureF": 3,
    "summary": "Freezing"
  }
]
```

For at lette mit skrive arbejde så se om du kan regne ud hvorfor du får
ovenstående tilbage når du laver en `GET` request.

[[Main/Noter/Ressourcer/API/Tutorial/api_trin_2\|Tilbage til trin 2]]

[[Main/Noter/Ressourcer/API/Tutorial/api_trin_4\|Videre til trin 4]]
