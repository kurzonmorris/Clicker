# Project Arasmas — Development Schedule

> **Status:** DRAFT — Open questions remain in plans.md
> **Last Updated:** 2026-04-30
> **Guide Purpose:** This file is the single source of truth for what to work on next. Any AI model (Claude Code or otherwise) should read this file FIRST to determine the current task.

---

## How to Use This Schedule

1. Read the **Current Phase** section to know what phase the project is in
2. Read the **Current Sprint** section to know what tasks are active
3. Check task status: `[ ]` = not started, `[~]` = in progress, `[x]` = done
4. Refer to `plans.md` for detailed specifications of each task
5. When a sprint is complete, move to the next sprint
6. Never skip ahead — phases are sequential and depend on prior work
7. Companion documents (`researchGB.md`, `toolsandequipmentGB.md`, `placeholderart.md`) are populated in parallel via separate chat sessions

---

## Current Phase

**Phase 0 — Planning & Decisions**

Open questions in plans.md must be answered before development begins. Civilization-specific content (research trees, equipment lists) is being developed in separate chat sessions.

---

## Phase Overview

| Phase | Name | Description | Est. Points | Status |
|-------|------|-------------|-------------|--------|
| 0 | Planning & Decisions | Answer all design questions, finalise plans.md, populate companion docs | — | IN PROGRESS |
| 1 | Project Setup | Godot install, project scaffold, GitHub repo, CI skeleton | 19 | NOT STARTED |
| 2 | Core Mechanics Prototype | Click-to-gather, sell, hire worker, basic equipment — one era only | 26 | NOT STARTED |
| 3 | Economy & Workers | Currency system, worker hiring/payment, cost scaling, big numbers, offline earnings | 34 | NOT STARTED |
| 4 | Era & Research System | Era progression, research system, civilization framework, production chains | 55+ | NOT STARTED |
| 5 | Education, Save & Equipment Depth | Education system, save/load, equipment upgrade paths, forward research | 39 | NOT STARTED |
| 6 | UI / UX & Boosts | Full menu system, adaptive layout, inventory/chest, boost system, accessibility | 34 | NOT STARTED |
| 7 | Crisis System | Interim era crises, probability engine, crisis settings, temporary/permanent effects | 21 | NOT STARTED |
| 8 | Audio & Competitors | SFX, era music, audio buses, competitor system (scope TBD) | 16–29 | NOT STARTED |
| 9 | Win Conditions & Achievements | Win states, Game+, platform achievements, milestones | 16 | NOT STARTED |
| 10 | Platform Builds | Export to Windows, Linux, Android (iOS deferred until Mac) | 13 | NOT STARTED |
| 11 | Monetisation & Store Integration | Ad system, DLC system, store SDKs (Steam, Epic, Google Play, Apple) | 34 | NOT STARTED |
| 12 | Modding Support | Mod loading, GitHub pipeline, mod browser, access restriction | 21 | NOT STARTED |
| 13 | Testing & QA | Full test pass, performance profiling, accessibility audit, balance pass | 13 | NOT STARTED |
| 14 | Launch Prep | Store listings, screenshots, trailers, marketing, final polish | 8 | NOT STARTED |

---

## Current Sprint

### Sprint 0.1 — Answer Remaining Open Questions

**Goal:** Get all remaining design decisions locked in so plans.md can be fully finalised.

