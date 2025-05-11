# D&D-Style Game in Unreal Engine 5 – Brainstorm Summary

## Table of Contents
- **[Game Features and Mechanics](#game-features-and-mechanics)**
  - [1. Realistic Visibility](#1-realistic-visibility)
  - [2. Time of Day Effects](#2-time-of-day-effects)
  - [3. Elevation Impact](#3-elevation-impact)
  - [4. Stealth System](#4-stealth-system)
  - [5. Line of Sight (LoS)](#5-line-of-sight-los)
  - [6. DM Control](#6-dm-control)
  - [7. Survival Mechanics](#7-survival-mechanics-dm-toggleable)
- **[Exploration & Map System](#exploration--map-system)**
  - [1. Preloaded World Map](#1-preloaded-world-map)
  - [2. Progressive Detail Reveal](#2-progressive-detail-reveal)
  - [3. Map Detail Tiers](#3-map-detail-tiers)
  - [4. Fast Travel System](#4-fast-travel-system)
  - [5. DM Map Tools](#5-dm-map-tools)
- **[Climbable Terrain System](#climbable-terrain-system)**
  - [1. Slope Detection](#1-slope-detection)
  - [2. Climb Requirements](#2-climb-requirements)
  - [3. DM Integration](#3-dm-integration)
  - [4. Bonus Features](#4-bonus-features)
- **[Gridless Movement & Distance](#gridless-movement--distance)**
- **[Weather & Climate System](#weather--climate-system)**
  - [1. Weather Types](#1-weather-types)
  - [2. Climate Zones](#2-climate-zones)
  - [3. Game Effects](#3-game-effects)
  - [4. DM Control](#4-dm-control)

---

## Game Features and Mechanics

### 1. Realistic Visibility
- **Max vision range**: 3 miles.
- **Environmental occlusion** dynamically limits sight:
  - **Clear desert**: up to 3 miles.
  - **Dense jungle**: 10–50 feet.
  - **Terrain** (hills, trees, buildings): blocks or reduces LoS naturally.

### 2. Time of Day Effects
- **Day**: Full vision range.
- **Night**: Severely reduced visibility unless lit.
- **Dawn/Dusk**: Moderate reduction in visibility.
- **Moonlight**: Slightly improved vision; good for stealth play.

### 3. Elevation Impact
- **Higher ground**:
  - Increases visual range.
  - Increases chance to hide from lower observers.
- **Lower ground**:
  - Decreases visual and stealth effectiveness.

### 4. Stealth System
- Players have a **Stealth Rating**, influenced by:
  - **Movement state**: walking, crouching, prone.
  - **Cover and concealment**: bushes, shadows, terrain.
  - **Armor type**: lighter gear improves stealth.
  - **Environmental factors**: darkness, fog, terrain.
- Opposed by **Perception Rating** of enemies or other players.
- Example modifiers:
  - **Crouch**: +5 Stealth
  - **Prone**: +10 Stealth
  - **Bright daylight**: -5 Stealth
  - **Dense foliage or shadows**: +5 Stealth

### 5. Line of Sight (LoS)
- Determined via **raycasting** with natural obstructions (foliage, terrain).
- Optional **fog of war** mechanic to obscure unexplored areas.
- Vision indicators for when a target is within LoS.

### 6. DM Control
- DM has:
  - **Full map visibility** and overrides.
  - Ability to **view each player’s LoS**.
  - Manual control over **encounters**, **spawned creatures**, and **environment**.
  - Tools to override stealth or perception outcomes.

### 7. Survival Mechanics (DM-Toggleable)
- **Toggle Framework**:
  - DM can enable/disable all survival systems globally.
  - Optional sub-toggles for **hunger**, **thirst**, **temperature**, **fatigue**, and **disease**.
- **Core Systems** (when enabled):
  - **Hunger/Thirst**: Gradual penalties (speed, CON, death) if unmet. Mitigated by rations, foraging, or spells.
  - **Temperature**: Extreme heat/cold requires protective gear or saves to avoid exhaustion.
  - **Fatigue**: Sleep deprivation reduces INT/WIS; camping/rest required.
  - **Disease**: Contaminated food/water or insect bites cause debuffs (optional sub-toggle).
- **DM Customization**:
  - Adjustable **severity sliders** (e.g., "Starvation Speed").
  - **Presets**: "Hardcore" (full realism) vs. "Cinematic" (disabled).
  - Per-player/NPC overrides (e.g., undead ignore hunger).
- **Player Tools**:
  - HUD warnings (e.g., "You are freezing!").
  - Automated foraging rolls (passive Survival skill).
  - Camping roles (Hunter, Cook, Lookout) for group bonuses.
- **Integration**:
  - Weather/climate intensifies effects (e.g., blizzards = hypothermia risk).
  - Fast travel consumes rations if enabled.

---

## Exploration & Map System

### 1. Preloaded World Map
- Players begin with a **basic world map** showing:
  - Major cities, towns, roads, and landmarks.
- These are **fast travel enabled** from the start.

### 2. Progressive Detail Reveal
- As players explore:
  - Map adds terrain, hidden features, encounter sites, etc.
  - Terrain details become more accurate.
- Map can include:
  - **Auto annotations** (e.g., “Ruins Discovered”)
  - **Player pins and notes**

### 3. Map Detail Tiers

| Tier | Visibility | Fast Travel | Notes |
|------|------------|-------------|-------|
| Tier 1 | Towns, roads, iconic landmarks | Yes | Fixed |
| Tier 2 | Nearby terrain, minor landmarks | No | Unlocks via exploration |
| Tier 3 | Precise terrain, hidden areas | No | Only visible after visit or scouting |

### 4. Fast Travel System
- Available to previously visited or pre-marked Tier 1 locations.
- Travel represented visually (map lines, animation).
- DM can **interrupt travel** with:
  - Random encounters
  - Narrative events
  - Environmental hazards

### 5. DM Map Tools
- Full map access:
  - All detail tiers visible
  - Hidden content toggles
  - Encounter triggers
  - Fog of war overrides

---

## Climbable Terrain System

### 1. Slope Detection
- Based on terrain angle:
  - `> 45°`: no standard movement
  - `> 60°`: climb check required

### 2. Climb Requirements
- **Climb Speed**: bypasses checks
- **No Climb Speed**:
  - Make **Climb Check** (DC based on surface type)
  - On success: slow movement
  - On fail: fall or slide

### 3. DM Integration
- DM can mark any terrain as:
  - **Climbable**
  - **Unscalable**
  - **Custom DC** surfaces

### 4. Bonus Features
- **Climb animations**
- **Gear/tools influence checks**
- **Fatigue or stamina drain for extended climbs**

---

## Gridless Movement & Distance
- No strict 5x5 grid required.
- Distances calculated using **real-world units**.
- **Navmesh + range indicators** replace traditional grids:
  - Movement: shaded radius
  - Attacks: cones, spheres, AoE visuals
- Grid logic can still run invisibly for tactical features if needed.

---

## Weather & Climate System

### 1. Weather Types

| Weather      | Effects                                                                 |
|--------------|-------------------------------------------------------------------------|
| Clear        | Normal vision and movement                                              |
| Overcast     | Slight vision reduction, mild stealth bonus                             |
| Rain         | Reduced visibility, muffles sound, may create mud (movement penalty)    |
| Thunderstorm | Lightning risk, loud ambient noise helps stealth, interrupts ranged     |
| Fog          | Severe visibility loss, major stealth bonus, potential for misnavigation|
| Snow         | Slight movement penalty, boosts stealth, tracks visible in snow         |
| Blizzard     | Heavy vision loss, movement slowed, DM decides if additional effects    |
| Heatwave     | Reduced stamina regen or armor penalties; optional, DM-controlled       |
| Windy        | Ranged attack penalties, sound distortion, flying hazards               |

### 2. Climate Zones

| Climate     | Description                     | Primary Effects                                        |
|-------------|---------------------------------|--------------------------------------------------------|
| Temperate   | Forests, grasslands             | Balanced rain, fog, storms                            |
| Desert      | Dry and hot                     | Frequent sandstorms, limited vegetation cover         |
| Arctic      | Cold, snowy                     | Frequent snow/blizzards, icy terrain                  |
| Tropical    | Hot, humid                      | Frequent rain, dense jungle fog                       |
| Mountainous | High elevation                  | Snow, thin air, wind exposure, treacherous slopes     |
| Coastal     | Near water                      | Storms, high humidity, thick fog                      |

### 3. Game Effects

#### Visibility & Stealth
- **Rain, Fog, Snow**: reduce visual range.
- **Wind or storms**: improve stealth chances due to ambient noise.
- Terrain + weather create natural variance in encounter visibility.

#### Movement
- Mud, snow, or wet terrain can slow or alter player pathing.
- Optional: DM determines if additional checks are needed for slippery or unstable ground.

#### Combat
- **Ranged attacks** affected by wind/rain.
- **Fire spells** may be weakened in wet weather (DM optional).
- Environmental effects can disrupt line of sight or advantage.

### 4. DM Control
- DM can trigger or override weather events.
- Option to apply or ignore mechanical effects like movement penalties.
- Use weather to create narrative shifts (e.g., storms reveal ruins, fog conceals enemy army).
