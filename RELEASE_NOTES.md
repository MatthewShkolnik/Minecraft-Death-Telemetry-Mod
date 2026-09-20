# Death Telemetry v1.0.0

Initial release of Death Telemetry for Minecraft 26.3 (Fabric).

Death Telemetry records pre-mortem player vitals and velocity data into an invulnerable "Autopsy Report" black box upon death, rendering an interactive flight-recorder dashboard with granular hover inspection.

---

## Release Highlights

- **10-Second Rolling Telemetry**: Records player status across the final 10 seconds (20 snapshots sampled at 2 Hz).
- **Health Line Graph**: Visualizes health trajectory (0 - 20 HP) with clear markers on damage events.
- **Y-Velocity Graph**: Plots vertical descent rate and jump arcs with ground calibration and freefall danger warnings.
- **X and Z Velocity Graph**: Overlapping dual-line graph displaying horizontal vectors (red for X, purple for Z) to analyze knockback and lateral velocity.
- **Precise Damage & Mob Attribution**: Identifies attacking mobs (Zombie, Skeleton, Creeper, etc.), direct projectiles, or formatted environmental hazards (Fire, Lava, Fall, The Void, Drowning, etc.).
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

- `death-telemetry-1.0.0.jar` - Production mod jar (client & server)
- `death-telemetry-1.0.0-sources.jar` - Source archive
