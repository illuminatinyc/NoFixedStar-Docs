# StingWasp Interior Reference

This file records the current StingWasp visual references and the as-built ship object data for the only active ship in the Godot project.

Companion tracker:

- `SHIP_TASKS.md`
- `STINGWASP_STRUCTURE.md`

## Visual Reference

- Hero exterior concept: `assets/ship/rustwing-hero.jpg`
- Side profile concept: `assets/ship/rustwing-side.jpg`
- Interior spine / cutaway reference: `assets/ship/rustwing-cutaway.svg`
- Canonical transport concept board: `playershipInternal.png`
- Canonical transport concept board alt: `playershipInternal2.png`
- Canonical design brief: `stingwaspDesignDev.txt`

Reference read:

- Hull language: battered ochre-painted plates over dark structural framing
- Interior tone: working independent transport with broader lived-in spaces, not clean sci-fi corridors
- Lighting: warm task strips and low ambient cabin light
- Surfaces: dark ribs, utility panels, exposed runs, storage built into the walls
- Layout target: a believable light transport with clear habitation, cargo, ops, and pressure-lock zones

## Current Ship Scene

- Root scene: `scenes/ship/StingWasp.tscn`
- Legacy retained scene: `scenes/ship/Rustwing.tscn`
- Root script: `src/NoFixedStar/Ship/ShipRoot.cs`
- Procedural interior assembler: `src/NoFixedStar/Ship/InteriorGreybox.cs`
- Room builders:
  - `src/NoFixedStar/Ship/ShipInteriorShellGreybox.cs`
  - `src/NoFixedStar/Ship/ShipCockpitGreybox.cs`
  - `src/NoFixedStar/Ship/ShipCabinGreybox.cs`
  - `src/NoFixedStar/Ship/ShipCargoGreybox.cs`
  - `src/NoFixedStar/Ship/ShipAirlockGreybox.cs`
  - `src/NoFixedStar/Ship/ShipExteriorHullGreybox.cs`
  - `src/NoFixedStar/Ship/ShipCompartmentSignageGreybox.cs`
- Shared greybox primitives: `src/NoFixedStar/Ship/ShipGreyboxPrimitives.cs`
- Layout constants: `src/NoFixedStar/Ship/ShipLayout.cs`
- Material helpers: `src/NoFixedStar/Art/SurfaceMats.cs`

## Interior Spine Layout

Units are meters. Forward is `+Z`.

| Module | Z Range | Width | Height | Notes |
|---|---:|---:|---:|---|
| Cockpit | `11.5` to `14.5` | `8.4` | `2.4` | Pilot seat, copilot seat, layered bridge consoles, avionics transition |
| Cabin | `6.5` to `11.5` | `8.4` | `2.4` | Crew berths, galley, commons, hygiene and med-locker cues |
| Cargo Bay | `0.5` to `6.5` | `8.4` | `2.6` | Workbench, cargo pad, side racks, center lane, tie-down and crane cues |
| Airlock | `-2.0` to `0.5` | `6.2` | `2.4` | Inner/outer door, suit lockers, pressure controls, lock threshold |

Shared constants:

- Door width: `1.8`
- Door height: `2.1`
- Wall thickness: `0.12`

## Current Interior Treatment

The interior pass now adds:

- Structural ribs and ceiling spine in each room
- Conduit runs and deck tracks along the spine
- Warm strip lighting instead of only flat omni fill
- Recessed pressure-hatch portals between the main compartments
- Cockpit avionics massing, layered bridge consoles, canopy framing, and monitor glow
- Cockpit exterior shell trimmed into side cheeks plus slimmer brow/chin framing so the seated pilot sightline stays open
- Cabin sub-zones for crew berths, galley, commons, head, and med-locker cues
- Cargo restraint language with side racks, center cargo lane, tie-down rails, and overhead handling structure
- Airlock utility lockers, pressure controls, and pressure-threshold treatment

## Gameplay-Critical Anchors

These should remain stable unless we intentionally rework navigation or interaction:

- `InteriorAnchor/PlayerSpawnCabin`
- `InteriorAnchor/CrewSpawn`
- `InteriorAnchor/Modules/Cockpit/PilotSeat`
- `InteriorAnchor/Modules/Cockpit/StandSpawn`
- `InteriorAnchor/Modules/Cabin/CrewSleep`
- `InteriorAnchor/Modules/Cabin/CrewEat`
- `InteriorAnchor/Modules/CargoBay/CrewWork`
- `InteriorAnchor/Modules/CargoBay/CargoSnap`
- `InteriorAnchor/Modules/Airlock/PlayerExitSpawn`
- `InteriorAnchor/Modules/Airlock/PlayerEnterSpawn`

## Current Constraint

This is still a procedural greybox ship built from `CsgBox3D` and simple collision. The active runtime implementation now lives in `StingWasp.tscn`, with `Rustwing.tscn` retained only as legacy fallback content. The design authority is the canonical StingWasp transport, which is the only active ship in the current project phase. The interior is now split into room-specific builders under a single assembler while preserving the navigation spine and gameplay-critical anchors.
