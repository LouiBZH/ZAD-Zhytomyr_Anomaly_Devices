# ZAD - Zhytomyr Anomaly Devices

## Project

Stalker Anomaly mod adding three experimental devices (Topaz, Quartz, Beryl) for anomaly study and artifact manipulation. Running on xray-monolith engine, based on the hideout furniture mod framework.

## Mod Structure

```
gamedata/
  ├── configs/items/zad_devices.ltx          # Item definitions (inventory + placed)
  ├── configs/misc/zad_devices_spawn.ltx     # Spawn configs
  ├── configs/text/eng/st_zad_devices.xml    # Localization
  ├── scripts/
  │   ├── zad_devices.script                 # Main init & device registry
  │   ├── beryl_device.script               # Beryl device HF wrapper (charging logic)
  │   ├── (topaz_device.script)             # TODO
  │   └── (quartz_device.script)            # TODO
  ├── meshes/                                # Device models
  ├── textures/                              # Textures
  ├── sounds/                                # Audio
  └── spawns/                                # Spawn points
```

## Current Implementation

- **Beryl Device** fully implemented:
  - HF-compatible wrapper class extending `bind_hf_base.hf_binder_wrapper`
  - State machine: idle → charging (60s) → cooldown → ready → idle
  - Auto-selects most damaged perk artifact from inventory
  - 60-second charging with anomaly particle effects and sound
  - Cooldown based on original artifact condition (30-150s range)
  - Proper save/load via NET_Packet serialization
  - Prevent pickup while charging
- Topaz & Quartz: basic placeholders (placeable HF objects, no logic yet)
- All devices use `equipments\devices\radio\radio.ogf` as placeholder model

## Device Architecture

Each device has TWO config sections:
1. **Inventory item** (`[zad_device_beryl]`): `class = II_ATTACH`, uses HF placement system
2. **Placed world object** (`[placeable_zad_device_beryl]`): `script_binding = beryl_device.init`

## Beryl Device Details

- **State**: idle → charging (60s) → cooldown → ready → idle
- **Charging**: spawns particle effects in 20m radius, looping sound, 5 anomaly points
- **Cooldown**: `ceil((1.0 - original_condition) * 120) + 30` seconds (30-150s)
- **Retrieval**: player interacts during "ready" state → gets artifact at 100% condition
- **Persistence**: state saved via `save(stpk)` / `load(stpk)` using NET_Packet serialization
- **Perk artifact detection**: checks for `perk_artefact`, `af_perk`, `perk_artifact` in section name

## Next Steps

1. Import/create models from Stalker 2
2. Implement Topaz and Quartz device logic
3. Create proper artifact selection UI (currently auto-selects most damaged)
4. Add more anomaly effect variants
5. Configure hideout placement and trader lists
