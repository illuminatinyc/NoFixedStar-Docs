# StingWasp Ship Task Tracker

Last updated: `2026-08-31`

This tracker is the working backlog for the StingWasp ship build inside the current Godot project. It exists to keep the ship effort grounded in the canonical StingWasp brief while preserving gameplay-critical anchors already wired into the MVP.

## Scope

- Build the StingWasp as the canonical and only active player ship for the current project phase, using the current implementation as its staging container
- Keep existing gameplay anchors, player flow, and current MVP systems intact unless a targeted move is necessary
- Stage the broader canonical ship inside the current scene architecture first, then split into richer room/system scenes later if needed
- Treat `Rustwing.tscn` as inactive legacy content, not the active runtime ship scene

## Canon Sources

- `stingwaspDesignDev.txt`
- `playershipInternal.png`
- `playershipInternal2.png`
- `SHIP_REFERENCE.md`

## Locked Constraints

- Do not remove unrelated gameplay systems
- Do not break these anchors unless intentionally reworked:
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
- Current implementation remains a procedural greybox in `src/NoFixedStar/Ship/InteriorGreybox.cs`
- Active runtime scene path is `scenes/ship/StingWasp.tscn`
- `scenes/ship/Rustwing.tscn` is retained only as legacy fallback content for now

## Current State

Status: `Canonical StingWasp Greybox Task List Complete`

Completed:

- Widened the interior footprint beyond the original cramped courier layout
- Rebuilt room transitions as recessed pressure-hatch portals with visible open passage
- Improved material language toward a used industrial transport look
- Reworked the cockpit into a broader bridge layout with pilot seat, copilot seat, layered consoles, canopy framing, and avionics transition cues
- Added mouse-wheel forward thrust and a seated throttle HUD readout
- Split the cabin into clearer functional zones: berths, galley, commons, head, med locker
- Split cargo into clearer working zones: hold, center lane, ops lockers, workbench, tie-down cues
- Added airlock pressure-lock cues, suit lockers, and local signage
- Updated `SHIP_REFERENCE.md` to reflect the current widened as-built ship
- Locked the design direction around StingWasp as the only active ship, with any second ship postponed to a later project phase
- Split cockpit, cabin, cargo, and airlock composition into dedicated greybox builder files while keeping `InteriorGreybox.cs` as the ship assembler
- Split the exterior hull shell into its own StingWasp greybox builder so cockpit sightline tuning stays isolated from room assembly
- Split the reusable room shell and hatch construction into its own builder so `InteriorGreybox.cs` stays focused on assembly
- Split the ship-wide compartment identity signage into its own builder so `InteriorGreybox.cs` stays orchestration-only
- Switched the live runtime ship instantiation from `Rustwing.tscn` to `StingWasp.tscn`

In progress:

- Residual visual QA from future in-engine screenshots
- Final screenshot-led polish on cockpit sightlines and compartment signage

## Task List

### Phase 1: Canon Greybox Alignment

- [x] Broaden the canonical deck footprint inside the existing scene
- [x] Replace flat door cutouts with recessed pressure hatches
- [x] Separate habitation and cargo/ops visually
- [x] Add visible room and sub-zone labels
- [x] Validate the wider layout against actual in-game movement and camera framing

### Phase 2: Cockpit / Bridge

- [x] Restore functional seated cockpit camera
- [x] Add transparent canopy glazing and stronger forward framing
- [x] Add layered bridge consoles and copilot presence
- [x] Add avionics-access transition cues behind the bridge
- [x] Tune seated view against screenshots from pilot camera
- [x] Reduce any remaining visual obstruction in the forward sightline
- [x] Decide whether the cockpit needs a distinct captain/navigator split beyond the current greybox

### Phase 3: Habitation Deck

- [x] Push bunks against the walls and preserve a center walk lane
- [x] Stage galley and commons as distinct functional spaces
- [x] Add head and med-locker cues
- [x] Decide whether to stage a captain berth or keep current berth arrangement for MVP
- [x] Add more believable built-in storage and wall utility without cluttering the walk lane
- [x] Review crew navigation around the new props in-engine

