# US Patent 3,055,113 Mechanical Reverse Engineering Analysis
**Title:** Tracing Device  
**Inventors:** Arthur Grandjean (filed July 23, 1959; issued September 25, 1962)  
**Original Concept:** André Cassagnes (*L'Écran Magique*, French Pat. 1,185,270)

---

## 1. Kinematic Schematic (US Patent 3,055,113)

```
       [ Top Cable 14 (Pulley 15 to Pulley 15) ]
    +-----------------------------------------------+
    |                  Rod 12 (Vertical Rail)       |
    |                         |                     |
    |     Cable 13 (Left)     v    Cable 13 (Right) |
    |      |            [=========]           |     |
    |      |            | Stylus  |           |     |
    | Rod 11 (Horiz) ===| Carriage|===========|==== |
    |      |            | (Brass) |           |     |
    |      |            [=========]           |     |
    |                         |                     |
    |                         v                     |
    |                 Stylus Tip Contact            |
    +-----------------------------------------------+
       [ Bottom Cable 14 (Pulley 16 to Pulley 16) ]
```

### Key Mechanical Components
1. **Vertical Guide Rail (Rod 12)**:
   - Hardened steel rod ($\varnothing 3.2\text{ mm}$), moving along the $X$-axis.
   - Fixed to horizontal cables (Cable 14) driven by the Left Rotary Knob (Horizontal Control).
2. **Horizontal Guide Rail (Rod 11)**:
   - Hardened steel rod ($\varnothing 3.2\text{ mm}$), moving along the $Y$-axis.
   - Fixed to vertical cables (Cable 13) driven by the Right Rotary Knob (Vertical Control).
3. **Stylus Carriage Block**:
   - A $28 \times 28 \times 12\text{ mm}$ brass block sliding at the intersection of Rod 11 and Rod 12.
   - Contains an internal phosphor-bronze leaf spring biasing the pointed stylus tip directly against the reverse face of the glass screen ($F \approx 0.35\text{ N}$).
4. **Endless Wire Cables (Cables 13 & 14)**:
   - Braided steel wire cables under continuous spring tension wrapped around 4 corner guide pulleys (Pulleys 15 & 16).
5. **Powder & Polystyrene Bead Layer**:
   - The sealed rear chamber contains ultra-fine aluminum flake powder (particle size $\approx 5\sim 15\,\mu\text{m}$) and polystyrene circulation beads ($\varnothing \approx 2\text{ mm}$).
   - The beads agitate the powder during mechanical shaking (Shake to Erase) to uniformly electrostatically re-coat the glass surface.

---

## 2. Inevitable Physics Imperfections

### 2.1 Drawing Arm Interference
1. **Crosshair Ambient Shadow**: Because the steel rods sit only $1.5\sim 2.0\text{ mm}$ behind the glass, ambient room light penetrating the translucent aluminum powder casts a soft diffuse silhouette of Rod 11 and Rod 12 across the entire screen.
2. **Groove Reflection**: When powder is scraped away, looking through the transparent window reveals the reflective metallic surface of Rod 11 and Rod 12 whenever they align with previously scraped trenches.

### 2.2 Powder Optics & Burr Glow
1. **Displaced Burr Ridges**: The rounded stylus tip plows through the aluminum powder, creating compressed ridges on both sides of every groove. These ridges catch light, producing bright silvery rim highlights.
2. **Incomplete Scraping**: Electrostatic forces cause microscopic aluminum dust to cling inside the groove, yielding a dark charcoal graphite texture with subtle metallic sparkles instead of absolute pitch black.
3. **Soda-Lime Glass**: $2.5\text{ mm}$ thick glass induces internal reflection, frame bevel shadows, and soft specular glare streaks.

---

## 3. Eulerian Polyline Topology (Pen Lifts: 0)
Because the stylus cannot be mechanically lifted from the glass, all multi-component graphics (such as Bad Apple frames) must be routed along the outer bezel frame edges ($y=0$ or $y=H-1$), hidden within the chassis bevel shadow.
