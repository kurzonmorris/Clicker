# Project Arasmas — Mini-Game: Marriage & Family System

> **Purpose:** Design document for the worker marriage and family mini-game. Covers inter-marriage, divorce, children, the children pool, and family tree viewing.
> **Last Updated:** 2026-04-17
> **Status:** DRAFT — Core concept defined, details to be refined during development
> **Related Files:** `plans.md` §1.5 (NPC Worker System), `buildingsGB.md` (worker capacity)

---

## Overview

Workers in Project Arasmas are not disposable resources — they are named individuals with family lineage spanning multiple eras. The Marriage & Family system is an optional mini-game that lets players build worker dynasties through arranged marriages, producing children who can later be recruited as workers.

This system serves multiple purposes:
- Creates emotional attachment to worker families
- Provides an alternative worker recruitment source (children vs immigrants)
- Adds a light simulation layer that complements the core production gameplay
- Feeds into the Family Tree viewer for long-term lineage tracking

---

## Core Rules

### Marriage

- **Any two workers can be married** regardless of their current building assignment or occupation
- Workers do NOT need to be in the same building to marry
- Marriage is initiated by the player through the worker's profile screen
- **No restrictions on who can marry whom** — any combination of available (unmarried) workers
- A married couple's relationship is tracked in both workers' profiles
- Marriage has no direct effect on worker stats or production — it exists to enable children

### Divorce

- **Divorce is allowed at any time** — the player can dissolve any marriage
- Divorced workers return to "unmarried" status and can remarry
- Divorce has no mechanical penalty (no stat loss, no production penalty)
- There is no limit on how many times a worker can marry and divorce
- Children from a dissolved marriage remain in the children pool and are unaffected

### Remarriage

- **Remarriage is unlimited** — a worker can marry, divorce, and remarry as many times as the player wishes
- A worker can only be married to one other worker at a time (no polygamy)

---

## Children

### Having Children

- A married couple can **produce children** through the mini-game interface
- Children are generated with a name (following civilization naming conventions) and basic stat tendencies
- **Maximum 8 children per couple** — this is a hard cap per parent pairing
  - If Worker A and Worker B have 8 children together, they cannot have more together
  - If Worker A divorces and marries Worker C, the 8-child counter resets for the new pairing
  - Worker A could theoretically have many children across multiple marriages, but each pairing is capped at 8
- Children are NOT immediately usable as workers — they enter the **Children Pool**

### Children Pool

- The children pool is a holding area for children who have been born but not yet recruited as workers
- Children in the pool are free — they do not cost wages
- When the player wants to hire a new worker, they can choose:
  - **Recruit from children pool** — select a specific child to become a working adult
  - **Hire an immigrant** — a new worker with random stats and no family lineage
- Children in the pool are listed with their parents' names, basic stat preview, and family lineage

### Child Stats

- **Base stat range:** All stats for new workers (immigrants AND children) randomly range from **8–12**
- **Child stat inheritance:** Children inherit the **top stat from each parent** — but only stats above 12:
  - For each parent, find their single highest stat that is above 12
  - That stat is automatically set to 12 for the child (instead of the random 8–12 range)
  - The child gets the top stat from Parent A and the top stat from Parent B (maximum 2 inherited stats)
  - If a parent has NO stats above 12, the child inherits nothing from that parent (all stats random 8–12)
  - If a parent has multiple stats above 12, only the HIGHEST one is inherited
  - **Example:** Parent A has Strength 14, Intelligence 13, Charisma 9, Luck 10. Parent B has Intelligence 15, Strength 11, Charisma 8, Luck 12. Child inherits: Strength guaranteed 12 (from Parent A's 14), Intelligence guaranteed 12 (from Parent B's 15). Charisma and Luck are random 8–12
- **Immigrant stats:** Fully random, all stats 8–12. No inheritance
- This creates a meaningful advantage to breeding workers vs hiring immigrants — children from high-stat parents are more likely to start with at least two stats at the top of the range

---

## The Mini-Game Interface

### Accessing the Mini-Game

