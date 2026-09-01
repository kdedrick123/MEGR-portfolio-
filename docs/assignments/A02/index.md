# MEGR 2156 Assignment 2 - Truss Stress

## 1. Truss Design

For this assignment, I designed a simple planar truss using A500 steel. I chose a load of:

$$
P=25\text{ kN}
$$

The required dimensions were:

$$
a=0.40\text{ m}
$$

$$
b=0.30\text{ m}
$$

The final truss has five joints labeled A, B, C, D, and E.

- A = pin support
- B = roller support
- C = upward load
- D = downward load
- E = center joint

The top length is:

$$
BA=1.20\text{ m}
$$

The bottom length is:

$$
CD=0.40\text{ m}
$$

The height is:

$$
b=0.30\text{ m}
$$

---

# 2. Truss Calculations

## 2a(i) Member Lengths

The two outside diagonal members are BC and DA.

Their horizontal distance is 0.40 m and their vertical distance is 0.30 m.

Using the Pythagorean theorem:

$$
L=\sqrt{(0.40)^2+(0.30)^2}
$$

$$
L=0.50\text{ m}
$$

Therefore:

$$
\boxed{L_{BC}=L_{DA}=0.50\text{ m}}
$$

The two inside diagonal members are CE and ED.

Their horizontal distance is 0.20 m and their vertical distance is 0.30 m.

$$
L=\sqrt{(0.20)^2+(0.30)^2}
$$

$$
L=0.3606\text{ m}
$$

Therefore:

$$
\boxed{L_{CE}=L_{ED}=0.3606\text{ m}}
$$

The top members are:

$$
L_{BE}=L_{EA}=0.60\text{ m}
$$

The bottom member is:

$$
L_{CD}=0.40\text{ m}
$$

The total member length is:

$$
L_{total}
=
0.60+0.60+0.50+0.50+0.3606+0.3606+0.40
$$

$$
\boxed{L_{total}=3.3212\text{ m}}
$$

---

## 2a(ii) Free Body Diagram and Reactions

The full truss free body diagram was drawn by hand.

The support reactions are:

- $A_x$
- $A_y$
- $B_y$

First:

$$
\sum F_x=0
$$

There are no horizontal external forces, so:

$$
\boxed{A_x=0}
$$

Now take moments about B:

$$
\sum M_B=0
$$

$$
A_y(1.20)+P(0.40)-P(0.80)=0
$$

$$
1.20A_y=0.40P
$$

$$
A_y=\frac{P}{3}
$$

Using:

$$
P=25\text{ kN}
$$

$$
A_y=\frac{25}{3}
$$

$$
\boxed{A_y=8.33\text{ kN}}
$$

Now use vertical equilibrium:

$$
\sum F_y=0
$$

$$
B_y+A_y+P-P=0
$$

$$
B_y=-A_y
$$

$$
\boxed{B_y=-8.33\text{ kN}}
$$

The negative sign means the reaction at B acts downward.

---

## 2a(iii) Symbolic Internal Forces

The method of joints was used to solve the internal member forces.

### Joint B

For member BC:

$$
\cos\theta=\frac{0.40}{0.50}=0.80
$$

$$
\sin\theta=\frac{0.30}{0.50}=0.60
$$

Vertical equilibrium:

$$
-\frac{P}{3}-0.60F_{BC}=0
$$

$$
\boxed{F_{BC}=-\frac{5P}{9}}
$$

BC is in compression.

Horizontal equilibrium:

$$
F_{BE}+0.80F_{BC}=0
$$

$$
\boxed{F_{BE}=\frac{4P}{9}}
$$

BE is in tension.

### Joint A

Vertical equilibrium:

$$
\frac{P}{3}-0.60F_{DA}=0
$$

$$
\boxed{F_{DA}=\frac{5P}{9}}
$$

DA is in tension.

Horizontal equilibrium:

$$
-F_{EA}-0.80F_{DA}=0
$$

$$
\boxed{F_{EA}=-\frac{4P}{9}}
$$

EA is in compression.

### Joint C

For member CE:

$$
\sin\theta=\frac{0.30}{0.3606}
$$

Vertical equilibrium gives:

