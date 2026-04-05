# Project Arasmas — Buildings: Great Britain

> **Purpose:** Complete list of all buildings, their stats, slots, worker positions, and delivery paths for the Great Britain civilization.
> **Last Updated:** 2026-04-04
> **Status:** Template created — Populating Era 1 (Primitive Age)
> **Related Files:**
> - `researchGB.md` — Research items that unlock/improve buildings
> - `toolsandequipmentGB.md` — Tools and equipment used in building slots
> - `plans.md` — Master game plan and system descriptions
> - `schedule.md` — Development schedule and current phase

---

## Cross-Reference System

All entries across project files use a **Ref ID** system for linking.

**Format:** `era[N].[building].[category].[item]`

| Scope | Format | Example |
|-------|--------|---------|
| Building | `era[N].[buildingname]` | `era1.huntinghut` |
| Tool (building-specific) | `era[N].[building].tool.[name]` | `era1.huntinghut.tool.spear` |
| Equipment (building-specific) | `era[N].[building].equip.[name]` | `era1.smokehouse.equip.dryingrack` |
| Research (building-specific) | `era[N].[building].res.[name]` | `era1.huntinghut.res.basictracking` |
| Shared tool (multi-building) | `era[N].tool.[name]` | `era1.tool.spear` |
| Shared equipment (multi-building) | `era[N].equip.[name]` | `era1.equip.carrysack` |
| Shared research | `era[N].res.[name]` | `era1.res.firemaking` |
| Worker role | `era[N].[building].role.[name]` | `era1.huntinghut.role.hunter` |
| Delivery route | `era[N].route.[from]-to-[to]` | `era1.route.huntinghut-to-smokehouse` |

**How to search:** To find everything related to a building, search for its Ref ID prefix (e.g. `era1.huntinghut`) across all project files. Every related tool, equipment, research, and route will contain this prefix in either its own Ref ID or its `Used In` / `Related Refs` fields.

---

## Slot Types — Definitions

Each building has a combination of slot types. Slots define what can be placed in a building and how many.

| Slot Type | Description | Example |
|-----------|-------------|---------|
| **Worker** | A position for an NPC worker. Each worker slot has a defined role. | Hunter, Butcher, Carrier |
| **Tool** | An item a worker uses directly to perform their task. One tool per worker per role. | Spear, Bone Scraper, Digging Stick |
| **Equipment** | An item that improves the building's operation. Not held by a worker — installed in the building. | Drying Rack, Storage Basket, Fire Pit |
| **Storage** | Capacity for holding input materials, output products, or both. Measured in units. | Raw Meat storage, Pelt storage |
| **Delivering** | A connection to another building. Defines what resource flows out and where it goes. | Meat → Smoke House, Pelts → Pelt Processing |

---

## Building Template

```
### [Ref ID] Building Name

**Era Introduced:** [Era number and name]
**Build Cost:** [Resources/currency required to construct]
**Build Time:** [Time to construct, if applicable]
**Prerequisites:** [Other buildings, research, or era requirements]
**Upgrade Path:** [How this building evolves in later eras, if applicable]

#### Description — How It Works (Game)

[Explanation of what this building does in-game, what it produces, how the player interacts with it, and why they need it. Written for the player to understand gameplay function.]

#### Description — Historical Context

[Historical explanation of what this building represents, how it was used in the relevant time period in Great Britain, and educational content. Minimum 2-3 paragraphs for depth.]

#### Worker Slots

| Slot # | Role Name | Role Ref ID | Stat Priority | Description |
|--------|-----------|-------------|---------------|-------------|
| 1 | [Role] | [Ref ID] | [Stat] | [What this worker does] |

#### Tool Slots

| Slot # | Assigned To (Role) | Tool Name | Tool Ref ID | Effect |
|--------|-------------------|-----------|-------------|--------|
| 1 | [Role] | [Tool] | [Ref ID] | [Production effect] |

#### Equipment Slots

| Slot # | Equipment Name | Equipment Ref ID | Effect |
|--------|---------------|-----------------|--------|
| 1 | [Equipment] | [Ref ID] | [Building-wide effect] |

#### Storage Slots

| Type | Resource | Capacity (Base) | Upgradeable |
|------|----------|-----------------|-------------|
| Input | [Resource name] | [Units] | [Yes/No] |
| Output | [Resource name] | [Units] | [Yes/No] |

#### Delivery Slots

| Slot # | Output Resource | Destination Building | Destination Ref ID | Route Ref ID |
|--------|----------------|--------------------|--------------------|--------------|
| 1 | [Resource] | [Building name] | [Ref ID] | [Route Ref ID] |

#### Production Formula

[How output is calculated: base rate × worker skill × tool multiplier × equipment bonus]

#### Related Refs

- **Research:** [List of research Ref IDs from researchGB.md]
- **Tools:** [List of tool Ref IDs from toolsandequipmentGB.md]
- **Equipment:** [List of equipment Ref IDs from toolsandequipmentGB.md]
- **Routes In:** [Delivery routes that bring resources TO this building]
- **Routes Out:** [Delivery routes that send resources FROM this building]
```

