# Project Arasmas — Achievements

> **Purpose:** Complete list of all achievements with unlock conditions, rewards, and platform mapping.
> **Last Updated:** 2026-04-05
> **Status:** Template created — to be populated as game systems are finalised

---

## How to Use This File

- Each achievement is defined with all data needed for the game's `data/achievements.json` file
- Achievements are organised by category
- Platform mapping indicates which achievements also appear on Steam, Google Play, and Apple Game Center
- Rewards define what the player receives for unlocking the achievement (boosts, cosmetics, etc.)

---

## Achievement Template

```
### [ID] Achievement Name
- **Category:** [Production / Research / Workers / Crises / Economy / Exploration / Meta]
- **Description:** What the player sees
- **Unlock Condition:** Exact condition to trigger
- **Reward:** What the player receives
- **Rarity:** [Common / Uncommon / Rare / Legendary]
- **Platform:** [All / Steam only / Mobile only]
- **Hidden:** [Yes / No] (hidden achievements not shown until unlocked)
```

---

## 1. Production Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| PROD_001 | Solo Operator | Complete a full production chain with only 1 building | Player completes a product using a single building | TBD | [ ] |
| PROD_002 | First Sale | Sell your first resource | Player sells any resource for the first time | TBD | [ ] |
| PROD_003 | Critical! | Get your first critical success | A building produces a critical success | TBD | [ ] |
| | | | | | |

*To be populated*

---

## 2. Research Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| RES_001 | Eureka | Complete your first research project | Player completes any research | TBD | [ ] |
| RES_002 | Historian | Read every historical description for a civilization | Player views all research/tool history text | TBD | [ ] |
| RES_003 | Forward Thinker | Research a technology from the next era | Player completes a forward research item | TBD | [ ] |
| | | | | | |

*To be populated*

---

## 3. Worker Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| WORK_001 | First Hire | Hire your first worker | Player hires any worker | TBD | [ ] |
| WORK_002 | Generational | Have a worker's descendant reach the Space Age | A single worker lineage survives from Era 1 to Era 12 | TBD | [ ] |
| WORK_003 | Jack of All Trades | Have a single worker hold 5 different occupations | A worker's former occupations list reaches 5 | TBD | [ ] |
| WORK_004 | Educator | Send a worker to education for the first time | Player uses the education system | TBD | [ ] |
| WORK_005 | Matchmaker | Arrange your first marriage between workers | Player marries two workers | TBD | [ ] |
| WORK_006 | Dynasty | Have a single family produce 20+ workers across all generations | Family tree reaches 20 recruited members | TBD | [ ] |
| WORK_007 | Specialist | Have a worker earn the Specialist tag | Worker stays in same building long enough | TBD | [ ] |
| WORK_008 | Full House | Have a married couple reach the 8-child limit | A couple has 8 children | TBD | [ ] |

*To be populated*

---

## 4. Crisis Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| CRIS_001 | Survivor | Survive your first crisis | Player completes any crisis event | TBD | [ ] |
| CRIS_002 | Unbreakable | Survive every type of crisis in a single playthrough | All crisis types experienced and survived | TBD | [ ] |
| CRIS_003 | Crisis Averted | Use a threshold boost to prevent a crisis | Player raises a crisis threshold above the accumulated value | TBD | [ ] |
| CRIS_004 | Survived the Dark Age | Survive a crisis chain reaction (3+ crises cascading) | Dark Age event completed | TBD | [ ] |
| CRIS_005 | Golden Age | Trigger a Golden Age after surviving crises | Golden Age event triggers | TBD | [ ] |

*To be populated*

---

## 5. Economy Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| ECON_001 | Delegate | Buy a resource from the computer for the first time | Player delegates a resource | TBD | [ ] |
| ECON_002 | Millionaire | Accumulate 1,000,000 coins | Player's coin total reaches 1M | TBD | [ ] |
| ECON_003 | Hostile Takeover | Buy out your first competitor | Player purchases a competitor | TBD | [ ] |
| | | | | | |

*To be populated*

---

## 6. Era / Exploration Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| ERA_001 | New Age | Advance to a new era for the first time | Player triggers any era change | TBD | [ ] |
| ERA_002 | Speed Runner | Reach the Space Age in under X hours | Player reaches Era 12 within time limit (TBD) | TBD | [ ] |
| ERA_003 | Completionist | Complete all research and upgrades in every era | All content experienced | TBD | [ ] |
| | | | | | |

*To be populated*

---

## 7. Meta / Game+ Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| META_001 | Victory | Complete any win condition | Player triggers any of the 3 win conditions | TBD | [ ] |
| META_002 | New Game Plus | Start a Game+ playthrough | Player begins Game+ | TBD | [ ] |
| META_003 | World Traveller | Complete a playthrough with each starting civilization | Player wins with GB, China, and Mediterranean | TBD | [ ] |
| | | | | | |

*To be populated*

---

## 8. Hidden Achievements

| ID | Name | Description | Unlock Condition | Reward | Status |
|----|------|-------------|-----------------|--------|--------|
| | | | | | |

*To be populated — hidden achievements are not shown to the player until unlocked*

---

## Summary

| Category | Total | Defined | Rewards Set |
|----------|-------|---------|-------------|
| Production | 3 | 3 | 0 |
| Research | 3 | 3 | 0 |
| Workers | 8 | 8 | 0 |
| Crisis | 5 | 5 | 0 |
| Economy | 3 | 3 | 0 |
| Era / Exploration | 3 | 3 | 0 |
| Meta / Game+ | 3 | 3 | 0 |
| Hidden | 0 | 0 | 0 |
| **TOTAL** | **28** | **28** | **0** |

---

## Platform Mapping Notes

- Steam: achievements via Steamworks SDK
- Google Play: achievements via Google Play Games Services
- Apple: achievements via Game Center
- Not all achievements need to exist on all platforms — some may be in-game only
- Platform-specific achievements (e.g. Steam Deck-specific) may be added later
