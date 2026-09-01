# No Fixed Star

![StingWasp transport](https://ibb.co/album/zVNJZv)

**No Fixed Star** is a first-person space-western game about finding a crew, finding work, and keeping an aging ship flying. The player lives aboard a working transport, takes contracts between hard-used stations, manages fuel, repairs, cargo, and pay, and gradually builds a life around the people who share the ship.

The current playable prototype is deliberately small: one ship, two stations, one repeatable cargo loop, and one crew member. It exists to prove that the core fantasy is fun before the project expands.

## The Vision

The long-term game is a character-driven spacefaring life sim, not a combat-first space game. Its center is the ship: a place to fly, maintain, sleep, work, argue, recover, and leave again.

Players should be able to:

- captain a distinct transport ship with a walkable, useful interior
- take freight work, meet deadlines, get paid, and keep the ship supplied
- travel between stations, settlements, planetary environments, and open space
- recruit crew with skills, needs, schedules, personal tradeoffs, and relationships
- respond to contracts, complications, world events, faction pressure, and consequences
- eventually engage with ship maintenance, exploration, combat, boarding, and a wider living world

Those broader systems are planned for later phases. They are **not** requirements for the first playable release.

## Current Prototype

The active player ship is the **StingWasp**, a used industrial transport with four connected areas:

- cockpit / bridge
- habitation deck with bunks, galley, commons, head, and medical storage
- cargo and operations deck
- airlock

The current playable loop is:

1. Start aboard the StingWasp.
2. Walk to the cockpit, sit, undock, and fly with assisted 6DOF controls.
3. Reach Prospect or Waystation 12 and dock.
4. Leave through the airlock, enter the station, and talk to its contact.
5. Accept a cargo job, carry it to the destination, and receive a payout.
6. Refuel, repair, take the return job, and save progress.

Current content scope:

- 1 active ship: `StingWasp`
- 2 locations: `Waystation 12` and `Prospect`
- 1 MVP cargo contract: `cargo_standard`
- 1 MVP crew member: `Ryn Calder`

## MVP Status

The eight systems required for the first playable are implemented. The remaining release work is end-to-end playtesting, bug fixing, and polish against the acceptance gates.

| MVP item | Status | Current implementation |
|---|---|---|
| Walkable ship interior | Implemented | StingWasp cockpit, cabin, cargo, and airlock greybox |
| Sit, launch, and fly | Implemented | Assisted 6DOF flight, fuel use, seated controls |
| Second destination | Implemented | Prospect in the shared space sandbox |
| Dock and talk | Implemented | Docking, station interiors, broker and clerk dialogue |
| Cargo contract | Implemented | Delivery state flow, deadline, cargo, radio warning |
| One crew member | Implemented | Ryn needs, behavior, movement policy, dialogue |
| Payout, fuel, repair | Implemented | Credits, salary, refuel, repair, inverse job flow |
| Save and load | Implemented | Versioned saves, slots, autosave on dock, Continue |

### Remaining First-Slice Work

- complete and record the full manual acceptance run without debug recovery
- fix any reproducible blocker found during prototype testing
- verify save/load in docked, active-contract, and mid-flight states
- verify Ryn resumes correctly after a real dock snap
- complete screenshot-led cockpit, signage, and collision regression QA
- package and test a clean Windows prototype before external distribution

The canonical StingWasp greybox task list is complete. Future ship work should be targeted polish or post-MVP production art, not a second ship or a new layout pass.

## Roadmap

The project has **15 total development phases**, numbered 0 through 14. The roadmap describes the whole game; it does not authorize building later features before the first playable passes its gates.

| Phase | Focus | Status |
|---|---|---|
| 0 | Preproduction: design, technical plan, visual language, prototypes | Substantially complete for the MVP |
| 1 | Core foundation: input, interaction, save framework, data, debug tools | Implemented for the MVP |
| 2 | Ship prototype: interior, cockpit, flight, docking, camera | Implemented for the StingWasp MVP; visual QA active |
| 3 | Crew simulation: needs, schedules, jobs, relationships, recruitment | MVP subset implemented: Ryn needs and behavior |
| 4 | Economy: credits, cargo, fuel, repairs, salaries, markets | MVP subset implemented |
| 5 | Contract system: objectives, deadlines, rewards, complications | MVP subset implemented: one cargo loop and radio complication |
| 6 | Dynamic narrative: world, crew, faction events and consequences | Planned after MVP |
| 7 | Combat: weapons, damage, targeting, boarding | Planned after MVP |
| 8 | World: stations, settlements, planets, space, populations | MVP subset implemented: two stations and a space sandbox |
| 9 | Vertical slice: integrate and prove all intended systems | Active: first playable acceptance and polish |
| 10 | Production: expand ships, worlds, NPCs, contracts, art, and audio | Planned |
| 11 | Alpha: feature complete | Planned |
| 12 | Beta: content complete, optimization, bugs, balance | Planned |
| 13 | Release candidate: QA, accessibility, localization, performance | Planned |
| 14 | Launch: PC first; console review afterward | Planned |

## What Is Explicitly Out Of Scope Right Now

The first playable does not include combat, boarding, planetary walking, settlements, recruitment, factions, reputation networks, multiplayer, mod support, multiple active ship classes, procedural event direction, or generative dialogue. These are future design goals, not current promises.

## Technology

- Godot `4.7.2` Mono / .NET
- C# / `.NET 8`
- Jolt Physics
- Windows target, keyboard and mouse first

The application entrypoint is `scenes/main/Boot.tscn`. Gameplay code is organized under `src/NoFixedStar/` by domain: core state, player, ship, flight, world, contracts, crew, dialogue, economy, persistence, UI, and debug tooling.

## Running Locally

Requirements:

- Windows
- Godot `4.7.2` Mono build
- `.NET 8 SDK`

Open the editor:

```bat
edit.bat
```

Run the project:

```bat
play.bat
```

Build the solution:

```powershell
dotnet build NoFixedStar.sln
```

Create a tester package:

```bat
tools\package_prototype.bat
```

The packaging script produces `dist\NoFixedStarPrototype-win64.zip`. Close a running prototype before rebuilding it.

## Controls

| Input | On foot | Seated |
|---|---|---|
| `WASD` | Move | Thrust |
| Mouse | Look | Ship attitude |
| `E` | Interact | Roll right |
| `Q` | - | Roll left |
| `F` | - | Stand |
| `R` | - | Dock / undock |
| Mouse wheel | - | Adjust forward thrust |
| `X` | - | Cut thrust |
| `Space` | Jump | - |
| `Shift` | Sprint | - |
| `Esc` | Pause / close dialogue | Pause |

Debug controls: `F3` overlay, `F7` refill fuel, `F8` skip-dock recovery, `F9` contract completion recovery.

## Project Documentation

- [DEVPLAN.md](DEVPLAN.md): locked first-playable scope, technical design, MVP gates
- [theplan.txt](theplan.txt): long-term identity, world vision, and production roadmap
- [SHIP_TASKS.md](SHIP_TASKS.md): completed StingWasp implementation tracker and residual QA
- [SHIP_REFERENCE.md](SHIP_REFERENCE.md): current as-built StingWasp reference

## Contributing Scope

Keep changes aligned with the current MVP gate. Preserve the active StingWasp, gameplay anchors, save compatibility, and the one-ship scope unless a change is explicitly approved. Do not add later-phase systems simply because they appear in the long-term vision.
