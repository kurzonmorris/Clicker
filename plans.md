# Project Arasmas — Master Plan

> **Status:** DRAFT — Core systems confirmed, open questions remain for fine-tuning
> **Last Updated:** 2026-04-30
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
   - 1.21 Laws System
   - 1.22 Happiness Buildings
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
- **Disrepair mechanic:** If a building (production or decorative) is NOT upgraded and the player advances another era (so the building is now 2 ages behind the current era), the building falls into **disrepair**. A building in disrepair must be completely rebuilt and all its upgrades restarted from scratch. This creates urgency to upgrade buildings promptly after an era change and prevents players from ignoring old buildings indefinitely

**Era Settings:** Each era will have its own settings file defining: available research, buildings, equipment, worker limits, inflation rates, production values, and crisis eligibility.

**Seasonal Cycles:**
- Within each era, the map cycles through **real-world seasons** (spring, summer, autumn, winter) that follow the player's actual real-world calendar
- Seasons have mild production effects: summer boosts farming/gathering, winter slows construction/outdoor work. **Default effect: ±10%** (changeable in settings files)
- Visual changes: trees change colour, snow in winter, flowers in spring — adds life to the map
- Season effects defined in settings files per building type

**Era Transition Cinematics (end of development feature):**
- When changing eras, a brief visual time-lapse shows the map transforming: dirt paths become cobblestone, wooden buildings gain stone walls, skyline changes
- This is a polish feature for late development — not a priority for early phases
- Even simple animation would make era transitions feel momentous rather than administrative

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
- Production tiers are era-dependent — new eras unlock new tiers and improve existing ones

**Resource Delegation / Buy from Computer:**
- As the game grows, managing every resource chain becomes overwhelming. The player can choose to **delegate** a resource by removing all workers from a building and buying that resource from the computer instead
- When delegated, the resource costs a set fee that is a **percentage above the minimum cost** the player would pay if they produced it themselves (markup for convenience)
- **Markup is set by difficulty level** (chosen at game start, editable in settings):
  - Easy: 10% markup
  - Normal: 33% markup
  - Hard: 50% markup
- This simplifies the game for players who don't want to micromanage every chain
- **Gameplay implications:** Buying from other companies instead of self-producing affects crisis probabilities (e.g. reduces Great Fire likelihood but increases dependency on external supply)
- This is an explicit option accessible from the building's management screen

