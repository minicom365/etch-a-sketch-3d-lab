# etch-a-sketch-3d-lab

Interactive 3D mechanical emulator, educational cutaway/exploded view analyzer, and continuous vector plotter based on **US Patent 3,055,113** (*"Tracing Device"*, Arthur Grandjean / André Cassagnes, 1962).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Zero Dependency](https://img.shields.io/badge/dependencies-0-brightgreen.svg)]()
[![Live Demo](https://img.shields.io/badge/demo-GitHub%20Pages-orange.svg)](https://minicom365.github.io/etch-a-sketch-3d-lab/)

![3D Etch A Sketch Lab Preview](assets/preview_toy.png)

---

## Overview

**etch-a-sketch-3d-lab** is an all-in-one educational physics emulator and mechanical visualization laboratory for the iconic mechanical drawing toy. Rather than simple 2D pixel manipulation, this project simulates the full internal mechanical kinematics and optical interactions of the original 1962 patent in real-time WebGL.

Runs 100% client-side with **zero external server dependencies**. Simply double-click `index.html` in any modern web browser or visit the [GitHub Pages Live Demo](https://minicom365.github.io/etch-a-sketch-3d-lab/).

---

## 3 Core Operational Modes

### 🎮 Mode 1: Interactive 3D Toy Emulator
- **Full 3D Orbit & Inspection**: Mouse drag to orbit 360°, scroll to zoom, right-click to pan. Quick presets for Front, Isometric 45°, and Stylus Macro Zoom.
- **Authentic Ohio Art Aesthetics**: Molded cherry-red chassis with beveled window cutout, metallic gold hot-stamped branding (`MAGIC Etch A Sketch SCREEN - US PAT. 3,055,113`), and 3D knurled white rotary dials with 24 serrated flutes.
- **Physical "Shake to Erase"**: Shaking animates realistic chassis rattling, tumbling 90+ polystyrene circulation beads, and progressive powder re-coating.
- **Butter-Smooth Keyboard Control**: 60 FPS continuous sub-pixel game loop (WASD / Arrow Keys) eliminates stepped dot artifacts.

### 🔬 Mode 2: US Patent 3,055,113 Mechanical Cutaway & Exploded View
![Mechanical Cutaway Exploded View](assets/preview_cutaway.png)
- **Continuous 3D Exploded View (0% to 100%)**:
  1. Top Cherry-Red Beveled Chassis ($Z = 19$)
  2. 2.5 mm Soda-Lime Glass Window Plate ($Z = 13.5$)
  3. Translucent Aluminum Powder Screen Surface ($Z = 11.8$)
  4. Brass Stylus Carriage with Phosphor-Bronze Leaf Spring ($Z = 5.0$)
  5. Vertical Hardened Steel Guide Rail (Rod 12, $X$-travel)
  6. Horizontal Hardened Steel Guide Rail (Rod 11, $Y$-travel)
  7. Continuous Steel Wire Drive Cables (Cables 13, 14) and 4 Corner Idler Pulleys (Pulleys 15, 16)
  8. Sealed Bottom Powder Chamber ($Z = -13$)
- **X-Ray Cutaway Transparency**: Slide from 0% to 100% to inspect internal rod motion while drawing in real-time.
- **Real-Time Kinematic Telemetry HUD**: Displays instant stylus coordinates, left/right dial angles, cable tension, spring force, and scraped powder ratio.

### 🎨 Mode 3: Single-Stroke Eulerian Vector Plotter & Screentone Converter
![Continuous Vector Plotter](assets/preview_plotter.png)
- **4 Classic Mathematical & Engineering Presets**:
  - **Spirograph (Hypotrochoid)**: Multi-loop harmonic epicycle rosette.
  - **1960s Classic Ohio Art House**: Classic architectural line drawing with pitched roof, chimney, cross-braced frame, and door.
  - **Mona Lisa One-Line**: Continuous tonal portrait contour.
  - **Lissajous Harmonic Resonance**: 3:4 frequency orthogonal harmonic curve.
- **Custom Image / Photo Vectorizer**: Upload any local PNG/JPG image to automatically convert it into a single continuous toolpath using the built-in `light-screentone` engine (supporting boustrophedon hatching, dot matrix, line screen, crosshatch, and Bayer ordered dithering).
- **Physical Imperfection & Kinematic Constraints**:
  - **Eulerian Single-Line Topology (`Pen Lifts: 0`)**: Mechanically constrained to never lift the stylus; voids are detoured via outer bezel shadows.
  - **Analog Human Jitter & Cable Backlash**: Simulates human neuromuscular variance ($\sigma \approx 0.6\text{ px}$) and cable backlash ($0.5\text{ px}$) to prevent artificial computer grid artifacts.
  - **Drawing Arm Optical Interference**: Simulates diffuse internal crosshair shadows and specular rod reflection through cleared grooves.
- **Vector Export**: One-click SVG download (`etch_a_sketch_toolpath.svg`) compatible with pen plotters and CNC routers.

---

## Repository Structure

```
etch-a-sketch-3d-lab/
├── index.html                   # All-in-One 3D WebGL Lab & UI Application
├── light-screentone.js          # Sub-library: Lightweight Functional Binary Screentone & Eulerian Engine
├── three.min.js                 # Standalone Three.js r128 bundle (Offline ready)
├── OrbitControls.js             # Standalone Three.js OrbitControls
├── PATENT_US3055113_ANALYSIS.md # US Patent 3,055,113 Reverse-Engineering & Kinematic Analysis
├── README.md                    # Official English Guide
├── README_KO.md                 # Detailed Korean Guide
└── assets/
    ├── preview_toy.png          # Mode 1: 3D Toy Emulator Screenshot
    ├── preview_cutaway.png      # Mode 2: Mechanical Exploded View Screenshot
    └── preview_plotter.png      # Mode 3: Continuous Vector Plotter Screenshot
```

---

## Running Locally

No npm, Node.js, Python, or build steps required. Simply open `index.html` in Chrome, Edge, Safari, or Firefox:

```powershell
# Optional local static HTTP server
python -m http.server 8080
```

Visit `http://localhost:8080` in your web browser.

---

## License

MIT License. (C) 2026 Minicom365.
