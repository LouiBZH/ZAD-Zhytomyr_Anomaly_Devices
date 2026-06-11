# ZAD - Zhytomyr Anomaly Devices

## Project Overview

ZAD is a mod for Stalker Anomaly that adds three experimental devices for anomaly study and artifact manipulation, inspired by the Topaz Device from Stalker 2:

- **Topaz Device** — Primary anomaly study device (placeholder)
- **Quartz Device** — Secondary variant (placeholder)
- **Beryl Device** — Perk Artifact Recharger ✅ (fully implemented)

All devices use the **Hideout Furniture** placement system ([Aoldri/anomaly-hf](https://github.com/Aoldri/anomaly-hf)).

## Beryl Device — Perk Artifact Recharger

The Beryl device recharges perk artifacts ([themrdemonized/STALKER-Anomaly-Perk-Based-Artefacts](https://github.com/themrdemonized/STALKER-Anomaly-Perk-Based-Artefacts)).

### How It Works

1. **Place** the Beryl device in the world using HF's placement system
2. **Interact** (F key) → device scans your inventory for perk artifacts
3. Auto-selects the **most damaged** perk artifact
4. Artifact is removed from inventory, device **charges for 60 seconds**:
   - Anomaly particle effects spawn in a 20m radius
   - Looping charge sound plays
   - Anomaly points pulse and shift dynamically
5. **After 60s**: anomalies dissipate, artifact condition = 100%
6. **Device cooldown**: depends on original condition (30-150s)
7. **Interact again**: retrieve the recharged artifact at full condition

### State Machine

```
idle → charging (60s) → cooldown (30-150s) → ready → idle
```

## Current Status

- ✅ Mod structure initialized
- ✅ Item configurations (inventory + placed world objects)
- ✅ Localization framework set up
- ✅ Beryl device fully implemented (HF wrapper class)
- ⏳ Topaz/Quartz device logic (basic placeholders only)
- ⏳ Model creation/import from Stalker 2
- ⏳ Artifact selection UI (currently auto-selects)

## Installation

1. Requires **Hideout Furniture** mod ([anomaly-hf](https://github.com/Aoldri/anomaly-hf))
2. Requires **Perk-Based Artefacts** mod ([STALKER-Anomaly-Perk-Based-Artefacts](https://github.com/themrdemonized/STALKER-Anomaly-Perk-Based-Artefacts))
3. Copy the mod folder to your Anomaly `mods` directory
4. Enable in Anomaly's mod manager (ensure HF loads first)
5. Restart Anomaly

## Technical Details

- **Engine**: xray-monolith
- **Base Format**: Anomaly mod structure + HF placement
- **Placeholder Model**: `equipments\devices\radio\radio.ogf` (from hideout furniture)
- **Script System**: HF `bind_hf_base.hf_binder_wrapper` extension
- **Language Support**: English (expandable)

## File Structure

See `gamedata/README.md` for detailed directory layout.
