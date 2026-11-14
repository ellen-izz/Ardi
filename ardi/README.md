# Ardi (أرضي): farming advice built on satellite data

**Ardi** ("my land" in Arabic) is a decision-support web app that helps farmers in the Levant and nearby regions pick better crop rotations, know when to sow, and plan how much to water. Its recommendations come from NASA Earth observation data.

Built for the **2026 NASA Space Apps Challenge** under the challenge **"Field Shift: Adapting Farms with NASA Data."**

> ⚠️ Ardi supports a farmer's decisions. It does not replace their experience or a local agronomist.

---

## The problem

Farmers are dealing with shifting temperatures, unpredictable rain, water shortages and declining soil health. Picking the next crop is hard. A crop that builds soil in one place may use too much water elsewhere, repeat a pest cycle, or fall outside the safe growing season.

## What Ardi does

- **Compares rotation plans.** It sets the farmer's own plan (or last season's crop) side by side with the **two best plans from NASA data** for their land. If the farmer hasn't decided yet, it shows the three best.
- **Explains every recommendation.** Each crop gets a verdict (*suits your land / possible with cautions / not recommended*) with plain reasons:
  - temperature at sowing compared with the germination range
  - how much of the crop's water need the season's rain covers
  - early-season frost risk and late-season heat stress
  - rotation rules: avoids repeating a crop or plant family, credits legumes for nitrogen fixation, ground cover against erosion, and drought or salinity tolerance
  - fit with the farmer's priority: saving water, improving soil, income, or the household table
- **Best sowing window.** It finds the best time to sow each crop from 25 years of climate data and compares it with the month the farmer usually sows.
- **Weekly irrigation advice.** It uses FAO-56 evapotranspiration: crop need, minus effective rain, minus stored soil moisture, given in mm and in m³ for the whole land. Rainfed farms see their water shortfall instead.
- **5-day weather warnings** for frost, heat waves, strong wind and heavy rain, with practical actions. Alerts can optionally go out on WhatsApp.
- **"What next?"** It suggests the following season's crop family so the rotation keeps going.
- **Chat assistant** that answers questions like *"When should I plant chickpea?"* or *"How much should I water this week?"* from the same NASA data. It accepts typed or voice questions (voice works in Chrome).
- **Ministry of Agriculture dashboard.** Farmers can choose to share anonymized totals (registered lands by crop, reported problems). Small counts are hidden to protect privacy, and no names are shown.
- **Arabic-first and bilingual.** Full Arabic (right-to-left) and English interface.

## Honest about uncertainty

Every result has a **"What we do not know"** section:

- Climate data is a regional estimate (a grid cell about 55 km wide), not a measurement of the farmer's field.
- Soil salinity, nitrogen and texture are not measured.
- Market data is approximate.
- Crop information shows an **agronomist-review badge**. It reads "not reviewed" until a real agronomist approves it.

## Data and methods

| Source | Use |
|---|---|
| **NASA POWER** (MERRA-2), daily 2000–2025 | Temperature, rainfall, solar radiation, humidity and wind, turned into monthly climatologies |
| **FAO-56** Penman-Monteith | Reference and crop evapotranspiration for water need and irrigation |
| Elevation correction | Temperature adjusted to the land's altitude |
| Rule-based scoring | Crop–climate fit, rotation rules and farmer priorities, with a visible reason behind every score |

**Covered regions with real NASA data:** 12 Palestinian governorates, plus Irbid (Jordan), Hauran (Syria), Bekaa (Lebanon), and Siverek and Diyarbakır (Türkiye). Other locations use approximate values, and the app says so.

## Try it

Ardi is a single, self-contained HTML file with no build step and no server.

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

Then open `ardi/index.html` in a modern browser (Chrome recommended for voice input).

- A **demo mode** is built in. The demo phone number shows on the sign-in screen, and the verification code appears as a message at the top of the screen.
- Settings include a **demo weather switch** (heavy rain, cold spell with frost) so you can see how warnings and advice react.
- Data is stored locally in your browser (`localStorage`). An internet connection is only needed for web fonts and the map.

## Project structure

```
ardi/
└── index.html   # the whole app: UI, Arabic/English text, NASA climate data, scoring and irrigation logic
README.md
```

## Roadmap

- Add more NASA datasets: SMAP soil moisture, GPM rainfall, MODIS/Landsat NDVI, ECOSTRESS heat stress, GRACE groundwater trends
- Field-level maps of erosion risk, water-stress hotspots and frost-prone areas
- Agronomist review of the crop tables for each region
- Real SMS/WhatsApp delivery and a backend for multi-device accounts
- Local market prices

## Challenge

[NASA Space Apps Challenge 2026: Field Shift: Adapting Farms with NASA Data](https://www.spaceappschallenge.org/)

## Acknowledgements

- **NASA POWER** project (NASA Langley Research Center) for open climate data
- **FAO** Irrigation and Drainage Paper 56 for the evapotranspiration method
- The farmers whose experience inspired this tool