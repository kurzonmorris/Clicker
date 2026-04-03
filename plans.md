# Project Arasmas — Master Plan

> **Status:** DRAFT — Some open questions remain (see bottom)
> **Last Updated:** 2026-04-03
> **Working Title:** Project Arasmas

---

## Table of Contents

1. [Section 1 — Game Story / Visual Elements](#section-1--game-story--visual-elements)
   - 1.1 Core Game Loop
   - 1.2 Era System
   - 1.3 Civilization System
   - 1.4 Production Chain / Progression Tiers
   - 1.5 NPC Worker System
   - 1.6 Education & Leveling System
   - 1.7 Equipment & Tool System
   - 1.8 Research System
   - 1.9 Crisis / Interim Era System
   - 1.10 Boost & Inventory System
   - 1.11 Economy / Balance
   - 1.12 Competitors / AI Players
   - 1.13 Win Conditions & Game+
   - 1.14 Visual Style / Art Direction
   - 1.15 UI / UX Layout
   - 1.16 Audio
   - 1.17 Story / Narrative
   - 1.18 Achievements / Milestones
   - 1.19 Monetisation Strategy
   - 1.20 Offline Earnings
2. [Section 2 — Coding / File Elements](#section-2--coding--file-elements)
   - 2.1 Engine (Confirmed)
   - 2.2 Project Architecture
   - 2.3 Data-Driven Design & Settings Files
   - 2.4 State Machine
   - 2.5 Save System
   - 2.6 Big Number System
   - 2.7 Platform-Specific Builds
   - 2.8 Input System
   - 2.9 Accessibility
   - 2.10 Modding Support & GitHub Pipeline
   - 2.11 Ad System
   - 2.12 DLC System
   - 2.13 CI / Build Pipeline
   - 2.14 Analytics & Telemetry
3. [Companion Documents](#companion-documents)
4. [Open Questions](#open-questions)

---

## Section 1 — Game Story / Visual Elements

### 1.1 Core Game Loop

**Description:** The fundamental play cycle the player repeats.

**Confirmed Flow:**
- **Click** a resource node (e.g. rock) to gather raw material
- **Sell** gathered material for currency (coins)
- **Hire** NPC workers to automate gathering (paid per second)
- **Buy** equipment and tools for workers to improve production
- **Research** new technologies using researchers (paid per second)
- **Upgrade** workers (through time/experience or education), equipment (incremental improvements or replacements), and buildings
- **Hit ceiling** — production maxes out for the current era
- **Advance era** — all buildings must be upgraded to new era first, inflation reduces currency, new production chains unlock
- **Repeat** through 12 eras from Primitive Age to Space Age

The game blends Civilization-style era progression, Factorio-lite production chains, and traditional clicker/idle mechanics.

**Estimated Work Phase:** Phase 2
**Estimated Points:** 13

---

### 1.2 Era System

**Description:** The game progresses through historical eras. The entire game world advances together — when the player triggers an era change, everything changes at once.

**Confirmed Eras (12):**

| # | Era | Notes |
|---|-----|-------|
| 1 | Primitive Age | Starting era — manual clicks, basic gathering |
| 2 | Stone Age | First tools, basic workers |
| 3 | Bronze Age | Metal working begins, smelting |
| 4 | Iron Age | Stronger tools, larger operations |
| 5 | Medieval | Expanded workforce, trade begins |
| 6 | Renaissance | Science and research accelerate |
| 7 | Colonial | Global trade, expansion, larger scale |
| 8 | Industrial Revolution | Machines replace manual labour, factories |
| 9 | World Wars | Military production, rapid tech advancement |
| 10 | Silicon Age | Electronics, early computing |
| 11 | Information Age | Digital systems, automation |
| 12 | Space Age | Final era — space mining, endgame |

**Era Change Mechanics:**
- When advancing to a new era, ALL buildings/industries must be upgraded to the new era's standards before anything else can be upgraded — this is the first priority
- **Inflation:** Currency is reduced by a set percentage on era change (hardcoded per civilization per era in the civilization settings file). All ongoing production is also reduced by the same inflation percentage
- **Forward Research:** Players can research the NEXT era's technologies while still in the current era, up to a limit. This research cannot be used until the era changes, but gives a head start. Strategic trade-off: advance quickly or stay and pre-research
- Each era unlocks new production chains, buildings, workers, equipment, and research
- Era-specific worker limits per building change with each era (e.g. Iron Age mine: 10 workers, Medieval mine: 20 workers)

**Era Settings:** Each era will have its own settings file defining: available research, buildings, equipment, worker limits, inflation rates, production values, and crisis eligibility.

**Estimated Work Phase:** Phase 4
**Estimated Points:** 21

---

### 1.3 Civilization System

**Description:** At the start of the game, the player chooses a civilization. This choice is locked for the entire playthrough and affects technology timings, visuals, historical text, and crisis events.

**Confirmed Starting Civilizations (3):**
- **Great Britain** — Gets muskets quickly after gunpowder, strong industrial era
- **China** — Gets gunpowder early but muskets late, different tech progression
- **Mediterranean** — (Specifics TBD in separate civilization chat)

**Future Civilizations (potential DLC/mods):**
- Native American
- African
- Mesoamerican (Aztec, Maya, Inca)

**Civilization Differences:**
- **Technology timing:** Same research exists across civilizations but unlocks at different times/costs. Each civilization has a unique tech tree ordering
- **Visual changes:** Art style reflects the civilization's architecture, clothing, tools
- **Historical text:** Every research item and tool has civilization-specific historical descriptions explaining how that civilization discovered/developed it
- **Crisis events:** Each civilization has specific crises tied to its history (e.g. Great Fire is specific to certain civilizations between Medieval and Industrial eras)
- **Skinnable:** The civilization is effectively a skin system — future civilizations can be added as DLC or mods

**Companion Documents:** Each civilization gets two dedicated files:
- `research[CIV].md` — Full research tree for that civilization
- `toolsandequipment[CIV].md` — Full tools and equipment list for that civilization

These are populated in separate chat sessions focused on each civilization.

**Estimated Work Phase:** Phase 4–5
**Estimated Points:** 21 per civilization

---

### 1.4 Production Chain / Progression Tiers

**Description:** Each tier introduces new materials, recipes, and upgrade paths. Production tiers exist within eras — as eras advance, new tiers become available.

**Note:** The specific production tiers, buildings, and chains will be defined in a separate dedicated chat. The system is NOT hardcoded — tiers are defined in data files and can be added/modified without code changes.

**General Principles:**
- Each tier takes input resources and produces output resources
- Later tiers consume outputs from earlier tiers or from purchased inputs
- Each building within a tier has its own worker capacity, equipment slots, and upgrade paths
- The player can choose to buy resources from "other companies" instead of producing them (this has gameplay implications — see Crisis system §1.9)
- Production tiers are era-dependent — new eras unlock new tiers and improve existing ones

**Estimated Work Phase:** Phase 4
**Estimated Points:** 21 (framework) + ongoing per tier

---

### 1.5 NPC Worker System

**Description:** Workers are hired NPC characters that automate production. Each worker is an individual entity with stats, experience, and equipment.

**Worker Stats:**
- **Strength** — Affects production output for physical tasks (mining, smithing, hauling)
- **Charisma** — Affects trade deals, negotiations, selling prices
- **Intelligence** — Affects research speed, complex equipment operation
- **Luck** — Causes critical events (both positive and negative):
  - Low luck: more likely to trigger negative criticals (production reduced by up to 40% based on how bad the luck roll is)
  - High luck: more likely to trigger positive criticals (production increased by up to 30% based on how good the luck roll is)
- **Additional stats:** May be added later based on gameplay needs

**Worker Mechanics:**
- Workers are hired with coins and cost coins per second to employ
- Each worker needs equipment to function (can't mine without a pickaxe)
- Workers gain experience over time by performing their task — this slowly levels them up
- Education can skip/accelerate leveling (see §1.6)
- Workers can be assigned to specific roles within a building (e.g. 5 mining, 5 hauling)
- Each era defines how many workers a specific building can hold and what role distribution looks like
- Workers carry over between era changes unchanged — they keep their stats, level, and equipment. New research in the new era allows them to learn new skills and use new tools
- Example: In one era workers use pickaxes; in the next era they get explosives. They're not good with explosives at first (low experience) but produce more than with pickaxes. As they gain experience with the new tool, production improves further

**Worker Settings:** Each worker type will have a settings file defining base stats, growth curves, equipment slots, and role capabilities.

**Estimated Work Phase:** Phase 3–4
**Estimated Points:** 21

---

### 1.6 Education & Leveling System

**Description:** Workers level up through use (experience over time) or through education (spending money to accelerate).

**Confirmed Mechanics:**
- **Experience leveling:** Workers slowly gain experience by working. Free but slow
- **Education:** Player pays coins to send workers to education, which levels them up faster. Education costs scale with worker level
- **No global prestige/reset.** Instead, individual workers, equipment, and tools can each be "prestiged" — upgraded/replaced with better versions
- **Diminishing returns:** As workers level up, each additional level provides less benefit. Research and better equipment are needed to make high-level workers useful again
- **No hard cap:** Currently no level cap, but diminishing returns create a soft cap. Alpha/beta testing may introduce hard limits

**Education replaces the traditional prestige system.** There is no game-wide reset mechanic.

**Estimated Work Phase:** Phase 5
**Estimated Points:** 13

---

### 1.7 Equipment & Tool System

**Description:** Every worker needs equipment. Equipment can be incrementally improved or fully replaced.

**Confirmed Mechanics:**
- **Incremental upgrades:** Within an era, equipment can be improved step by step. Example: pickaxe → better handle → rope-wrapped handle → reinforced head. Each step costs money and may require specific research
- **Full replacements:** When research unlocks a fundamentally better tool, the old one is replaced entirely. Example: pickaxe → explosives
- **Upgrade paths:** Where possible, the player can CHOOSE which improvements to apply (if they have the research). Some upgrades have prerequisites (must do A before B)
- **Era requirements:** When changing eras, equipment MUST be upgraded to era-appropriate versions before buildings can function at full capacity
- **Equipment affects production:** Better equipment = more output. Combined with worker skill, this creates the core production formula
- **Equipment settings:** Each piece of equipment has a settings file defining: cost, production multiplier, prerequisites, era, civilization availability

**Companion Document:** `toolsandequipment[CIV].md` for each civilization lists all equipment and upgrade paths.

**Estimated Work Phase:** Phase 3–4
**Estimated Points:** 13 (system) + ongoing per equipment item

---

### 1.8 Research System

**Description:** Research unlocks new technologies, equipment, buildings, and capabilities.

**Confirmed Mechanics:**
- **Researchers:** Hired NPCs that cost coins per second (like workers). They generate Research Points passively
- **Researcher rate:** Flat rate per researcher. Researchers can be given upgrades and tools to speed up research, but those tools also need to be researched first
- **Research cost:** After a technology has been researched (using Research Points), it costs coins to actually unlock/apply
- **Parallel research:** Initially only one research project at a time. Researching "parallel research" unlocks the ability to run multiple projects simultaneously
- **Forward research:** Players can research the next era's technologies while in the current era, up to a limit. Cannot use the results until the era changes
- **Civilization-specific:** Each civilization has the same general research items but different unlock timings and costs. The historical description text is unique per civilization
- **Research points from boosts:** Each completed research gives the player a boost item they can store and activate later (see §1.10)

**Companion Document:** `research[CIV].md` for each civilization lists the full tech tree.

**Estimated Work Phase:** Phase 4
**Estimated Points:** 13 (system) + ongoing per research item

---

### 1.9 Crisis / Interim Era System

**Description:** Between regular eras, crisis events can occur that cause temporary and permanent negative effects. These are full "interim eras" with their own mechanics.

**Confirmed Mechanics:**

**Crisis Examples:**
- Great Fire — destroys buildings
- Black Plague/Black Death — kills workers (e.g. 60% of workers die)
- Rebellion/Uprising — production disruption
- Famine — resource depletion
- Library Destruction — research setbacks
- Rat Infestation — food/resource consumption
- Currency devaluation — money loses value

**Crisis Triggers:**
- **Player-configurable frequency:** At game start, the player sets how often crises can occur (a difficulty slider)
- **Probability-based:** Each crisis has conditions that increase or decrease its likelihood. These probabilities shift based on player actions:
  - Owning many companies increases Great Fire probability (Medieval–Industrial only)
  - Buying from other companies instead of self-producing decreases Great Fire probability
  - Stockpiling food reduces Famine probability BUT increases Rat Infestation probability
  - After Rat Infestation (food consumed), Famine and Black Death probability increase
- **Civilization-specific:** Each civilization has its own set of possible crises tied to historical events
- **Era-restricted:** Each crisis can only occur within certain era ranges

**Crisis Effects (two phases):**
1. **Immediate temporary effect:** A negative percentage modifier on all production (severity varies per crisis). Lasts a real-world timer (approximately 10 minutes, varies per crisis). Simulates the crisis happening
2. **Permanent effect:** After the timer expires, the temporary modifier is removed BUT the permanent damage remains — workers killed stay dead, buildings destroyed stay destroyed, etc. The player must rebuild

**Crisis Settings:** Every crisis has its own settings file defining:
- Era range (when it can happen)
- Probability modifiers (what increases/decreases likelihood)
- Temporary effect duration and severity
- Permanent effects (what gets destroyed/killed/lost)
- Civilization availability
- Positive outcomes (some crises may have silver linings)

**Strategic Depth:** Players can use boosts to mitigate crisis effects. Enemy NPC players may also be able to use negative effects against the player (and vice versa — see §1.12).

**Master Settings File:** A default settings file defines baseline probabilities. Era changes compound/modify these settings. The crisis system reads from this master file plus era-specific and civilization-specific overrides.

**Estimated Work Phase:** Phase 7
**Estimated Points:** 21

---

### 1.10 Boost & Inventory System

**Description:** Boosts are storable items that provide temporary positive effects. They are stored in a chest/inventory system.

**Boost Sources:**
- Completing research (each research grants a related boost)
- Purchased with in-game currency
- DLC bonuses
- Watching ads (free version — boost type depends on what screen the player is viewing)

**Boost Types (examples — full list TBD):**
- Double research point production
- Increase hired worker experience gain
- Increase worker level or speed
- Increase money production
- Stat-specific boosts (e.g. +5% Strength to a worker or tool)
- Building-wide boosts (e.g. +10% production for an entire mine)
- Anti-crisis boosts (mitigate negative effects during a crisis)

**Rarity Grades:**
- **Common** — Small effect (e.g. +5% Strength)
- **Uncommon** — Moderate effect
- **Rare** — Strong effect
- **Legendary** — Very strong effect

Rarity affects the magnitude of the boost. A boost can affect a worker stat, a tool's performance, or an entire building's output.

**Matching/Crafting System:**
- 5 Common → 1 Uncommon
- 5 Uncommon → 1 Rare
- 5 Rare → 1 Legendary
- (Numbers subject to change based on playtesting — defined in a dedicated matching settings file)

**Stacking:**
- Boosts CAN stack, but with diminishing returns
- Formula: First boost = full value. Second boost = value × 50% added on top. Third boost = another reduced amount. Example: 2x production boost × 2 stacked = 3x (not 4x). Three stacked = ~3.5x (not 6x)
- Once the stack reaches a maximum effect cap, additional boosts extend the DURATION instead
- Duration extension also has a cap
- Stacking rules defined in a settings file

**Inventory / Chest:**
- Initially: 4 slots for different boost types, maximum 5 of each type
- Researchable upgrades: more slots, larger stack limits
- **DLC: Unlimited types** (removes slot limit)
- **DLC: Unlimited quantity** (removes stack limit)
- When inventory is full, the player is prompted to use or stack boosts before receiving new ones

**Estimated Work Phase:** Phase 6
**Estimated Points:** 13

---

### 1.11 Economy / Balance

**Description:** How currency flows and how progression is gated.

**Confirmed:**
- **Primary Currency:** Coins — earned by selling products
- **No premium currency.** No gems, tokens, or paid currency
- **Worker costs:** Hired workers cost coins per second (flat rate per worker)
- **Researcher costs:** Researchers cost coins per second (flat rate per researcher)
- **Research costs:** After research is complete (via Research Points), coins are paid to unlock the result
- **Equipment costs:** Tools, upgrades, and replacements cost coins
- **Education costs:** Leveling workers through education costs coins
- **Cost scaling:** Exponential cost curves for upgrades (standard idle game formula)
- **Inflation on era change:** A set percentage of currency is lost when advancing to a new era. Ongoing production also reduced by the same percentage. Inflation rates are per-civilization per-era in settings files
- **No premium currency:** Temporary boosts replace what premium currency would typically provide

**Estimated Work Phase:** Phase 3
**Estimated Points:** 13

---

### 1.12 Competitors / AI Players

**Description:** Other entities in the game world that are also developing and building. Priority: NOT an early implementation — depends on complexity.

**Confirmed Design Intent:**
- Competitors serve as a gauge — the player can see if they're progressing faster or slower than the AI
- Competitors are a win condition target — "buy all competitors" is one way to win
- Competitors may be able to use negative effects against the player (and vice versa)
- Implementation complexity will determine whether competitors are active AI entities or abstract progress bars

**Deferred:** Detailed competitor design will be determined after core systems are built. If AI competitors are too complex, they may be simplified to static progress markers.

**Estimated Work Phase:** Phase 8+ (late development)
**Estimated Points:** 21 (if active AI) or 8 (if abstract)

---

### 1.13 Win Conditions & Game+

**Description:** The game has multiple win conditions. After winning, the player can continue or start Game+.

**Win Conditions (complete ANY one):**
1. **Buy all competitors** — Purchase every competing entity in the game
2. **Reach space mining** — Progress to the Space Age and establish space mining operations
3. **Accumulate a fortune** — Reach a static currency threshold high enough to buy every company except competitors (exact number TBD)

**Post-Win:**
- After winning, the player can continue playing until ALL research is complete, ALL tools bought and upgraded, and ALL content experienced
- The player can then choose to start **Game+**

**Game+ Mode:**
- Same game, fresh start from Primitive Age
- All costs are 50%–100% higher (exact multiplier TBD, likely a settings value)
- More frequent/severe crisis events
- Increased research speed and other stat adjustments to compensate
- Purpose: increased difficulty for replayability

**Estimated Work Phase:** Phase 9
**Estimated Points:** 8

---

### 1.14 Visual Style / Art Direction

**Description:** The look and feel of the game.

**Current Direction:** Low-Poly 3D or Cel-Shaded Cartoon effect (not yet finalised — decision between these two)

**Art Pipeline:**
- **Phase 1:** All art is AI-generated placeholder
- **Phase 2:** Artist-produced final art replaces placeholders
- All placeholder art is tracked in `placeholderart.md` with a complete list of every asset that needs replacement

**Skin System:** The visual theme is tied to the civilization choice. Different civilizations have different architectural styles, clothing, tools, and environmental art. Future civilizations (DLC/mods) add new visual skins.

**Estimated Work Phase:** Ongoing from Phase 2
**Estimated Points:** 21+ (art is the largest ongoing effort)

---

### 1.15 UI / UX Layout

**Description:** How the game screen is organised.

**Confirmed:** Adaptive layout — portrait for mobile, landscape for desktop/Steam Deck. Both orientations supported.

**Proposed Layout:**

```
┌─────────────────────────────┐
│  [Currency / Era / Header]  │
├─────────────────────────────┤
│                             │
│   [Main Production View]    │
│   (clickable resource node, │
│    workers, machines,       │
│    production animation)    │
│   Player can zoom into      │
│   individual buildings      │
│                             │
├─────────────────────────────┤
│  [Upgrade Panel / Shop]     │
│  (scrollable list of        │
│   purchasable upgrades)     │
├─────────────────────────────┤
│  [Bottom Nav Bar]           │
│  Overview | Buildings |     │
│  Research | Inventory | ... │
└─────────────────────────────┘
```

- Main view: overview of all buildings/production, zoomable to individual buildings
- Zooming into a building shows its workers, equipment, production, and building-specific options
- Ad-watch bonus is contextual to what's on screen (see §1.19)
- Bottom nav switches between major game sections
- Settings accessible from header
- Currently list/menu-based, but architecture should support future map/grid view if funded

**Estimated Work Phase:** Phase 6
**Estimated Points:** 13

---

### 1.16 Audio

**Description:** Sound effects and music.

- **SFX:** Click/tap feedback, purchase sounds, production sounds (pickaxe, furnace, hammer), milestone fanfares, crisis alerts, era change fanfares
- **Music:** Era-appropriate ambient tracks (primitive drums → medieval lutes → industrial machinery → electronic)
- **Audio Buses:** SFX, Music, UI — independently adjustable
- Audio changes with era to reinforce progression

**Estimated Work Phase:** Phase 8
**Estimated Points:** 8

---

### 1.17 Story / Narrative

**Description:** Partial story — focused on the history of the real world as told through research and tools.

**Confirmed Approach:**
- **Historical text:** Every research item and every tool/equipment piece has an extensive historical description explaining how it was developed in the real world
- **Civilization-specific:** The historical text is different for each civilization, reflecting how each culture independently developed (or didn't develop) each technology
- **World region flavour:** The player's chosen civilization provides a specific historical slant on all content
- **Not a traditional game story** — no characters, dialogue trees, or cutscenes. The "story" IS the history of human development, experienced through gameplay
- **3 initial starting perspectives:** Great Britain, China, Mediterranean
- **Future perspectives:** Native American, African, Mesoamerican (DLC/mods)

**Estimated Work Phase:** Ongoing (tied to research/equipment content creation)
**Estimated Points:** 21+ (massive content effort, done per civilization)

---

### 1.18 Achievements / Milestones

**Description:** Goals and rewards for the player.

- Platform achievements (Steam, Google Play, Apple Game Center)
- In-game milestone rewards (bonus boosts, cosmetic unlocks)
- Tracking: total clicks, total earnings, workers hired, equipment upgraded, eras completed, crises survived, research completed, Game+ completions

**Estimated Work Phase:** Phase 9
**Estimated Points:** 8

---

### 1.19 Monetisation Strategy

**Description:** How the game makes money.

**Confirmed Model: Low-price paid + Free ad-supported version**

**Paid Version (PC + Mobile):**
- Low initial purchase price (exact price TBD)
- No ads
- Full access to modding
- DLC available

**Free Version (Mobile initially, possibly Desktop later as demo):**
- Small persistent ad bar on screen
- Player can tap the ad bar, watch a rewarded ad, then choose a boost from a contextual list:
  - If zoomed into a specific building: boost options relate to that building's production
  - If on the main overview or research screen: boost options are random/general
- 15-minute cooldown per building for ad-watch bonuses (each building has its own cooldown)
- Mods are LOCKED in the free version — unlocked by purchasing ad-removal IAP
- DLC available to both free and paid versions

**DLC (available to both versions):**
- New civilizations
- New eras
- Cosmetic packs
- Gameplay expansions
- Daily recharging boosts
- Unlimited boost type slots (inventory)
- Unlimited boost quantity (inventory)
- Increased offline earnings percentage
- Increased offline earnings duration
- Access to cheats (if implemented)
- Specific DLC packages TBD — the main game must be fully playable and enjoyable without any DLC

**Estimated Work Phase:** Phase 11
**Estimated Points:** 13

---

### 1.20 Offline Earnings

**Description:** Players earn resources while the app is closed.

**Confirmed:**
- **Base rate:** 25% of normal production while offline
- **Duration:** Collects for up to 3 hours
- **DLC upgrades:** DLC can increase the offline percentage and extend the collection duration
- On game load, the system calculates elapsed time since last save and awards offline earnings accordingly

**Estimated Work Phase:** Phase 3
**Estimated Points:** 5

---

## Section 2 — Coding / File Elements

### 2.1 Engine (Confirmed)

**Engine: Godot 4.x with GDScript**

**Confirmed Reasons:**
- Free and open-source — no royalties, no licence fees
- GDScript is Python-like — easiest language for a non-coder
- Exports to all targets: Windows, Linux, Android, iOS, macOS, Web
- Built-in UI system — perfect for a UI-heavy clicker game
- Small binary size — good for mobile
- Active community — lots of tutorials for idle/clicker games
- Steam Deck compatible — native Linux support, no Proton needed

**iOS Note:** iOS builds require macOS for signing. A Mac will be acquired eventually. Until then, iOS builds are deferred. Cloud build services are an alternative if needed sooner.

**Estimated Work Phase:** Phase 1
**Estimated Points:** 3

---

### 2.2 Project Architecture

**Description:** How the codebase is structured.

**Proposed Structure:**

```
project_root/
├── assets/
│   ├── sprites/
│   ├── audio/
│   │   ├── sfx/
│   │   └── music/
│   ├── fonts/
│   └── ui/
├── src/
│   ├── autoloads/              # Singletons
│   │   ├── game_manager.gd
│   │   ├── save_manager.gd
│   │   ├── audio_manager.gd
│   │   ├── economy_manager.gd
│   │   ├── era_manager.gd
│   │   ├── crisis_manager.gd
│   │   ├── boost_manager.gd
│   │   ├── ad_manager.gd
│   │   └── mod_manager.gd
│   ├── resources/              # Godot Resource files
│   ├── scenes/
│   │   ├── main_menu/
│   │   ├── game/
│   │   ├── settings/
│   │   ├── research/
│   │   ├── inventory/
│   │   └── components/         # Reusable UI components
│   ├── systems/
│   │   ├── production_system.gd
│   │   ├── upgrade_system.gd
│   │   ├── economy_system.gd
│   │   ├── research_system.gd
│   │   ├── worker_system.gd
│   │   ├── equipment_system.gd
│   │   ├── education_system.gd
│   │   ├── crisis_system.gd
│   │   ├── boost_system.gd
│   │   ├── achievement_system.gd
│   │   ├── competitor_system.gd
│   │   └── offline_system.gd
│   ├── entities/
│   │   ├── resource_node.gd
│   │   ├── worker.gd
│   │   ├── building.gd
│   │   ├── equipment.gd
│   │   └── researcher.gd
│   └── utils/
│       ├── constants.gd
│       ├── big_number.gd       # Large number formatting
│       └── signal_bus.gd       # Global event bus
├── data/
│   ├── settings/
│   │   ├── master_defaults.json        # Master default settings for all systems
│   │   ├── eras/
│   │   │   ├── primitive_age.json
│   │   │   ├── stone_age.json
│   │   │   ├── bronze_age.json
│   │   │   ├── iron_age.json
│   │   │   ├── medieval.json
│   │   │   ├── renaissance.json
│   │   │   ├── colonial.json
│   │   │   ├── industrial_revolution.json
│   │   │   ├── world_wars.json
│   │   │   ├── silicon_age.json
│   │   │   ├── information_age.json
│   │   │   └── space_age.json
│   │   ├── crises/
│   │   │   ├── great_fire.json
│   │   │   ├── black_plague.json
│   │   │   ├── famine.json
│   │   │   ├── rat_infestation.json
│   │   │   ├── rebellion.json
│   │   │   ├── library_destruction.json
│   │   │   └── ... (one per crisis)
│   │   ├── civilizations/
│   │   │   ├── great_britain/
│   │   │   │   ├── civilization.json    # Era inflation rates, tech timings, etc.
│   │   │   │   ├── research.json
│   │   │   │   ├── equipment.json
│   │   │   │   └── crises.json          # Civilization-specific crisis overrides
│   │   │   ├── china/
│   │   │   │   └── ... (same structure)
│   │   │   └── mediterranean/
│   │   │       └── ... (same structure)
│   │   ├── buildings/
│   │   │   └── ... (one per building type)
│   │   ├── workers/
│   │   │   └── ... (worker type definitions, stat growth curves)
│   │   ├── equipment/
│   │   │   └── ... (one per equipment type)
│   │   ├── boosts/
│   │   │   ├── boost_types.json
│   │   │   ├── matching.json            # 5 common → 1 uncommon, etc.
│   │   │   └── stacking.json            # Diminishing returns formula
│   │   └── economy/
│   │       ├── balance.json             # Base rates, multipliers, cost curves
│   │       └── offline.json             # Offline earning rates and caps
│   ├── achievements.json
│   └── dlc/
│       └── ... (DLC content definitions)
├── mods/                                # Community mods loaded from here
├── tests/
├── docs/
│   ├── plans.md
│   ├── schedule.md
│   ├── placeholderart.md
│   ├── researchGB.md
│   ├── toolsandequipmentGB.md
│   └── CHANGELOG.md
└── project.godot
```

**Key Principle:** Every aspect of buildings, NPCs, tools, equipment, environment, crises, eras, civilizations, boosts, and economy has its own settings file that can be changed without touching code.

**Estimated Work Phase:** Phase 1
**Estimated Points:** 8

---

### 2.3 Data-Driven Design & Settings Files

**Description:** The entire game is data-driven. All content and balance are defined in external JSON/cfg files.

**Settings File Hierarchy:**
1. **Master defaults** (`master_defaults.json`) — Base values for everything
2. **Era overrides** (`eras/*.json`) — Era-specific changes that compound on top of defaults
3. **Civilization overrides** (`civilizations/*/`) — Civilization-specific changes
4. **Crisis overrides** (`crises/*.json`) — Crisis-specific temporary and permanent modifiers
5. **Building/worker/equipment definitions** — Individual entity settings

**Runtime resolution:** Master defaults → Era overlay → Civilization overlay → Active crisis overlay. Each layer overrides or modifies the previous.

**Modding:** Because everything is in JSON files, modders can create new civilizations, equipment, research, crises, and buildings by adding new data files. The mod system loads from `mods/` directory using the same settings file format.

**Estimated Work Phase:** Phase 1–2
**Estimated Points:** 13

---

### 2.4 State Machine

**Description:** Game state management.

**States:**
- `Loading` → `CivilizationSelect` → `DifficultySettings` (crisis frequency) → `Playing`
- `Playing` → `Paused` → `Playing`
- `Playing` → `Crisis` (temporary state during crisis timer) → `Playing`
- `Playing` → `EraChange` (transition animation/inflation) → `Playing`
- `Playing` → `WinScreen` → `Continue` or `GamePlus`
- `GamePlus` → `CivilizationSelect` (same civ locked?) → `Playing` (with Game+ modifiers)
- `Any` → `Settings` → `Previous`

**Estimated Work Phase:** Phase 2
**Estimated Points:** 5

---

### 2.5 Save System

**Description:** Persistent game state.

- **Local saves:** JSON file on device
- **Cloud saves:** Steam Cloud, Google Play Games, iCloud (platform-specific)
- **Save versioning:** Version number in save file for migration compatibility
- **Auto-save:** Every 30 seconds + on app close/background
- **Save slots:** Minimum 3 slots
- **Offline calculation:** On load, calculate 25% earnings for up to 3 hours since last save
- **Save contents:** All worker states (stats, levels, equipment), all building states, research progress, inventory/boosts, economy state, era, crisis probabilities, civilization choice

**Estimated Work Phase:** Phase 5
**Estimated Points:** 13

---

### 2.6 Big Number System

**Description:** Idle games quickly reach numbers in the millions/billions/trillions.

- Custom number formatting: 1,000 → 1K, 1,000,000 → 1M, etc.
- Arbitrary precision or scientific notation for very large numbers
- All economy calculations must handle large numbers without overflow
- Inflation calculations must be precise to avoid rounding exploits

**Estimated Work Phase:** Phase 3
**Estimated Points:** 5

---

### 2.7 Platform-Specific Builds

**Description:** Export and distribution per platform.

| Platform | Store | Build Notes |
|----------|-------|-------------|
| Windows | Steam, Epic | Standard Godot export template |
| Linux | Steam (native) | Native, no Proton needed. Steam Deck / Steam Frame compatible |
| Android | Google Play | APK/AAB, touch input, portrait+landscape, ad SDK |
| iOS | Apple App Store | Requires macOS for build signing — DEFERRED until Mac acquired |
| Steam Deck | Steam | Runs Linux build, gamepad input, Steam Input API |

**Estimated Work Phase:** Phase 10
**Estimated Points:** 13

---

### 2.8 Input System

**Description:** Cross-platform input handling.

- **Touch:** Tap to click resources, tap buildings to zoom in, swipe to scroll, pinch-to-zoom
- **Mouse:** Click, scroll wheel for lists, hover tooltips
- **Keyboard:** Tab navigation for menus, hotkeys for common actions
- **Gamepad:** D-pad/stick for menu navigation, A button to click, Steam Input API for Steam Deck/Steam Controller/Steam Frame
- All input goes through an abstraction layer — game logic never checks raw input
- Minimum 44×44px touch targets on mobile

**Estimated Work Phase:** Phase 2
**Estimated Points:** 8

---

### 2.9 Accessibility

**Description:** Making the game usable by everyone.

- Colour-blind friendly palette (avoid red/green only distinctions)
- WCAG AA contrast ratios for all text
- Scalable UI / font sizes
- Screen reader support (where possible in Godot)
- Configurable click speed / auto-click accessibility option
- All menus keyboard-navigable AND touch-friendly
- Steam Deck / controller fully navigable

**Estimated Work Phase:** Phase 6
**Estimated Points:** 8

---

### 2.10 Modding Support & GitHub Pipeline

**Description:** Community modding system with a GitHub-based approval pipeline.

**Mod Loading:**
- Mods are loaded from a `mods/` directory
- Player clicks "Load Mods" button in the mods menu — game checks for and loads available mods
- Mods are NOT loaded automatically on game start (to avoid interfering with offline play)
- Mods are data files in the same JSON format as the base game's settings files

**Mod Types:**
- New civilizations (full research tree, equipment, historical text, visual skin)
- New equipment and tools
- New characters/workers
- New eras
- New crises
- Balance modifications

**GitHub Pipeline:**
- Modders upload mods to a community GitHub repository
- Kurzon reviews and authorises mods
- Authorised mods are moved to the main repository
- The game's mod browser reads from the main repository and allows players to download approved mods

**Access Restriction:** Mods are only available to players who have purchased the game (paid version or ad-removal IAP on free version).

**Path to Official Content:** Popular/high-quality mods can be promoted to official content with modder credit.

**Estimated Work Phase:** Phase 12
**Estimated Points:** 21

---

### 2.11 Ad System

**Description:** Ad integration for the free version.

- Small persistent ad bar on screen
- Rewarded ad button available per building (contextual to what's on screen)
- 15-minute cooldown per building for ad-watch bonuses
- Each building has its own independent cooldown timer
- Ad rewards: player chooses a boost from a contextual list related to the current view
- On main overview/research screen: random/general boost options
- Ad SDK integration for Android (Google AdMob) and potentially iOS
- No ads in paid version

**Estimated Work Phase:** Phase 11
**Estimated Points:** 8

---

### 2.12 DLC System

**Description:** Downloadable content delivery.

- DLC content defined in `data/dlc/` directory, same format as base game data files
- DLC detected and loaded on game start
- Platform-specific DLC delivery (Steam DLC, Google Play IAP, Apple IAP)
- Main game must be fully playable and enjoyable without any DLC
- DLC available to both free and paid versions

**Estimated Work Phase:** Phase 11
**Estimated Points:** 13

---

### 2.13 CI / Build Pipeline

**Description:** Automated building and testing.

- GitHub repository for version control and collaboration
- GitHub Actions for automated builds (all platforms except iOS initially)
- Separate debug and release configurations
- Debug: verbose logging, hitbox visualisers enabled
- Release: strip all debug output, optimise assets
- Automated linting of GDScript
- Automated testing of game logic
- Semantic versioning: MAJOR.MINOR.PATCH
- Tagged releases; never commit directly to `main`
- CHANGELOG.md updated with every meaningful change

**Estimated Work Phase:** Phase 1
**Estimated Points:** 8

---

### 2.14 Analytics & Telemetry (Optional)

**Description:** Understanding how players play.

- Opt-in only
- Track: era progression speed, research popularity, session length, crisis survival rate, boost usage, worker stats distribution
- Useful for balancing updates post-launch

**Estimated Work Phase:** Phase 13
**Estimated Points:** 5

---

## Companion Documents

| File | Purpose | Status |
|------|---------|--------|
| `schedule.md` | Development schedule — what to work on and when | Active |
| `placeholderart.md` | Complete list of all placeholder art to be replaced | Created — to be populated |
| `researchGB.md` | Full research tree for Great Britain civilization | Created — to be populated in separate chat |
| `toolsandequipmentGB.md` | Full tools and equipment list for Great Britain | Created — to be populated in separate chat |

**Future companion documents (created when civilizations are designed):**
- `researchChina.md` + `toolsandequipmentChina.md`
- `researchMediterranean.md` + `toolsandequipmentMediterranean.md`
- (One pair per civilization)

---

## Open Questions

*These must be answered before specific sections can be finalised.*

### Pending (from latest round)

1. **Research system details:** Researchers cost a flat rate — but does this rate increase per era (due to inflation), or is it always the same base cost?
2. **Worker assignment:** When workers are assigned to roles in a building (e.g. 5 mining, 5 hauling), can the player freely reassign them, or are they locked to a role?
3. **Building purchase:** How does the player acquire new buildings? Are they unlocked by research, purchased with coins, or both?
4. **"Buy from other companies":** You mentioned players can buy resources from other companies instead of producing them. Is this an explicit menu option (e.g. "Buy 100 Iron Ore for X coins"), or is it abstracted?
5. **Game+ civilization:** In Game+, does the player replay with the same civilization, or can they choose a new one?
6. **Negative effects on competitors:** You mentioned the player can use negative effects on enemy NPCs and vice versa. Is this an active "attack" mechanic, or passive events?
7. **Crisis visual indicator:** How should crises be communicated to the player? A warning before they hit, or sudden events? Is there a "crisis incoming" alert?
8. **Map vs. list view:** You said currently list/menu-based but possibly a map later. Should the architecture plan for a spatial grid from the start (e.g. buildings have x/y coordinates in their data), or is this truly a "maybe later" feature?
9. **Worker names/identity:** Are workers named individuals (e.g. "John the Miner, Level 5") or anonymous (e.g. "Miner #3, Level 5")?
10. **Sound design:** Should era-appropriate music be AI-generated placeholder like the art, or will you source from royalty-free libraries?