| # | Task | Status | Plans.md Ref |
|---|------|--------|-------------|
| 1 | Confirm engine choice (Godot 4.x + GDScript) | [x] | §2.1 |
| 2 | Confirm era list (12 eras) | [x] | §1.2 |
| 3 | Confirm civilization system (3 starting civs) | [x] | §1.3 |
| 4 | Confirm worker stat system (Str/Cha/Int/Luck) | [x] | §1.5 |
| 5 | Confirm education replaces prestige | [x] | §1.6 |
| 6 | Confirm equipment upgrade path system | [x] | §1.7 |
| 7 | Confirm research system mechanics | [x] | §1.8 |
| 8 | Confirm crisis/interim era system | [x] | §1.9 |
| 9 | Confirm boost/inventory system with matching | [x] | §1.10 |
| 10 | Confirm economy (no premium currency) | [x] | §1.11 |
| 11 | Confirm win conditions (3 paths + Game+) | [x] | §1.13 |
| 12 | Confirm monetisation (paid + free ad-supported) | [x] | §1.19 |
| 13 | Confirm offline earnings (25%, 3hr) | [x] | §1.20 |
| 14 | Confirm mod system + GitHub pipeline | [x] | §2.10 |
| 15 | Confirm ad system (contextual, per-building cooldown) | [x] | §2.11 |
| 16 | Confirm worker naming + generational lineage system | [x] | §1.5 |
| 17 | Confirm worker community pool + auto-assignment | [x] | §1.5 |
| 18 | Confirm unrestricted worker role assignment | [x] | §1.5 |
| 19 | Confirm difficulty settings (delegation markup, competitor count, crisis freq) | [x] | §1.11 |
| 20 | Confirm resource delegation system | [x] | §1.4 |
| 21 | Confirm critical success mechanic | [x] | §1.4 |
| 22 | Confirm attack boosts (research-gated) | [x] | §1.10 |
| 23 | Confirm Crisis Monitor unlocked in Iron Age | [x] | §1.9 |
| 24 | Confirm disrepair mechanic (2 ages behind = rebuild) | [x] | §1.2 |
| 25 | Confirm map free-form placement + road drawing | [x] | §1.15 |
| 26 | Confirm decorative buildings fixed list per era + research | [x] | buildingsGB.md |
| 27 | Confirm town hall = visual centre + community stats display | [x] | buildingsGB.md |
| 28 | Confirm all-numbers-editable principle | [x] | §2.3 |
| 29 | Finalise art style (Low-Poly 3D vs Cel-Shaded — DEFERRED until artist cost known) | [ ] | §1.14 |
| 30 | Confirm poor worker ratios cause inefficiency (backlog/waste mechanic) | [x] | §1.5 |
| 31 | Confirm no generational stat variance (permanent) | [x] | §1.5 |
| 32 | Confirm difficulty locked for playthrough | [x] | §1.11 |
| 33 | Confirm Crisis Monitor upgradeable through later research | [x] | §1.9 |
| 34 | Confirm competitor adaptive difficulty (dev benchmarks + multipliers) | [x] | §1.12 |
| 35 | Confirm attack boost results visible to player | [x] | §1.12 |
| 36 | Confirm production buildings must be placed on map before use | [x] | §1.15 |
| 37 | Confirm disrepair: same rebuild cost, can relocate | [x] | §1.15 |
| 38 | Confirm Town Hall = stats dashboard for all buildings (upgrades per era) | [x] | §1.15, buildingsGB.md |
| 39 | Confirm buildings movable for era-appropriate fee | [x] | §1.15 |
| 40 | Confirm competitors are named regional rivals (reveal progressively through eras) | [x] | §1.12 |
| 41 | Confirm built-in benchmark recording mode for dev playtesting | [x] | §1.12 |
| 42 | Confirm crisis effects on competitors visible (both summary + detail) | [x] | §1.12 |
| 43 | Confirm worker specialist bonus (stays in same building = bonus tag) | [x] | §1.5 |
| 44 | Confirm worker family tree viewer | [x] | §1.5 |
| 45 | Confirm marriage & family mini-game (marry, divorce, 8 children max per couple) | [x] | minigame_family.md |
| 46 | Confirm worker recruitment: immigrant OR child from children pool | [x] | §1.5 |
| 47 | Confirm crisis chain reactions → Dark Age events | [x] | §1.9 |
| 48 | Confirm Golden Ages (post-crisis or sustained prosperity) | [x] | §1.9 |
| 49 | Confirm building adjacency zones (bonuses + negatives) | [x] | §1.15 |
| 50 | Confirm "Did You Know?" historical pop-ups | [x] | §1.17 |
| 51 | Confirm seasonal cycles following real-world calendar | [x] | §1.2 |
| 52 | Confirm boost installation into buildings (1 per building, permanent at reduced effect) | [x] | §1.10 |
| 53 | Confirm era transition cinematics (end of development feature) | [x] | §1.2 |
| 54 | Confirm worker happiness system (50% baseline, ±2% speed per 1%) | [x] | §1.5 |
| 55 | Confirm Laws system (global modifiers, enact/retract at will, era-appropriate) | [x] | §1.21 |
| 56 | Confirm happiness buildings category | [x] | §1.22 |
| 57 | Confirm specialist system rework (95% threshold, progress/decay tracking) | [x] | §1.5 |
| 58 | Confirm child stat inheritance (top stat per parent at 12, base range 8–12) | [x] | minigame_family.md |
| 59 | Confirm adjacency zones REMOVED | [x] | §1.15 |
| 60 | Confirm seasonal default ±10% | [x] | §1.2 |
| 61 | Confirm Golden Age trigger (85% efficiency sustained 1hr default) | [x] | §1.9 |
| 62 | Confirm competitor reveal schedule per civilization settings | [x] | §1.12 |
| 63 | Confirm map starting size 10×10 grid | [x] | §1.15, buildingsGB.md |
| 64 | Confirm boost installation: 1 per category per building, replacement loses old boost only | [x] | §1.10 |
| 65 | Confirm happiness buildings global effect + class-based targeting | [x] | §1.22 |
| 66 | Confirm happiness factors (golden age, crisis, overcharge, enemy boosts) | [x] | §1.5 |
| 67 | Confirm laws unlimited + mutual exclusivity + cooldowns (15min enact, 1hr minimum active) | [x] | §1.21 |
| 68 | Confirm specialist progress rate (1%/min, 95 min to specialist) | [x] | §1.5 |
| 69 | Confirm specialist inverse decay (1:1 ratio new vs old) | [x] | §1.5 |
| 70 | Confirm map grows by +10 per era (10×10 to 120×120) | [x] | §1.15, buildingsGB.md |
| 71 | Confirm Era 1 has no happiness buildings | [x] | §1.22 |
| 72 | Confirm individual + per-building average happiness visible | [x] | §1.5 |
| 73 | Confirm building overcharge mode (increased production, reduced happiness) | [x] | §1.4 |
| 74 | Answer remaining open questions (fine-tuning items in plans.md) | [~] | §Open Questions |
| 75 | Finalise plans.md with all decisions | [ ] | All |
| 76 | Create detailed Phase 1 sprint breakdown | [ ] | §2.2 |

