MEGR 2156 — Assignment 8: Pulley System
Project: Belt-driven power transmission between two parallel shafts  
Course: MEGR 2156 — Sophomore Design  
Project status: Preliminary engineering analysis and CAD/build documentation; experimental results pending.
1. Objective
Design a two-pulley, open-belt drive system capable of transmitting power between two parallel shafts with a pulley center distance of 4–6 in, pulley diameters of 3 in, shaft speed of 1,000–2,000 rpm, stationary belt tension of 4–6 lbf, and minimum static design safety factor of 3.
1.1 Selected design specifications
Parameter	Value
Pulley 1 and 2 diameter, `D`	3.000 in (belt pitch diameter used in calculations)
Shaft center distance, `C`	5.000 in
Input speed, `N1`	1,500 rpm
Stationary belt tension per span, `T0`	5.000 lbf
Belt–pulley friction coefficient, `μ`	0.30
Belt material	Polyurethane elastomer
Belt tensile yield strength, `Sy,b`	471 psi (at 20% strain per assignment)
Selected round-belt diameter	0.250 in
Pulley material	6061-T6 aluminum
Shaft material	Hardened AISI 1060 steel
Shaft design yield strength, `Sy,s`	97,000 psi (material/heat-treatment condition to be verified)
Selected shaft diameter	0.375 in
Distance between bearings on each shaft, `Ls`	1.500 in
Bearing material	Oil-impregnated sintered bronze
Bearing length, `Lb`	0.500 in
Frame material	6061-T6 aluminum
Preliminary base plate	10 × 5 × 0.25 in
Minimum safety factor	3.0
Analysis conventions: Belt weight, centrifugal tension, speed-dependent friction, elastic creep, transient loads, groove wedging, and bearing frictional losses are outside the initial static sizing model. The belt-tension results therefore represent the limiting no-slip condition for the selected friction coefficient, rather than verified steady-state operating tension. The final purchased belt and pulley geometry must be checked for their real operating limits.
---
2. Belt and pulley design (25%)
2.1 Knowns and unknowns
Known: `D1 = D2 = 3.000 in`; `C = 5.000 in`; `N1 = 1500 rpm`; `T0 = 5.000 lbf`; `μ = 0.30`; `Sy,b = 471 psi`; required `FS = 3`.
Unknown: Tight-span tension `T1`, slack-span tension `T2`, allowable belt stress, required area, minimum belt diameter, belt loop length, shaft torque, belt speed, and transmitted power.
2.2 Free-body diagram — belt and pulleys
![Belt and pulley FBD](assets/belt_pulley_fbd.png)
The upper run is labeled the tight side (`T1`); the lower run is labeled the loose side (`T2`). Each pulley receives the sum of the belt-span forces directed toward the opposite pulley. The effective tangential drive force is the difference between the tensions, `T1 − T2`. The bearing load is approximately the sum, `T1 + T2`, for parallel belt spans.
2.3 Symbolic solution for tight-side and loose-side tensions
For a flat-belt friction model at impending slip:
$$\frac{T_1}{T_2}=e^{\mu\theta}$$
For equal-diameter pulleys, the wrap angle is:
$$\theta=\pi\ \mathrm{rad}$$
Set:
$$k=e^{\mu\pi}$$
The initial static belt tension gives:
$$T_0=\frac{T_1+T_2}{2} \quad\Rightarrow\quad T_1+T_2=2T_0$$
Since `T1 = k T2`:
$$kT_2+T_2=2T_0$$
$$\boxed{T_2=\frac{2T_0}{1+k}}$$
$$\boxed{T_1=\frac{2kT_0}{1+k}}$$
2.4 Numerical tension calculation
$$k=e^{0.30\pi}=2.56633$$
$$T_2=\frac{2(5.000)}{1+2.56633}=\boxed{2.8040\ \mathrm{lbf}}$$
$$T_1=10.000-2.8040=\boxed{7.1960\ \mathrm{lbf}}$$
Check:
$$T_1+T_2=7.1960+2.8040=10.000\ \mathrm{lbf}$$
2.5 Symbolic minimum belt area and diameter
Allowable tensile stress:
$$\sigma_{\mathrm{allow}}=\frac{S_{y,b}}{FS}$$
Normal tensile stress:
$$\sigma=\frac{T_1}{A}$$
Therefore:
$$A_{\min}=\frac{T_1}{\sigma_{\mathrm{allow}}}=\frac{FS,T_1}{S_{y,b}}$$
For a round belt:
$$A=\frac{\pi d_b^2}{4}$$
Solve for diameter:
$$\boxed{d_{b,\min}=\sqrt{\frac{4FS,T_1}{\pi S_{y,b}}}}$$
2.6 Numerical minimum belt diameter
$$\sigma_{\mathrm{allow}}=\frac{471}{3}=\boxed{157.0\ \mathrm{psi}}$$
$$A_{\min}=\frac{7.1960}{157.0}=\boxed{0.045834\ \mathrm{in^2}}$$
$$d_{b,\min}=\sqrt{\frac{4(0.045834)}{\pi}}=\boxed{0.24157\ \mathrm{in}}$$
Selected: `db = 0.250 in` (nominal 1/4-in round polyurethane belt).
Actual section area:
$$A_{\mathrm{actual}}=\frac{\pi(0.250)^2}{4}=\boxed{0.049087\ \mathrm{in^2}}$$
Tight-span normal stress:
$$\sigma_b=\frac{7.1960}{0.049087}=\boxed{146.60\ \mathrm{psi}}$$
Static tensile safety factor:
$$FS_b=\frac{471}{146.60}=\boxed{3.21}$$
Result: The nominal tension-only factor of safety is greater than 3. This is not a comprehensive belt life or bending-strain check. The specified 471-psi value corresponds to 20% strain, and belt stretch, pretension, pulley diameter compatibility, and product manufacturer ratings must be verified.
2.7 Belt loop length
For an open belt drive, measured along the belt centerline (pitch line):
$$L=2C+\frac{\pi}{2}(D_1+D_2)+\frac{(D_1-D_2)^2}{4C}$$
Because `D1 = D2 = D`:
$$L=2C+\pi D$$
$$L=2(5.000)+\pi(3.000)$$
$$\boxed{L=19.4248\ \mathrm{in}}$$
This is a geometric belt centerline circumference, not a verified McMaster product's ordered free length. Purchased belt length must be selected from its manufacturer sizing convention and installation-stretch guidance. The adjustable bearing mounts accommodate belt installation and tensioning.
2.8 Belt speed, torque, and ideal power
Equal pulley diameters give equal shaft speeds (neglecting slip):
$$N_1D_1=N_2D_2$$
$$N_2=\frac{N_1D_1}{D_2}=\frac{1500(3)}{3}=\boxed{1500\ \mathrm{rpm}}$$
Belt speed:
$$V_b=\frac{\pi DN}{12}=\frac{\pi(3)(1500)}{12}=\boxed{1178.10\ \mathrm{ft/min}}$$
Tangential driving force at the limiting friction condition:
$$F_t=T_1-T_2=7.1960-2.8040=\boxed{4.3920\ \mathrm{lbf}}$$
Torque:
$$M_t=F_t\frac{D}{2}=(4.3920)(1.500)=\boxed{6.5880\ \mathrm{lbf\cdot in}}$$
Ideal transmitted horsepower at this limit:
$$HP=\frac{M_tN}{63025}=\frac{(6.5880)(1500)}{63025}=\boxed{0.1568\ \mathrm{hp}}$$
$$P=0.1568(745.7)=\boxed{116.9\ \mathrm{W}}$$
Interpretation: These are friction-limited theoretical values, not measured test results or guaranteed continuous power rating.
---
3. Hardened-steel shaft analysis (25%)
3.1 Knowns and unknowns
Known: `D = 3.000 in`; `T1 + T2 = 10.000 lbf`; `Mt = 6.5880 lbf·in`; bearing-to-bearing span `Ls = 1.500 in`; shaft design yield strength `Sy,s = 97,000 psi`; required `FS = 3`.
Unknown: Bearing reactions `RA` and `RB`, peak bending moment, minimum shaft diameter, bending stress, torsional shear stress, combined von Mises stress, and shaft safety factor.
3.2 Free-body diagram — shaft
![Shaft FBD](assets/shaft_fbd.png)
A pulley is centered between supports `A` and `B`. The net transverse belt load of `10.0 lbf` acts through the pulley center. The shaft also transmits `6.588 lbf·in` of torque. The illustration depicts an isolated pulley shaft; actual support orientation in CAD may be horizontal or vertical as long as the load and reaction directions are consistent.
3.3 Symbolic shaft reaction calculation
Force balance:
$$\sum F_y=0: \quad R_A+R_B-F=0$$
Moment about bearing `A`:
$$\sum M_A=0: \quad R_BL_s-F\frac{L_s}{2}=0$$
Solve:
$$\boxed{R_B=\frac{F}{2}}$$
$$\boxed{R_A=F-R_B=\frac{F}{2}}$$
Numerically:
$$R_B=\frac{10.000}{2}=\boxed{5.000\ \mathrm{lbf}}$$
$$R_A=10.000-5.000=\boxed{5.000\ \mathrm{lbf}}$$
3.4 Maximum bending moment
The maximum bending moment is directly under the centered pulley:
$$M_{\max}=R_A\frac{L_s}{2}=\frac{FL_s}{4}$$
$$M_{\max}=\frac{10.000(1.500)}{4}=\boxed{3.750\ \mathrm{lbf\cdot in}}$$
3.5 Symbolic minimum shaft diameter
For a solid circular shaft:
$$\sigma_b=\frac{32M_{\max}}{\pi d_s^3}$$
$$\tau_t=\frac{16M_t}{\pi d_s^3}$$
Von Mises combined stress:
$$\sigma_{vm}=\sqrt{\sigma_b^2+3\tau_t^2}$$
Substitute both stress formulas:
$$\sigma_{vm}=\frac{\sqrt{(32M_{\max})^2+3(16M_t)^2}}{\pi d_s^3}$$
For the required factor of safety:
$$\sigma_{vm}\le\frac{S_{y,s}}{FS}$$
Rearrange:
$$\boxed{d_{s,\min}=\left[\frac{FS\sqrt{(32M_{\max})^2+3(16M_t)^2}}{\pi S_{y,s}}\right]^{1/3}}$$
3.6 Numerical shaft diameter
Allowable yield stress:
$$\sigma_{\mathrm{allow}}=\frac{97000}{3}=\boxed{32333.3\ \mathrm{psi}}$$
Substituting:
$$d_{s,\min}=\left[\frac{3\sqrt{(32\cdot3.750)^2+3(16\cdot6.5880)^2}}{\pi\cdot97000}\right]^{1/3}$$
$$\boxed{d_{s,\min}=0.12908\ \mathrm{in}}$$
Selected shaft: `ds = 0.375 in` (3/8 in).
3.7 Shaft stress and factor-of-safety verification
$$\sigma_b=\frac{32(3.750)}{\pi(0.375)^3}=\boxed{724.33\ \mathrm{psi}}$$
$$\tau_t=\frac{16(6.5880)}{\pi(0.375)^3}=\boxed{636.25\ \mathrm{psi}}$$
$$\sigma_{vm}=\sqrt{(724.33)^2+3(636.25)^2}=\boxed{1318.75\ \mathrm{psi}}$$
$$FS_s=\frac{97000}{1318.75}=\boxed{73.55}$$
Result: The nominal smooth-shaft static yield factor of safety exceeds 3. The very high computed factor indicates a conservatively sized shaft under these light loads; it does not establish resistance to keyway stress concentrations, pulley attachment failure, shaft deflection, fatigue, or misalignment. Check these features in the constructed assembly.
---
4. Journal bearing analysis (30%)
4.1 Knowns and unknowns
Known: Each shaft carries two bearings; centered shaft load `F = 10.000 lbf`; load per bearing `Fb = 5.000 lbf`; shaft diameter `ds = 0.375 in`; bearing length `Lb = 0.500 in`; shaft speed `N = 1500 rpm`.
Design screening limits for selected bronze bearing material:
Maximum bearing pressure: `Pallow = 2000 psi`.
Maximum surface speed: `Vallow = 1200 ft/min`.
Rated PV screening value: `PVallow = 50,000 psi·ft/min`.
More conservative sustained-use PV check: `PVconservative = 20,000 psi·ft/min`.
Unknown: Projected area, bearing pressure, shaft surface speed, PV rating, minimum length, and material suitability.
4.2 Free-body diagram — single bearing
![Journal bearing FBD](assets/bearing_fbd.png)
The bearing receives a `5.000 lbf` radial load from the shaft and transfers an equal and opposite force to the housing/frame. Bearing projected area is diameter multiplied by axial length, not the cylindrical curved surface area.
4.3 Bearing pressure
$$A_p=d_sL_b$$
$$A_p=(0.375)(0.500)=\boxed{0.1875\ \mathrm{in^2}}$$
$$P=\frac{F_b}{A_p}=\frac{F_b}{d_sL_b}$$
$$P=\frac{5.000}{0.1875}=\boxed{26.667\ \mathrm{psi}}$$
Pressure check:
$$26.667<2000\ \mathrm{psi}\quad\checkmark$$
4.4 Surface velocity
$$V=\frac{\pi d_sN}{12}$$
$$V=\frac{\pi(0.375)(1500)}{12}=\boxed{147.262\ \mathrm{ft/min}}$$
Speed check:
$$147.262<1200\ \mathrm{ft/min}\quad\checkmark$$
4.5 PV product
$$PV=P\times V$$
$$PV=(26.667)(147.262)=\boxed{3927.0\ \mathrm{psi\cdot ft/min}}$$
Check against the sustained-use screening value:
$$3927.0<20000\ \mathrm{psi\cdot ft/min}\quad\checkmark$$
4.6 Minimum bearing length
Substitute `P = Fb/(ds Lb)` and `V = π ds N/12` into `PV = P V`:
$$PV=\left(\frac{F_b}{d_sL_b}\right)\left(\frac{\pi d_sN}{12}\right)$$
Cancel shaft diameter:
$$PV=\frac{\pi F_bN}{12L_b}$$
Solve for the minimum length:
$$\boxed{L_{b,\min}=\frac{\pi F_bN}{12PV_{\mathrm{allow}}}}$$
Use the sustained-use screening limit:
$$L_{b,\min}=\frac{\pi(5.000)(1500)}{12(20000)}=\boxed{0.09817\ \mathrm{in}}$$
Selected bearing: 3/8-in bore × 1/2-in axial length oil-impregnated sintered-bronze sleeve bearing. Outside diameter, fit, clearance, lubricant compatibility, and actual operating limits are to be matched to the purchased part's datasheet.
---
5. Frame and CAD design (15%)
5.1 Concept geometry
Base: `10 in × 5 in × 0.25 in` aluminum 6061-T6 plate.
Shafts: parallel and `5.00 in` apart at the design belt tension.
Pulleys: 3.00-in nominal pitch diameter, coplanar to prevent belt tracking problems.
Bearing arrangement: two supports per shaft, with the pulley centered between support centers `1.50 in` apart.
Drive shaft: fixed in position.
Driven shaft: two bearing supports adjusted together using slotted mounting holes.
Belt guards: cover rotating pulley rims, belt runs, and pinch points for powered testing.
5.2 Frame loads
The approximately horizontal resultant pulley load is:
$$F_{\mathrm{pulley}}=T_1+T_2=7.1960+2.8040=\boxed{10.000\ \mathrm{lbf}}$$
For a centered pulley between two supports:
$$R_A=R_B=\frac{10.000}{2}=\boxed{5.000\ \mathrm{lbf}}$$
The belt pulls the two shafts toward each other. The frame must resist these opposing loads while keeping the shaft axes parallel. A local support that carries one bearing must resist `5.0 lbf` radial bearing reaction at the selected operating load model.
5.3 Frame design process
Create the base plate and set the shaft centerlines 5.00 in apart.
Model four bearing supports with aligned cylindrical bores.
Set bearing-center spacing on each shaft to 1.50 in.
Create 3-in pitch-diameter pulleys with a round-belt-compatible groove, 3/8-in bores, and suitable hubs/shaft attachments.
Model two 3/8-in steel shafts; finalize length based on bearings, collars, motor coupling, and guard clearance.
Use slots and shared alignment hardware to move the driven shaft supports together for belt tension adjustment.
Verify clearances between belt, pulleys, frame, and mounting fasteners.
Check pulley-hub fastening, shaft axial retention, bearing mounting, and frame stiffness prior to power-on testing.
Frame verification still required: Exact support shape, fasteners, mounting slot edge distances, bending stress, deflection, motor mount, and guard design depend on CAD dimensions and chosen hardware. They cannot be verified from the base-plate dimensions alone.
---
6. Design challenges, troubleshooting, and corrections
The following are design challenges to check and document. Mark each issue as encountered only when observed during CAD, assembly, or testing; replace the blank observation fields with your actual findings.
Design or build issue	Why it matters	Correction / verification step	Actual observation
Belt slips under load	Available friction may be insufficient for transmitted torque	Measure static tension, inspect groove cleanliness, align shafts, reduce load if necessary	To be recorded
Belt too loose or too tight	Insufficient tension causes slip; excessive tension loads bearings and stretches belt	Use driven-shaft slots to adjust tension evenly; record measured pretension	To be recorded
Pulley axes not aligned	Causes tracking error, wear, and vibration	Align pulley faces and shaft axes with straightedge/caliper; verify under slow rotation	To be recorded
Shaft fits tightly or binds in bronze bearing	Incorrect bore fit or misalignment increases heat/friction	Check selected bearing fit and shaft finish; align bearing housings before tightening	To be recorded
Pulley slips on steel shaft	Hub connection may fail before the shaft yields	Provide a suitable clamping hub, key, or manufacturer-rated shaft attachment	To be recorded
Vibration during operation	Eccentricity, unbalanced pulley, loose hardware, or belt joint can excite motion	Check runout, fastener tightness, belt joint, and frame rigidity	To be recorded
Measured rpm differs from target	Drive slip, motor speed variations, or loading change output rpm	Measure input/output rpm with tachometer and compare with 1:1 ideal speed ratio	To be recorded
6.1 Problem-description paragraph for the portfolio
The main design challenges involve coordinating belt geometry, shaft alignment, pulley attachment, and adjustable tensioning. Selecting a belt based on tensile area alone is not sufficient, because slip resistance also depends on the tension ratio and contact friction. The shaft support layout must keep both pulleys coplanar, and the driven shaft requires a tensioning adjustment without changing its orientation. The bearing bores and mounting locations require accurate alignment to avoid binding and unnecessary friction. During fabrication and testing, observed fit problems, slipping, noise, vibration, and changes in speed will be documented along with the corrective action and retest outcome.
---
7. Final test plan and measurement record
No experimental measurements have yet been provided. The table separates calculated design values from fields that must be populated by actual tests. Do not report predicted values as observed measurements.
7.1 Setup and safety
Confirm motor, electrical connection, guards, and emergency shutoff are appropriate for the test.
Lock down the frame and verify no belt or pulley contacts the structure.
Measure pulley diameters, shaft spacing, and initial belt pretension with power off.
Run at low speed first; observe vibration, tracking, and unusual noise from a safe position behind the guards.
Increase speed toward 1500 rpm only if all components operate normally.
Use a tachometer to measure both shaft speeds; use suitable instrumentation for belt force and output torque if available.
Stop and disconnect power before making tension or alignment adjustments.
7.2 Results and expected targets
Parameter	Calculated / selected target	Actual measured value	Instrument / method
Driving pulley pitch diameter	3.000 in	Pending	Caliper / pulley drawing
Driven pulley pitch diameter	3.000 in	Pending	Caliper / pulley drawing
Shaft center distance	5.000 in	Pending	Caliper / tape
Initial static belt tension per span	5.000 lbf	Pending	Calibrated belt-tension method
Input shaft speed	1500 rpm	Pending	Tachometer
Output shaft speed (no slip)	1500 rpm	Pending	Tachometer
Nominal speed ratio	1.000	Pending	Calculated from measured speeds
Limiting no-slip tight-side force	7.196 lbf	Not directly measured	Belt force instrument if used
Limiting no-slip loose-side force	2.804 lbf	Not directly measured	Belt force instrument if used
Theoretical limiting torque	6.588 lbf·in	Pending, if torque-tested	Torque sensor / brake test
Theoretical friction-limited power	0.1568 hp	Pending, if power-tested	Torque and rpm
Bearing temperature	No calculated target	Pending	Contact thermometer
Slipping, belt tracking, vibration	Stable/no visible slip	Pending	Inspection and measurements
7.3 Processing test results
If actual test speeds are `N1,test` and `N2,test`, compute output-speed deviation from ideal 1:1 operation:
$$%\ \mathrm{speed\ deviation}=100\left|\frac{N_{1,\mathrm{test}}-N_{2,\mathrm{test}}}{N_{1,\mathrm{test}}}\right|$$
If measured shaft output torque and rpm are available:
$$HP_{\mathrm{out}}=\frac{M_{\mathrm{out}}(\mathrm{lbf\cdot in}),N_{2,\mathrm{test}}(\mathrm{rpm})}{63025}$$
For measured input and output torque:
$$\eta=\frac{M_{\mathrm{out}}N_{2,\mathrm{test}}}{M_{\mathrm{in}}N_{1,\mathrm{test}}}\times100%$$
Experimental conclusion placeholder: The assembled pulley system was tested at _____ rpm on _____ (date). The measured output speed was _____ rpm, corresponding to _____% speed deviation. Belt tracking was _____, bearing temperatures were _____, and the main corrective action was _____. Based on these measurements, the system _____ (did / did not) meet its tested performance criteria.
---
8. Engineering lessons learned (5%)
Friction governs torque transmission. The tight-to-loose tension ratio depends on the belt/pulley interface and wrap angle. Tensile stress alone cannot establish whether the drive will transmit the desired torque without slipping.
Nominal shaft strength is not the whole design. Even a shaft with a very high smooth-section factor of safety needs a properly secured hub, sufficient stiffness, and correctly aligned bearings.
PV is a combined bearing selection check. The surface velocity and projected pressure must be examined together to screen possible porous-metal bearing materials.
Frame geometry affects drive reliability. Adjustable supports must change center distance without rotating a shaft out of parallel or moving the pulleys out of their common plane.
Testing verifies analytical predictions. Measured tension, input/output rpm, temperature, and motion quality determine whether simplified calculations represent the physical prototype.
---
9. Project photo and time log
Date	Activity / revision	Photo or CAD screenshot	Actual elapsed time
Pending	Concept sketch and FBDs	Add image	Record time
Pending	Belt and shaft calculations	Add image	Record time
Pending	Bearing selection and frame CAD	Add image	Record time
Pending	Fabrication and first assembly	Add image	Record time
Pending	Adjustments and final tests	Add image	Record time
	Total recorded hours		Pending
