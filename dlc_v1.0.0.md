# Project Arasmas — DLC Planning Document

> **Purpose:** Master list of all planned and potential DLC packages. Each entry includes concept, content scope, estimated complexity, and dependencies.
> **Last Updated:** 2026-04-30
> **Status:** Planning — no DLC in development yet. Main game must be fully playable and enjoyable without any DLC.
> **Related Files:** `plans.md` §1.19 (Monetisation), §2.12 (DLC System)

---

## How to Use This File

- DLC is available to BOTH paid and free (ad-supported) versions of the game
- DLC content is defined in `data/dlc/` directory using the same JSON format as base game data files
- DLC is detected and loaded on game start
- Platform-specific delivery: Steam DLC, Google Play IAP, Apple IAP
- The main game MUST be fully playable and enjoyable without any DLC — DLC enhances, never gates core gameplay

---

## DLC Status Key

- `[CONCEPT]` = Idea stage — not yet designed
- `[DESIGNED]` = Design complete, not yet built
- `[IN DEV]` = Currently being developed
- `[COMPLETE]` = Ready for release
- `[RELEASED]` = Live and available

---

## 1. Civilization Packs

**Description:** New playable civilizations with full research trees, equipment, buildings, laws, historical text, visual skins, and era-specific crises.

| # | DLC Name | Civilization | Status | Notes |
|---|----------|-------------|--------|-------|
| 1.1 | Native American Civilization Pack | Native American | [CONCEPT] | Full research tree, equipment, buildings, laws, historical text, visual skin |
| 1.2 | African Civilization Pack | African | [CONCEPT] | Full research tree, equipment, buildings, laws, historical text, visual skin |
| 1.3 | Mesoamerican Civilization Pack | Mesoamerican (Aztec, Maya, Inca) | [CONCEPT] | Full research tree, equipment, buildings, laws, historical text, visual skin |

**Scope per pack:** Each civilization requires: `research[CIV].md`, `toolsandequipment[CIV].md`, `buildings[CIV].md`, `laws[CIV].md`, visual assets for all 12 eras, worker name lists, competitor reveal schedule, crisis definitions.

**Note:** Popular community-made civilization mods can be promoted to official DLC with modder credit.

---

## 2. Gameplay Expansion DLC

### 2.1 Combat & Warfare Expansion

**Status:** [CONCEPT]

**Description:** A major expansion adding military production, troop recruitment, attack/defence mechanics, and fortification systems. Transforms the competitor system from passive rivalry into active warfare.

**Core Mechanics:**

**Military Production Chain:**
- Resources from existing production chains are used to manufacture **weapons** appropriate to each era (stone spears → bronze swords → iron armour → muskets → tanks → missiles, etc.)
- Weapons are produced in dedicated military production buildings (armoury, weapons factory, munitions plant, etc.)
- Military production buildings follow all standard building rules: worker capacity, equipment, upgrades, era changes, disrepair, map placement

**Troop Recruitment:**
- Workers can be recruited as **troops** — removing them from the civilian workforce
- Troops require: weapons, food supply, training, and ongoing maintenance (coins per second, like regular workers)
- Troops level up through training (similar to worker education system)
- Troop stats may use the same system as worker stats (Strength, Luck, etc.) with additional military-specific stats (TBD)

**Attack System:**
- The player can send troops to **attack NPC competitors**
- Attacks consume troops, weapons, and resources
- **No attack can totally defeat a competitor** — attacks can destroy fortifications, damage buildings, damage equipment, and slow the competitor's progress, but cannot eliminate them
- A potential **mini-game** may be included for each attack (format TBD — could be tactical placement, timing-based, or strategic choices)
- Attack results are visible to the player with detailed statistics

**Defence / Fortification System:**
- The player must build **fortifications** to defend against competitor attacks
- Fortifications are buildings placed on the map (walls, towers, bunkers, missile defence, etc.) that evolve with each era
- Fortifications require a **steady supply of resources** to remain active:
  - **Food** — to feed the garrison
  - **Weapons** — to arm the garrison
  - **Manpower** — troops assigned to defence
  - **Training** — garrison troops need training to be effective
- Fortifications can be **levelled up** through upgrades (like any building)
- If resource supply is cut (e.g. food runs out, weapons depleted), fortification effectiveness drops
- Undefended or under-supplied fortifications are vulnerable to competitor attacks

**Damage from Attacks:**
- Successful enemy attacks can:
  - Destroy fortifications (must be rebuilt)
  - Damage production buildings (reduced output, may fall into disrepair)
  - Damage equipment (must be repaired or replaced)
  - Kill workers (removed from workforce)
- Damage is NOT total — the player always survives and can rebuild
- Damage interacts with the existing crisis system (a devastating attack could trigger crisis-like effects)

**Era Progression:**
- Military technology progresses with eras like everything else
- Each era introduces new weapons, fortification types, and military capabilities
- Military research is integrated into the existing research system (or may have its own military research branch)

