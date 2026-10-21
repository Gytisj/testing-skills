---
name: miestu-oras
description: Parodo dabartiniam laikui artimiausią orų prognozę penkiems didžiausiems Lietuvos miestams (Vilnius, Kaunas, Klaipėda, Šiauliai, Panevėžys), pateikdamas temperatūrą ir oro sąlygas iš oficialaus meteo.lt API. Naudok, kai prašoma „miestų oras“, „miestu-oras“, penkių didžiausių Lietuvos miestų orų arba jų temperatūrų palyginimo.
---

# Miestų oras

Pateik penkių didžiausių Lietuvos miestų **artimiausio prognozės laiko** temperatūrą ir orų sąlygas lietuviškai.

## Duomenų gavimas

1. Kiekvieną kartą iš naujo kreipkis į oficialų Lietuvos hidrometeorologijos tarnybos API `https://api.meteo.lt/v1/` naudodamas prieinamą žiniatinklio ar HTTP įrankį. Nenaudok atmintyje likusių orų reikšmių.
2. Siųsk GET užklausas į:
   - `https://api.meteo.lt/v1/places/vilnius/forecasts/long-term`
   - `https://api.meteo.lt/v1/places/kaunas/forecasts/long-term`
   - `https://api.meteo.lt/v1/places/klaipeda/forecasts/long-term`
   - `https://api.meteo.lt/v1/places/siauliai/forecasts/long-term`
   - `https://api.meteo.lt/v1/places/panevezys/forecasts/long-term`
3. Iš `forecastTimestamps` pasirink pirmą įrašą, kurio `forecastTimeUtc` nėra ankstesnis už esamą UTC laiką. Jei tokio nėra, miestui rodyk „duomenų nėra“, o ne pasenusį įrašą.
4. Iš pasirinkto įrašo paimk `airTemperature` (°C), `conditionCode` ir `forecastTimeUtc`. Jei `airTemperature` arba `conditionCode` trūksta, rodyk „duomenų nėra“ atitinkamame lauke. Nespėliok.
5. `conditionCode` išversk į lietuvių kalbą pagal reikšmes: `clear` – giedra; `partly-cloudy` – mažai debesuota; `cloudy-with-sunny-intervals` – debesuota su pragiedruliais; `cloudy` – debesuota; `light-rain` – nedidelis lietus; `rain` – lietus; `heavy-rain` – smarkus lietus; `thunder` – perkūnija; `isolated-thunderstorms` – trumpas lietus su perkūnija; `thunderstorms` – lietus su perkūnija; `heavy-rain-with-thunderstorms` – smarkus lietus su perkūnija; `light-sleet` – nedidelė šlapdriba; `sleet` – šlapdriba; `freezing-rain` – lijundra; `hail` – kruša; `light-snow` – nedidelis sniegas; `snow` – sniegas; `heavy-snow` – smarkus sniegas; `fog` – rūkas. Nežinomą ar `null` kodą rodyk kaip „nenustatyta“.
6. Laiko žymas, kurios yra UTC, parodyk Lietuvos laiku (`Europe/Vilnius`), atsižvelgdamas į vasaros / žiemos laiką. Jei API neveikia, trumpai įvardyk klaidą, tęsk su kitais miestais ir neteik išgalvotų duomenų.

## Atsakymo formatas

Pateik trumpą lentelę šia tvarka:

| Miestas | Temperatūra | Oro sąlygos | Prognozės laikas |
|---|---|---|---|
| Vilnius | … °C | … | … |
| Kaunas | … °C | … | … |
| Klaipėda | … °C | … | … |
| Šiauliai | … °C | … | … |
| Panevėžys | … °C | … | … |

Po lentele parašyk: „Šaltinis: [meteo.lt](https://api.meteo.lt/). Tai prognozė artimiausiam laikui, ne tiesioginiai meteorologiniai matavimai.“ Įtrauk šaltinių nuorodas / citatas, jei jas palaiko naudojamas įrankis.

Nepridėk kitų miestų, nebent vartotojas to paprašo. Nevadink prognozės realiuoju laiku išmatuota temperatūra.
