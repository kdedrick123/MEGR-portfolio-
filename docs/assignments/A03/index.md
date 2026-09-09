# MEGR 2156 Assignment: Parametric and FEA

## Introduction

For this assignment, I designed an aluminum bar using parametric modeling and finite element analysis. The goal was to design the bar so that the maximum axial deflection stayed below 0.009 in while using a load between 300 and 500 lbf.

I also used a parametric equation to control the length of the bar. This means that if the load, diameter, Young's modulus, or maximum deflection changes, the length of the bar will automatically change.

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

The bar uses a circular cross section. The area is found using:

$$
A=\frac{\pi D^2}{4}
$$

Using a diameter of 0.375 in:

$$
A=\frac{\pi(0.375)^2}{4}
$$

$$
\boxed{A=0.11045\text{ in}^2}
$$

<p align="center">
  <img src="IMG_0428.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 1. Hand calculation for the cross-sectional area.</em>
</p>

---

## Symbolic Derivation

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

Substitute the area equation into the length equation:

$$
L=
\frac{\delta E}{F}
\left(
\frac{\pi D^2}{4}
\right)
$$

Therefore:

$$
\boxed{
L=\frac{\pi D^2E\delta}{4F}
}
$$

<p align="center">
  <img src="IMG_0429.jpeg" width="750">
</p>

<p align="center">
  <em>Figure 2. Symbolic derivation and numerical bar length calculation.</em>
</p>

### Numerical Length Calculation

Using the selected values:

$$
L=
\frac{(0.009)(0.11045)(10.0\times10^6)}
{400}
$$

$$
\boxed{L=24.85\text{ in}}
$$

The final bar dimensions were:

- Diameter = 0.375 in
- Length = 24.85 in

---

# 2. Parametric CAD Model

The bar was designed parametrically instead of manually typing in the final length.

The main variables used were:

- Load
- Young's modulus
- Maximum deflection
- Diameter
- Area
- Length
- Density
- Weight

The main equation controlling the bar length was:

$$
\boxed{
L=\frac{\delta AE}{F}
}
$$

This allows the CAD model to automatically change length if one of the main design variables changes.

The Equation Manager was set up with the main design parameters and equations.

<p align="center">
  <img src="solidworks_aluminum_bar_equations_dialog.png" width="850">
</p>

<p align="center">
  <em>Figure 3. Equation Manager showing the parametric variables used for the bar.</em>
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

Substituting $V=AL$:

$$
W=\rho AL
$$

The symbolic length equation is:

$$
L=\frac{\delta AE}{F}
$$

Substituting this into the weight equation gives:

$$
W=
\rho A
\left(
\frac{\delta AE}{F}
\right)
$$

Therefore:

$$
\boxed{
W=\frac{\rho\delta EA^2}{F}
}
$$

### Numerical Volume

$$
V=AL
$$

$$
V=(0.11045)(24.85)
$$

$$
\boxed{V=2.7447\text{ in}^3}
$$

### Numerical Weight

Using an aluminum density of:

$$
\rho=0.0975\text{ lb/in}^3
$$

the weight is:

$$
W=\rho V
$$

$$
W=(0.0975)(2.7447)
$$

$$
\boxed{W=0.268\text{ lb}}
$$

<p align="center">
  <img src="IMG_0426.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 5. Hand calculation for bar volume and weight.</em>
</p>

---

# 4. Finite Element Analysis

A static finite element analysis was used to check the displacement and stress in the bar.

The same loading conditions used for the hand calculations were used in the FEA.

The left end of the bar was fixed, and a 400 lbf tensile load was applied to the right end.

$$
F=400\text{ lbf}
$$

<p align="center">
  <img src="solidworks_axial_tension_simulation.png" width="850">
</p>

<p align="center">
  <em>Figure 6. FEA boundary conditions and 400 lbf axial load.</em>
</p>

---

## FEA Mesh

A finite element mesh was generated across the full bar.

Because the bar has a simple shape and constant cross section, the mesh does not need to be extremely fine to give a reasonable result.

<p align="center">
  <img src="solidworks_mesh_analysis_of_aluminum_bar.png" width="850">
