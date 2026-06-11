# ZAD Mod Structure

## Directory Layout

```
gamedata/
├── configs/
│   ├── items/
│   │   └── zad_devices.ltx          # Item definitions (inventory + placed)
│   ├── misc/
│   │   └── zad_devices_spawn.ltx    # Spawn configurations
│   └── text/
│       └── eng/
│           └── st_zad_devices.xml   # English localization strings
├── scripts/
│   ├── zad_devices.script           # Main init & device registry
│   ├── beryl_device.script         # Beryl device HF wrapper (charging logic)
│   ├── (topaz_device.script)       # TODO
│   └── (quartz_device.script)      # TODO
├── meshes/
│   └── devices/                     # Device models (currently using radio model)
├── textures/                        # Device textures
├── sounds/                          # Device sound effects
└── spawns/                          # Spawn point definitions
```

## Files Overview

- **modinfo.json** — Mod metadata for Anomaly mod manager
- **zad_devices.ltx** — Item definitions (inventory items with `class = II_ATTACH` + placed world objects)
- **zad_devices_spawn.ltx** — Spawn section configurations
- **st_zad_devices.xml** — Localization strings (expandable for other languages)
- **zad_devices.script** — Core script with device registry and initialization
- **beryl_device.script** — Beryl device wrapper extending `bind_hf_base.hf_binder_wrapper`

## Device Architecture

Each device has two config sections:
1. **Inventory item** (e.g., `[zad_device_beryl]`): `class = II_ATTACH`, uses HF placement system via `use1_functor = placeable_furniture.place_item`, `placeable_section = placeable_zad_device_beryl`
2. **Placed world object** (e.g., `[placeable_zad_device_beryl]`): `class = physic_object`, with `script_binding` and `item_section` for pickup

## Beryl Device Implementation

The Beryl device is implemented as a wrapper class extending `bind_hf_base.hf_binder_wrapper`:
- **State machine**: idle → charging (60s) → cooldown → ready → idle
- **Artifact selection**: auto-selects most damaged perk artifact from inventory
- **Charging**: 60-second timer with particle effects and looping sound
- **Cooldown**: `ceil((1.0 - original_condition) * 120) + 30` seconds (30-150s range)
- **Persistence**: save/load via NET_Packet serialization (w_stringZ, w_float, etc.)

## Next Steps

1. Create/import device models (currently using radio.ogf placeholder)
2. Implement Topaz and Quartz device logic
3. Create proper artifact selection UI (currently auto-selects most damaged)
4. Add more anomaly effect variants
5. Configure hideout placement and trader lists