### Sprint 0.2 — Populate Companion Documents (parallel, separate chats)

**Goal:** Fill in civilization-specific content.

| # | Task | Status | File |
|---|------|--------|------|
| 1 | Populate Great Britain research tree | [ ] | researchGB.md |
| 2 | Populate Great Britain tools & equipment | [ ] | toolsandequipmentGB.md |
| 3 | Populate Great Britain buildings | [ ] | buildingsGB.md |
| 4 | Populate Great Britain laws | [ ] | lawsGB.md |
| 5 | Populate achievements list | [ ] | achievements.md |
| 6 | Create + populate China research tree | [ ] | researchChina.md |
| 7 | Create + populate China tools & equipment | [ ] | toolsandequipmentChina.md |
| 8 | Create + populate China buildings | [ ] | buildingsChina.md |
| 9 | Create + populate China laws | [ ] | lawsChina.md |
| 10 | Create + populate Mediterranean research tree | [ ] | researchMediterranean.md |
| 11 | Create + populate Mediterranean tools & equipment | [ ] | toolsandequipmentMediterranean.md |
| 12 | Create + populate Mediterranean buildings | [ ] | buildingsMediterranean.md |
| 13 | Create + populate Mediterranean laws | [ ] | lawsMediterranean.md |
| 14 | Define production tier structure (chains, resources) | [ ] | Separate dedicated chat |

---

## Future Sprints (Phase 1+)

> Will be populated in detail once Phase 0 is complete. Below is a high-level preview.

### Phase 1 — Project Setup

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Install Godot 4.x, create project | §2.1 |
| 2 | Create folder structure per §2.2 | §2.2 |
| 3 | Initialise GitHub repository | §2.13 |
| 4 | Set up CI pipeline skeleton (GitHub Actions) | §2.13 |
| 5 | Create master_defaults.json template | §2.3 |
| 6 | Create era settings file templates (12 files) | §2.3 |
| 7 | Create signal_bus.gd and constants.gd | §2.2 |
| 8 | Set up debug vs release build configs | §2.13 |
| 9 | Create CHANGELOG.md | §2.13 |

