# Project Arasmas — Buildings: Great Britain

> **Purpose:** Complete list of all buildings for the Great Britain civilization, including production buildings, decorative/map buildings, and their settings per era.
> **Last Updated:** 2026-04-07
> **Status:** Template created — to be populated in a separate dedicated chat session
> **Related Files:** `researchGB.md` (research required to unlock buildings), `toolsandequipmentGB.md` (equipment used within buildings)

---

## How to Use This File

- Each building is defined with all data needed for the game's `data/settings/buildings/` and `data/settings/civilizations/great_britain/` files
- Buildings are organised by type (Production vs Decorative) and by era
- Production buildings have worker limits, equipment slots, resource inputs/outputs, and upgrade paths
- Decorative buildings are placed on the map for aesthetics (no direct gameplay effect, except Town Hall which displays community stats)
- Each building's worker limit and production values change per era
- **Worker role assignment is unrestricted** — players can assign any combination of workers to any roles within the building's total worker limit
- **Map placement is free-form** — players drag and drop buildings, draw roads with finger/mouse. Loose grid for alignment but not restricted to fixed tiles

---

## Building Rules

### Era Upgrade Requirement
When the player advances to a new era, ALL buildings must be upgraded to the current era's standards. Buildings that are not upgraded to the current era cannot receive any other upgrades.

### Disrepair Mechanic
If a building is NOT upgraded and the player advances **another** era (so the building is now 2 ages behind the current era), the building falls into **disrepair**:
- A building in disrepair is non-functional (produces nothing, decorative buildings visually degrade)
- It must be **completely rebuilt** from scratch
- All upgrades must be restarted from the beginning
- This applies to BOTH production buildings and decorative/map buildings

### Town Hall / Town Square
- The Town Hall is the visual centre of the map in every era
- It is the **community stats dashboard** — instead of loading into each building individually, the player can view production stats for ALL buildings from the Town Hall in a single overview
- Stats displayed include: each building's production output, worker counts, equipment status, and other per-building info (exact stat list TBD)
- It upgrades with each era like any other building (subject to disrepair if 2 ages behind)
- It is NOT a production building — it generates nothing
- Can be relocated when rebuilt (same as other buildings)

---

## Building Types

1. **Production Buildings** — Generate resources, require workers and equipment. Core gameplay. Also placed on the map
2. **Happiness Buildings** — Improve worker happiness globally. Require workers to operate. Era-appropriate (taverns, temples, parks, theatres, hospitals, etc.). Some target all workers, others target specific worker classes. No happiness buildings in Era 1 (Primitive Age). Listed alongside production buildings
3. **Decorative Buildings** — Placed on the map for aesthetics. No gameplay effect (except Town Hall). Given to the player in set quantities per era based on research
4. **Town Hall** — Special building. Visual centre of the map. Displays community stats. One per game, always present

---

## Production Building Template

```
### [ID] Building Name
- **Era Introduced:** Which era this building first becomes available
- **Research Required:** Research ID(s) from researchGB.md
- **Build Cost:** Coins to construct
- **Category:** [Mining / Smelting / Smithing / Manufacturing / Trading / Research / Other]
- **Resource Input:** What this building consumes
- **Resource Output:** What this building produces
- **Base Production Rate:** Units per second at base level
- **Critical Success Chance:** Base probability of a critical success (before research/luck modifiers)
- **Available Roles:** [e.g. Miner, Hauler, Operator] — player assigns workers to any combination
- **Worker Capacity Per Era:**

| Era | Max Workers | Notes |
|-----|-------------|-------|
| [Era Name] | [Number] | [Any era-specific changes] |

- **Equipment Slots:** What equipment types this building supports
- **Upgrade Path:** How this building changes across eras (must be upgraded to current era or falls into disrepair after 2 ages)
- **Delegation Available:** [Yes/No] Can this building's resource be bought from the computer instead?
- **Map Grid Size:** [e.g. 2x2, 3x3] How much space this takes on the map
- **Historical Description (Great Britain):** Civilization-specific text
```

