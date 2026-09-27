# Death Telemetry v1.2.0

Release v1.2.0 of Death Telemetry for Minecraft 26.3 (Fabric).

Death Telemetry records pre-mortem player vitals and velocity data into an invulnerable "Autopsy Report" black box upon death, rendering an interactive flight-recorder dashboard with granular hover inspection.

---

## What's New in v1.2.0

- **Configurable Settings via `config.json`**:
  - Full configuration support with automated JSON generation and deserialization in `.minecraft/config/death_telemetry/config.json` (or `.minecraft/config/death_telemetry.json`).
  - **Telemetry Customization**:
    - `snapshotCount`: Adjustable buffer capacity (5 to 600 snapshots).
    - `sampleIntervalTicks`: Sampling rate in game ticks (1 to 100 ticks).
  - **Item Drop & World Behavior**:
    - `dropOnDeath`: Toggle whether autopsy reports drop on death.
    - `invulnerableItem`: Toggle immunity to explosions, fire, and lava.
    - `glowingItem`: Toggle outline glow effect on dropped black box entities.
    - `preventDespawn`: Prevent black box items from despawning after 5 minutes.
    - `respectKeepInventory`: Honor the `keepInventory` gamerule.
  - **Item Lore Customization**:
    - `showVictimInLore`, `showCauseInLore`, and `showCoordinatesInLore` toggles (ideal for PvP servers wishing to hide coordinates).
  - **Client HUD Preferences**:
    - `freefallWarningThreshold`: Custom descent velocity threshold for warnings.
    - `pauseGameOnScreen`: Singleplayer pause screen toggle.
  - **Live Reload Command**:
    - `/death_telemetry reload`: Reload configuration on active servers without restarting.
- **Dynamic HUD Scaling**:
  - Time scale axes dynamically adjust according to configured recording duration.

---

## Core Features

- **Rolling Telemetry Buffer**: Zero-overhead in-memory rolling ring buffer tracking pre-mortem vitals.
- **Health Line Graph**: Visualizes health trajectory (0 - 20 HP) with clear markers on damage events.
- **Y-Velocity Graph**: Plots vertical descent rate and jump arcs with ground calibration and freefall danger warnings.
- **X and Z Velocity Graph**: Overlapping dual-line graph displaying horizontal vectors (red for X, purple for Z) to analyze knockback and lateral velocity.
- **Precise Damage & Mob Attribution**: Identifies attacking mobs, direct projectiles, or environmental hazards.
- **Interactive Scrubber Tooltip**: Hover anywhere over the timeline to inspect exact coordinate, velocity, health, and damage details.
- **Multi-Language Support (i18n)**: English, Spanish, and Simplified Chinese.

---

## Compatibility

- Minecraft: 26.3
- Fabric Loader: >= 0.19.5
- Fabric API: compatible with 26.3
- Java: 25

---

## Files

- `death-telemetry-1.2.0.jar` - Production mod jar (client & server)
- `death-telemetry-1.2.0-sources.jar` - Source archive