- The marriage and family system is accessed through any worker's **profile screen**
- A "Family" tab shows: current marriage status, spouse (if married), children, and family tree
- Actions available:
  - **Propose Marriage** — select another unmarried worker to marry
  - **Have Child** — available to married couples who have fewer than 8 children together
  - **Divorce** — dissolve current marriage
  - **View Family Tree** — opens the dynasty viewer

### Marriage Selection

- When proposing marriage, the player sees a list of all unmarried workers
- Workers are listed with their stats, current occupation, and building assignment
- The player selects a partner and confirms — marriage is immediate

### Having a Child (the mini-game element)

- When a married couple chooses to have a child, a brief mini-game or animation plays
- The exact mini-game format is TBD but should be:
  - **Quick** — no more than 30 seconds
  - **Optional** — players who don't want to engage can auto-generate children
  - **Light-hearted** — thematically appropriate for all ages
  - **Potential mechanic:** A simple matching/combining game where the player influences one minor aspect of the child (e.g. choosing which stat gets a slight boost), while other stats are random
- After the mini-game, the child is born with generated stats and enters the children pool

---

## Family Tree Viewer

- Every worker has a viewable **family tree** that shows their complete lineage
- The tree displays:
  - All ancestors (previous generations from earlier eras)
  - Current generation (the worker themselves, their spouse, siblings)
  - Children (in the children pool or already recruited as workers)
  - Former marriages (if divorced and remarried)
- The tree grows across eras as generational lineage continues
- Special visual indicator for families that have survived many eras ("The Mayer family has served your empire for 8 eras")
- Achievement: "Generational" — have a worker's family line survive from Era 1 to Era 12

---

## Interaction with Other Systems

### Generational Lineage (Era Changes)

- When a new era begins, workers undergo generational name changes (first name + possibly gender change)
- Children in the children pool also age up / undergo generational changes
- Marriages persist across era changes — a married couple stays married in the new era (under their new generational names)
- The family tree tracks all name changes across generations

### Worker Recruitment Flow

```
Player wants a new worker
├── Option A: Recruit from Children Pool
│   ├── Browse available children
│   ├── View stats and family lineage
│   └── Recruit → child becomes active worker
└── Option B: Hire Immigrant
    ├── New worker with random stats
    ├── No family lineage
    └── Hire → immigrant becomes active worker
```

### Specialist Bonus

- Children recruited from the pool start with no specialist bonus
- They must earn specialist status through time spent in a building (same as any worker)
- There is no inherited specialist bonus from parents

### Crisis Effects

- Crises that kill workers (e.g. Black Death) can kill married workers, creating widows/widowers
- Children in the children pool are NOT affected by worker-killing crises (they're not yet employed)
- Orphaned children (both parents killed) remain in the pool and can still be recruited

---

## Settings Files

All marriage and family values are defined in settings files:

- `data/settings/workers/family.json`:
  - `max_children_per_couple`: 8 (default)
  - `child_stat_base_min`: 8
  - `child_stat_base_max`: 12
  - `child_inheritance_threshold`: 12 (parent stat must be above this to inherit)
  - `child_inherited_stat_value`: 12 (what the inherited stat is set to)
  - `child_max_inherited_stats`: 2 (one per parent)
  - `divorce_cooldown`: 0 (no cooldown, default)
  - `marriage_cost`: 0 (free by default, could be era-scaled)
  - `mini_game_enabled`: true (false = auto-generate children)
  - `mini_game_stat_boost_amount`: (if mini-game grants a stat boost)

---

## Modding Considerations

- Modders can adjust family settings (increase child cap, enable stat inheritance, etc.)
- Modders can add new naming conventions for new civilizations
- The family tree viewer should handle arbitrary lineage depth gracefully

---

## Summary

| Feature | Status |
|---------|--------|
| Marriage system | Designed |
| Divorce system | Designed |
| Children generation | Designed |
| Children pool | Designed |
| Recruitment (child vs immigrant) | Designed |
| Family tree viewer | Designed |
| Mini-game (child creation) | Concept — format TBD |
| Stat inheritance from parents | Designed — top stat per parent inherited at 12 |
| Crisis interaction | Designed |
| Settings files | Designed |
