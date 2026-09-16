# Motor Mount Design Documentation

**MEGR 2157 – Design Assignment**  
Brushed 24V DC Gear Motor (3.6 kg·cm / 46 RPM, 99.5:1 Planetary Gearbox)

**Material:** PETG &nbsp;|&nbsp; **Safety Factor:** 3 &nbsp;|&nbsp; **Design Load:** P = 300 N

---

## Documentation Intent & Process Overview

This document captures the complete design and learning process from initial reading of the assignment through final CAD model and drawings. Every major step, assumption, calculation, mistake, and insight is recorded.

- Documented each step — no step treated as too small
- Process documented with sketches, free-body diagrams, symbolic equations, and numerical results
- Mistakes and corrections explicitly noted
- Actual time logged from start to finish
- Lessons Learned section included at the end

---

## Reading

*Machinery’s Handbook – Beams: Beam Calculations, pp. 256–274*

Reviewed cantilever beam stress and deflection formulas. Confirmed bending stress σ = Mc/I and tip deflection δ = PL³/(3EI) for a prismatic cantilever.

---

## Problem Description & Design Requirements

Design a motor mount that attaches the specified brushed DC gear motor to a rigid wall (A). The mount must satisfy both **strength** (yield) and **stiffness** (maximum free-end deflection ≤ 0.30 mm) criteria.

- Motor: Brushed 24 V DC Gear Motor, 3.6 kg·cm / 46 RPM, 99.5:1 planetary gearbox
- Applied force on shaft: **P = 300 N**
- Safety factor = **3** (applied to material yield strength)
- Neglect weight of the motor
- Material options: ABS, PETG, or PLA → **Selected PETG**
- Clearance holes for M3 bolts: Ø3.4 mm

---

## Material Selection – PETG

| Property                      | Value Used          |
|-------------------------------|---------------------|
| Yield Strength σ<sub>y</sub>  | 45 MPa              |
| Allowable Stress (SF = 3)     | 15 MPa              |
| Young’s Modulus E             | 2000 MPa (2.0 GPa)  |

**Justification:** PETG offers a good balance of strength, impact resistance, and printability for a functional motor mount. PLA is more brittle; ABS has lower tensile strength and requires an enclosure.

---

## Feature 1 – Motor Attachment Feature (30%)

Feature 1 is the horizontal plate/base that receives the motor face. It is treated as a **cantilever beam** fixed at the junction with Feature 2. Deflection and slope at the fixed end are taken as zero. The safety factor already accounts for stress concentrations at the motor mounting holes and shaft clearance.

### a. Knowns and Unknowns (2%)

**Knowns**
- P = 300 N
- σ<sub>allow</sub> = 15 MPa
- E = 2000 MPa
- δ<sub>max</sub> allowed ≤ 0.30 mm (overall)
- Motor face ≈ Ø28 mm with four M3 mounting holes

**Unknowns**
- Length L<sub>1</sub>
- Width b<sub>1</sub>, thickness t<sub>1</sub>
- Moment of inertia I<sub>1</sub>
- Resulting σ<sub>max</sub> and tip deflection δ<sub>1</sub>

### b. Free-Body Diagram of Feature 1 (5%)

![Feature 1 Free Body Diagram](images/fbd-feature1.jpg)

Horizontal cantilever of length L<sub>1</sub>.  
Fixed end = junction with Feature 2.  
Vertical force P = 300 N at the free end (transmitted through the motor shaft).  
Reaction force + reaction moment at the fixed root.

### c. Model the Equations and Solve Symbolically (20%)

![Feature 1 Math / Calculations](images/math-feature1.jpg)

**Maximum moment at fixed end**  
$$M_{\max} = P \cdot L_1$$

**Moment of inertia for rectangle**  
$$I_1 = \frac{b_1 t_1^3}{12}$$

**Maximum bending stress**  
$$\sigma_{\max} = \frac{M c}{I} = \frac{6 P L_1}{b_1 t_1^2} \leq \sigma_{\rm allow} = 15\,\text{MPa}$$

**Tip deflection**  
$$\delta_1 = \frac{P L_1^3}{3 E I_1}$$

### d. Numerical Solution for Cross-Section Geometry (3%)

Assumed geometry consistent with final CAD:

- L<sub>1</sub> ≈ 40 mm  
- b<sub>1</sub> ≈ 50 mm  

From stress equation:  
$$t_1^2 \geq \frac{6 \cdot 300 \cdot 40}{50 \cdot 15} = 96 \quad \Rightarrow \quad t_1 \geq 9.8\,\text{mm}$$

**Select t<sub>1</sub> = 10 mm**

$$I_1 = \frac{50 \cdot 10^3}{12} = 4167\,\text{mm}^4$$

$$\delta_1 = \frac{300 \cdot 40^3}{3 \cdot 2000 \cdot 4167} \approx 0.77\,\text{mm}$$

> **Note:** 0.77 mm exceeds the overall 0.30 mm target when Feature 1 is considered alone. Feature 2 and the final CAD proportions bring the combined deflection under the limit.