---

## Era 1 — Primitive Age

> **Era Description:** Before the use of stone tools. The community relies on bare hands, sharpened sticks, bones, fire, and natural materials. The player's business provides essential goods and services to a small tribal group.

### era1.huntinghut | Hunting Hut

**Era Introduced:** Era 1 — Primitive Age
**Build Cost:** [TBD — awaiting balance pass]
**Build Time:** [TBD]
**Prerequisites:** None (starting building)
**Upgrade Path:** [TBD — evolves in Era 2]

#### Description — How It Works (Game)

[TBD — awaiting answers to design questions]

#### Description — Historical Context

[TBD — awaiting answers to design questions]

#### Worker Slots

| Slot # | Role Name | Role Ref ID | Stat Priority | Description |
|--------|-----------|-------------|---------------|-------------|
| [TBD] | [TBD] | era1.huntinghut.role.[TBD] | [TBD] | [TBD] |

#### Tool Slots

| Slot # | Assigned To (Role) | Tool Name | Tool Ref ID | Effect |
|--------|-------------------|-----------|-------------|--------|
| [TBD] | [TBD] | [TBD] | era1.huntinghut.tool.[TBD] | [TBD] |

#### Equipment Slots

| Slot # | Equipment Name | Equipment Ref ID | Effect |
|--------|---------------|-----------------|--------|
| [TBD] | [TBD] | era1.huntinghut.equip.[TBD] | [TBD] |

#### Storage Slots

| Type | Resource | Capacity (Base) | Upgradeable |
|------|----------|-----------------|-------------|
| Output | Raw Meat | [TBD] | [TBD] |
| Output | Animal Pelts | [TBD] | [TBD] |
| Output | Animal Bones | [TBD] | [TBD] |

#### Delivery Slots

| Slot # | Output Resource | Destination Building | Destination Ref ID | Route Ref ID |
|--------|----------------|--------------------|--------------------|--------------|
| 1 | Raw Meat | Smoke House | era1.smokehouse | era1.route.huntinghut-to-smokehouse |
| 2 | Animal Pelts | Pelt Processing | era1.peltprocessing | era1.route.huntinghut-to-peltprocessing |
| 3 | Animal Bones | [TBD — Bone Workshop?] | [TBD] | [TBD] |

#### Production Formula

[TBD]

#### Related Refs

- **Research:** [TBD — see researchGB.md]
- **Tools:** [TBD — see toolsandequipmentGB.md]
- **Equipment:** [TBD — see toolsandequipmentGB.md]
- **Routes In:** None (primary producer)
- **Routes Out:** era1.route.huntinghut-to-smokehouse, era1.route.huntinghut-to-peltprocessing, [TBD]

---

### era1.smokehouse | Smoke House