---

## Decorative Building Template

```
### [ID] Decorative Building Name
- **Era Introduced:** Which era this becomes available
- **Research Required:** Research ID (if any — some decorative buildings may require research)
- **Category:** [House / Shop / Government / Road / Community / Religious / Other]
- **Quantity Per Era:** How many the player receives each era
- **Map Grid Size:** [e.g. 1x1, 2x2] Space on the map
- **Disrepair:** Falls into disrepair if not upgraded within 2 eras
- **Visual Description:** What it looks like (for art direction)
- **Historical Description (Great Britain):** Civilization-specific text
```

**Note:** Decorative buildings are a fixed list per era, defined in building settings files. The list is determined by era and research unlocks. Modders can add new decorative types via the modding system.

---

## Happiness Building Template

```
### [ID] Happiness Building Name
- **Era Introduced:** Which era this building first becomes available
- **Research Required:** Research ID(s) from researchGB.md
- **Build Cost:** Coins to construct
- **Worker Class Target:** [All / Upper-class (financial/trading) / Normal (labour/production) / Specific roles]
- **Happiness Effect:** +X% happiness to targeted workers (global — map position irrelevant)
- **Worker Capacity Per Era:**

| Era | Max Workers | Notes |
|-----|-------------|-------|
| [Era Name] | [Number] | [Any era-specific changes] |

- **Upgrade Path:** How this building changes across eras
- **Map Grid Size:** [e.g. 2x2, 3x3] Space on the map
- **Historical Description (Great Britain):** Civilization-specific text
```

---

## Production Buildings

### Era 1 — Primitive Age

*To be populated*

---

### Era 2 — Stone Age

*To be populated*

---

### Era 3 — Bronze Age

*To be populated*

---

### Era 4 — Iron Age

*To be populated*

---

### Era 5 — Medieval

*To be populated*

---

### Era 6 — Renaissance

*To be populated*

---

### Era 7 — Colonial

*To be populated*

---

### Era 8 — Industrial Revolution

*To be populated*

---

### Era 9 — World Wars

*To be populated*

---

### Era 10 — Silicon Age

*To be populated*

---

### Era 11 — Information Age

*To be populated*

---

### Era 12 — Space Age

*To be populated*

---

## Decorative / Map Buildings

### Era 1 — Primitive Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 2 — Stone Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 3 — Bronze Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 4 — Iron Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 5 — Medieval

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 6 — Renaissance

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 7 — Colonial

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 8 — Industrial Revolution

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 9 — World Wars

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 10 — Silicon Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 11 — Information Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

### Era 12 — Space Age

| Type | Quantity | Grid Size | Description |
|------|----------|-----------|-------------|
| | | | |

*To be populated*

---

## Map Layout Progression

**Description:** The map grows with each era. The centre is always the Town Square / Town Hall. Pathways radiate outward.

| Era | Map Grid Size | Path Type | New Features |
|-----|--------------|-----------|-------------|
| Primitive Age | 10×10 | Dirt trails | Basic camp layout. No happiness buildings |
| Stone Age | 20×20 | Worn paths | |
| Bronze Age | 30×30 | Stone paths | |
| Iron Age | 40×40 | Cobblestone | |
| Medieval | 50×50 | Cobblestone roads | Town wall? |
| Renaissance | 60×60 | Paved roads | |
| Colonial | 70×70 | Wide roads | Expansion outward |
| Industrial Revolution | 80×80 | Paved + rail | Railway lines |
| World Wars | 90×90 | Tarmac roads | |
| Silicon Age | 100×100 | Highways | Suburban sprawl |
| Information Age | 110×110 | Modern highways | |
| Space Age | 120×120 | Futuristic paths | Launch facilities |

*Grid sizes increase by 10 per era. Values may change with further development — defined in settings files.*

---

## Summary

| Category | Total Buildings | Per Era Defined |
|----------|----------------|----------------|
| Production | 0 | 0 |
| Decorative | 0 | 0 |
| **TOTAL** | **0** | **0** |
