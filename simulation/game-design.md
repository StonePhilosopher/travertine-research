# Simulation Design: Travertine Terraces

## Core Concept

A game where players place geothermal wells on a preset tectonic map and watch travertine terraces emerge through chemistry and physics.

## Interface

### Primary Interaction: Click-and-Hold to Place Wells

- **Click** on terrain → begins well placement
- **Hold duration** → controls initial flow rate
  - Short click (~0.5s) = low flow (gentle spring)
  - Medium hold (~2s) = moderate flow
  - Long hold (~5s+) = high flow (gushing spring)
- **Release** → well is placed, water begins flowing

### Visual Feedback During Placement

- Cursor shows well depth indicator growing during hold
- Terrain highlights show where water will flow
- Color gradient indicates flow rate (blue = low, white = high)

## Game Loop

```
1. Player places wells (click-and-hold)
2. Water flows from wells downhill following terrain
3. CO₂ degasses at surface, CaCO₃ precipitates
4. Terraces form: pools deepen, rims build up, cascades develop
5. Time passes (accelerated: 1 real minute = 1 game year)
6. Seismic events randomly shift vents and redirect flow
7. Player adapts: place new wells, abandon dry ones
8. Over time, a travertine landscape emerges
```

## Physics Model

### Water Flow

- **Flow rate (Q)** determined by well pressure + terrain slope
- **Velocity (v)** = Q / cross-sectional area
- **Depth (d)** varies with slope and flow rate
- Flow follows steepest descent but spreads laterally on gentle slopes

### CO₂ Degassing

```
Rate of CO₂ loss ∝ surface_area / volume × turbulence

Thin sheet (rim): high surface area, high turbulence → rapid CO₂ loss
Pool: low surface area, low turbulence → slow CO₂ loss
```

### Precipitation Rate

```
Precipitation_rate ∝ supersaturation × flow_rate

Where supersaturation = f(CO₂_loss, temperature)
```

### Terrace Growth

- **Pool floors:** grow slowly (diffusion-limited, ~1-2 mm/year)
- **Rims:** grow faster (advection + CO₂ loss, ~5-10 mm/year)
- **Cascades:** grow fastest (turbulent, continuous fresh water)
- **Maximum rim height:** ~4-5 mm per step (surface tension limit)

### Seismic Events

Random events that:
- **Open new fractures** → new well sites become available
- **Seal old fractures** → existing wells lose flow or go dry
- **Redirect flow** → water finds new paths, old terraces starve
- **Change flow rates** → pressure shifts alter spring output
- **Cause collapse** → undercut terraces or seismic shaking destroys features

Frequency: adjustable (rare = stable world, frequent = dynamic chaos)

## Tectonic Map

### Preset Starting Maps

1. **Yellowstone Mode**
   - Active tectonics, frequent seismicity
   - Rapid deposition (~1 cm/year)
   - Short terrace lifespan (vents shift often)
   - Colorful (microbial mats active)

2. **Pamukkale Mode**
   - Stable tectonics, rare earthquakes
   - Slow deposition (~1-2 mm/year)
   - Long-lived terraces
   - White/cream (cooler water, fewer thermophiles)

3. **Plitvice Mode**
   - River-based system (cooler, biological)
   - Tufa (biological deposition dominant)
   - Cascades and lakes
   - Green/brown (algae-dominated)

4. **Custom Mode**
   - Player-defined fault geometry
   - Adjustable heat source depth
   - Variable limestone availability
   - Custom seismic frequency

### Hidden Tectonic Layer

Beneath the visible terrain:
- **Fracture map** (hidden) — where vents can appear
- **Heat source depth** — controls water temperature
- **Limestone distribution** — controls dissolved CaCO₃
- **Stress zones** — high stress = more seismicity, more vent openings

Player doesn't see the fracture map directly, but can infer it from:
- Where wells successfully produce flow
- Seismic patterns
- Terrace color (temperature indicator)

## Visual Aesthetic

### Color Palette

| Feature | Color | Cause |
|---------|-------|-------|
| Fresh aragonite | White/cream | Hot, rapid precipitation |
| Weathered travertine | Tan/brown | Organic staining, aging |
| Active microbial mats | Orange/yellow | Carotenoid pigments |
| Cool pools | Green | Algae/cyanobacteria |
| Water | Blue-white | Depth + suspended particles |

### Texture Detail

- **Pools:** smooth, slightly porous, subtle layering
- **Rims:** sharp edges, compact, often banded
- **Cascades:** rough, turbulent, aerated
- **Dry terraces:** cracked, weathered, vegetation encroaching

## Game Modes

### Sandbox Mode
- Unlimited wells
- Adjustable time rate
- No objectives
- Pure experimentation

### Scenario Mode
- Recreate specific real-world sites:
  - "Build Minerva Terrace" (Yellowstone)
  - "Restore Pamukkale" (Turkey)
  - "Grow Plitvice Lakes" (Croatia)
- Objectives: specific terrace height, area coverage, color pattern

### Challenge Mode
- Limited wells
- Competing objectives: maximize terrace area vs. preserve microbial diversity
- Seismic disasters must be survived
- Budget constraints on well maintenance

## Connection to Vugg Simulator

The travertine simulation shares physics with the Vugg's evaporite chemistry:

| Feature | Vugg | Travertine |
|---------|------|------------|
| Supersaturation | ✓ | ✓ (CO₂-driven) |
| Crystal growth | ✓ | ✓ (but macro scale) |
| Temperature effects | ✓ | ✓ (aragonite/calcite) |
| Fluid dynamics | ✓ | ✓ (gravity flow) |
| Evaporation | ✓ | ✗ (minor role) |
| CO₂ degassing | ✗ | ✓ (primary driver) |
| Tectonic forcing | ✗ | ✓ (seismic events) |
| Biological templating | ✗ | ✓ (microbial mats) |

**Reusable code:** Fluid flow, supersaturation tracking, crystal growth rates, temperature-dependent mineral stability.

**New code:** CO₂ degassing model, surface tension physics, terrace morphology generation, seismic event system.

## Open Questions

1. Should microbial color banding be cosmetic or gameplay-relevant?
2. Should terrace collapse be player-triggered or purely random?
3. How much should the hidden fracture map be inferable vs. discoverable?
4. Is the goal beauty, accuracy, or emergent complexity?

---

*Design document started 2026-05-18*  
*Conversation: Professor (StonePhilosopher) and 🪨✍️ (Rock Bot)*
