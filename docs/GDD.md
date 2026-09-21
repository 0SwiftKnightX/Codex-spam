# Master Game Design Document

**Project:** Codex-spam  
**Document:** Master Game Design Document (GDD)  
**Status:** Living design document — foundation pass  
**Platform target:** Android  
**Genre:** 3D action RPG / open-world survival / civilization & construction RPG  
**Primary perspective:** Third-person exploration and combat  

---

## 1. Vision

Codex-spam is a large-scale 3D Android action RPG built around exploration, fast third-person combat, survival logistics, recruitable companions, player construction, civilization development, and long-term world progression.

The player begins in a protected central hub while the outside world is toxic and dangerous. From the hub, the player builds a party, manages equipment and carrying capacity, ventures into the hazardous world, gathers resources, fights enemies, develops technology, constructs settlements and structures, and progressively expands access to the world.

The long-term goal is a scalable game framework capable of supporting very large environments, multiple floors/regions, expanding technology trees, player-created structures, companions, NPC communities, and continuing content updates.

---

## 2. Design Pillars

### 2.1 Player-Made Progression
The player should meaningfully create, improve, repair, recruit, build, and organize their own progression.

### 2.2 Exploration With Consequences
Leaving safety has logistical consequences. Equipment, weight, supplies, durability, companions, and environmental hazards matter.

### 2.3 Fast Action Combat
Combat should emphasize responsive third-person movement, lock-on targeting, mobility, attacks, defense, and encounters that can continue dynamically in the open world.

### 2.4 Living Party System
NPCs and mercenaries are persistent members of the player's organization. They can accompany the player, live in owned housing, or be assigned elsewhere.

### 2.5 Build and Upgrade
Construction, equipment, civilization technology, crafting, and infrastructure should form interconnected progression systems.

### 2.6 Expandable World
The initial development target contains three floors/major world layers. Future updates can add additional floors, regions, enemies, systems, and progression.

---

## 3. Core Gameplay Loop

1. Begin at the main hub.
2. Prepare equipment, supplies, party, and carrying capacity.
3. Select a destination or objective.
4. Leave the protected hub.
5. Explore the toxic outside world.
6. Gather resources and discover locations.
7. Fight enemies and other threats.
8. Manage equipment durability and gas-mask condition.
9. Recruit or meet NPCs and mercenaries.
10. Return to safety or establish/expand infrastructure.
11. Craft, repair, upgrade, build, and research.
12. Assign party members and supplies.
13. Increase civilization and technology capability.
14. Unlock deeper/larger areas.
15. Repeat with increasing scale and complexity.

---

## 4. World Structure

### 4.1 Main Hub

Everyone begins at a central protected hub.

The hub is the safe organizational center for:
- Party management
- Mercenary recruitment
- Housing access
- Inventory management
- Equipment preparation
- Crafting
- Technology progression
- Civilization progression
- Construction
- World travel/preparation

### 4.2 Toxic Outside World

The world outside the protected hub is toxic and unsafe without appropriate respiratory protection.

The gas mask is therefore both:
- Survival equipment
- A logistical resource

Gas masks can become dirty through use outside.

### 4.3 Floors

The world is structured into major floors/regions.

Initial development scope:
- Floor 1
- Floor 2
- Floor 3

The architecture must allow later updates to introduce additional floors without redesigning the entire game.

---

## 5. Gas Mask & Environmental Survival

A new player receives a brand-new gas mask in a protective case.

The case and gas mask become inventory objects.

The system tracks:
- Gas-mask condition
- Dirt/contamination
- Weight
- Inventory location
- Equipment state

The player must decide how much protective equipment and supplies to carry.

Future expansion may include:
- Cleaning
- Replacement filters
- Protective upgrades
- Environmental resistance
- Specialized masks
- Repair/maintenance stations

---

## 6. Inventory & Carrying Capacity

Items have weight.

Player carrying capacity is determined by character statistics and can be increased through progression.

Potential capacity modifiers include:
- Character stats
- Equipment
- Pets
- Companions
- Special carriers
- Technology
- Civilization upgrades

The inventory system must distinguish between:
- Personal carried inventory
- Equipped items
- Stored items
- Carrier inventories
- Housing/settlement storage
- World containers

---

## 7. M.U.L.E. Carrier System

### 7.1 Identity

**M.U.L.E.** is a large military AI carrier machine.

Physical concept:
- Large machine
- Four legs
- Heavy-duty construction
- Designed to carry substantial supplies
- Operates as a persistent world entity

### 7.2 Logistics

M.U.L.E. dramatically expands expedition carrying capacity.

It can carry:
- Resources
- Equipment
- Crafting materials
- Supplies
- Quest/objective items
- Other approved inventory categories

### 7.3 Failure

M.U.L.E. can become damaged, disabled, or stuck in the world.

When disabled:
- It remains at its world location.
- Its carried supplies remain associated with it.
- The player can return to repair/retrieve it.

### 7.4 Abandon/Return Command

If the player cannot or does not want to retrieve M.U.L.E., the player can command it to:
1. Drop all carried supplies at the current location.
2. Return to an appropriate safe destination.

