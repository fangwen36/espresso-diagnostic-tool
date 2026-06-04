# Espresso Extraction Diagnostic Tool

A pure front-end espresso extraction physics simulation and diagnostic tool. Input via drawn pressure curves or sensory descriptions, and the engine — based on Darcy's Law for flow through porous media — back-calculates real-time flow rate, flavor extraction, and outputs targeted brewing correction advice.

**English | [中文](README.md)**

## Features

- **Dual Input Mode** — Draw pressure curves directly on Canvas, or describe extraction via sensory choices (crema, color, flow, taste)
- **Physics Engine** — Darcy's Law-based simulation that dynamically calculates flow rate and flavor profile from pressure input
- **Multi-Device Support** — Lever machines and pump machines
- **Basket Selection** — Standard, high-flow, and pressurized baskets with auto-adjusted thresholds
- **Channeling Detection** — Automatically identifies puck shear failure, channeling, grind issues, and other typical extraction faults
- **Flavor Visualization** — Real-time acid/sweet/bitter flavor ratio bars
- **Diagnostic Prescription** — Actionable correction advice covering dose, grind, tamp, and lever technique
- **Mobile Friendly** — Touch drawing support, responsive layout

## Quick Start

Open `coffee_sim.html` in any browser — no server or dependencies required:

```bash
open index.html
```

1. **Step ① — Input**: Select machine and basket type, adjust dose/yield/time parameters, then draw a pressure curve or describe sensory observations
2. **Step ② — Diagnosis**: Click "Start Analysis" — the engine simulates flow, flavor, and outputs a diagnosis
3. **Refine**: Click "Rediagnose" to return to input, adjust parameters, and re-analyze

## Physics Model

The simulation is based on **Darcy's Law** for porous media flow:

$$F(t) = \frac{P(t)}{R(t)}$$

- **$F(t)$** — Instantaneous flow rate (g/s)
- **$P(t)$** — Instantaneous pressure (bar)
- **$R(t)$** — Instantaneous puck resistance

Resistance $R(t)$ evolves through three factors:

1. **Base Resistance** — Determined by grind size and dose
2. **Channel Collapse** — When pressure exceeds the puck's shear strength ($P_{rupture}$), the puck tears and resistance drops sharply
3. **Solubility Erosion** — Resistance naturally decreases as solubles are extracted

### Diagnostic Logic

| Symptom | Diagnosis | Fix |
|---------|-----------|-----|
| Low pressure + High flow | Coarse grind / low dose | Grind 2-3 steps finer, increase dose |
| High pressure + Low flow | Fine grind / choke | Grind 1-2 steps coarser, reduce dose |
| Mid-drop pressure + Flow spike | Channeling | WDT + level tamp |
| Stable pressure in basket range | Normal extraction | Keep the recipe |

## Tech Stack

- Pure HTML5 / CSS3 / JavaScript (zero dependencies)
- Canvas 2D rendering engine
- Dark Glassmorphism UI
- Responsive layout (mobile + desktop)
- Google Fonts (Outfit + JetBrains Mono)

## Project Structure

```
espresso-diagnostic-tool/
├── index.html            # Main application (single HTML file with all styles and logic)
├── TODO.md               # Development task tracking & iteration history
├── README.md             # Chinese documentation
├── README.en.md          # English documentation (this file)
└── .gitignore            # Git ignore rules
```

## About

This project is an interactive espresso extraction physics simulation and diagnostic tool. It helps coffee enthusiasts and professional baristas understand the fluid dynamics behind espresso extraction, quickly identify brewing defects, and find the right corrections.
