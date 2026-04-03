# Project Arasmas — Development Schedule

> **Status:** DRAFT — Open questions remain in plans.md
> **Last Updated:** 2026-04-03
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
| 16 | Finalise art style (Low-Poly 3D vs Cel-Shaded — pending) | [ ] | §1.14 |
| 17 | Answer remaining open questions (10 items in plans.md) | [ ] | §Open Questions |
| 18 | Finalise plans.md with all decisions | [ ] | All |
| 19 | Create detailed Phase 1 sprint breakdown | [ ] | §2.2 |

### Sprint 0.2 — Populate Companion Documents (parallel, separate chats)

**Goal:** Fill in civilization-specific content.

| # | Task | Status | File |
|---|------|--------|------|
| 1 | Populate Great Britain research tree | [ ] | researchGB.md |
| 2 | Populate Great Britain tools & equipment | [ ] | toolsandequipmentGB.md |
| 3 | Create + populate China research tree | [ ] | researchChina.md |
| 4 | Create + populate China tools & equipment | [ ] | toolsandequipmentChina.md |
| 5 | Create + populate Mediterranean research tree | [ ] | researchMediterranean.md |
| 6 | Create + populate Mediterranean tools & equipment | [ ] | toolsandequipmentMediterranean.md |
| 7 | Define production tier structure (buildings, chains) | [ ] | Separate dedicated chat |

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
