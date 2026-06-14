# ZAD - Zhytomyr Anomaly Devices

## Project Overview

ZAD is a mod for Stalker Anomaly that adds three experimental devices for anomalous study and artifact manipulation, inspired by the TOPAZ-2M Scanner from Stalker 2:

- **Quartz Device** — Upcoming
- **TOPAZ-1M Scanner** — Perk Artifact Recharger ✅ (fully implemented)
- **Beryl Device** — Upcoming

All devices use the **Hideout Furniture** placement system ([Aoldri/anomaly-hf](https://github.com/Aoldri/anomaly-hf)).

## Quartz Device — Anomaly artifact scanner

A device that you'll be able to place in any major anomaly field, and will warn you when an artifact spawns in it, and show you its nature.

## TOPAZ-1M Scanner — Perk Artifact Recharger

An experimental anomalous study device designed to recharge perk artifacts. Once placed, select a perk artifact from your inventory and the device will draw from the Zone's connection to the Noosphere to restore it to full condition over a minute. Be careful though, as the device is very unstable and if you take too much time getting it back, you risk having done all this for nothing. The strain put on the Topaz will force you to let it cool down between uses.

## Beryl Device — Anomaly stimulator

A device that you'll be able to place in any major anomaly field, allowing you to feed it an artifact and force the anomaly to spawn an artifact from its pool. The rarer the artifact you sacrifice, the better the reward. But in the end, it'll all come down to luck...

## Requirements

**Hideout Furniture** ([anomaly-hf](https://github.com/Aoldri/anomaly-hf))
**Perk-Based Artefacts** ([STALKER-Anomaly-Perk-Based-Artefacts](https://github.com/themrdemonized/STALKER-Anomaly-Perk-Based-Artefacts))
**Dynamic Anomalies Overhaul** (https://github.com/themrdemonized/Dynamic-Anomalies-Overhaul)
Latest modded exes for DLTX
Tested on GAMMA, which includes all these natively. Should work on Anomaly 1.5.3 with those prerequisites.

## Installation

Drop in MO2 at any priority, there should be no overwrites

## To do

- 
- 


## Technical Details

- **Engine**: xray-monolith
- **Base Format**: Anomaly mod structure + HF placement
- **Script System**: HF `bind_hf_base.hf_binder_wrapper` extension
- **Language Support**: English (expandable)
- Some references :
   - Engine documentation : https://github.com/themrdemonized/xray-monolith
   - Anomaly modding book : https://github.com/TheParaziT/anomaly-modding-book
   - X-Ray engine documentation in russian : https://xray-engine.org/index.php?title=%D0%97%D0%B0%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F_%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0
   - Stalker GAMMA github : https://github.com/Grokitach/Stalker_GAMMA
   - Dynamic Anomalies Overhaul : https://github.com/themrdemonized/Dynamic-Anomalies-Overhaul