This creates a meaningful logistics choice rather than deleting the carrier.

### 7.5 Related Carrier Entities

Other carrier entities may use similar behavior.

Pets or companion-based carriers may:
- Follow the player
- Carry limited supplies
- Become separated or disabled
- Require recovery
- Provide specialized bonuses

---

## 8. Character System

Characters are fully developed stylized 3D characters rather than stick figures.

The visual direction supports:
- Stylized 3D characters
- Cell-shaded presentation
- Multiple animation styles
- 3D pixel-inspired characters
- Colorful environments
- Strong readable silhouettes

The exact final art direction remains open during early development.

---

## 9. Camera & Movement

### Exploration

The player uses a third-person free camera while exploring.

The player can:
- Run
- Navigate freely
- Explore open environments
- Interact with world objects
- Enter and leave combat

### Combat Lock-On

When the player locks onto an enemy, monster, opponent, or other valid combat target:
- Camera behavior becomes combat-oriented.
- Camera remains positioned behind/around the player and target.
- Player movement and attacks prioritize the locked target.

The player is not permanently trapped in combat.

Open-world encounters can be escaped by running away, although enemies may pursue.

---

## 10. Combat Direction

Combat is a fast third-person action-RPG system.

Core goals:
- Responsive controls
- Target lock-on
- Melee and/or ranged attacks
- Defensive actions
- Mobility
- Enemy pursuit
- World-space combat
- Character abilities
- Equipment-based progression

Combat implementation must remain modular so additional weapons, skills, enemies, effects, and combat mechanics can be added without rewriting the foundation.

---

## 11. Party System

The player can build a persistent party from:
- Hired mercenaries
- Recruitable NPCs
- Other future companion types

### 11.1 Mercenary Guild

A mercenary guild exists in a less reputable part of town, associated with a bar.

Recruitment flow:
1. Player speaks to the bartender.
2. Player asks about finding a mercenary.
3. Bartender directs the player to a book/list.
4. Player selects a mercenary.
5. Player pays the bartender.
6. The bartender instructs the player to go outside.
7. The selected mercenary joins the party shortly afterward.

The system must not require the player to physically chase the mercenary down.

If the player runs away, the mercenary uses a catch-up/spawn/fast-travel mechanism to join the party.

### 11.2 NPC Recruitment

For ordinary recruitable NPCs:
1. Talk to the NPC.
2. Ask the NPC to join.
3. If accepted, the conversation closes.
4. The NPC becomes a party member.

### 11.3 Persistence

Party members remain permanent until:
- They die, or
- The player explicitly asks them to leave.

This persistence is a core design rule.

---

## 12. Housing

If the player owns a house, party members can be assigned to it.

House capacity depends on house type.

The player can own multiple houses.

The player can assign different NPCs/party members to different houses.

Potential future housing functions:
- Party rest
- Storage
- Crafting
- Production
- NPC interaction
- Companion management
- Defensive upgrades
- Settlement specialization

---

## 13. Civilization System

The game includes a civilization-development system inspired by civilization strategy mechanics.

Civilization progression governs the development of the player's society and infrastructure.

Possible categories:
- Infrastructure
- Production
- Defense
- Resource processing
- Transportation
- Construction
- Research
- Social development
- Specialized technologies

Civilization progression should create meaningful tradeoffs rather than simply providing a linear list of stronger upgrades.

---

## 14. Technology & Upgrade Trees

The game uses interconnected upgrade systems inspired by survival/building progression.

Potential technology branches include:
- Weapons
- Armor
- Crafting
- Construction
- Resource processing
- Machines
- Power
- Transportation
- Survival
- Gas-mask technology
- M.U.L.E. upgrades
- Companion systems
- Civilization systems
- Combat abilities

Technology should unlock new capabilities, not only larger numerical values.

---

## 15. Building & Construction

Construction is a major progression system.

Players should eventually be able to construct:
- Buildings
- Housing
- Workshops
- Storage
- Production facilities
- Defensive structures
- Infrastructure
- Civilization facilities

Construction progression is connected to technology and available resources.

The underlying architecture should support expansion without requiring every building to be hard-coded individually.

---

## 16. Crafting & Resource Economy

Resources obtained from exploration can be used for:
- Crafting
- Repair
- Construction
- Equipment upgrades
- Technology
- Civilization development
- Carrier maintenance
- Housing
- Infrastructure

Resource categories and recipes will be defined in the Content Bible and implementation specifications.

---

## 17. NPC & Companion Behavior

Companion architecture should support:
- Follow
- Wait
- Defend
- Fight
- Move to housing
- Assigned jobs
- Recovery
- Equipment
- Inventory
- Death/persistence rules
- Relationship/progression systems

The architecture should separate character data from AI behavior so the same character framework can support different roles.

---

## 18. Enemy & World Threats

Enemies and environmental threats exist throughout the world.

Threat types may include:
- Hostile creatures
- Monsters
- Human opponents
- Environmental hazards
- Toxic areas
- Special encounters
- Boss encounters

