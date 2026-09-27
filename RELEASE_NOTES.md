# Death Telemetry v1.1.0

Release v1.1.0 of Death Telemetry for Minecraft 26.3 (Fabric).

Death Telemetry records pre-mortem player vitals and velocity data into an invulnerable "Autopsy Report" black box upon death, rendering an interactive flight-recorder dashboard with granular hover inspection.

---

## What's New in v1.1.0

- **Multi-Language Support (i18n)**:
  - Added native **Spanish** localization (`es_es`, `es_mx`, `es_ar`, `es_cl`, `es_ec`, `es_uy`, `es_ve`).
  - Added native **Simplified Chinese** localization (`zh_cn` / 简体中文).
  - All HUD dashboard titles, graph legends, buttons, coordinate and dimension indicators, timestamps, and hover inspection tooltips now dynamically adapt to your selected Minecraft client language.
  - Autopsy Report item names and item lore now adapt dynamically using translatable components.
- **Dynamic HUD Alignment**: Time scale labels and fatal incident markers now dynamically align to accommodate variable text lengths across languages.
- **Localized Damage & Dimension Attribution**: Standard environmental hazards (Fire, Lava, Suffocation, Drowning, Falling, Void, etc.) and dimensions (Overworld, The Nether, The End) are now fully translated.

---

## Core Features

- **10-Second Rolling Telemetry**: Records player status across the final 10 seconds (20 snapshots sampled at 2 Hz).
- **Health Line Graph**: Visualizes health trajectory (0 - 20 HP) with clear markers on damage events.
- **Y-Velocity Graph**: Plots vertical descent rate and jump arcs with ground calibration and freefall danger warnings.
- **X and Z Velocity Graph**: Overlapping dual-line graph displaying horizontal vectors (red for X, purple for Z) to analyze knockback and lateral velocity.
- **Precise Damage & Mob Attribution**: Identifies attacking mobs (Zombie, Skeleton, Creeper, etc.), direct projectiles, or environmental hazards.
- **Interactive Scrubber Tooltip**: Hover anywhere over the timeline to inspect exact coordinate, velocity, health, and damage details.
- **Invulnerable Black Box Item**: Protects against destruction in lava, fire, and explosion death scenarios.

---

## Compatibility

- Minecraft: 26.3
- Fabric Loader: >= 0.19.5
- Fabric API: compatible with 26.3
- Java: 25

---

## Files

- `death-telemetry-1.1.0.jar` - Production mod jar (client & server)
- `death-telemetry-1.1.0-sources.jar` - Source archive