**Dependencies:**
- Requires core game completion (production chains, worker system, competitor system, building system)
- Military buildings, research, and equipment need entries in civilization-specific files
- Competitor AI needs to be updated to include attack/defence behaviour

**Estimated Complexity:** Very high — this is the largest potential DLC

**Open Questions for Combat DLC:**
1. Does military production use existing buildings or entirely new building types?
2. Can troops return to civilian work after being recruited, or is recruitment permanent?
3. How is attack timing determined — player-initiated only, or can competitors attack at any time?
4. What triggers a competitor to attack the player — random, provoked by player attacks, or based on rivalry level?
5. Do fortifications have adjacency/placement requirements on the map?
6. Should military research be a separate branch in the research tree, or integrated into the main tree?
7. What does the attack mini-game look like? Turn-based? Real-time? Card-based?

---

### 2.2 Unlimited Boost Slots (Inventory)

**Status:** [CONCEPT]

**Description:** Removes the boost type slot limit from the inventory/chest system.

**Effect:** Player can store unlimited types of boosts (normally limited to researchable slot count).

**Scope:** Small — modifies one value in the boost inventory settings.

---

### 2.3 Unlimited Boost Quantity (Inventory)

**Status:** [CONCEPT]

**Description:** Removes the boost stack quantity limit from the inventory/chest system.

**Effect:** Player can store unlimited quantities of each boost type (normally limited to researchable stack size).

**Scope:** Small — modifies one value in the boost inventory settings.

---

### 2.4 Increased Offline Earnings — Percentage

**Status:** [CONCEPT]

**Description:** Increases the offline earnings percentage above the base 25%.

**Effect:** Player earns a higher percentage of normal production while the app is closed. Exact percentage TBD (e.g. 50%, 75%, or 100%).

**Scope:** Small — modifies offline earnings settings.

---

### 2.5 Increased Offline Earnings — Duration

**Status:** [CONCEPT]

**Description:** Extends the offline earnings collection duration beyond the base 3 hours.

**Effect:** Player collects offline earnings for a longer period. Exact duration TBD (e.g. 6 hours, 12 hours, or 24 hours).

**Scope:** Small — modifies offline earnings settings.

---

### 2.6 Daily Recharging Boosts

**Status:** [CONCEPT]

**Description:** A set of boosts that recharge daily (real-world time), giving the player a small daily bonus for logging in.

**Effect:** Each day the player receives a selection of boosts (rarity and type may vary or follow a schedule). Encourages daily engagement.

**Scope:** Medium — needs a daily refresh system and UI element.

---

### 2.7 Cheat Pack

**Status:** [CONCEPT]

**Description:** Access to developer-style cheats for players who want a sandbox experience.

**Possible Cheats:**
- Infinite coins
- Instant research completion
- Skip era requirements
- Spawn any boost
- Disable crises
- Max worker stats
- Instant specialist progress
- Unlock all buildings

**Scope:** Medium — needs a cheat console UI and cheat command system. Cheats should disable achievements and possibly mark the save file as "cheated."

---

## 3. Content Packs

### 3.1 New Eras

**Status:** [CONCEPT]

**Description:** Additional eras beyond the Space Age (Era 12). Could include far-future or alternate history content.

**Possible Eras:**
- Post-Singularity Age
- Interstellar Age
- Alternate history branches

**Scope:** Large — each new era needs buildings, research, equipment, laws, visual assets, and balance tuning.

---

### 3.2 Cosmetic Packs

**Status:** [CONCEPT]

**Description:** Visual customisation for the player's map and buildings.

**Possible Content:**
- Alternative building skins
- Seasonal decorative sets
- Custom road styles
- Map backgrounds / terrain themes
- Worker outfit customisation

**Scope:** Medium — primarily art assets with minimal code changes.

---

## 4. Bundle Packs

**Description:** Combinations of smaller DLC offered at a discount.

| # | Bundle Name | Contents | Status |
|---|------------|----------|--------|
| 4.1 | Inventory Upgrade Bundle | Unlimited Boost Slots + Unlimited Boost Quantity | [CONCEPT] |
| 4.2 | Offline Upgrade Bundle | Increased Offline % + Increased Offline Duration | [CONCEPT] |
| 4.3 | Complete Upgrade Bundle | All small gameplay DLC combined | [CONCEPT] |

---

## Summary

| Category | Count | Designed | In Dev | Released |
|----------|-------|----------|--------|----------|
| Civilization Packs | 3 | 0 | 0 | 0 |
| Gameplay Expansions | 7 | 0 | 0 | 0 |
| Content Packs | 2 | 0 | 0 | 0 |
| Bundle Packs | 3 | 0 | 0 | 0 |
| **TOTAL** | **15** | **0** | **0** | **0** |

---

## DLC Pricing Strategy

- **Not yet determined** — pricing will depend on scope of each DLC, platform norms, and competitive analysis
- Civilization packs = premium price (large content)
- Combat expansion = premium price (major feature)
- Small gameplay DLC (inventory, offline) = low price
- Cosmetic packs = low to medium price
- Bundles = discounted vs individual purchase
- All DLC available to both paid and free versions of the game