Enemies should be designed around readable combat roles rather than simple stat inflation.

---

## 19. Visual Identity

The visual target is stylized 3D rather than photorealism.

References for visual exploration include:
- Fortnite-style stylized 3D character presentation
- Cell shading
- 3D pixel-inspired characters
- Colorful stylized environments
- Multiple compatible 3D animation styles

These are reference points, not instructions to copy protected characters, assets, or designs.

The project must use original characters, assets, names, environments, animations, and implementation.

---

## 20. Inspiration Map

The following works are design references only:

- Mega Man Battle Network — systems/world/gameplay inspiration
- Dark Cloud — progression/world structure inspiration
- Dragon Ball Xenoverse 2 — third-person action combat and lock-on inspiration
- Diablo 3 — 3D action-RPG presentation and progression inspiration
- Fable — interactive 3D world and NPC interaction inspiration
- Fortnite — large map scale and stylized character/environment references
- Age of Mythology — civilization development inspiration
- Rust — building and technology progression inspiration
- ARK — survival, crafting, technology, and progression inspiration

The project is an original work. References must not be implemented as direct copies.

---

## 21. Initial Development Target

The first playable development target should establish the foundation rather than attempt the entire final game at once.

### Prototype priorities

1. Android application launches reliably.
2. Third-person 3D character can move.
3. Third-person camera works.
4. Basic world loads.
5. Basic interaction system works.
6. Inventory foundation works.
7. Equipment foundation works.
8. Gas-mask item exists.
9. Basic toxic-world condition exists.
10. Basic enemy exists.
11. Lock-on combat foundation works.
12. Basic party/NPC framework exists.
13. Basic M.U.L.E. carrier framework exists.
14. Basic building/crafting data architecture exists.
15. Save/load foundation exists.

### Initial world target

The broader development target is three playable floors/major world layers.

The game should become playable as early as possible for development testing. The lead developer should be able to install and test working builds throughout development.

---

## 22. Architecture Principles

The codebase must favor modular systems.

Major systems should be independently testable and communicate through well-defined interfaces/data structures.

Avoid:
- Giant monolithic managers
- Hard-coded content where data-driven content is practical
- Tight coupling between UI and game logic
- Systems that cannot be extended
- Premature implementation of every planned feature

Prioritize:
- Stable core systems
- Data-driven content
- Save compatibility
- Performance on Android
- Incremental development
- Clear ownership of systems
- Automated validation where practical

---

## 23. Android-First Requirements

The project is intended for Android.

Development decisions must account for:
- Mobile CPU/GPU limitations
- Memory limits
- Touch controls
- Variable device performance
- Battery consumption
- Asset size
- Loading times
- Save reliability
- Offline-capable core gameplay where practical

Performance must be treated as an architectural requirement from the beginning, not a final optimization pass.

---

## 24. Save & Persistence

Persistent systems are fundamental to the game.

The save architecture must eventually support:
- Player character
- Inventory
- Equipment
- Party members
- NPC states
- Housing assignments
- M.U.L.E. location/state
- World discoveries
- Construction
- Technology progression
- Civilization progression
- Quest/objective state
- Floor/world progression

World persistence must be designed so that destroyed, moved, built, recruited, or assigned entities can retain state when appropriate.

---

## 25. Development Rules

1. This GDD is a living source of truth for high-level game design.
2. New systems should be documented before or alongside implementation.
3. Major design changes should be recorded in a decision log.
4. Prototype work must not silently redefine established mechanics.
5. Inspirations are references, not assets or direct copies.
6. Android performance is a first-class requirement.
7. New content should be designed to scale with future floors and updates.
8. Systems should be modular and data-driven where practical.
9. The playable build should remain testable throughout development.
10. Do not add major scope simply because a related feature sounds interesting; document and prioritize it first.

---

## 26. Open Design Questions

These items remain intentionally unresolved and should be decided during development:

- Final game title
- Final engine/framework
- Exact Android minimum version/device profile
- Multiplayer requirements, if any
- Exact combat weapon categories
- Character stat formulas
- Enemy roster
- Exact civilization branches
- Exact technology trees
- Building-piece rules
- Crafting recipes
- Gas-mask durability/cleaning mechanics
- M.U.L.E. exact capacity and upgrade progression
- Death and recovery rules
- Quest structure
- Floor-specific themes
- Final art pipeline
- Monetization model, if any

Unresolved questions must not be treated as finalized requirements until explicitly decided.

---

## 27. Development Status

**Current phase:** Concept / GDD foundation.

**Immediate objective:** Establish the master design document and technical foundation before large-scale implementation.

**Initial repository:** 0SwiftKnightX/Codex-spam

**Target:** A scalable Android 3D action RPG that can grow from a small playable prototype into a large multi-floor world.

---

## 28. Document Ownership

This document is maintained as the project's master design reference.

**Initial authoring:** GPT-5.6 Luna, based on the lead developer's stated design requirements.

**Lead developer:** Travis Marshall

**Status:** Living document — subject to explicit design decisions and documented revisions.