</p>

<p align="center">
  <em>Figure 7. Finite element mesh used for the analysis.</em>
</p>

---

# 5. Deflection Results

The hand-calculated maximum deflection was:

$$
\boxed{
\delta_{hand}=0.00900\text{ in}
}
$$

The FEA displacement result was:

$$
\boxed{
\delta_{FEA}=0.00900\text{ in}
}
$$

The displacement increased from approximately zero at the fixed end to the maximum value at the loaded end.

<p align="center">
  <img src="solidworks_aluminum_bar_displacement_plot.png" width="850">
</p>

<p align="center">
  <em>Figure 8. FEA displacement map.</em>
</p>

---

## Percent Difference Between Hand Calculation and FEA

The percent difference equation is:

$$
\%\text{ Difference}
=
\frac{
|\delta_{FEA}-\delta_{hand}|
}{
\delta_{hand}
}
\times100
$$

Substituting the results:

$$
\%\text{ Difference}
=
\frac{
|0.00900-0.00900|
}{
0.00900
}
\times100
$$

$$
\%\text{ Difference}
=
\frac{0}{0.00900}
\times100
$$

$$
\boxed{
\%\text{ Difference}=0.00\%
}
$$

<p align="center">
  <img src="IMG_0431.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 9. Hand calculation for percent difference between the analytical and FEA deflection.</em>
</p>

The two results are essentially the same because the geometry and loading are very simple. The bar has a uniform cross section and is loaded directly along its axis.

Small differences can normally happen because of mesh size, numerical rounding, material properties, or boundary conditions.

For this simple bar, I would trust the hand calculation because the equation directly represents this loading case. For more complicated geometry, FEA would be more useful because it can show local stress concentrations.

---

# 6. Stress Results

The normal axial stress is found using:

$$
\sigma=\frac{F}{A}
$$

For the circular cross section:

$$
A=\frac{\pi D^2}{4}
$$

The stress equation can also be written as:

$$
\sigma=
\frac{F}{
\pi D^2/4
}
$$

Therefore:

$$
\boxed{
\sigma=\frac{4F}{\pi D^2}
}
$$

### Numerical Stress

$$
\sigma=
\frac{400}{0.11045}
$$

$$
\sigma=3621.7\text{ psi}
$$

Converting to ksi:

$$
\sigma=
\frac{3621.7}{1000}
$$

$$
\boxed{
\sigma=3.62\text{ ksi}
}
$$

<p align="center">
  <img src="IMG_0427.jpeg" width="750">
</p>

<p align="center">
  <em>Figure 10. Hand calculation for axial stress.</em>
</p>

The FEA von Mises stress was also approximately:

$$
\boxed{
\sigma_{FEA}=3.62\text{ ksi}
}
$$

<p align="center">
  <img src="solidworks_von_mises_stress_analysis.png" width="850">
</p>

<p align="center">
  <em>Figure 11. FEA von Mises stress map.</em>
</p>

The maximum stress is much lower than the assigned aluminum strength:

$$
3.62\text{ ksi}<40\text{ ksi}
$$

Therefore, the bar meets the strength requirement.

---

# 7. Safety Factor

The safety factor is:

$$
SF=\frac{S_y}{\sigma}
$$

Because:

$$
\sigma=\frac{F}{A}
$$

the safety factor can also be written symbolically as:

$$
SF=
\frac{S_y}{F/A}
$$

Therefore:

$$
\boxed{
SF=\frac{S_yA}{F}
}
$$

Using:

$$
S_y=40\text{ ksi}
$$

and:

$$
\sigma=3.62\text{ ksi}
$$

the safety factor is:

$$
SF=
\frac{40}{3.62}
$$

$$
\boxed{
SF=11.04
}
$$

<p align="center">
  <img src="IMG_0430.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 12. Hand calculation for the original bar safety factor.</em>
</p>

The safety factor is about 11, which means the bar is well below the assigned strength limit.

---

# 8. Pin Hole Stress Concentration

The assignment also asked what would happen if a fairly large pin hole was added to the bar.

A hole creates a stress concentration because the load has to travel around the missing material.

