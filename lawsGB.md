# Project Arasmas — Laws: Great Britain

> **Purpose:** Complete list of all laws for the Great Britain civilization. Each law includes: era, research cost, effects (positive and negative), replacement laws, and historical basis.
> **Last Updated:** 2026-04-29
> **Status:** Template created — to be populated in a separate dedicated chat session
> **Related Files:** `researchGB.md` (laws are researched like any technology), `plans.md` §1.21 (Laws System)

---

## How to Use This File

- Laws are global modifiers that affect ALL workers and/or ALL buildings when enacted
- Once researched, laws can be enacted and retracted at will at no cost
- Laws are era-appropriate — no modern laws in ancient eras
- Laws from previous eras remain available in later eras UNLESS replaced by a newer version
- Multiple laws can be active simultaneously
- Each law has both positive and negative effects — trade-offs are intentional
- All values defined here feed into `data/settings/laws/` JSON files

---

## Law Template

```
### [ID] Law Name
- **Era Available:** Earliest era this law can be researched
- **Research Point Cost:** RP to complete research
- **Coin Cost to Publish:** Coins to unlock after research
- **Replaces:** [Law ID] or "None" — if this law replaces an older version, the old one becomes unavailable
- **Mutually Exclusive With:** [Law ID(s)] or "None" — enabling this law auto-disables these laws
- **Enactment Cooldown:** 15 minutes after research (default — can be overridden per law)
- **Minimum Active Period:** 1 hour or until era change (default — can be overridden per law)
- **Effects When Enacted:**
  - Positive: [e.g. +10% worker happiness, +5% research speed]
  - Negative: [e.g. -5% production speed, +10% worker cost]
- **Effects When Retracted:** All effects removed immediately
- **Historical Basis (Great Britain):** The real-world historical context for this law
```

---

## Era 1 — Primitive Age

*Laws unlikely at this era — tribal customs rather than formal laws. To be determined.*

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

*To be populated — examples: feudal obligations, guild regulations, tithe laws*

---

## Era 6 — Renaissance

*To be populated — examples: patent laws, trade charters, religious tolerance acts*

---

## Era 7 — Colonial

*To be populated — examples: trade monopoly acts, navigation acts, colonial labour laws*

---

## Era 8 — Industrial Revolution

*To be populated — examples: factory acts, child labour restrictions, minimum wage, worker safety, work hour limits*

---

## Era 9 — World Wars

*To be populated — examples: rationing, conscription, wartime production mandates, emergency powers*

---

## Era 10 — Silicon Age

*To be populated — examples: environmental regulations, health and safety, equal pay, anti-discrimination*

---

## Era 11 — Information Age

*To be populated — examples: data protection, digital rights, remote work policies, gig economy regulations*

---

## Era 12 — Space Age

*To be populated — examples: space resource rights, AI labour laws, universal basic income*

---

## Law Replacement Chains

*Visual representation of how laws evolve and replace earlier versions across eras.*

```
Example:
Bronze Age: Basic Rest Day (1 rest day per 10 work days)
    → Medieval: Sabbath Observance (1 rest day per 7 work days) [REPLACES Basic Rest Day]
    → Industrial Revolution: Saturday Half-Day (5.5 day work week) [REPLACES Sabbath Observance]
    → Information Age: 5-Day Work Week [REPLACES Saturday Half-Day]
    → Space Age: 4-Day Work Week [REPLACES 5-Day Work Week]
```

---

## Summary

| Era | Total Laws | Replacement Laws |
|-----|-----------|-----------------|
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
