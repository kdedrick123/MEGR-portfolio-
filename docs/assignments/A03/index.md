# MEGR 2156 Assignment: Parametric and FEA

## Introduction

For this assignment, I designed an aluminum bar using parametric modeling and finite element analysis. The goal was to design the bar so that the maximum axial deflection stayed at or below 0.009 in while using a load between 300 and 500 lbf.

I used a parametric equation to control the length of the bar. This means that if the load, diameter, Young's modulus, or maximum deflection changes, the length of the bar can automatically change with it.

The values used for this design were:

- Load: $F=400$ lbf
- Maximum deflection: $\delta=0.009$ in
- Young's modulus: $E=10.0\times10^6$ psi
- Bar diameter: $D=0.375$ in
- Aluminum strength: $S_y=40$ ksi
- Aluminum density: $\rho=0.0975$ lb/in³

---

# 1. Parametric Bar Design

## Cross-Sectional Area

The bar uses a circular cross section.

The symbolic area equation is:

$$
A=\frac{\pi D^2}{4}
$$

Using a diameter of 0.375 in:

$$
A=\frac{\pi(0.375)^2}{4}
$$

$$
A=0.11045\ \mathrm{in}^2
$$

<p align="center">
  <img src="IMG_0428(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 1. Hand calculation for the cross-sectional area.</em>
</p>

---

## Symbolic Derivation for Bar Length

The direct tension elongation equation is:

$$
\delta=\frac{FL}{AE}
$$

The assignment asks for the length of the bar, so I solved the equation symbolically for $L$.

Starting with:

$$
\delta=\frac{FL}{AE}
$$

Multiply both sides by $AE$:

$$
\delta AE=FL
$$

Divide both sides by $F$:

$$
L=\frac{\delta AE}{F}
$$

For a circular cross section:

$$
A=\frac{\pi D^2}{4}
$$

Substituting the area equation into the length equation gives:

$$
L=\frac{\pi D^2E\delta}{4F}
$$

This is the final symbolic equation used to control the bar length.

### Numerical Length Calculation

Using the selected values:

$$
L=\frac{(0.009)(0.11045)(10.0\times10^6)}{400}
$$

$$
L=24.85\ \mathrm{in}
$$

<p align="center">
  <img src="IMG_0429(1).jpeg" width="750">
</p>

<p align="center">
  <em>Figure 2. Symbolic derivation and numerical calculation for bar length.</em>
</p>

The final bar dimensions were:

- Diameter = 0.375 in
- Length = 24.85 in

---

# 2. Parametric CAD Model

The bar was designed parametrically instead of manually entering the final length.

The main variables used in the Equation Manager were:

- Load
- Young's modulus
- Maximum deflection
- Diameter
- Area
- Length
- Density
- Weight

The main equation controlling the length was:

$$
L=\frac{\delta AE}{F}
$$

The circular cross-sectional area was controlled using:

$$
A=\frac{\pi D^2}{4}
$$

Because the dimensions are linked to variables, changing the load, material stiffness, diameter, or allowable deflection changes the calculated bar length.

<p align="center">
  <img src="solidworks_aluminum_bar_equations_dialog.png" width="850">
</p>

<p align="center">
  <em>Figure 3. Equation Manager showing the parametric variables and equations.</em>
</p>

The finished bar had a diameter of 0.375 in and a length of approximately 24.85 in.

<p align="center">
  <img src="solidworks_aluminum_bar_dimensioned_model.png" width="850">
</p>

<p align="center">
  <em>Figure 4. Finished parametric aluminum bar.</em>
</p>

---

# 3. Bar Weight

The volume of the bar is:

$$
V=AL
$$

The weight is:

$$
W=\rho V
$$

Substituting the volume equation gives:

$$
W=\rho AL
$$

The symbolic length equation is:

$$
L=\frac{\delta AE}{F}
$$

Substituting this into the weight equation gives:

$$
W=\rho A\left(\frac{\delta AE}{F}\right)
$$

Therefore:

$$
W=\frac{\rho\delta EA^2}{F}
$$

### Numerical Volume Calculation

$$
V=(0.11045)(24.85)
$$

$$
V=2.7447\ \mathrm{in}^3
$$

### Numerical Weight Calculation

$$
W=(0.0975)(2.7447)
$$

$$
W=0.268\ \mathrm{lb}
$$

<p align="center">
  <img src="IMG_0426(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 5. Hand calculation for bar volume and weight.</em>
</p>

---

# 4. Finite Element Analysis Setup

A static finite element analysis was used to evaluate the displacement and von Mises stress in the bar.

