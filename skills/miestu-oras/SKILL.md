---
name: miestu-oras
description: Pateikia 5 didžiausių Lietuvos miestų (Vilniaus, Kauno, Klaipėdos, Šiaulių ir Panevėžio) artimiausią oro temperatūrą ir orų sąlygas, pirmiausia ieškodamas oficialiuose meteo.lt miestų puslapiuose per žiniatinklio paiešką, tikrindamas prognozės datą ir laiką. Naudok, kai vartotojas prašo „miestu-oras“, „miestų oras“, šių miestų temperatūrų ar orų palyginimo.
---

# Miestų oras

## Esminė taisyklė

Kiekvieną kartą iš naujo ieškok duomenų internete. **Pagrindinis gavimo kelias – paieška ir oficialių meteo.lt puslapių skaitymas, ne tiesioginė API užklausa.** Neapsiribok vienu paieškos rezultatu. Paieškos ištrauka gali būti savaičių senumo: niekada nelaikyk jos dabartiniais orais be aiškiai patvirtinto prognozės laiko. Nepateik išgalvotų reikšmių.

## Miestai

Fiksuota tvarka: Vilnius, Kaunas, Klaipėda, Šiauliai, Panevėžys. Vietovių identifikatoriai: `vilnius`, `kaunas`, `klaipeda`, `siauliai`, `panevezys`.

## Duomenų gavimo seka (vykdyk kiekvienam miestui atskirai)

1. Nustatyk dabartinę Lietuvos datą ir laiką `Europe/Vilnius`, įskaitant vasaros ir žiemos laiko pasikeitimus.
2. Interneto paieškos įrankiu ieškok `site:meteo.lt/prognozes/lietuvos-miestai/ <miestas> <šiandienos data> orai temperatūra` ir `site:meteo.lt/home?area=<slug> <miestas> orai`. Jei galima, atverk oficialų puslapį tiesiogiai: `https://www.meteo.lt/prognozes/lietuvos-miestai/?area=<slug>` arba `https://www.meteo.lt/home?area=<slug>`. Pirmenybę teik pilnam puslapiui su prognozės valandų lentele, ne paieškos ištraukai.
3. Patikrink, kad išrinktos temperatūros ir sąlygų pora priklauso būtent pasirinktam miestui ir konkrečiai datai bei valandai. Rinkis artimiausią **nepraėjusią** prognozės valandą. Jei puslapio data neatitinka dabartinės datos (arba artimiausios būsimos valandos jau kitą dieną), rezultato nenaudok. Paieškos „crawled“ data nėra prognozės data. Ignoruok archyvinius puslapius, pasenusias indeksuotas ištraukas ir kelių dienų senumo prognozes.
4. Jei svetainė negrąžina tinkamo įrašo, papildomai mėgink oficialų meteo.lt JSON endpointą `https://api.meteo.lt/v1/places/<slug>/forecasts/long-term` per prieinamą interneto skaitymo įrankį. Iš `forecastTimestamps` pasirink mažiausią `forecastTimeUtc`, kuris nėra ankstesnis už dabartinį UTC laiką; temperatūra: `airTemperature`, sąlygos: `conditionCode`. Neinterpretuok paieškos sistemos talpykloje esančio istorinio JSON kaip gyvos prognozės.
5. Jei nei vienas oficialus meteo.lt kelias nepateikia aiškiai laiku pažymėtų duomenų, rašyk „duomenų nėra“, o ne spėk. Nenaudok kito tiekėjo (pvz., Open-Meteo) neinformavęs vartotojo ir negavęs jo leidimo: šis skillas žada meteo.lt duomenis.

## Kokybės patikra

- Kiekvienam miestui atskirai patikrink: vietovę, prognozės datą, valandą, temperatūrą °C ir sąlygų aprašymą. Nepriskirk vieno miesto orų kitam.
- HTML prognozės lentelės reiškinių aprašymus gali nuskaityti iš piktogramų alternatyvaus teksto; neimk „juntamosios temperatūros“ vietoje oro temperatūros.
- API kodus versk: `clear` – giedra; `partly-cloudy` – mažai debesuota; `cloudy-with-sunny-intervals` – debesuota su pragiedruliais; `cloudy` – debesuota; `light-rain` – nedidelis lietus; `rain` – lietus; `heavy-rain` – smarkus lietus; `thunder` – perkūnija; `isolated-thunderstorms` – trumpas lietus su perkūnija; `thunderstorms` – lietus su perkūnija; `heavy-rain-with-thunderstorms` – smarkus lietus su perkūnija; `light-sleet` – nedidelė šlapdriba; `sleet` – šlapdriba; `freezing-rain` – lijundra; `hail` – kruša; `light-snow` – nedidelis sniegas; `snow` – sniegas; `heavy-snow` – smarkus sniegas; `fog` – rūkas; nežinomi kodai – „nenustatyta“.
- Jei įmanoma, cituok konkretaus miesto oficialų puslapį. Aiškiai nurodyk, kuriems miestams duomenys nepatvirtinti.

## Atsakymas

| Miestas | Temperatūra | Oro sąlygos | Prognozės laikas |
|---|---|---|---|
| Vilnius | … °C | … | … |
| Kaunas | … °C | … | … |
| Klaipėda | … °C | … | … |
| Šiauliai | … °C | … | … |
| Panevėžys | … °C | … | … |

Po lentele pridėk „Šaltinis: [meteo.lt](https://www.meteo.lt/). Tai artimiausio laiko prognozė, o ne tiesiogiai išmatuota temperatūra.“ Jei paieškos indeksas neleidžia patvirtinti naujumo, aiškiai paaiškink ribojimą. Negarantuok 100 % pasiekiamumo.
