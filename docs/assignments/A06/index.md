## Strength-Driven CAD Equation

The rear web thickness was controlled by the bending-stress equation below.

**Bending stress equation:**

σ = (6 × F × e) / (b × t²)

Solving the equation for the required web thickness gives:

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

## Linkage Equation

The linkage overall length was controlled by the hole-center spacing and the outside width.

L_link = Hole Center Distance + Outside Width

L_link = 2.000 in + 1.500 in

L_link = 3.500 in