### Phase 4: Cargo / Ops Deck

- [x] Keep a broad central cargo lane
- [x] Add workbench and ops-locker read
- [x] Add tie-down and crane cues
- [x] Review cargo snap readability and physical clearances in-engine
- [x] Decide whether to stage a stronger workshop corner inside the current cargo volume
- [x] Decide whether to hint a secondary/starboard access path visually before a true second airlock exists
- [x] Decide how to keep the current StingWasp implementation stable while postponing any second-ship work

### Phase 5: Airlock / EVA

- [x] Preserve main airlock gameplay flow
- [x] Add suit-locker identity and pressure-lock controls
- [x] Review player enter/exit spawn framing against the widened greybox
- [x] Decide whether to visually stage outer docking hardware more strongly from the interior

### Phase 6: Documentation / Production Prep

- [x] Maintain an as-built reference file
- [x] Create a ship-specific task tracker
- [x] Capture a screenshot-driven review set for cockpit, cabin, cargo, and airlock
- [x] Translate the current greybox into a more formal room/system breakdown if the MVP scene begins to get too dense
- [x] Draft a future split plan for `Cockpit`, `Cabin`, `CargoBay`, and `Airlock` sub-builders or scenes if needed

## Residual QA

The implementation backlog is complete. Remaining work is ordinary visual/playtest QA:

1. Recheck seated pilot and standing bridge screenshots after future cockpit edits.
2. Recheck sign scale and prop intrusion after any new room pass.
3. Re-evaluate whether a technical rename away from `Rustwing` is worth the churn after MVP stabilization.

## Work Log

### 2026-08-31

- Widened room and airlock beam in `ShipLayout`
- Rebuilt bulkhead transitions as recessed pressure hatches
- Iterated the cockpit layout multiple times to restore seated functionality and reduce cramped sightlines
- Carved the exterior cockpit shell away from the seated forward view by splitting the nose mass into side structure and slimmer upper/lower framing
- Added wheel-based seated thrust control and HUD throttle display
- Added room-level and sub-zone signage throughout the ship
- Reduced intrusive floating room labels and unified local signage through shared greybox primitives
- Extracted the exterior hull shell into its own builder after trimming the forward cockpit shell for visibility
- Extracted the reusable room shell and hatch construction into its own builder to keep the StingWasp assembler lean
- Extracted ship-wide compartment signage into its own builder to finish isolating presentation from assembly
- Added a live `StingWasp.tscn` ship scene and pointed runtime loading at it
- Staged habitation details for galley, commons, head, and med storage
- Staged cargo details for center lane, tie-down language, crane read, and ops zone
- Staged airlock pressure controls and lock signage
- Refreshed `SHIP_REFERENCE.md` to reflect the current as-built state
- Narrowed the ship effort to StingWasp as the only active development vessel
- Closed the remaining ship design backlog items with documented design decisions and split-plan notes
- Extracted room-specific cockpit, cabin, cargo, and airlock builders to keep the ship implementation modular

## Primary Implementation Files

- `src/NoFixedStar/Ship/ShipLayout.cs`
- `src/NoFixedStar/Ship/InteriorGreybox.cs`
- `src/NoFixedStar/Ship/ShipCockpitGreybox.cs`
- `src/NoFixedStar/Ship/ShipCabinGreybox.cs`
- `src/NoFixedStar/Ship/ShipCargoGreybox.cs`
- `src/NoFixedStar/Ship/ShipAirlockGreybox.cs`
- `src/NoFixedStar/Ship/ShipExteriorHullGreybox.cs`
- `src/NoFixedStar/Ship/ShipInteriorShellGreybox.cs`
- `src/NoFixedStar/Ship/ShipCompartmentSignageGreybox.cs`
- `src/NoFixedStar/Ship/ShipGreyboxPrimitives.cs`
- `src/NoFixedStar/Art/SurfaceMats.cs`
- `src/NoFixedStar/Player/SeatedController.cs`
- `src/NoFixedStar/UI/HudPresenter.cs`
- `SHIP_REFERENCE.md`
- `STINGWASP_STRUCTURE.md`
