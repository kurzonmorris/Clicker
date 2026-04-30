# Project Arasmas — Tools & Equipment: Great Britain

> **Purpose:** Complete list of all tools, equipment, and their upgrade paths for the Great Britain civilization. Every item includes: era, cost, prerequisites, production effects, and upgrade path.
> **Last Updated:** 2026-04-03
> **Status:** Template created — to be populated in a separate dedicated chat session
> **Related File:** `researchGB.md` (research required to unlock these items)

---

## How to Use This File

- Each tool/equipment item is defined with all data needed for the game's `data/settings/civilizations/great_britain/equipment.json` file
- Items are organised by era and by the building/role they belong to
- Upgrade paths show both incremental improvements and full replacements
- Prerequisites reference research items from `researchGB.md` by their ID
- Equipment that workers need experience with is marked — new equipment starts with low proficiency

---

## Equipment Item Template

```
### [ID] Equipment Name
- **Era:** Which era this equipment belongs to
- **Building/Role:** Which building and worker role uses this
- **Coin Cost:** Cost to purchase
- **Research Required:** Research ID(s) from researchGB.md
- **Production Multiplier:** How this affects base production (e.g. 1.5x)
- **Worker Stat Requirement:** Which stat(s) matter (e.g. Strength, Intelligence)
- **Experience Required:** Whether workers need to gain proficiency with this tool
- **Upgrade Path:**
  - Incremental: List of small improvements available (e.g. better handle, rope wrap)
  - Replacement: What this tool is replaced by in the next era
- **Historical Description (Great Britain):** Civilization-specific text
```

---

## Incremental Upgrade Template

```
#### [ID] Upgrade Name (for [Parent Equipment ID])
- **Coin Cost:** Cost to apply this upgrade
- **Research Required:** Research ID (if any)
- **Effect:** What this upgrade changes (e.g. +10% production, +5% durability)
- **Prerequisites:** Other upgrades that must be applied first (if any)
- **Historical Description (Great Britain):** Civilization-specific text
```

---

## Era 1 — Primitive Age

### Mining/Gathering Tools

*To be populated*

### Processing Tools

*To be populated*

---

## Era 2 — Stone Age

### Mining/Gathering Tools

*To be populated*

### Processing Tools

*To be populated*

---

## Era 3 — Bronze Age

### Mining Tools

*To be populated*

### Smelting Equipment

*To be populated*

### Smithing Tools

*To be populated*

---

## Era 4 — Iron Age

### Mining Tools

*To be populated*

### Smelting Equipment

*To be populated*

### Smithing Tools

*To be populated*

### Hauling Equipment

*To be populated*

---

## Era 5 — Medieval

### Mining Tools

*To be populated*

### Smelting Equipment

*To be populated*

### Smithing Tools

*To be populated*

### Trade Equipment

*To be populated*

---

## Era 6 — Renaissance

*To be populated*

---

## Era 7 — Colonial

*To be populated*

---

## Era 8 — Industrial Revolution

### Mining Equipment

*To be populated*

### Factory Equipment

*To be populated*

### Transport Equipment

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

## Upgrade Path Diagrams

*Visual representation of how equipment evolves across eras. To be populated.*

```
Example:
Primitive Age: Bare hands
    → Stone Age: Stone pickaxe
        → [Upgrade: Sharpened edge]
        → [Upgrade: Wooden handle]
        → [Upgrade: Rope-wrapped handle]
    → Bronze Age: Bronze pickaxe (REPLACEMENT)
        → [Upgrade: Reinforced head]
        → [Upgrade: Balanced weight]
    → Iron Age: Iron pickaxe (REPLACEMENT)
        → ...
    → Medieval: Steel pickaxe (REPLACEMENT)
        → ...
    → Industrial Revolution: Pneumatic drill (REPLACEMENT)
        → ...
```

---

## Summary

| Era | Total Equipment Items | Total Incremental Upgrades |
|-----|--------------------- |---------------------------|
| Primitive Age | 0 | 0 |
| Stone Age | 0 | 0 |
| Bronze Age | 0 | 0 |
| Iron Age | 0 | 0 |
| Medieval | 0 | 0 |
| Renaissance | 0 | 0 |
| Colonial | 0 | 0 |
| Industrial Revolution | 0 | 0 |
| World Wars | 0 | 0 |
| Silicon Age | 0 | 0 |
| Information Age | 0 | 0 |
| Space Age | 0 | 0 |
| **TOTAL** | **0** | **0** |