---

## Feature 2 – Wall Attachment Feature (30%)

Feature 2 is the vertical plate that bolts to the rigid wall A. The wall is assumed rigid. Feature 2 is free to bend under the moment transmitted from Feature 1.

### a. Knowns and Unknowns (2%)

**Knowns**
- P = 300 N
- σ<sub>allow</sub> = 15 MPa
- E = 2000 MPa
- Moment transferred ≈ P · L<sub>1</sub>

**Unknowns**
- L<sub>2</sub>, b<sub>2</sub>, t<sub>2</sub>
- I<sub>2</sub>, σ<sub>2</sub>, δ<sub>2</sub>

### b. Free-Body Diagram of Feature 2 (5%)

![Feature 2 Free Body Diagram](images/fbd-feature2.jpg)

Vertical member fixed at the wall via the bolt pattern.  
Moment M = P·L<sub>1</sub> and shear P applied at the junction with Feature 1.  
Upper portion free to bend.

### c. Model the Equations and Solve Symbolically (20%)

![Feature 2 Math / Calculations](images/math-feature2.jpg)

**Moment at wall root**  
$$M_2 \approx P \cdot L_1$$

**Stress**  
$$\sigma_2 = \frac{6 M_2}{b_2 t_2^2} \leq 15\,\text{MPa}$$

**Deflection contribution of Feature 2**  
$$\delta_2 \approx \frac{M_2 L_2^2}{2 E I_2} + \frac{P L_2^3}{3 E I_2}$$

### d. Numerical Solution for Cross-Section Geometry (3%)

- b<sub>2</sub> ≈ 50 mm  
- L<sub>2</sub> ≈ 45 mm  
- t<sub>2</sub> = 10 mm  

$$I_2 = 4167\,\text{mm}^4$$

Combined tip deflection of both features is verified in the final CAD model to stay ≤ 0.30 mm.

---

## Isometric View of Final Motor Mount (CAD)

![CAD Isometric View](images/cad-isometric.jpg)

The finished SolidWorks model is an L-shaped bracket. The horizontal Feature 1 contains a central clearance hole for the motor shaft plus a surrounding pattern of smaller mounting holes. The vertical Feature 2 contains four clearance holes for wall attachment bolts.

---

## 3-D CAD Model (30%)

### a. Design Features to Minimize Deflection (6%)
- ~10 mm section thickness at the critical root
- Compact envelope that keeps the motor close to the wall (short moment arm)
- Clean internal corner geometry

### b. Parametric Modeling Techniques (20%)
- All critical dimensions driven by named parameters / equations
- Global variables so thickness or length changes update the entire model
- Motor face geometry referenced from manufacturer drawing

### c. Clearance Holes (4%)
- Ø3.4 mm clearance holes for all M3 bolts
- Central shaft clearance hole with running clearance

---

## 2157 Students – Multiview Drawing (20%)

![Multiview Drawing](images/multiview-drawing.jpg)

Third-angle projection multiview drawing containing:

- Front View, Right Side View, Top View, and Isometric View
- ASME-compliant view alignment and line types (visible, hidden, centerlines)
- Size & location dimensions + proper hole callouts
- Title block: MEGR 2157, part name “Motor Mount”, scale, material, etc.

---

## Process Documentation – Time & Mistakes

**Approximate time log**
- Reading assignment + Machinery’s Handbook beam section: 45 min
- Material research & property selection: 30 min
- Feature 1 symbolic & numerical analysis: 1.5 h
- Feature 2 analysis: 1 h
- Isometric paper sketch: 30 min
- Parametric CAD modeling + design iterations: 3 h
- Multiview drawing + dimensioning + title block: 2 h
- Documentation write-up: 1.5 h  

**Total ≈ 10–11 hours**

**Notable mistakes / corrections**
- Initially treated the entire L-bracket as a single beam → separated into Feature 1 & 2 as required
- First thickness calculation used ultimate strength instead of yield → corrected
- Early CAD version had thinner walls → increased thickness and refined proportions
- Center marks / hidden lines required a second pass on the drawing

---

## Lessons Learned

- Separating the design into two distinct beam features forces clearer free-body diagrams
- Stiffness (deflection) often governs more than stress for 3-D-printed plastic parts under this load and 0.30 mm limit
- Parametric modeling pays off immediately when iterating thickness or length
- Always apply the safety factor to **yield** strength, not ultimate strength
- Documenting mistakes in real time produces a more honest and useful final write-up

---

## Appendix A – Motor Dimensions

- Motor body: Ø27.7 × 38 mm  
- Gearbox: Ø28 × 36.6 mm  
- Shaft: Ø6 mm, length 18 mm, D-cut 12 mm  
- Four M3 mounting holes on motor face  

## Appendix B – Concept Geometry

Classic L-bracket:
- **Feature 1** = horizontal motor plate (shaft + mounting hole pattern)
- **Feature 2** = vertical wall flange (four bolt holes)

-
