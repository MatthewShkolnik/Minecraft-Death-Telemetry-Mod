# Death Telemetry

Death Telemetry is a server-and-client Fabric mod for Minecraft 26.3 that captures pre-mortem telemetry in a zero-overhead rolling ring buffer. When a player dies, an invulnerable Autopsy Report "Black Box" item drops at the exact point of death. Right-clicking the item opens an authentic, interactive flight recorder HUD that visualizes the victim's final 10 seconds.

---
<p align="center">
  <a href="https://buymeacoffee.com/MatthewShkolnik" target="_blank">
    <img src="https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me A Coffee">
  </a>
  <a href="https://www.curseforge.com/members/MatthewShkolnik/projects" target="_blank">
    <img src="https://img.shields.io/badge/CurseForge-Profile-f16436?style=for-the-badge&logo=curseforge&logoColor=white" alt="CurseForge">
  </a>
</p>
---

![Death Telemetry Banner](banner.jpg)

---

## Features

- **Pre-Mortem Flight Recording**: Continuously tracks vital signs and movement trajectories during the final 10 seconds leading up to death (20 snapshots sampled at 2 Hz / every 10 ticks).
- **Invulnerable Autopsy Report Drop**: Spawns an item at the exact death coordinates that is completely immune to lava, fire, and explosions, ensuring recovery in extreme death scenarios.
- **Interactive Telemetry Dashboard**:
  - **Health Graph**: A dedicated line graph tracking player health from 0 to 20 HP with distinct damage event tick markers.
  - **Y-Velocity Graph**: Visualizes vertical speed, fall rates, and jump arcs with ground velocity calibration and freefall warnings.
  - **X and Z Velocity Graph**: An overlapping dual-line graph displaying horizontal motion vectors (red for X-velocity, purple for Z-velocity) to analyze knockback and directional movement.
  - **Detailed Entity and Hazard Attribution**: Resolves the exact mob or player attacker (such as Zombie, Skeleton, Creeper, or custom-named mobs), projectile types, or environmental hazard names (such as Fire, Lava, Fall, The Void, Drowning, etc.).
  - **Interactive Hover Inspection**: Hover over any column on the telemetry timeline to view exact values for that half-second window, including time before death, health, velocity components, and damage breakdown.
- **Multi-Language Support (i18n)**:
  - **English** (`en_us`)
  - **Spanish** (`es_es`, `es_mx`, `es_ar`, `es_cl`, `es_ec`, `es_uy`, `es_ve`)
  - **Simplified Chinese** (`zh_cn` / 简体中文)
  - Full client-side localization for the flight recorder HUD, graph titles and axes, hover tooltips, item name and lore, dimension names, and environmental damage causes.

---

## Requirements

- **Minecraft**: 26.3
- **Mod Loader**: Fabric Loader (>= 0.19.5)
- **Fabric API**: Installed for Minecraft 26.3
- **Java**: 25

---

## Installation

### Client Installation
1. Install Minecraft 26.3 with Fabric Loader.
2. Download `death-telemetry-1.2.0.jar` from the GitHub Releases page.
3. Download the matching **Fabric API** for Minecraft 26.3.
4. Place both `.jar` files into your `.minecraft/mods` directory:
   - **Windows**: `%appdata%\.minecraft\mods`
   - **macOS**: `~/Library/Application Support/minecraft/mods`
   - **Linux**: `~/.minecraft/mods`
5. Launch Minecraft using the Fabric profile.

### Server Installation
1. Set up a Minecraft 26.3 dedicated server using Fabric Loader.
2. Place `death-telemetry-1.2.0.jar` and the Fabric API jar into the server's `mods/` directory.
3. Restart the server.

*Note: While Death Telemetry operates server-side to record telemetry data and drop the black box, clients must also have the mod installed to open and view the interactive telemetry GUI.*

---

## In-Game Usage

### Obtaining the Black Box
- **Survival Gameplay**: Whenever a player dies, an Autopsy Report black box is automatically dropped at their death location. The item is invulnerable and will not burn in lava or be destroyed by explosions.
- **Commands**: Operators can generate test reports using:
  ```text
  /give @p death_telemetry:autopsy_report
  ```

### Inspecting the Report
1. Place the `Autopsy Report` into your main hand.
2. **Right-Click** to open the telemetry screen.
3. Review the header details (victim name, timestamp, death coordinates, dimension, fatal cause).
4. Analyze the three telemetry graphs (Health, Y-Velocity, X & Z Velocities).
5. Move the cursor horizontally across the graphs to inspect granular data for each point in time.

---

## Configuration

Death Telemetry creates a `config.json` file in your `.minecraft/config/death_telemetry/config.json` directory (or `.minecraft/config/death_telemetry.json`). You can customize any of the following settings to your wish:

```json
{
  "snapshotCount": 20,
  "sampleIntervalTicks": 10,
  "dropOnDeath": true,
  "invulnerableItem": true,
  "glowingItem": false,
  "preventDespawn": true,
  "respectKeepInventory": false,
  "logDeathCoordinates": true,
  "showVictimInLore": true,
  "showCauseInLore": true,
  "showCoordinatesInLore": true,
  "freefallWarningThreshold": -0.6,
  "pauseGameOnScreen": false
}
```

### Options Breakdown

| Setting | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `snapshotCount` | Integer | `20` | Number of telemetry snapshot samples retained in the rolling buffer (5–600). |
| `sampleIntervalTicks` | Integer | `10` | Frequency of telemetry recordings in game ticks (10 ticks = 0.5s / 2 Hz; 20 ticks = 1.0s / 1 Hz). |
| `dropOnDeath` | Boolean | `true` | Whether the Autopsy Report black box is dropped when a player dies. |
| `invulnerableItem` | Boolean | `true` | Whether the dropped black box item is immune to damage from lava, fire, and explosions. |
| `glowingItem` | Boolean | `false` | Whether the dropped black box item has an outline glow effect in the world. |
| `preventDespawn` | Boolean | `true` | Whether the dropped black box item never despawns (prevents vanilla 5-minute despawn timer). |
| `respectKeepInventory` | Boolean | `false` | If `true`, does not drop the report when the `keepInventory` gamerule is enabled. |
| `logDeathCoordinates` | Boolean | `true` | Logs death coordinates and report creation to the server console. |
| `showVictimInLore` | Boolean | `true` | Shows victim name in the item tooltip lore. |
| `showCauseInLore` | Boolean | `true` | Shows fatal cause / death message in the item tooltip lore. |
| `showCoordinatesInLore` | Boolean | `true` | Shows death coordinates in the item tooltip lore (useful to disable on PvP servers). |
| `freefallWarningThreshold`| Decimal | `-0.6` | Vertical velocity descent rate (m/s) that triggers the freefall danger warning in the GUI. |
| `pauseGameOnScreen` | Boolean | `false` | In singleplayer, whether opening the autopsy report screen pauses the game. |

### In-Game Reload
Server operators and singleplayer players can reload the configuration at runtime without restarting the server:
```text
/death_telemetry reload
```

---

### To-Do
1. Make the Autopsy Report item craftable for situations where it is unrecoverable.
2. [Completed] Add a config file to change preferences (`config.json`).
3. Create a menu to analyze from every death in the world.
4. Add a more interactive and fun way to view data.

---

### Use in Projects
You are free to use this mod in any modpack or compilation and may also share this product in any way adhering to the MIT License. If you do use this pack in another project or modpack, please provide credit to me, thanks. :)

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