For this estimate, the assumed hole-to-width ratio was:

$$
\frac{d}{W}=0.50
$$

The estimated stress concentration factor was:

$$
\boxed{
K_t=4.31
}
$$

The nominal stress away from the hole is:

$$
\sigma_{nom}=3.62\text{ ksi}
$$

The peak stress is found using:

$$
\sigma_{peak}=K_t\sigma_{nom}
$$

Substituting the values:

$$
\sigma_{peak}
=
(4.31)(3.62)
$$

$$
\boxed{
\sigma_{peak}=15.6\text{ ksi}
}
$$

<p align="center">
  <img src="IMG_0432.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 13. Hand calculation for the estimated stress near the pin hole.</em>
</p>

The hole causes the local stress to increase from about 3.62 ksi to about 15.6 ksi.

---

# 9. Pin Hole Safety Factor

The safety factor with the hole is:

$$
SF_{hole}
=
\frac{S_y}{\sigma_{peak}}
$$

Substituting the values:

$$
SF_{hole}
=
\frac{40}{15.6}
$$

$$
\boxed{
SF_{hole}=2.56
}
$$

<p align="center">
  <img src="IMG_0433.jpeg" width="700">
</p>

<p align="center">
  <em>Figure 14. Hand calculation comparing the original and pin-hole safety factors.</em>
</p>

The original safety factor was:

$$
SF_{original}=11.04
$$

The safety factor with the hole was:

$$
SF_{hole}=2.56
$$

This shows that adding a hole can greatly increase the local stress even when the applied load stays the same.

---

# 10. Design Reflection

The hand calculation and the FEA result gave essentially the same displacement.

The main reason is that this problem uses a straight bar with a constant cross section and a simple axial tensile load. There are no complicated shapes in the original bar.

The analytical equation is:

$$
\delta=\frac{FL}{AE}
$$

This equation works very well for this type of geometry.

The FEA is still useful because it gives a visual map of the displacement and stress across the full part.

For the basic bar, I would trust the hand calculation because it is a direct solution to this exact problem.

For a part with holes, fillets, notches, or more complicated shapes, I would trust FEA more because those features create local stress concentrations that are harder to calculate with a simple equation.

---

# 11. Lessons Learned

This assignment helped me understand the difference between manually entering dimensions and using a parametric CAD model.

One of the biggest things I learned was that the final bar length should not just be calculated and manually entered into CAD. Instead, the equation should control the dimension.

The main equation used was:

$$
\boxed{
L=\frac{\delta AE}{F}
}
$$

This was linked to the bar length so that changing the load, Young's modulus, diameter, or maximum deflection changes the geometry.

I also learned how hand calculations and FEA can be used together.

For a simple axial bar, the hand calculations and FEA results should be very close. For more complicated parts, FEA becomes more useful because it can show areas with higher local stress.

Another important part of the assignment was seeing how much a pin hole can affect the design. The original safety factor was approximately:

$$
SF_{original}=11.04
$$

After adding the estimated pin-hole stress concentration:

$$
SF_{hole}=2.56
$$

This showed that even though the applied load stayed the same, changing the geometry can have a large effect on the strength of the part.

**Actual time spent:** INSERT YOUR ACTUAL TIME HERE

---

# 12. CAD Files

The CAD files used for the project can be downloaded below.

[Download CAD Package](MEGR2156_Parametric_Aluminum_Bar_CAD_Package.zip)

Make sure the download link works before submitting the assignment.

---

# Final Results

| Item | Result |
|---|---:|
| Load | 400 lbf |
| Diameter | 0.375 in |
| Area | 0.11045 in² |
| Bar Length | 24.85 in |
| Bar Weight | 0.268 lb |
| Hand Deflection | 0.00900 in |
| FEA Deflection | 0.00900 in |
| Percent Difference | 0.00% |
| Nominal Stress | 3.62 ksi |
| FEA von Mises Stress | 3.62 ksi |
| Original Safety Factor | 11.04 |
| Pin Hole Stress Concentration Factor | 4.31 |
| Estimated Pin Hole Peak Stress | 15.6 ksi |
| Pin Hole Safety Factor | 2.56 |
