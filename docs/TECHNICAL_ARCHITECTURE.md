# Technical Architecture

**Project:** Codex-spam  
**Platform:** Android  
**Status:** Pre-implementation architecture  
**Owner:** Travis Marshall

## 1. Architecture Goal

Build the game as a modular, data-driven Android 3D RPG that can begin as a small playable prototype and scale toward the full design without replacing its core systems.

The architecture must prioritize:
- Android performance
- modular systems
- persistent world state
- data-driven content
- deterministic save/load behavior
- clear separation between gameplay systems and presentation
- incremental development and testing

## 2. Engine / Framework Status

The final engine/framework has **not** been locked.

The architecture therefore defines system boundaries first. Engine-specific implementation should be selected only after validating:
1. Android 3D performance
2. third-person controller support
3. animation and character support
4. world streaming
5. save/persistence options
6. touch/controller input
7. building/construction feasibility
8. development workflow on the user's available hardware

No engine dependency should be introduced into the design documents as if it were final until this decision is made.

## 3. Core System Layers

### Presentation Layer
Responsible for:
- rendering
- camera
- animation
- UI
- VFX/audio presentation
- input presentation

Presentation must consume gameplay state rather than become the authoritative owner of game rules.

### Gameplay Layer
Responsible for:
- player movement
- combat
- targeting/lock-on
- inventory
- equipment
- stats
- party
- NPCs
- enemies
- quests
- crafting
- building
- civilization
- technology
- environmental hazards

### World Layer
Responsible for:
- world regions
- floors
- dungeon/area state
- interactable objects
- resources
- construction state
- persistent world changes
- M.U.L.E. location/state

### Persistence Layer
Responsible for:
- save slots
- serialization
- versioning
- migration
- validation
- recovery from incomplete/corrupt writes

## 4. Data-Driven Design

Major content should be represented as data rather than hardcoded behavior wherever practical.

Examples:
- items
- weapons
- armor
- NPC definitions
- enemy definitions
- companions
- pets
- M.U.L.E. configurations
- recipes
- building pieces
- technology nodes
- civilization technologies
- quests
- floors
- resources
- status effects

A content definition should identify properties and references; systems should interpret those definitions.

## 5. Entity Identity

Persistent entities require stable identifiers.

Examples:
- player ID
- NPC ID
- party member ID
- M.U.L.E. ID
- item instance ID when item state matters
- building instance ID
- world object ID
- quest/objective ID

Stable IDs prevent save data from depending on scene/object ordering.

## 6. Inventory Architecture

Inventory should distinguish:
- item definitions
- item instances
- stackable quantities
- equipment state
- durability/condition where applicable
- weight
- container ownership

Carrying capacity should be calculated from player stats plus valid modifiers from equipment, pets, companions, and carrier systems.

The gas mask and its case are inventory objects and therefore participate in weight/carry rules.

## 7. Party Architecture

Party members should be independent persistent entities.

Party state should include:
- identity
- recruitment source
- current status
- equipment
- inventory when applicable
- combat role
- relationship/state data
- housing assignment
- death/leave state

Recruitment methods:
- paid hiring through the mercenary system
- direct NPC recruitment

Leaving a party and permanent death must be explicit state transitions.

## 8. M.U.L.E. Architecture

M.U.L.E. is a persistent carrier entity.

Required state:
- location
- supplies
- condition
- operational/broken state
- destination
- current command
- ownership

Commands must include:
- follow
- hold
- transport
- drop supplies and return

A broken M.U.L.E. remains at its world location until repaired/recovered or otherwise handled by the defined gameplay rules.

## 9. World Persistence

The save system must be capable of recording persistent world changes without serializing an entire rendered scene blindly.

Prefer compact state records such as:
- object ID
- transform
- ownership
- condition
- construction state
- inventory/content
- destroyed/removed flag
- assignment
- discovered state

World streaming and persistence should be designed together.

## 10. Combat Architecture

Combat should be modular.

Core interfaces/concepts:
- actor
- target
- attack/action
- damage event
- defense/resistance
- status effect
- ability
- cooldown/resource
- hit confirmation
- death/downed state

Lock-on is a targeting/camera mode, not the sole source of combat logic.

Open-world movement must allow disengagement from combat.

## 11. Building Architecture

Building should use modular construction data.

A placed structure should record:
- piece definition
- unique instance ID
- transform
- owner
- attachment/support data
- condition/HP
- upgrades
- contained inventory/workstation state when applicable

Construction rules should be validated by gameplay systems rather than trusted solely to the UI.

## 12. Civilization + Technology

Technology progression should be represented as persistent nodes and unlock states.

Separate but interconnected progression domains may include:
- civilization
- combat
- weapons
- crafting
- construction
- infrastructure
- world/floor progression

Permanent choices and tradeoffs should be represented in data so they can be tested and balanced.

## 13. Toxic Environment / Gas Mask

Environmental exposure should be a gameplay system.

The system should track:
- toxic exposure
- protection state
- mask condition
- mask consumption/wear rules
- safe/unsafe zones

The gas mask should not be a cosmetic-only object.

## 14. Save Format

The initial save format should be:
- versioned
- human-debuggable where practical
- schema-driven
- tolerant of missing optional fields
- validated before loading

Recommended high-level save domains:
- metadata
- player
- inventory
- equipment
- party
- housing
- world
- construction
- M.U.L.E.
- quests
- technology
- civilization
- discoveries

## 15. Save Safety

Use an atomic or recoverable write strategy.

Never assume a save completed successfully merely because the UI initiated it.

The implementation should support:
- temporary write
- validation
- replacement/commit
- recovery from previous valid save

## 16. Android Requirements

The project must account for:
- touch controls
- varying aspect ratios
- variable device performance
- memory pressure
- thermal throttling
- battery consumption
- suspend/resume
- limited storage
- offline play where applicable

Performance budgets should be established before large-scale content production.

## 17. Prototype Strategy

Do not implement the entire game at once.

First prove the architecture with a small vertical slice containing:
1. one controllable third-person character
2. one small 3D area
3. basic movement
4. one enemy
5. basic lock-on
6. one attack
7. inventory
8. one item with weight
9. gas mask state
10. one recruitable NPC
11. one basic buildable object
12. save/load

Once this slice survives repeated save/load and Android testing, expand the systems.

## 18. Testing Strategy

Every major system should have:
- isolated logic tests where practical
- integration tests
- save/load tests
- Android device tests

Critical regression tests:
- save then reload
- recruit NPC then reload
- move M.U.L.E. then reload
- build object then reload
- destroy object then reload
- change technology then reload
- alter inventory weight then reload
- enter/exit toxic area
- die/leave party member according to rules

## 19. Development Rule

**Do not solve scale by prematurely building scale.**

The first implementation should prove the architecture with a small amount of content. Systems must be designed so that additional floors, NPCs, enemies, weapons, technologies, structures, and civilizations can be added through data and modular code.

## 20. Current Status

- GDD created
- Architecture document created
- Engine/framework decision pending
- Prototype implementation pending
- Android target confirmed
- Full production scope remains intentionally expandable

## 21. Ownership

This document records the architecture direction for Codex-spam.

**Document owner:** Travis Marshall  
**Prepared/structured by:** GPT-5.6 Luna  