**Era Introduced:** Era 1 — Primitive Age
**Build Cost:** [TBD]
**Build Time:** [TBD]
**Prerequisites:** [TBD — Firekeeper's Pit? Hunting Hut?]
**Upgrade Path:** [TBD — evolves in Era 2]

#### Description — How It Works (Game)

[TBD — awaiting answers to design questions]

#### Description — Historical Context

[TBD — awaiting answers to design questions]

#### Worker Slots

| Slot # | Role Name | Role Ref ID | Stat Priority | Description |
|--------|-----------|-------------|---------------|-------------|
| [TBD] | [TBD] | era1.smokehouse.role.[TBD] | [TBD] | [TBD] |

#### Tool Slots

| Slot # | Assigned To (Role) | Tool Name | Tool Ref ID | Effect |
|--------|-------------------|-----------|-------------|--------|
| [TBD] | [TBD] | [TBD] | era1.smokehouse.tool.[TBD] | [TBD] |

#### Equipment Slots

| Slot # | Equipment Name | Equipment Ref ID | Effect |
|--------|---------------|-----------------|--------|
| [TBD] | [TBD] | era1.smokehouse.equip.[TBD] | [TBD] |

#### Storage Slots

| Type | Resource | Capacity (Base) | Upgradeable |
|------|----------|-----------------|-------------|
| Input | Raw Meat | [TBD] | [TBD] |
| Output | Smoked Meat | [TBD] | [TBD] |

#### Delivery Slots

| Slot # | Output Resource | Destination Building | Destination Ref ID | Route Ref ID |
|--------|----------------|--------------------|--------------------|--------------|
| [TBD] | Smoked Meat | [TBD — Market? Community?] | [TBD] | [TBD] |

#### Production Formula

[TBD]

#### Related Refs

- **Research:** [TBD]
- **Tools:** [TBD]
- **Equipment:** [TBD]
- **Routes In:** era1.route.huntinghut-to-smokehouse
- **Routes Out:** [TBD]

---

### era1.peltprocessing | Pelt Processing

**Era Introduced:** Era 1 — Primitive Age
**Build Cost:** [TBD]
**Build Time:** [TBD]
**Prerequisites:** [TBD — Hunting Hut?]
**Upgrade Path:** [TBD — evolves in Era 2]

#### Description — How It Works (Game)

[TBD — awaiting answers to design questions]

#### Description — Historical Context

[TBD — awaiting answers to design questions]

#### Worker Slots

| Slot # | Role Name | Role Ref ID | Stat Priority | Description |
|--------|-----------|-------------|---------------|-------------|
| [TBD] | [TBD] | era1.peltprocessing.role.[TBD] | [TBD] | [TBD] |

#### Tool Slots

| Slot # | Assigned To (Role) | Tool Name | Tool Ref ID | Effect |
|--------|-------------------|-----------|-------------|--------|
| [TBD] | [TBD] | [TBD] | era1.peltprocessing.tool.[TBD] | [TBD] |

#### Equipment Slots

| Slot # | Equipment Name | Equipment Ref ID | Effect |
|--------|---------------|-----------------|--------|
| [TBD] | [TBD] | era1.peltprocessing.equip.[TBD] | [TBD] |

#### Storage Slots

| Type | Resource | Capacity (Base) | Upgradeable |
|------|----------|-----------------|-------------|
| Input | Animal Pelts | [TBD] | [TBD] |
| Output | Processed Pelts | [TBD] | [TBD] |

#### Delivery Slots

| Slot # | Output Resource | Destination Building | Destination Ref ID | Route Ref ID |
|--------|----------------|--------------------|--------------------|--------------|
| [TBD] | Processed Pelts | [TBD — Shelter Builder? Market?] | [TBD] | [TBD] |

#### Production Formula

[TBD]

#### Related Refs

- **Research:** [TBD]
- **Tools:** [TBD]
- **Equipment:** [TBD]
- **Routes In:** era1.route.huntinghut-to-peltprocessing
- **Routes Out:** [TBD]

---

### era1.spearproduction | Spear Production

**Era Introduced:** Era 1 — Primitive Age
**Build Cost:** [TBD]
**Build Time:** [TBD]
**Prerequisites:** [TBD]
**Upgrade Path:** [TBD — evolves in Era 2]

#### Description — How It Works (Game)

[TBD — awaiting answers to design questions]

#### Description — Historical Context

[TBD — awaiting answers to design questions]

#### Worker Slots

| Slot # | Role Name | Role Ref ID | Stat Priority | Description |
|--------|-----------|-------------|---------------|-------------|
| [TBD] | [TBD] | era1.spearproduction.role.[TBD] | [TBD] | [TBD] |

#### Tool Slots

| Slot # | Assigned To (Role) | Tool Name | Tool Ref ID | Effect |
|--------|-------------------|-----------|-------------|--------|
| [TBD] | [TBD] | [TBD] | era1.spearproduction.tool.[TBD] | [TBD] |

#### Equipment Slots

| Slot # | Equipment Name | Equipment Ref ID | Effect |
|--------|---------------|-----------------|--------|
| [TBD] | [TBD] | era1.spearproduction.equip.[TBD] | [TBD] |

#### Storage Slots

| Type | Resource | Capacity (Base) | Upgradeable |
|------|----------|-----------------|-------------|
| Input | [TBD — Wood? Bone?] | [TBD] | [TBD] |
| Output | Spears | [TBD] | [TBD] |

#### Delivery Slots

| Slot # | Output Resource | Destination Building | Destination Ref ID | Route Ref ID |
|--------|----------------|--------------------|--------------------|--------------|
| 1 | Spears | Hunting Hut | era1.huntinghut | era1.route.spearproduction-to-huntinghut |

#### Production Formula

[TBD]

#### Related Refs

- **Research:** [TBD]
- **Tools:** [TBD]
- **Equipment:** [TBD]
- **Routes In:** [TBD]
- **Routes Out:** era1.route.spearproduction-to-huntinghut

---

## Era 2 — Stone Age

*To be populated*

---

## Era 3 — Bronze Age

*To be populated*

---

## Era 4 — Iron Age

*To be populated*

---

## Era 5 — Medieval

*To be populated*

---

## Era 6 — Renaissance

*To be populated*

---

## Era 7 — Colonial

*To be populated*

---

## Era 8 — Industrial Revolution

*To be populated*

---

## Era 9 — World Wars

*To be populated*

---

## Era 10 — Silicon Age

*To be populated*

---

## Era 11 — Information Age

*To be populated*

---

## Era 12 — Space Age

*To be populated*

---

## Delivery Route Index

> Quick-reference for all delivery routes across all eras.

### Era 1 — Primitive Age

| Route Ref ID | From | To | Resource | Notes |
|-------------|------|----|----------|-------|
| era1.route.huntinghut-to-smokehouse | Hunting Hut | Smoke House | Raw Meat | [TBD] |
| era1.route.huntinghut-to-peltprocessing | Hunting Hut | Pelt Processing | Animal Pelts | [TBD] |
| era1.route.spearproduction-to-huntinghut | Spear Production | Hunting Hut | Spears | [TBD] |
| [More TBD] | | | | |

---

## Summary

| Era | Total Buildings | Total Worker Slots | Total Delivery Routes |
|-----|----------------|-------------------|----------------------|
| Primitive Age | 4 | 0 | 3 |
| Stone Age | 0 | 0 | 0 |
| Bronze Age | 0 | 0 | 0 |
| Iron Age | 0 | 0 | 0 |
| Medieval | 0 | 0 | 0 |
| Renaissance | 0 | 0 | 0 |
| Colonial | 0 | 0 | 0 |
| Industrial Revolution | 0 | 0 | 0 |
| World Wars | 0 | 0 | 0 |
| Silicon Age | 0 | 0 | 0 |
| Information Age | 0 | 0 | 0 |
| Space Age | 0 | 0 | 0 |
| **TOTAL** | **4** | **0** | **3** |