$$
\boxed{
F_{CE}
=
-\frac{2\sqrt{13}}{9}P
}
$$

CE is in compression.

Horizontal equilibrium gives:

$$
\boxed{F_{CD}=0}
$$

CD is a zero-force member.

### Joint D

Vertical equilibrium gives:

$$
\boxed{
F_{ED}
=
\frac{2\sqrt{13}}{9}P
}
$$

ED is in tension.

---

## 2a(iv) Numerical Internal Forces

Using:

$$
P=25\text{ kN}
$$

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

$$
\boxed{F_{max}=20.03\text{ kN}}
$$

---

# 2b. Truss Member Sizing

## 2b(i) Knowns and Unknown

Known values:

$$
F_{max}=20.03\text{ kN}
$$

$$
N=3.5
$$

For A500 Grade B steel:

$$
S_y=46\text{ ksi}
$$

The unknown is the minimum cross-sectional area:

$$
A_{min}=?
$$

---

## 2b(ii) Symbolic Area Equation

Normal stress is:

$$
\sigma=\frac{F}{A}
$$

The allowable stress is:

$$
\sigma_{allow}=\frac{S_y}{N}
$$

Therefore:

$$
\frac{F}{A}
=
\frac{S_y}{N}
$$

Solving for area:

$$
\boxed{
A_{min}
=
\frac{NF}{S_y}
}
$$

---

## 2b(iii) Numerical Area

Using:

$$
F=20.03\text{ kN}
$$

$$
N=3.5
$$

$$
S_y=317\text{ MPa}
$$

$$
A_{min}
=
\frac{(3.5)(20.03\times10^3)}
{317\times10^6}
$$

$$
A_{min}
=
2.21\times10^{-4}\text{ m}^2
$$

$$
\boxed{
A_{min}=221\text{ mm}^2
}
$$

This is approximately:

$$
\boxed{
A_{min}=0.343\text{ in}^2
}
$$

The final CAD model uses:

$$
1\text{ in}\times1\text{ in}\times0.125\text{ in square tube}
$$

The cross-sectional area is approximately:

$$
A
=
1^2-(0.75)^2
$$

$$
A=0.4375\text{ in}^2
$$

Since:

$$
0.4375>0.343
$$

the selected tubing meets the required area.

---

## 2b(iv) Estimated Truss Weight

The selected cross-sectional area is:

$$
A=0.4375\text{ in}^2
$$

The total member length is:

$$
L=3.3212\text{ m}
$$

Convert to inches:

$$
L=130.76\text{ in}
$$

Volume:

$$
V=AL
$$

$$
V=(0.4375)(130.76)
$$

$$
V=57.21\text{ in}^3
$$

Using steel density:

$$
\rho=0.284\text{ lb/in}^3
$$

Weight:

$$
W=\rho V
$$

$$
W=(0.284)(57.21)
$$

$$
\boxed{
W_{truss}\approx16.25\text{ lb}
}
$$

---

# 3. Pin Design

The pins are made from hardened tool steel.

Given values:

$$
\tau_y=170\text{ ksi}
$$

$$
\rho=0.278\text{ lb/in}^3
$$

The required safety factor is:

$$
N=4
$$

The pins are treated as single-shear connections.

---

## 3a(i) Knowns and Unknowns

Known values:

$$
V=25\text{ kN}
$$

$$
N=4
$$

$$
\tau_y=170\text{ ksi}
$$

Unknowns:

$$
A_{pin}=?
$$

$$
d_{pin}=?
$$

---

## 3a(ii) Critical Pin

The largest applied joint load is:

$$
P=25\text{ kN}
$$

Therefore the C or D connection can be used as the critical pin.

The shear force on the critical pin is:

$$
\boxed{
V=25\text{ kN}
}
$$

---

## 3a(iii) Symbolic Pin Area

Shear stress is:

$$
\tau=\frac{V}{A}
$$

Allowable shear stress is:

$$
\tau_{allow}=\frac{\tau_y}{N}
$$

Therefore:

$$
\frac{V}{A}
=
\frac{\tau_y}{N}
$$

Solving for area:

$$
\boxed{
A_{pin}
=
\frac{NV}{\tau_y}
}
$$

