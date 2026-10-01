# MEGR 2157 - Parametric Bracket and Link Design

**Student:** Kaleb Dedrick  
**Material:** 6061-T6 Aluminum  
**Design Load:** 800 lbf  
**Safety Factor:** 4  
**Allowable Stress:** 10,000 psi  
**Maximum Allowable Deflection:** 0.005 in  

## Objective

The purpose of this assignment was to convert my previous bracket design into a parametric CAD model and create detailed engineering drawings for the bracket and link. The bracket must support the 800 lbf design load while maintaining the required sliding-fit clearance over the rigid T-beam. The model and drawings communicate the part geometry, material, tolerances, fits, and manufacturing requirements.

![Completed bracket CAD model](bracketimg.png)

## Parametric Bracket Design

The bracket was modeled using named parameters instead of entering unrelated dimensions manually. This allows the model to update if the load, material, mating feature, or part dimensions change later.

The main bracket dimensions are listed below.

- Rear web thickness: 0.498 in
- Body depth: 0.9992 in
- Clear jaw gap: 1.499 in
- Lower jaw thickness: 0.500 in
- Upper jaw thickness: 0.750 in
- Jaw length: 2.000 in
- Pin boss diameter: 1.125 in

The clear jaw gap is a functional dimension because it controls how the bracket slides over the rigid T-beam. The rear web thickness is a strength-driven dimension because it resists the applied load.

![CAD Equation Manager and Global Variables](value.png)

## Strength-Driven CAD Equation

The rear web thickness was controlled using the bending-stress equation below.

**Bending stress equation:**

σ = (6 × F × e) / (b × t²)

Solving the equation for the required rear web thickness gives:

t = √[(6 × F × e) / (σ_allow × b)]

Where:

- F = 800 lbf
- e = 0.5163 in
- b = 0.9992 in
- σ_allow = 10,000 psi
- t = required rear web thickness

Substituting the design values:

t = √[(6 × 800 × 0.5163) / (10,000 × 0.9992)]

t = √(2478.24 / 9992)

t = √(0.2480)

t = 0.498 in

Therefore, the rear web thickness was set to **0.498 in**.

The Equation Manager contains the design variables and web-thickness calculation used to document the design basis. The variables can be updated if the design load, allowable stress, or body depth changes.

## Stress and Deflection Check

### Stress Check

σ = (6 × F × e) / (b × t²)

σ = [6 × 800 × 0.5163] / [0.9992 × (0.498)²]

σ = 10,000 psi

The calculated bending stress equals the allowable stress of 10,000 psi.

### Deflection Check

The deflection equation used was:

δ = (4 × F × e³) / (E × b × t³)

Where:

- δ = deflection
- E = 10,000,000 psi for 6061-T6 aluminum

Substituting the values:

δ = [4 × 800 × (0.5163)³] / [10,000,000 × 0.9992 × (0.498)³]

δ ≈ 0.00036 in

Since:

0.00036 in < 0.005 in

the bracket meets the deflection requirement.

![Stress and deflection calculation](<strress calc.png>)

## Engineering Drawing and Tolerances

The bracket drawing is arranged in third-angle projection with front, top, right, and isometric views. The drawing title block identifies the part as 6061-T6 aluminum with a mill finish.

The general tolerance block used on the drawing is:

- X.X: +/- 0.02 in
- X.XX: +/- 0.01 in
- X.XXX: +/- 0.005 in

The 1.499 in jaw gap is a functional mating surface because it slides over the rigid T-beam. This dimension uses a tighter tolerance of:

1.499 in +0.005 / -0.000

This tolerance protects the assembly clearance and prevents the gap from becoming too small after manufacturing.

The rear web thickness should also use the tighter tolerance class because it is controlled by the strength equation. A non-critical outside edge can use the looser X.X +/- 0.02 tolerance because it does not locate a mating component or affect the sliding fit.

Using the tightest tolerance on every dimension would increase machining time, inspection requirements, and manufacturing cost without improving the function of non-critical features.

![Completed bracket drawing in third-angle projection](<bracket drw.png>)

## Link Design - MEGR 2157 Requirement

The link was modeled parametrically from the bracket interface dimensions. The link is 1.500 in wide, 0.375 in thick, and has a 2.000 in hole-center distance.

The link overall length was controlled by the equation below.

L_link = Hole Center Distance + Outside Width

L_link = 2.000 in + 1.500 in

L_link = 3.500 in

The smaller 0.500 in hole is a sliding interface using an H7/g6 fit. The 1.000 in hole is a controlled H7/p6 interface.

The drawing datums are:

- Datum A: Broad flat face of the link
- Datum B: Axis of the 1.000 in hole
- Datum C: Axis of the 0.500 in hole

The drawing includes these position callouts:

- Position of 1.000 in hole: DIA 0.005 | A | B | C
- Position of 0.500 in hole: DIA 0.010 | A | B

## Process Documentation

I began by reviewing the geometry and dimensions from the previous bracket assignment. The bracket geometry was separated into strength-driven dimensions and fit-controlled dimensions. The rear web thickness was identified as the primary strength-driven feature because it resists the bending load. The jaw gap was identified as the primary fit-controlled feature because it must slide over the T-beam.

I used the bending-stress equation to determine the rear web thickness. This connected the engineering analysis to the CAD design basis and showed how a change to the load, material, or body depth affects the required web thickness.

While creating the drawings, I checked that the views were arranged in third-angle projection and that the important dimensions were visible without duplicate dimensions. I also verified that the material, finish, tolerance block, title block, drawing number, revision, and third-angle projection symbol were included.

**Correction or mistake I encountered:**  
[Add one real issue you corrected while creating your CAD model or drawing.]

**Actual time spent:**  
[Enter your actual time spent here.]

## Lessons Learned

This assignment showed that a parametric model is more useful than a model with disconnected dimensions. The rear web thickness was controlled by a stress equation, so the model can respond to changes in loading or material properties. This reduces manual rework and keeps the engineering analysis connected to the physical design.

I also learned that tolerances communicate design intent. The 1.499 in gap needs tighter control because it is a sliding-fit interface with the rigid T-beam. A non-critical external edge does not need the same accuracy. Selecting tolerances based on the function of each feature improves manufacturability while protecting the dimensions that control fit, strength, and assembly.

## CAD Download Links

- **Bracket CAD file:** [Download the bracket STEP file](Kaleb_Dedrick_MEGR2157_Bracket.step)
- **Link CAD file:** [Download the link STEP file](Kaleb_Dedrick_MEGR2157_Link_Parametric.step)