**Critical Success System:**
- Every building has a small chance of producing a **critical success** on any production cycle
- When a critical success occurs: the building produces extra items/money AND generates a random boost (stored in the player's chest — see §1.10)
- The probability of critical success can be increased through research
- Worker Luck stat also affects critical success probability (see §1.5)

**Building Overcharge:**
- Any production building can be put into **overcharge mode** — temporarily increasing production output at the cost of reduced worker happiness
- Overcharge is toggled on/off by the player per building
- While overcharged: production speed increases by X% (defined in settings) but worker happiness in that building decreases continuously
- Useful for short-term bursts when resources are needed urgently, but unsustainable long-term due to happiness impact

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
- **Happiness** — Affects worker speed (see Worker Happiness System below). Starts at 50%, affected by happiness buildings, laws, crises, and working conditions
- **Additional stats:** May be added later based on gameplay needs
- **Stat range:** Base stats for new workers (immigrants and children) range from 8–12. See §1.5 Worker Recruitment and `minigame_family.md` for child stat inheritance rules

**Worker Mechanics:**
- Workers are hired with coins and cost coins per second to employ
- Each worker needs equipment to function (can't mine without a pickaxe)
- Workers gain experience over time by performing their task — this slowly levels them up
- Education can skip/accelerate leveling (see §1.6)
- Workers can be assigned to specific roles within a building (e.g. 5 mining, 5 hauling)
- **Role assignment is unrestricted** — the player can assign any number of workers to any combination of roles within a building's total worker limit. There is no enforced ratio and no penalty for idle workers

**Worker Happiness System:**
- Every worker has a **Happiness** stat (0%–100%)
- Workers start at **50% happiness** (neutral baseline)
- Happiness directly affects worker speed:
  - For every 1% below 50%, worker speed is reduced by 2%
  - For every 1% above 50%, worker speed is increased by 2%
  - Minimum happiness: 5% (cannot go lower)
  - Maximum happiness: 100%
  - At 5% happiness: worker operates at 10% speed (45% below baseline × 2% = 90% reduction)
  - At 100% happiness: worker operates at 200% speed (50% above baseline × 2% = 100% increase)
- **Happiness factors:**
  - **Happiness buildings** (global effect — see §1.22). Some happiness buildings only affect specific worker classes (e.g. cinema affects everyone, theatre affects upper-class/financial workers, bowling affects normal workers)
  - **Laws** (global modifiers — see §1.21)
  - **Golden Ages** — happiness boost during Golden Age periods
  - **Crisis events** — happiness reduction during/after crises
  - **Building overcharge** — putting a building into overcharge mode increases production temporarily but reduces worker happiness
  - **Enemy competitor negative boosts** — NPC competitors can use negative boosters that reduce player worker happiness
- **Happiness visibility:** The player can see each worker's **individual happiness %** AND an **average happiness per building**
- All happiness values, thresholds, and multipliers are defined in settings files
- **Workers can be freely reassigned** to any building, any job at any time. Their stats travel with them
- **Worker limits are set by the building itself** — each building defines how many total workers it can hold per era (defined in building settings files, see `buildingsGB.md`)
- Workers carry over between era changes — they keep their stats, level, and equipment. New research in the new era allows them to learn new skills and use new tools
- Example: In one era workers use pickaxes; in the next era they get explosives. They're not good with explosives at first (low experience) but produce more than with pickaxes. As they gain experience with the new tool, production improves further

**Worker Community Pool:**
- If a building is destroyed (by crisis) or no longer exists after an era change, displaced workers are moved into a **Community of Workers** pool
- The community pool is a holding area — workers in the pool are not working and not costing wages
- When the player assigns a worker to a building, the system **automatically selects the most suitable worker** from the community pool based on stats and the building's requirements
- Any worker can have a **"No Automatic Move" flag** set on them — these workers will never be auto-assigned and must be manually placed by the player
- The player can always manually browse the community pool and choose specific workers

**Worker Naming & Identity:**
- Every worker is a named individual with a randomly generated gender-appropriate first name and random last name
- Name lists are pulled from data files: separate lists for male first names, female first names, and last names
- The player can rename any worker to a custom name
- **Generational lineage:** When a new era begins, the worker's first name and possibly gender change to represent the next generation of the family. This is purely cosmetic — the last name stays the same, ALL stats stay the same (no variance), level stays the same, equipment stays the same, building assignment stays the same. Literally only the first name and gender can change. The worker profile shows their family lineage (list of previous first names/generations)
- If the player has given a custom name, the generational rename does NOT occur — the custom name persists
- Workers track a list of former occupations (jobs they've previously held)
- Worker display format: "[First Name] [Last Name] — [Current Occupation], Level [X]" with former occupations and family lineage viewable in their profile
- **Family tree viewer:** A visual family tree shows each worker's lineage across eras. Players can see which families have served the longest. ("The Mayer family has served your empire for 8 eras")

**Worker Specialist System:**
- Workers build **specialist progress** towards the building they're currently assigned to (0%–100%)
- **Progress rate:** 1% per minute of constant work (default — defined in settings files). Reaching specialist status (95%) takes approximately 95 minutes of continuous work
- **Specialist bonus activates at 95% progress** — grants a speed boost and productivity boost for that specific building type (e.g. +20% speed, +20% productivity — values in settings files)
- A worker can only be a specialist in **one building type at a time**
- **Transferring workers:**
  - When a specialist moves to a different building, their specialist bonus stops immediately
  - Their associated stats (e.g. Strength) are NOT lost — stats are permanent
  - They begin building progress towards the new building type from 0%
  - **Inverse decay:** Progress towards the new building erodes progress towards the old building at a 1:1 ratio. For every 1% gained in the new speciality, they lose 1% of their old speciality. Example: a woodcutter at 100% specialist transfers to mining. After reaching 10% mining specialist, their woodcutting specialist drops to 90%
  - If they return to the old building before the old speciality drops below 95%, the old bonus reactivates
  - This creates a small window for temporarily helping other buildings without losing specialist status
- **Specialist activation threshold (95%) is a settings value** — can be tuned during playtesting
- All specialist bonus values, progress rates, and decay rates defined in settings files

**Worker Recruitment:**
- When the player wants a new worker, they choose from two sources:
  - **Immigrant:** A new worker with randomly generated stats, name, and no family lineage. Immediate availability
  - **Child from the children pool:** A child born from existing worker families (see Marriage & Family Mini-Game). May inherit traits or have stat tendencies based on parents
- The children pool is populated through the marriage and family mini-game (see companion document `minigame_family.md`)

**Marriage & Family Mini-Game:**
- Workers can inter-marry and have children through a small optional mini-game
- Players can arrange marriages between workers, and married couples can produce children (up to 8 children per couple)
- Divorce is allowed; remarriage is allowed
- Children enter the **children pool** and can be recruited as workers when the player needs new hires
- Full details in companion document `minigame_family.md`

**Worker Settings:** Each worker type will have a settings file defining base stats, growth curves, equipment slots, role capabilities, and specialist bonus rates. Name lists are stored in `data/settings/workers/names/` with separate files per civilization for culturally appropriate names.

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
- **Researcher hiring cost:** Flat rate per researcher within an era. **Researcher costs DO increase with era changes** due to inflation (same inflation mechanic as all other costs). However, the Research Point cost for each technology is STATIC — the number of RP needed does not change. The RP requirements naturally scale up for later-era technologies, so no inflation is needed on RP costs. This lets the player plan research more predictably
- **Research cost:** After a technology has been researched (using Research Points), it costs coins to "publish" the research (release a scientific paper). Only after this coin payment is the technology actually unlocked and usable
- **Building unlock flow:** Research technology (costs RP + time) → Pay coins to publish → Building/technology becomes available to build/use
- **Researcher upgrades:** Researchers can be given tools and upgrades to speed up research, but those tools also need to be researched first
- **Parallel research:** Initially only one research project at a time. Researching "parallel research" unlocks the ability to run multiple projects simultaneously
- **Forward research:** Players can research the next era's technologies while in the current era, up to a limit. Cannot use the results until the era changes
- **Civilization-specific:** Each civilization has the same general research items but different unlock timings and costs. The historical description text is unique per civilization
- **Research boosts:** Each completed research gives the player a boost item they can store and activate later (see §1.10)

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
- Threshold value (default 100 — when the accumulated modifier reaches this number, the crisis triggers)

**Crisis Warning & Visibility System:**
- A dedicated **Crisis Monitor** menu shows ALL active crisis modifiers and their current accumulated values
- **The Crisis Monitor must be unlocked through research in the Iron Age** — it is not available from the start. Until researched, crises can strike without warning
- **Crisis Monitor upgrades:** Further research in later eras can upgrade the Crisis Monitor to show more detail, predict crisis timing more accurately, and provide earlier/more precise warnings. Upgrade tiers and effects defined in research settings files
- Example display: "Rat Infestation: modifier +0.01/minute (current total: 47/100)" — the player can see the crisis building
- Modifiers accumulate slowly (e.g. +0.01 per minute for mild stockpiling) but accelerate based on player actions (e.g. +0.5 per minute for excessive food stockpiling)
- When the accumulated value reaches the threshold (default 100), the crisis triggers
- **Threshold boosts:** Players can use boosts to increase the threshold (e.g. raise the trigger from 100 to 1000 for X hours), effectively postponing or preventing a crisis while they fix the underlying cause
- Multiple modifiers can affect the same crisis simultaneously (both increasing and decreasing its probability)

**Strategic Depth:** Players can use boosts to mitigate crisis effects or raise thresholds. Enemy NPC competitors can also trigger crises against the player using attack boosts (see §1.12). The crisis modifier system applies to competitors as well as the player.

**Crisis Chain Reactions:**
- Crises can cascade: one crisis increases the probability of another (rats → famine → plague). If three or more crises trigger within a short time window, this is classified as a **"Dark Age"** event
- Dark Ages have special visual treatment, unique achievement ("Survived the Dark Age"), and increased severity
- Chain reaction probabilities defined in crisis settings files

**Golden Ages:**
- After surviving a crisis (or series of crises), there is a chance of triggering a **Golden Age** — a temporary period of bonus production, research speed, and positive effects
- **Sustained prosperity trigger:** A Golden Age can also trigger when ALL buildings are operating above **85% efficiency** (speed, productivity, and deliveries) and sustain that level for a continuous period. Default threshold: **1 hour of constant play** (this value will change significantly through playtesting and is defined in settings files)
- Golden Ages are the reward for good management. Duration and bonuses defined in settings files

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
- **Critical successes:** Buildings have a small chance of producing a critical success — when this happens, the building produces extra items/money AND generates a random boost. Research can increase the probability of critical successes
- Progress milestones

**Boost Types (examples — full list TBD):**
- Double research point production
- Increase hired worker experience gain
- Increase worker level or speed
- Increase money production
- Stat-specific boosts (e.g. +5% Strength to a worker or tool)
- Building-wide boosts (e.g. +10% production for an entire mine)
- Anti-crisis boosts (mitigate negative effects during a crisis)
- Crisis threshold boosts (raise the trigger threshold to postpone crises — see §1.9)
- **Attack boosts (negative):** Same system as positive boosts but with negative effects — used against competitors. Examples: slow competitor progress, increase competitor crisis probability, reduce competitor production. Attack boosts are stored in the same chest/inventory as regular boosts. **Attack boosts must be researched before they can be obtained** from any source (critical successes, progress, DLC). Further research can improve attack boost effectiveness

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

**Boost Installation (permanent):**
- Instead of activating a boost temporarily, the player can **install** a boost permanently into a specific building
- An installed boost provides a smaller but permanent effect (e.g. a legendary 2x production boost used normally might last 30 minutes, but installed gives a permanent +10%)
- **One installed boost per building** — choosing which boost to install is a strategic decision
- **One active boost per category at a time** — if a building already has a production boost installed, installing a new production boost replaces the old one
- **Replacement cost:** Installing a new boost costs only the boost itself. The previously installed boost is lost — no additional coin cost
- Installation values (the conversion from temporary effect to permanent effect) defined in settings files

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
- **Researcher costs:** Researchers cost coins per second (flat rate per researcher). Researcher hiring costs increase with era changes (inflation)
- **Research Point costs:** Static — the number of RP needed per technology does NOT change with inflation. RP costs naturally scale up for later-era technologies
- **Research unlock costs:** After research is complete (via Research Points), coins are paid to publish/unlock the result
- **Equipment costs:** Tools, upgrades, and replacements cost coins
- **Education costs:** Leveling workers through education costs coins
- **Cost scaling:** Exponential cost curves for upgrades (standard idle game formula)
- **Inflation on era change:** A set percentage of currency is lost when advancing to a new era. Ongoing production also reduced by the same percentage. Inflation rates are per-civilization per-era in settings files
- **No premium currency:** Temporary boosts replace what premium currency would typically provide

**Difficulty Settings (set at game start, LOCKED for the playthrough — cannot be changed mid-game):**
- **Resource delegation markup:** Easy 10% / Normal 33% / Hard 50%
- **Competitor count:** Easy 3 / Normal 5 / Hard 8
- **Crisis frequency:** Set via difficulty slider (see §1.9)
- All difficulty values are stored in editable settings files for developer playtesting
- In-game research and purchases can modify related game values but cannot change the base difficulty tier

**Estimated Work Phase:** Phase 3
**Estimated Points:** 13

---

### 1.12 Competitors / AI Players

**Description:** Other entities in the game world that are also developing and building. NOT an early implementation priority.

**Confirmed Design:**
- Competitors simulate other players in the world who are also progressing through eras
- **Regional naming:** Competitors are named as historically appropriate regional rivals for the player's civilization:
  - Great Britain → France, Germany, Ireland, Spain, Portugal, etc.
  - China → Korea, Japan, Mongols, India, etc.
  - Mediterranean → (TBD in civilization chat)
- **Progressive appearance:** Not all competitors are visible from the start. Competitors appear based on **when that civilization historically became known** to the player's civilization:
  - Each civilization's settings file contains a **reveal schedule** defining which competitors appear at which era
  - Example (Great Britain): Nearby rivals (France, Ireland) visible from the start. Renaissance → Turkey appears. Industrial → China becomes visible
  - The number of competitors that EXIST is set at game start (Easy 3 / Normal 5 / Hard 8), but they are revealed progressively according to the civilization's reveal schedule
- **Passive events:** Competitors generate passive news/events that the player learns about (e.g. "France has advanced to the Iron Age", "Germany has built a new factory"). This creates the illusion of real opponents
- Competitors serve as a progress gauge — the player can see if they're ahead or behind
- Competitors are a win condition target — "buy all competitors" is one way to win
- **Attack boosts:** The player can activate attack boosts that target specific competitors, causing negative effects (e.g. slowing their progress, triggering crisis events against them). When an attack is used, the player sees **a statistic of what changed** for the competitor (e.g. "France production reduced by 20% for 30 minutes"). Competitors can also cause negative effects against the player
- **Crisis system integration:** The crisis modifier system works for competitors as well as the player. When a competitor suffers a crisis, the player sees **both a summary event AND detailed effects** (e.g. "Germany suffered a Great Fire — 3 buildings destroyed, production reduced by 40% for 10 minutes"). Competitor crises and attacks are driven by the same settings files and probability engine
- **Competitor count** is set by the player in the game settings at the start (locked for the playthrough, cannot be changed mid-game):
  - Easy: 3 competitors
  - Normal: 5 competitors
  - Hard: 8 competitors

**Adaptive Competitor Difficulty:**
- Competitor progression uses **adaptive difficulty based on developer playtesting data**
- The developers/Kurzon will play through the game and record progress benchmarks at various points
- **Built-in benchmark recording mode:** The game includes a developer tool that records gameplay progress data and stores it in a reasonably-sized file. This data is used to calibrate competitor progression curves, making it easy to create and tune competitor characters
- The competitor system compares the player's current progress against these recorded benchmarks
- If the player is progressing **too far ahead** of the benchmark, competitors receive speed-up multipliers to close the gap
- If the player is **falling too far behind**, competitors receive slow-down multipliers
- This creates the illusion that competitors are real, adaptive opponents while actually being tuned to provide a good gameplay experience
- The multipliers, thresholds for "too far ahead/behind", and benchmark data are all stored in settings files

**Deferred:** Detailed competitor design will be determined after core systems are built. Developer playtesting data must be collected before the adaptive system can be calibrated.

**Estimated Work Phase:** Phase 8+ (late development)
**Estimated Points:** 21

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
- **Player can choose a different civilization** for Game+ (not locked to original choice)
- All costs are 50%–100% higher (exact multiplier TBD, likely a settings value)
- More frequent/severe crisis events
- Increased research speed and other stat adjustments to compensate
- Purpose: increased difficulty and replayability (try different civilizations with harder challenge)

**Estimated Work Phase:** Phase 9
**Estimated Points:** 8

---

### 1.14 Visual Style / Art Direction

**Description:** The look and feel of the game.

**Current Direction:** Low-Poly 3D or Cel-Shaded Cartoon effect (not yet finalised — decision between these two)

**Art Pipeline:**
- **Priority 1:** Royalty-free asset libraries for sprites, objects, and visual elements wherever possible
- **Priority 2:** AI-generated placeholders only where royalty-free assets are not available or appropriate
- **Priority 3:** Artist-produced final art replaces ALL placeholders before full release
- **Hard rule:** NO AI-generated placeholder art may remain in the full release build. Alpha and beta builds may contain AI placeholders, but release builds must not
- All placeholder art (both royalty-free temp and AI-generated) is tracked in `placeholderart.md` with a complete list of every asset that needs final artist replacement

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

- Main view: the spatial map, zoomable to individual buildings. The map IS the main game view
- Tapping/clicking a building on the map opens its management screen (workers, equipment, production, building-specific options)
- Ad-watch bonus is contextual to what's on screen (see §1.19)
- Bottom nav switches between major game sections
- Settings accessible from header
- **Map view is required:** Both production buildings and decorative buildings exist on the spatial map. When a player purchases a new production facility, it **must be placed on the map before it can be used**. A menu/list view also exists for quick access to building management, but the map is the primary view
- **Map layout:** The map is centred on the Town Hall / town square, with pathways radiating outward in different directions. The map grows larger with each era. Walkways, paths, roads, and highways appear automatically as eras progress. Each era gives the player a set number of decorative buildings they can place: houses, shops, government buildings, roads, community structures, etc.
- **Town Hall dashboard:** The Town Hall displays production stats for every building in a single overview — instead of loading into each building individually, the player can see all buildings' info from the Town Hall. It is the community stats hub. **The Town Hall gains features when upgraded each era** — earlier eras show basic stats, later eras add graphs, comparisons, trend lines, and more detailed explanations. Each era's upgrade adds more analytical depth to the dashboard
- **Free-form placement:** Players can drag and drop buildings anywhere on the map. Roads are drawn by selecting the road tool and drawing with finger/mouse across the screen. Buildings snap to a loose grid for alignment but placement is not restricted to fixed tiles
- **Map starting size:** Primitive Age starts at a **10×10 grid**. Each era increases the grid by **10 in each dimension** (Stone Age = 20×20, Bronze Age = 30×30, etc., up to Space Age = 120×120). These values may change with further development and are defined in settings files
- **Building upgrade & disrepair:** All buildings on the map must be upgraded when eras change. If a building is not upgraded and the player advances another era (2 ages behind), the building falls into **disrepair** — it must be rebuilt from scratch and all upgrades restarted. Disrepaired buildings do not cost more to rebuild than the original, but **can be relocated** on the map during rebuilding
- **Building relocation:** Any building (including functioning ones not in disrepair) can be moved on the map at any time **for an era-appropriate fee**. The fee is defined in settings files per era. This allows the player to reorganise their map layout as their town grows
- Crisis Monitor accessible from header or nav bar once researched (see §1.9)

**Estimated Work Phase:** Phase 6
**Estimated Points:** 13

---

### 1.16 Audio

**Description:** Sound effects and music.

- **SFX:** Click/tap feedback, purchase sounds, production sounds (pickaxe, furnace, hammer), milestone fanfares, crisis alerts, era change fanfares
- **Music:** Era-appropriate ambient tracks (primitive drums → medieval lutes → industrial machinery → electronic)
- **Audio Buses:** SFX, Music, UI — independently adjustable
- Audio changes with era to reinforce progression

**Audio Asset Pipeline:**
- **Priority 1:** Royalty-free sound libraries for music, SFX, and ambient sounds wherever possible
- **Priority 2:** AI-generated audio only where royalty-free options are not available or appropriate
- **Hard rule:** NO AI-generated audio placeholders may remain in the full release build. Alpha and beta builds may contain AI placeholders, but release builds must not

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

**"Did You Know?" Pop-ups:**
- When the player completes significant research or unlocks a major tool, a brief **"Did you know?"** card appears
- Each card includes a small image, a short fascinating historical fact, and a link to the full detailed historical description
- Cards are optional and dismissable — they surface the educational content to players who might never click into the full descriptions
- Card content is civilization-specific and defined in the research/equipment data files

**Estimated Work Phase:** Ongoing (tied to research/equipment content creation)
**Estimated Points:** 21+ (massive content effort, done per civilization)

---

### 1.18 Achievements / Milestones

**Description:** Goals and rewards for the player. Achievements encourage varied playstyles and exploration of game mechanics.

- Platform achievements (Steam, Google Play, Apple Game Center)
- In-game milestone rewards (bonus boosts, cosmetic unlocks)
- Tracking: total clicks, total earnings, workers hired, equipment upgraded, eras completed, crises survived, research completed, Game+ completions

**Achievement Examples (full list in achievements.md):**
- "Solo Operator" — Complete a full production chain with only 1 building
- "Speed Runner" — Reach the Space Age in under X hours
- "Historian" — Read every historical description for a civilization
- "Crisis Survivor" — Survive every type of crisis in a single playthrough
- "Delegate" — Buy a resource from the computer for the first time
- "Generational" — Have a worker's descendant reach the Space Age
- (Many more — see companion document)

**Companion Document:** `achievements.md` — Full list of all achievements with unlock conditions, rewards, and platform mapping.

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

### 1.21 Laws System

**Description:** Laws are global modifiers that, once researched, can be enacted and retracted at will. They represent societal/governmental policies that affect all workers and production globally.

**Confirmed Mechanics:**
- Laws must be **researched** before they can be used (costs Research Points + coins to publish, like all research)
- Once researched, a law can be **enacted or retracted** — but with cooldowns:
  - **Enactment cooldown:** After researching a law, there is a **15-minute cooldown** before it can be enacted (default — defined in settings)
  - **Minimum active period:** Once enacted, a law **cannot be turned off for 1 hour** OR until the player changes era (whichever comes first)
  - These timers prevent the player from constantly toggling laws for micro-advantages
- **Unlimited active laws:** There is no cap on how many laws can be active simultaneously
- **Mutual exclusivity:** Some laws are mutually exclusive — enabling one automatically disables the other. Example: "Free Trade" and "Protectionist Tariffs" cannot both be active
- Laws are **era-appropriate** — no modern laws in ancient eras
- Laws from previous eras remain available in later eras, UNLESS a newer version of the law replaces it (the old version becomes unavailable when the replacement is researched)
- **Global effect:** An enacted law affects ALL workers, ALL buildings, and/or ALL production simultaneously
- Laws can have both positive and negative effects — the player must weigh trade-offs

**Law Examples (to be fully defined in lawsGB.md):**
- Rest days (reduces work hours but increases happiness)
- Minimum wage (increases worker cost but increases happiness)
- Child labour laws (restricts children pool recruitment age but increases happiness)
- Trade agreements (improves selling prices but may increase crisis probability)
- Safety regulations (reduces accident/crisis severity but slows production)
- Education mandates (workers level up faster but cost more)
- Environmental protections (later eras — affects pollution-related crises)

**Law Settings:** Each law has a settings file defining: era available, research cost, effects (positive and negative), replacement law (if any), and civilization availability. Laws are era-specific and civilization-specific — different civilizations may get different laws or get the same laws at different times.

**Companion Document:** `lawsGB.md` — Full list of laws for Great Britain with historical basis. Research files (`researchGB.md` etc.) will include a Laws section.

**Estimated Work Phase:** Phase 5
**Estimated Points:** 13

---

### 1.22 Happiness Buildings

**Description:** Buildings specifically designed to improve worker happiness. These are production buildings that "produce" happiness instead of resources.

**Confirmed Mechanics:**
- **Global effect:** All happiness buildings affect workers globally — the map is purely aesthetic, so proximity to a happiness building does not matter
- **Class-based targeting:** Some happiness buildings affect ALL workers, while others only affect specific worker classes. Examples:
  - Cinema (later eras) → affects everyone
  - Theatre/plays → affects upper-class/financial workers only
  - Bowling alley → affects normal/labour workers only
  - Tavern (earlier eras) → may affect everyone or specific classes (TBD per building in buildingsGB.md)
- Worker classes are defined by their current occupation/building assignment (e.g. workers in financial/trading buildings = upper-class, workers in mines/factories = normal workers)
- **Era 1 (Primitive Age) has NO happiness buildings** — happiness buildings start appearing from Era 2 onwards
- Happiness buildings require workers to operate (like any building) and cost coins to maintain
- Each era introduces era-appropriate happiness buildings (specific types and quantities defined in buildingsGB.md)
- The happiness effect value is defined in each building's settings file

**Estimated Work Phase:** Phase 4
**Estimated Points:** 8

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
│   │   │   └── names/
│   │   │       ├── great_britain_male_first.json
│   │   │       ├── great_britain_female_first.json
│   │   │       ├── great_britain_last.json
│   │   │       ├── china_male_first.json
│   │   │       ├── china_female_first.json
│   │   │       ├── china_last.json
│   │   │       └── ... (one set per civilization)
│   │   ├── equipment/
│   │   │   └── ... (one per equipment type)
│   │   ├── boosts/
│   │   │   ├── boost_types.json
│   │   │   ├── matching.json            # 5 common → 1 uncommon, etc.
│   │   │   └── stacking.json            # Diminishing returns formula
│   │   ├── laws/
│   │   │   └── ... (one per law, era-specific)
│   │   ├── happiness/
│   │   │   └── happiness_buildings.json  # Happiness building effects
│   │   └── economy/
│   │       ├── balance.json             # Base rates, multipliers, cost curves
│   │       └── offline.json             # Offline earning rates and caps
│   ├── achievements.json
│   ├── map/
│   │   ├── grid_layout.json         # Spatial map/grid positions for buildings
│   │   └── decorative/
│   │       └── ... (decorative building types per era: houses, shops, roads, etc.)
│   └── dlc/
│       └── ... (DLC content definitions)
├── mods/                                # Community mods loaded from here
├── tests/
├── docs/
│   ├── plans.md
│   ├── schedule.md
│   ├── placeholderart.md
│   ├── achievements.md
│   ├── contacts.md
│   ├── dlc.md
│   ├── minigame_family.md
│   ├── lawsGB.md
│   ├── researchGB.md
│   ├── toolsandequipmentGB.md
│   ├── buildingsGB.md
│   └── CHANGELOG.md
└── project.godot
```

**Key Principle:** Every aspect of buildings, NPCs, tools, equipment, environment, crises, eras, civilizations, boosts, and economy has its own settings file that can be changed without touching code.

**Estimated Work Phase:** Phase 1
**Estimated Points:** 8

---

### 2.3 Data-Driven Design & Settings Files

**Description:** The entire game is data-driven. All content and balance are defined in external JSON/cfg files. **Every stat and every number in the game must be easily changeable** — both through the initial difficulty settings (which the player sets at game start) and through settings files that the developer can edit during playtesting without touching code.

**Core Principle:** This is a numbers and statistics-based game. If a value exists in the game — production rates, worker stats, crisis thresholds, markup percentages, competitor counts, boost magnitudes, upgrade costs, inflation rates, experience curves — it MUST live in an editable settings file, never hardcoded. This is non-negotiable for both balance tuning and modding support.

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
- `GamePlus` → `CivilizationSelect` (player can choose new civ) → `DifficultySettings` → `Playing` (with Game+ modifiers)
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

- **Godot 4.x integer limit:** 64-bit signed integers — max value 9,223,372,036,854,775,807 (approximately 9.2 quintillion). This is more than sufficient for gameplay numbers
- **Godot 4.x float limit:** 64-bit double precision — adequate for all production/economy calculations
- Custom number formatting: 1,000 → 1K, 1,000,000 → 1M, etc.
- Arbitrary precision or scientific notation for very large numbers if needed beyond 64-bit range
- All economy calculations must handle large numbers without overflow
- Inflation calculations must be precise to avoid rounding exploits
- **Performance note:** The bigger concern is not number limits but active entity count. Having hundreds of animated workers on screen simultaneously will require object pooling and only rendering visible entities. The architecture must plan for this from the start

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

**Companion Document:** `dlc.md` — Full list of all planned and potential DLC packages including civilization packs, gameplay expansions (combat, inventory, offline), content packs, and bundles.

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
| `achievements.md` | Full list of all achievements with unlock conditions | Created — to be populated |
| `contacts.md` | People/companies to contact and why | Created |
| `dlc.md` | DLC planning — all planned and potential DLC packages | Created |
| `minigame_family.md` | Marriage & family mini-game design document | Created |
| `lawsGB.md` | Full list of laws for Great Britain with historical basis | Created — to be populated in separate chat |
| `researchGB.md` | Full research tree for Great Britain civilization | Created — to be populated in separate chat |
| `toolsandequipmentGB.md` | Full tools and equipment list for Great Britain | Created — to be populated in separate chat |
| `buildingsGB.md` | Full list of buildings for Great Britain civilization | Created — to be populated in separate chat |

**Future companion documents (created when civilizations are designed):**
- `researchChina.md` + `toolsandequipmentChina.md` + `buildingsChina.md` + `lawsChina.md`
- `researchMediterranean.md` + `toolsandequipmentMediterranean.md` + `buildingsMediterranean.md` + `lawsMediterranean.md`
- (One set per civilization)

---

## Open Questions

*Fine-tuning items — these won't block development starting.*

### Pending

1. **Worker classes definition:** Happiness buildings target worker classes (upper-class/financial vs normal/labour). Is worker class determined purely by their current building assignment (e.g. anyone in a trading post = upper-class, anyone in a mine = normal), or is it a separate attribute on the worker?
2. **Overcharge — production boost amount:** How much does overcharge increase production? 25%? 50%? 100%? And how fast does happiness drain while overcharged?
3. **Overcharge — cooldown after disabling:** After turning off overcharge, is there a recovery period before it can be re-enabled?
4. **Law cooldown timer — does it pause offline?** The 15-minute enactment cooldown and 1-hour minimum active period — do these count real-world time only, or do they also tick down during offline play?
5. **Mutual exclusivity — how communicated?** When a player tries to enact a law that conflicts with an active one, does the game show a warning/confirmation, or just auto-disable the conflicting law silently?
6. **Happiness buildings — worker requirement:** Happiness buildings need workers to operate. Do these workers also get happiness benefits from the building they work in, or are they excluded?
7. **Overcharge + specialist interaction:** If a building is overcharged, does specialist progress still accumulate at the normal rate, or does it accelerate/slow down?
8. **Worker class mobility:** If a worker moves from a mine (normal class) to a trading post (upper class), does their happiness immediately adjust based on what happiness buildings are targeting their new class?
9. **Map aesthetic buildings — overcharge visual?** Should overcharged buildings have a visual indicator on the map (e.g. smoke, glow, warning icon)?
10. **Art style decision:** Deferred until external artist cost is known.

### Previously Answered (archived)

All original open questions (7 rounds, ~66 confirmed decisions) have been answered and integrated into the relevant sections.
