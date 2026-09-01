1. **No Fixed Star**

   * One-sentence pitch
   * Current development status
   * Hero image / StingWasp image
   * Godot version and core technology

2. **The Vision**

   * “Find a crew. Find a job. Keep flying.”
   * Space-western sandbox philosophy
   * Player fantasy
   * Why WaywardSky exists
   * What differentiates it from a conventional space combat game

3. **Core Gameplay Loop**

   * Find contracts
   * Prepare the ship
   * Assemble/manage crew
   * Fly
   * Dock / land
   * Complete jobs
   * Deal with consequences
   * Repair/refuel/resupply
   * Keep flying

4. **The StingWasp STW-T01**

   * 31 m transport
   * Exterior
   * Cockpit
   * Deck 1
   * Deck 2
   * Service deck
   * Cargo systems
   * Engineering
   * Airlocks
   * Landing gear
   * Docking
   * Crew spaces
   * Ship traversal
   * Interactive systems

5. **Planned Feature Matrix**

   * Flight
   * Walking aboard ships
   * Seamless ship interiors
   * Crew
   * NPCs
   * Contracts/jobs
   * Cargo
   * Docking
   * Stations
   * EVA
   * Engineering
   * Ship damage
   * Repairs
   * Fuel/resources
   * Economy
   * Navigation
   * Exploration
   * Reputation/factions
   * Persistence
   * Save/load
   * etc.

   And critically, each gets a status:

   `✅ Complete`
   `🟢 Implemented / Iterating`
   `🟡 In Development`
   `🔵 Planned`
   `⚪ Future`

6. **Current Vertical Slice**

   This deserves its own major section because that is what you're actually building now.

   The README should explain what the MVP proves:

   > Player enters the StingWasp → walks its interior → enters the cockpit → takes control → flies → approaches a station → docks → leaves the cockpit → traverses the ship → accesses cargo / station gameplay.

   That gives anyone visiting GitHub an immediate understanding of what "MVP" means.

7. **Development Roadmap**

   Not merely "Phase 1, Phase 2."

   Something more like:

   ```text
   PHASE 0  — Project Foundation
   PHASE 1  — Player Foundation
   PHASE 2  — StingWasp Ship Foundation
   PHASE 3  — Walkable Ship Interior
   PHASE 4  — Flight Systems
   PHASE 5  — Docking Systems
   PHASE 6  — Station Foundation
   PHASE 7  — Cargo & Jobs
   PHASE 8  — Crew & NPC Systems
   PHASE 9  — Ship Engineering
   PHASE 10 — Damage / Repair / Survival
   PHASE 11 — Economy & Persistence
   PHASE 12 — World / Sector Simulation
   PHASE 13 — Vertical Slice Integration
   PHASE 14 — Content Expansion
   PHASE 15 — Production Hardening
   PHASE 16 — Alpha
   PHASE 17 — Beta
   PHASE 18 — Release
   ```

   Those names/count are only an illustration until I see your canonical roadmap. I won't quietly promote my example into project law.

8. **Completed Work**

   This is especially important.

   Instead of a vague percentage, show actual evidence:

   ```text
   STINGWASP
   ✅ Ship root architecture
   ✅ FlightBody
   ✅ FlightController
   ✅ DockingSystem
   ✅ EngineLoop
   ✅ InteriorAnchor
   ✅ NavigationRegion3D
   ✅ PlayerSpawnCabin
   ✅ CrewSpawn
   ✅ CargoHold
   ✅ Interior greybox framework
   ✅ Cockpit greybox
   ✅ Cabin greybox
   ✅ Cargo greybox
   ✅ Airlock greybox
   ✅ Exterior hull greybox framework
   🟡 Production StingWasp geometry
   ```

   Those are grounded in the ship structure/files you've shown in this conversation, but I'd verify them against the repository before declaring them completed in the final README.

9. **Architecture**

   Show the actual system relationship:

   ```text
   WaywardSky
       │
       ├── Player
       │
       ├── Ships
       │     └── STW-T01 StingWasp
       │           ├── Flight
       │           ├── Interior
       │           ├── Cargo
       │           ├── Docking
       │           ├── Engineering
       │           └── Crew
       │
       ├── Stations
       ├── NPC / Crew
       ├── Contracts
       ├── Economy
       ├── World Simulation
       └── Persistence
   ```

10. **Technology**

    * Godot 4.7
    * C# / .NET
    * procedural/CSG greybox systems where applicable
    * asset pipeline
    * data architecture
    * development platform

11. **Design Principles**

    This is where the project gets personality:

    > **The ship is a place, not a menu.**

    > **Cargo physically exists.**

    > **Crew physically occupies the world.**

    > **Travel matters.**

    > **Maintenance matters.**

    > **Jobs create stories rather than simply awarding currency.**

    > **The player should become attached to their ship because they live aboard it.**

    That communicates WaywardSky better than fifty feature bullets.

12. **Repository Structure**

13. **Build / Run Instructions**

14. **Contribution / Current Needs**

    This could explicitly include your current need for a 3D modeller for the StingWasp, with the canonical drawings/specifications available.

15. **Long-Term Vision**

    Explain what WaywardSky becomes after the vertical slice rather than letting visitors assume the StingWasp demo *is* the whole game.

The really useful part is that we can make the top of the README immediately communicate development state:

```text
WAYWARD SKY
Find a crew. Find a job. Keep flying.

Engine        Godot 4.7 / C#
Stage         MVP Vertical Slice
Primary Ship  STW-T01 StingWasp
Platform      PC
Status        Active Development

CURRENT DEVELOPMENT TARGET
──────────────────────────────────────────
Playable StingWasp Vertical Slice

Player
  ↓
Walkable StingWasp
  ↓
Cockpit
  ↓
Flight
  ↓
Station Approach
  ↓
Docking
  ↓
Ship Traversal
  ↓
Cargo / Contract Interaction
