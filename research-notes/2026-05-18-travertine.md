# Research Notes: Daily Thread — 2026-05-18

## Topic: Mammoth Hot Springs Travertine Simulation

### Initial Observation

Professor mentioned Mammoth Hot Springs as a long-term creative project: "recreating the travertine of Mammoth Hot Springs would be a wonderful project, but that's a huge undertaking."

I initially framed it as a chemistry problem (supersaturation, precipitation, CO₂ degassing). Professor corrected me — I had left out the tectonic architecture entirely.

### Tectonic Correction

The Mammoth system requires:
1. **Yellowstone Caldera** (~631,000 years old) — provides the fracture network and heat source
2. **Hebgen Lake Fault** — intersects the caldera, reactivates features
3. **Norris-Mammoth Corridor** — the critical north-south fault that pipes heat from Norris to Mammoth through limestone bedrock

Without the Norris-Mammoth fault, you have hot water OR limestone OR a surface spring. You do not have Mammoth Hot Springs.

### Simulation Concept Emerged

Professor proposed a game interface:
- **Preset tectonic map** (hidden fracture network)
- **Click-and-hold to place wells** (duration = flow rate)
- **Dynamic vents** that shift over time
- **Flow rates change** based on seismic activity
- **Emergent travertine terraces** from the physics

### Research Conducted

1. Searched for academic papers on travertine dam formation
2. Found Hammer et al. (2007/2010) — the key geometric scaling law: **IDD = h tan(α) + k**
3. Confirmed surface tension controls terrace height (~4-5 mm)
4. Verified CO₂ degassing (not evaporation) is the primary precipitation driver
5. Documented temperature-dependent polymorphism (aragonite vs calcite)
6. Researched microbial color banding (thermophile zonation)

### Key Physics

| Process | Mechanism |
|---------|-----------|
| Precipitation | CO₂ degassing shifts Ca²⁺ + 2HCO₃⁻ ⇌ CaCO₃↓ + H₂O + CO₂↑ |
| Terrace height | Surface tension meniscus limit (~4-5 mm) |
| Rim growth | Thin-sheet flow = max CO₂ loss = max precipitation |
| Pool growth | Slow, diffusion-limited, biological |
| Seismic control | Earthquakes shift vents, redirect flow, collapse terraces |

### Design Document

Created comprehensive game design covering:
- Click-and-hold well placement
- Fluid flow + CO₂ degassing + precipitation coupling
- Seismic event system
- Preset tectonic maps (Yellowstone, Pamukkale, Plitvice modes)
- Visual aesthetic (microbial color banding, terrace textures)
- Connection to existing Vugg Simulator codebase

### Open Questions

1. Should microbial color be cosmetic or gameplay-relevant?
2. Player-triggered or purely random seismic events?
3. How inferable should the hidden fracture map be?
4. Goal: beauty, accuracy, or emergent complexity?

### Files Created

- `README.md` — Overview and research thread
- `geology/tectonic-setting.md` — Tectonic architecture
- `chemistry/precipitation-mechanics.md` — Chemistry and physics
- `simulation/game-design.md` — Full game design document
- `references/sources.md` — Academic papers and web sources

---

*Research thread complete. Pushed to GitHub as StonePhilosopher/travertine-research.*
