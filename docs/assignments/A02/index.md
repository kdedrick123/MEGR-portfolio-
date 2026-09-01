# MEGR 2156 Assignment 2 - Truss Stress

## 1. Truss Design

For this assignment, I designed a simple planar truss using A500 steel. I chose a load of:

**P = 25 kN**

The required dimensions were:

**a = 0.40 m**

**b = 0.30 m**

The final truss has five joints labeled A, B, C, D, and E.

- A = pin support
- B = roller support
- C = upward load
- D = downward load
- E = center joint

The top length is:

**BA = 1.20 m**

The bottom length is:

**CD = 0.40 m**

The height is:

**b = 0.30 m**

---

# 2. Truss Calculations

## 2a(i) Member Lengths

The two outside diagonal members are BC and DA.

Their horizontal distance is 0.40 m and their vertical distance is 0.30 m.

Using the Pythagorean theorem:

**L = √[(0.40)² + (0.30)²]**

**L = 0.50 m**

Therefore:

**L_BC = L_DA = 0.50 m**

The two inside diagonal members are CE and ED.

Their horizontal distance is 0.20 m and their vertical distance is 0.30 m.

**L = √[(0.20)² + (0.30)²]**

**L = 0.3606 m**

Therefore:

**L_CE = L_ED = 0.3606 m**

The top members are:

**L_BE = L_EA = 0.60 m**

The bottom member is:

**L_CD = 0.40 m**

The total member length is:

**L_total = 0.60 + 0.60 + 0.50 + 0.50 + 0.3606 + 0.3606 + 0.40**

**L_total = 3.3212 m**

---

## 2a(ii) Free Body Diagram and Reactions

The full truss free body diagram was drawn by hand.

The support reactions are:

- A_x
- A_y
- B_y

First:

**ΣF_x = 0**

There are no horizontal external forces, so:

**A_x = 0**

Now take moments about B:

**ΣM_B = 0**

**A_y(1.20) + P(0.40) - P(0.80) = 0**

**1.20A_y = 0.40P**

**A_y = P / 3**

Using:

**P = 25 kN**

**A_y = 25 / 3**

**A_y = 8.33 kN**

Now use vertical equilibrium:

**ΣF_y = 0**

**B_y + A_y + P - P = 0**

**B_y = -A_y**

**B_y = -8.33 kN**

The negative sign means the reaction at B acts downward.

---

## 2a(iii) Symbolic Internal Forces

The method of joints was used to solve the internal member forces.

### Joint B

For member BC:

**cosθ = 0.40 / 0.50 = 0.80**

**sinθ = 0.30 / 0.50 = 0.60**

Vertical equilibrium:

**-P / 3 - 0.60F_BC = 0**

**F_BC = -5P / 9**

BC is in compression.

Horizontal equilibrium:

**F_BE + 0.80F_BC = 0**

**F_BE = 4P / 9**

BE is in tension.

### Joint A

Vertical equilibrium:

**P / 3 - 0.60F_DA = 0**

**F_DA = 5P / 9**

DA is in tension.

Horizontal equilibrium:

**-F_EA - 0.80F_DA = 0**

**F_EA = -4P / 9**

EA is in compression.

### Joint C

For member CE:

**sinθ = 0.30 / 0.3606**

Vertical equilibrium gives:

**F_CE = -(2√13 / 9)P**

CE is in compression.

Horizontal equilibrium gives:

**F_CD = 0**

CD is a zero-force member.

### Joint D

Vertical equilibrium gives:

**F_ED = (2√13 / 9)P**

ED is in tension.

---

## 2a(iv) Numerical Internal Forces

Using:

**P = 25 kN**

the member forces are:

| Member | Force | Type |
|---|---:|---|
| BC | 13.89 kN | Compression |
| BE | 11.11 kN | Tension |
| CE | 20.03 kN | Compression |
| CD | 0 kN | Zero Force |
| ED | 20.03 kN | Tension |
| DA | 13.89 kN | Tension |
| EA | 11.11 kN | Compression |

The largest internal force is:

**F_max = 20.03 kN**

---

# 2b. Truss Member Sizing

## 2b(i) Knowns and Unknown

Known values:

**F_max = 20.03 kN**

**N = 3.5**

For A500 Grade B steel:

**S_y = 46 ksi**

The unknown is the minimum cross-sectional area:

**A_min = ?**

---

## 2b(ii) Symbolic Area Equation

Normal stress is:

**σ = F / A**

The allowable stress is:

**σ_allow = S_y / N**

Therefore:

**F / A = S_y / N**

Solving for area:

**A_min = (N × F) / S_y**

---

## 2b(iii) Numerical Area

Using:

**F = 20.03 kN**

**N = 3.5**

**S_y = 317 MPa**

The minimum area is:

**A_min = [(3.5)(20.03 × 10³)] / (317 × 10⁶)**

**A_min = 2.21 × 10⁻⁴ m²**

**A_min = 221 mm²**

This is approximately:

**A_min = 0.343 in²**

The final CAD model uses:

**1 in × 1 in × 0.125 in square tube**

The cross-sectional area is approximately:

**A = 1² - (0.75)²**

**A = 0.4375 in²**

Since:

**0.4375 > 0.343**

the selected tubing meets the required area.

---

## 2b(iv) Estimated Truss Weight

The selected cross-sectional area is:

**A = 0.4375 in²**

The total member length is:

**L = 3.3212 m**

Convert to inches:

**L = 130.76 in**

Volume:

**V = A × L**

**V = (0.4375)(130.76)**

**V = 57.21 in³**

Using steel density:

**ρ = 0.284 lb/in³**

Weight:

**W = ρ × V**

**W = (0.284)(57.21)**

**W_truss ≈ 16.25 lb**

---

# 3. Pin Design

The pins are made from hardened tool steel.

Given values:

**τ_y = 170 ksi**

**ρ = 0.278 lb/in³**

The required safety factor is:

**N = 4**

The pins are treated as single-shear connections.

---

## 3a(i) Knowns and Unknowns

Known values:

**V = 25 kN**

**N = 4**

**τ_y = 170 ksi**

Unknowns:

**A_pin = ?**

**d_pin = ?**

---

## 3a(ii) Critical Pin

The largest applied joint load is:

**P = 25 kN**

Therefore the C or D connection can be used as the critical pin.

The shear force on the critical pin is:

**V = 25 kN**

---

## 3a(iii) Symbolic Pin Area

Shear stress is:

**τ = V / A**

Allowable shear stress is:

**τ_allow = τ_y / N**

Set the actual shear stress equal to the allowable shear stress:

**V / A = τ_y / N**

Solving for area:

**A_pin = (N × V) / τ_y**

For a circular pin:

**A = πd² / 4**

Therefore:

**d_min = √[(4 × N × V) / (π × τ_y)]**

---

## 3a(iv) Numerical Pin Size

Convert 25 kN to pounds-force:

**25 kN ≈ 5620 lbf**

Minimum pin area:

**A_pin = (4 × 5620) / 170000**

**A_pin = 0.1322 in²**

Now solve for diameter:

**d = √[(4 × 0.1322) / π]**

**d_min = 0.410 in**

A standard 7/16 in pin was selected.

**d = 0.4375 in**

This is larger than the minimum required diameter.

---

## 3a(v) Pin Weight

Each pin has:

**d = 0.4375 in**

**L = 1.50 in**

Volume of one pin:

**V = (πd² / 4)L**

**V = [π(0.4375)² / 4](1.50)**

**V = 0.2255 in³**

Weight of one pin:

**W = 0.2255 × 0.278**

**W = 0.0627 lb**

There are five pins:

**W_total = 5 × 0.0627**

**W_pins = 0.313 lb**

---

# 4. CAD Model

The final CAD model was created using the dimensions and member sizes found from the calculations.

The truss uses:

**1 in × 1 in × 0.125 in square tube**

The pins use:

**7/16 in diameter**

and:

**1.50 in length**

All seven truss members use the same cross section. All five pins use the same geometry.

The CAD model includes:

- truss body
- five pins
- full truss with pins
- dimensioned drawing

---

## CAD and Hand Weight Comparison

The hand-calculated truss weight was approximately:

**W_hand,truss = 16.25 lb**

The calculated pin weight was:

**W_pins = 0.313 lb**

Total hand-calculated weight:

**W_hand,total = 16.25 + 0.313**

**W_hand,total = 16.56 lb**

The CAD model predicted approximately:

**W_CAD,total = 16.16 lb**

Percent difference:

**Percent Difference = |16.56 - 16.16| / 16.56 × 100**

**Percent Difference ≈ 2.4%**

The CAD weight is slightly lower because the CAD model removes material at the joints and pin holes. The hand calculation treats each member as if it keeps its full length and cross-sectional area.

---

# 5. Engineering Lessons Learned

One thing I learned from this assignment was that the member size should be calculated before choosing the final tubing size. At first I considered using 2 in × 2 in × 0.25 in tubing, but the calculations showed that this was much larger than needed. Using a smaller member reduced the weight while still meeting the required safety factor.

I also learned how important the support reactions are when solving a truss. The pin support at A and roller support at B behave differently, so the correct free body diagram had to be made before the internal forces could be found.

Another lesson was that CAD weight and hand-calculated weight will not always be exactly the same. The CAD model accounts for holes and joint geometry, while the hand calculation uses a simpler volume estimate. The final values were still very close.

I also learned that fully defining the SolidWorks sketch is important. When the sketch was not fully constrained, changing one dimension caused the shape to move. Once all the main dimensions were added, the model became much easier to work with.

---

# CAD Files

- Truss Body 
- Pins
- Finished Truss
- Dimensions
- FBD
- (all linked in the PDF)

**Total project time:**  
This project took me around 2 hours to finish. Solidworks being the Easiest as i use it every day at my job.