### Phase 2 — Core Mechanics Prototype

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement clickable resource node | §1.1 |
| 2 | Implement basic inventory (raw material count) | §1.1 |
| 3 | Implement sell button (material → coins) | §1.1, §1.11 |
| 4 | Implement basic worker hiring | §1.5 |
| 5 | Implement worker auto-production | §1.5 |
| 6 | Implement basic equipment purchase | §1.7 |
| 7 | Implement state machine (Menu, Playing, Paused, Settings) | §2.4 |
| 8 | Implement input abstraction layer | §2.8 |
| 9 | Basic UI layout (header, main view, upgrade panel, nav) | §1.15 |

### Phase 3 — Economy & Workers

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement full economy system (coins, per-second costs) | §1.11 |
| 2 | Implement worker stats (Str/Cha/Int/Luck) | §1.5 |
| 3 | Implement worker experience/leveling | §1.5, §1.6 |
| 4 | Implement cost scaling (exponential curves) | §1.11 |
| 5 | Implement big number system | §2.6 |
| 6 | Implement offline earnings calculation | §1.20 |
| 7 | Implement worker role assignment within buildings | §1.5 |
| 8 | Implement critical hit system (Luck stat) | §1.5 |

### Phase 4 — Era & Research System

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement era data loading from settings files | §1.2, §2.3 |
| 2 | Implement era change mechanic (inflation, building upgrade requirement) | §1.2 |
| 3 | Implement civilization selection screen | §1.3 |
| 4 | Implement civilization data loading | §1.3 |
| 5 | Implement research system (researchers, Research Points, coin cost to unlock) | §1.8 |
| 6 | Implement parallel research unlock | §1.8 |
| 7 | Implement forward research (next-era research with limits) | §1.8 |
| 8 | Implement production chain framework (data-driven) | §1.4 |
| 9 | Load and render Great Britain research tree | §1.8 |
| 10 | Load and render Great Britain equipment | §1.7 |

### Phase 5 — Education, Save & Equipment Depth

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement education system (pay to level workers) | §1.6 |
| 2 | Implement diminishing returns on worker leveling | §1.6 |
| 3 | Implement equipment incremental upgrade paths | §1.7 |
| 4 | Implement equipment full replacement | §1.7 |
| 5 | Implement save/load system (JSON, versioned) | §2.5 |
| 6 | Implement auto-save (30s + app close) | §2.5 |
| 7 | Implement save slots (minimum 3) | §2.5 |

### Phase 6 — UI / UX & Boosts

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement full adaptive layout (portrait + landscape) | §1.15 |
| 2 | Implement building zoom view | §1.15 |
| 3 | Implement boost inventory/chest system | §1.10 |
| 4 | Implement boost matching/crafting (5→1) | §1.10 |
| 5 | Implement boost stacking with diminishing returns | §1.10 |
| 6 | Implement settings screen (volume, fullscreen, controls) | §1.15 |
| 7 | Implement accessibility features | §2.9 |
| 8 | Implement difficulty settings screen (crisis frequency) | §1.9 |

### Phase 7 — Crisis System

| # | Task | Plans.md Ref |
|---|------|-------------|
| 1 | Implement crisis probability engine | §1.9 |
| 2 | Implement crisis trigger conditions | §1.9 |
| 3 | Implement temporary effect phase (timer + production modifier) | §1.9 |
| 4 | Implement permanent effect phase (workers killed, buildings destroyed) | §1.9 |
| 5 | Load crisis settings files per civilization | §1.9 |
| 6 | Implement master settings overlay system | §2.3 |

### Phase 8+ — Later Phases

*Detailed sprint breakdowns created when earlier phases complete.*

- Phase 8: Audio & Competitors
- Phase 9: Win Conditions & Achievements
- Phase 10: Platform Builds
- Phase 11: Monetisation & Store Integration
- Phase 12: Modding Support
- Phase 13: Testing & QA
- Phase 14: Launch Prep