For a circular pin:

$$
A=\frac{\pi d^2}{4}
$$

Therefore:

$$
\boxed{
d
=
\sqrt{
\frac{4NV}
{\pi\tau_y}
}
}
$$

---

## 3a(iv) Numerical Pin Size

Convert 25 kN to pounds-force:

$$
25\text{ kN}\approx5620\text{ lbf}
$$

Minimum area:

$$
A_{pin}
=
\frac{(4)(5620)}
{170000}
$$

$$
\boxed{
A_{pin}=0.1322\text{ in}^2
}
$$

Now solve for diameter:

$$
d
=
\sqrt{
\frac{4(0.1322)}
{\pi}
}
$$

$$
\boxed{
d_{min}=0.410\text{ in}
}
$$

A standard 7/16 in pin was selected.

$$
\boxed{
d=0.4375\text{ in}
}
$$

This is larger than the minimum required diameter.

---

## 3a(v) Pin Weight

Each pin has:

$$
d=0.4375\text{ in}
$$

$$
L=1.50\text{ in}
$$

Volume of one pin:

$$
V
=
\frac{\pi d^2}{4}L
$$

$$
V
=
\frac{\pi(0.4375)^2}{4}(1.50)
$$

$$
V=0.2255\text{ in}^3
$$

Weight of one pin:

$$
W=(0.2255)(0.278)
$$

$$
W=0.0627\text{ lb}
$$

There are five pins:

$$
W_{total}
=
5(0.0627)
$$

$$
\boxed{
W_{pins}=0.313\text{ lb}
}
$$

---

# 4. CAD Model

The final CAD model was created using the dimensions and member sizes found from the calculations.

The truss uses:

$$
1\times1\times0.125\text{ in square tube}
$$

The pins use:

$$
7/16\text{ in diameter}
$$

and:

$$
1.50\text{ in length}
$$

All seven truss members use the same cross section. All five pins use the same geometry.

The CAD model includes:

- truss body
- five pins
- full truss with pins
- dimensioned drawing

---

## CAD and Hand Weight Comparison

The hand-calculated truss weight was approximately:

$$
W_{hand,truss}=16.25\text{ lb}
$$

The calculated pin weight was:

$$
W_{pins}=0.313\text{ lb}
$$

Total hand-calculated weight:

$$
W_{hand,total}
=
16.25+0.313
$$

$$
\boxed{
W_{hand,total}=16.56\text{ lb}
}
$$

The CAD model predicted approximately:

$$
\boxed{
W_{CAD,total}=16.16\text{ lb}
}
$$

Percent difference:

$$
\%\text{ Difference}
=
\frac{|16.56-16.16|}
{16.56}(100)
$$

$$
\boxed{
\%\text{ Difference}\approx2.4\%
}
$$

The CAD weight is slightly lower because the CAD model removes material at the joints and pin holes. The hand calculation treats each member as if it keeps its full length and cross-sectional area.

---

# 5. Engineering Lessons Learned

One thing I learned from this assignment was that the member size should be calculated before choosing the final tubing size. At first I considered using 2 in x 2 in x 0.25 in tubing, but the calculations showed that this was much larger than needed. Using a smaller member reduced the weight while still meeting the required safety factor.

I also learned how important the support reactions are when solving a truss. The pin support at A and roller support at B behave differently, so the correct free body diagram had to be made before the internal forces could be found.

Another lesson was that CAD weight and hand-calculated weight will not always be exactly the same. The CAD model accounts for holes and overlapping joint geometry, while the hand calculation uses a simpler volume estimate. The final values were still very close.

I also learned that fully defining the SolidWorks sketch is important. When the sketch was not fully constrained, changing one dimension caused the shape to move. Once all the main dimensions were added, the model became much easier to work with.

---

# CAD Files

- `[Truss Body STEP](ADD LINK HERE)`
- `[Pins STEP](ADD LINK HERE)`
- `[Complete Truss STEP](ADD LINK HERE)`
- `[Dimensioned Drawing PDF](ADD LINK HERE)`

**Total project time:**  
`ADD YOUR ACTUAL TIME HERE`