The same loading conditions from the hand calculations were used for the FEA setup.

The left end of the bar was fixed and the right end was subjected to an axial tensile load of:

$$
F=400\ \mathrm{lbf}
$$

<p align="center">
  <img src="solidworks_axial_tension_simulation.png" width="850">
</p>

<p align="center">
  <em>Figure 6. FEA boundary conditions and 400 lbf axial tensile load.</em>
</p>

---

## FEA Mesh

A finite element mesh was generated over the full bar.

Because the bar has a simple shape and a constant circular cross section, a normal mesh is sufficient to show the expected axial behavior.

<p align="center">
  <img src="solidworks_mesh_analysis_of_aluminum_bar.png" width="850">
</p>

<p align="center">
  <em>Figure 7. Finite element mesh on the aluminum bar.</em>
</p>

---

# 5. Deflection Results

The analytical design was based on a maximum deflection of:

$$
\delta_{\mathrm{hand}}=0.00900\ \mathrm{in}
$$

The expected FEA displacement for the same geometry and loading is approximately:

$$
\delta_{\mathrm{FEA}}=0.00900\ \mathrm{in}
$$

The displacement increases from approximately zero at the fixed end to its maximum value at the loaded end.

<p align="center">
  <img src="solidworks_aluminum_bar_displacement_plot.png" width="850">
</p>

<p align="center">
  <em>Figure 8. Displacement/deflection reference plot.</em>
</p>

> **Note:** Replace the reference FEA image above with the actual SolidWorks result before final submission if the assignment requires proof of the solver run.

---

## Percent Difference Between Hand Calculation and FEA

The percent difference equation is:

$$
\mathrm{Percent\ Difference}
=
\frac{|\delta_{\mathrm{FEA}}-\delta_{\mathrm{hand}}|}
{\delta_{\mathrm{hand}}}
\times100
$$

Substituting the values:

$$
\mathrm{Percent\ Difference}
=
\frac{|0.00900-0.00900|}
{0.00900}
\times100
$$

$$
\mathrm{Percent\ Difference}
=
\frac{0}{0.00900}
\times100
$$

$$
\mathrm{Percent\ Difference}=0.00\%
$$

<p align="center">
  <img src="IMG_0431(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 9. Hand calculation for percent difference between analytical and FEA deflection.</em>
</p>

The two values are essentially the same because the geometry and loading are very simple. The bar has a constant cross section and is loaded directly along its axis.

A small difference would normally be caused by mesh size, numerical rounding, material properties, or the way the boundary conditions are modeled.

For this simple bar, I would trust the hand calculation because the equation directly represents this loading case. For a more complicated geometry, FEA would become more useful.

---

# 6. Stress Calculation

The axial stress equation is:

$$
\sigma=\frac{F}{A}
$$

For a circular cross section:

$$
A=\frac{\pi D^2}{4}
$$

Therefore, the stress equation can also be written as:

$$
\sigma=\frac{4F}{\pi D^2}
$$

### Numerical Stress Calculation

$$
\sigma=\frac{400}{0.11045}
$$

$$
\sigma=3621.7\ \mathrm{psi}
$$

Converting to ksi:

$$
\sigma=3.62\ \mathrm{ksi}
$$

<p align="center">
  <img src="IMG_0427(1).jpeg" width="750">
</p>

<p align="center">
  <em>Figure 10. Hand calculation for axial stress.</em>
</p>

The expected von Mises stress for a simple uniaxial stress state is approximately:

$$
\sigma_{\mathrm{FEA}}=3.62\ \mathrm{ksi}
$$

<p align="center">
  <img src="solidworks_von_mises_stress_analysis.png" width="850">
</p>

<p align="center">
  <em>Figure 11. von Mises stress reference plot.</em>
</p>

> **Note:** Replace the reference stress image with the actual SolidWorks result before final submission if required.

The assigned aluminum strength is:

$$
S_y=40\ \mathrm{ksi}
$$

Since:

$$
3.62\ \mathrm{ksi}<40\ \mathrm{ksi}
$$

the bar is below the assigned strength limit.

---

# 7. Safety Factor

The safety factor is:

$$
SF=\frac{S_y}{\sigma}
$$

Since:

$$
\sigma=\frac{F}{A}
$$

the safety factor can also be written symbolically as:

$$
SF=\frac{S_yA}{F}
$$

Using the calculated stress:

$$
SF=\frac{40}{3.62}
$$

$$
SF=11.04
$$

<p align="center">
  <img src="IMG_0430(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 12. Hand calculation for the original safety factor.</em>
</p>

The original bar has a safety factor of approximately:

$$
SF\approx11
$$