Required images: Concept sketch, belt/pulley FBD, shaft FBD, bearing FBD, part CAD screenshots, full CAD assembly, fabricated components, test setup, and final build.
---
10. Final calculation summary
Quantity	Result
Belt wrap angle	180°
Maximum tight/loose tension ratio	2.5663
Tight-side tension	7.1960 lbf
Loose-side tension	2.8040 lbf
Minimum belt cross section	0.045834 in²
Minimum round-belt diameter	0.24157 in
Selected belt diameter	0.250 in
Nominal tensile safety factor	3.21
Geometric belt centerline length	19.4248 in
Ideal belt speed	1178.10 ft/min
Maximum ideal tangential drive force	4.3920 lbf
Theoretical limiting torque	6.5880 lbf·in
Theoretical limiting ideal power	0.1568 hp
Load per shaft	10.000 lbf
Load per bearing	5.000 lbf
Maximum shaft bending moment	3.750 lbf·in
Minimum smooth shaft diameter	0.12908 in
Selected shaft diameter	0.375 in
Shaft bending stress	724.33 psi
Shaft torsional shear stress	636.25 psi
Shaft equivalent von Mises stress	1318.75 psi
Nominal static shaft safety factor	73.55
Bearing projected area	0.1875 in²
Bearing pressure	26.667 psi
Bearing sliding speed	147.262 ft/min
Bearing PV	3927.0 psi·ft/min
Minimum bearing length at PV 20,000	0.09817 in
Selected bearing length	0.500 in
11. References and design validation
MEGR 2156 Assignment 8: Pulley System, instructor-provided assignment description, design requirements, polyurethane belt yield strength, and required calculations.
McMaster-Carr: Round Belts — supplier catalog for matching diameter, joining method, and length designation.
D. J. Dunn, Solid Mechanics — Dynamics: Tutorial — Pulley Drive Systems — course-provided reading.
Machinery's Handbook, bearing PV and porous-metal bearing reference, p. 2440 as assigned — confirm edition and exact material ratings.
AISI 1060 steel — purchase a known hardened/tempered grade and verify the actual heat-treatment yield value from the supplier's datasheet.
Next design checks before fabrication: Actual polyurethane belt rated diameter/smallest pulley, recommended installation tension and free loop length, pulley groove shape and pitch diameter, real friction at the operating speed, shaft-to-hub torque capacity, shaft deflection and stress risers, bearing manufacturer PV and fit limits, frame-support strength, and complete rotating-parts guarding.