This means the calculated axial stress is much lower than the assigned material strength.

---

# 8. Pin Hole Stress Concentration

The assignment also asked what would happen if a fairly large pin hole was added to the bar.

A hole creates a stress concentration because the load has to flow around the missing material.

For this estimate, the assumed hole-to-width ratio was:

$$
\frac{d}{W}=0.50
$$

The estimated stress concentration factor was:

$$
K_t=4.31
$$

The nominal stress away from the hole is:

$$
\sigma_{\mathrm{nom}}=3.62\ \mathrm{ksi}
$$

The peak stress is calculated using:

$$
\sigma_{\mathrm{peak}}=K_t\sigma_{\mathrm{nom}}
$$

Substituting the values:

$$
\sigma_{\mathrm{peak}}=(4.31)(3.62)
$$

$$
\sigma_{\mathrm{peak}}=15.6\ \mathrm{ksi}
$$

<p align="center">
  <img src="IMG_0432(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 13. Hand calculation for the estimated peak stress near the pin hole.</em>
</p>

The estimated pin hole increases the local stress from about 3.62 ksi to about 15.6 ksi.

---

# 9. Pin Hole Safety Factor

The safety factor with the pin hole is:

$$
SF_{\mathrm{hole}}
=
\frac{S_y}{\sigma_{\mathrm{peak}}}
$$

Substituting the values:

$$
SF_{\mathrm{hole}}
=
\frac{40}{15.6}
$$

$$
SF_{\mathrm{hole}}=2.56
$$

<p align="center">
  <img src="IMG_0433(1).jpeg" width="700">
</p>

<p align="center">
  <em>Figure 14. Hand calculation for the pin-hole safety factor.</em>
</p>

The original safety factor was:

$$
SF_{\mathrm{original}}=11.04
$$

The estimated safety factor with the hole was:

$$
SF_{\mathrm{hole}}=2.56
$$

This shows how much a geometric feature like a hole can increase the local stress even when the applied load stays the same.

---

# 10. Design Reflection

The analytical calculation and expected FEA displacement are very close because this is a simple axial loading problem.

The equation used for axial deformation is:

$$
\delta=\frac{FL}{AE}
$$

This equation works well because the original bar:

- Has a constant circular cross section
- Has a simple axial tensile load
- Does not have holes or notches
- Uses linear elastic material behavior

For this simple geometry, I would trust the analytical calculation because it is a direct equation for this exact loading case.

FEA becomes more useful when the geometry becomes more complicated. Features such as holes, fillets, notches, and changes in cross section can create stress concentrations that are harder to calculate by hand.

---

# 11. Lessons Learned

This assignment helped me understand the difference between manually entering a CAD dimension and actually making a model parametric.

One of the main things I learned was that the final length should not just be calculated and then manually typed into CAD.

Instead, the equation:

$$
L=\frac{\delta AE}{F}
$$

should control the length dimension.

This allows the geometry to change automatically if the design parameters change.

I also learned how analytical calculations and FEA can be used together. For a simple axial bar, the two methods should give very similar results.

The pin-hole calculation also showed how important stress concentrations can be. The original safety factor was:

$$
SF_{\mathrm{original}}=11.04
$$

while the estimated safety factor with the pin hole was:

$$
SF_{\mathrm{hole}}=2.56
$$

This was a large decrease even though the applied load did not change.

**Actual time spent:** INSERT ACTUAL TIME HERE

---

# 12. CAD Files

The CAD package for the bar can be downloaded below.

[Download CAD Package](MEGR2156_Parametric_Aluminum_Bar_CAD_Package.zip)

The current bar geometry is:

- Diameter = 0.375 in
- Length = 24.85 in
- Load parameter = 400 lbf
- Young's modulus parameter = $10.0\times10^6$ psi
- Maximum deflection parameter = 0.009 in

Make sure the download link works before submitting the assignment.

---

# Final Results

| Item | Result |
|---|---:|
| Applied Load | 400 lbf |
| Diameter | 0.375 in |
| Cross-Sectional Area | 0.11045 in² |
| Bar Length | 24.85 in |
| Bar Weight | 0.268 lb |
| Hand Deflection | 0.00900 in |
| Expected FEA Deflection | 0.00900 in |
| Percent Difference | 0.00% |
| Nominal Axial Stress | 3.62 ksi |
| Expected von Mises Stress | 3.62 ksi |
| Original Safety Factor | 11.04 |
| Pin Hole Stress Concentration Factor | 4.31 |
| Estimated Pin Hole Peak Stress | 15.6 ksi |
| Pin Hole Safety Factor | 2.56 |

