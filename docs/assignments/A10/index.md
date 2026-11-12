# A10: Lead Screw Design

**Kaleb Dedrick**  
**Sophomore Design — Part 1**  
**Project:** Bench-top dual-lead-screw tensile tester

## Project overview

For this assignment, I developed a concept for a bench-top tensile tester using two lead screws to move a crosshead and apply an axial pulling force to a test specimen. The target is a total load of **2 kN** and a crosshead speed of **1–50 mm/min**. I used hand calculations, component research, CAD models, and reference FEA studies to evaluate the design. The machine is intended to operate mechanically, without electronic control software.

![General concept for a two-lead-screw tensile tester](Screenshot%202026-11-11%20230228.png)

*Figure 1. General concept for a two-lead-screw tensile tester.*

## Design requirements

| Requirement | Design target |
|---|---|
| Maximum tensile load | 2,000 N total |
| Lead screws | Two identical screws |
| Crosshead speed | 1–50 mm/min |
| Minimum lead screw length | 18 in |
| Required design factor of safety | 4 |
| Maximum crosshead deflection | 1 mm |
| System | Mechanical, bench-top |

## Overall machine layout

The two lead screws sit on opposite sides of the crosshead. Each screw engages a matching nut, and the crosshead moves when the screws rotate together. The specimen is intended to be gripped near the center so the applied tensile load stays aligned. An aluminum T-slot frame provides support. A mechanical linkage would be needed to keep the screws synchronized.

![Reference CAD frame and crosshead layout](Screenshot%202026-11-11%20230314.png)

*Figure 2. Reference CAD frame and crosshead layout.*

## 1. Lead screw sizing

### Knowns and unknowns

| Known quantity | Value |
|---|---|
| Total axial load | 2,000 N |
| Number of screws | 2 |
| Assumed axial force per screw | 1,000 N |
| Safety factor | 4 |
| Initial reference material | 1018 carbon steel |
| Screw length | At least 18 in (457.2 mm) |

**Unknowns:** minimum screw root diameter, buckling resistance, and suitable standard screw diameter.

### Axial stress calculation

I began with axial stress acting over the screw's root area:

$$\sigma=\frac{F_s}{A},\qquad A=\frac{\pi d^2}{4}$$

For a required safety factor of `N = 4`, the diameter relationship is:

$$d_{\min}=\sqrt{\frac{4NF_s}{\pi S_y}}$$

The reference 1018-steel calculation gives an initial diameter of approximately **3.71 mm** based on its assumed material yield strength. This only checks axial yielding, not buckling or the actual Acme screw's minor diameter.

![Reference axial stress calculation](Screenshot%202026-11-11%20230320.png)

*Figure 3. Reference axial stress calculation.*

### Buckling check

Because the screws are relatively long, I also considered Euler buckling where compressive loading may occur:

$$P_{cr}=\frac{\pi^2EI}{(KL)^2},\qquad I=\frac{\pi d^4}{64}$$

The preliminary reference calculation used `K = 2` and gave a required diameter of approximately **9.67 mm**. In the conventional column model, `K = 2` represents a fixed-free condition, so the actual end supports need to be verified. I selected a nominal **1/2-inch Acme lead screw** for the initial concept.

![Reference buckling diameter calculation](Screenshot%202026-11-11%20230325.png)

*Figure 4. Reference buckling diameter calculation.*

## 2. Lead screw rotational speed

The 1/2–10 single-start Acme thread has ten threads per inch. The lead is therefore:

$$L=\frac{1}{10}\text{ in/rev}=0.100\text{ in/rev}=2.54\text{ mm/rev}$$

Screw rotational speed is the linear crosshead speed divided by lead:

$$n=\frac{v}{L}$$

At the minimum crosshead speed:

$$n_{\min}=\frac{1}{2.54}=\boxed{0.394\text{ rpm}}$$

At the maximum crosshead speed:

$$n_{\max}=\frac{50}{2.54}=\boxed{19.685\text{ rpm}}$$

Each synchronized screw therefore needs to rotate at approximately **0.39–19.69 rpm**.

![Reference lead screw speed calculations](Screenshot%202026-11-11%20230331.png)

*Figure 5. Reference lead screw speed calculations.*

## 3. Drive torque estimate

For a preliminary torque estimate I used an assumed **25% efficiency** for an Acme screw and bronze nut. With equal load sharing, each screw carries 1,000 N:

$$T=\frac{F_sL}{2\pi\eta}$$

$$T=\frac{(1{,}000)(0.00254)}{2\pi(0.25)}=\boxed{1.62\text{ N}\cdot\text{m per screw}}$$

The combined idealized torque is approximately **3.23 N·m**, before losses in the bearings, coupling, and drive system. Real torque must be checked using the selected components.

![Reference screw torque equation](Screenshot%202026-11-11%20230336.png)

*Figure 6. Reference screw torque equation.*

## 4. Lead screw, nut, and flange selection

My working concept uses a 1/2–10 Acme screw with a compatible bronze nut and flange. A matching thread form is important because the nut transfers the lead screw's motion to the crosshead. The final product selection needs to match the CAD model's part number, screw root geometry, and flange mounting holes.

![Example 1018-steel Acme screw listing from the reference report](Screenshot%202026-11-11%20230341.png)

*Figure 7. Example 1018-steel Acme screw listing from the reference report.*

![Reference bronze nut](Screenshot%202026-11-11%20230345.png)

*Figure 8. Reference bronze nut.*

![Reference nut-mounting flange](Screenshot%202026-11-11%20230349.png)

*Figure 9. Reference nut-mounting flange.*

### Nut thread engagement

I considered thread bending and bearing pressure when checking the bronze nut. The reference engagement estimate is about **0.20 in**, after increasing a preliminary result to provide extra engagement. The actual nut material, engaged thread count, and manufacturer dimensions still need verification before this is considered a final strength check.

![Reference bronze-nut thread bending work](Screenshot%202026-11-11%20230354.png)

*Figure 10. Reference bronze-nut thread bending work.*

## 5. Crosshead design

The reference crosshead is about **9 in long**, **3 in wide**, and approximately **0.985 in thick**. The model uses aluminum and has two lead screw/nut locations with a center opening for the specimen gripping arrangement. These are reference dimensions; I would check them against the final SolidWorks model.

### Bending stress

For a simplified beam with a central point load:

$$M_{max}\approx\frac{FL}{4},\qquad \sigma_{max}=\frac{Mc}{I},\qquad I=\frac{bh^3}{12}$$

### Deflection

For the same simply supported beam approximation:

$$\delta_{max}\approx\frac{FL^3}{48EI}$$

I used these relationships to understand how crosshead dimensions affect stress and deflection. The real attachment holes and flanges can change the results, so a final beam calculation and SolidWorks simulation should use the exact CAD dimensions. The assignment's deflection limit is **1 mm**.

![Crosshead CAD reference showing screw mounting and specimen openings](Screenshot%202026-11-11%20230359.png)

*Figure 14. Crosshead CAD reference showing screw mounting and specimen openings.*

## 6. CAD assembly and supporting parts

The assembly includes the lead screws, nuts, crosshead, and T-slot aluminum frame. The screw axes need to remain parallel, the nuts must be firmly attached to the crosshead, and the frame needs enough room for gripping and specimen travel.

![T-slot frame extrusion reference](Screenshot%202026-11-11%20230403.png)

*Figure 15. T-slot frame extrusion reference.*

![Crosshead mounted around the two lead screws](Screenshot%202026-11-11%20230407.png)

*Figure 16. Crosshead mounted around the two lead screws.*

![Bottom view of nut/flange connections](Screenshot%202026-11-11%20230411.png)

*Figure 17. Bottom view of nut/flange connections.*

### Bearings and screw supports

The axial screw load should pass through thrust-bearing supports into the frame. The screw support brackets can mount to aluminum extrusions with T-slot fasteners, while the remaining bearing support keeps each screw aligned. The bearing seats and shaft ends have to match the real purchased parts.

### Screw synchronization

Since both screws must travel at the same rate, I considered a common mechanical linkage using matching gears, sprockets/chain, or pulleys/timing belt. The coupling needs equal ratios and enough input torque for both screws. This is a proposed mechanical detail, not a verified final transmission model.

### Fasteners and flange mounting

The nut/flange interfaces must have adequate bolt engagement and edge clearance. Bolt selection depends on the actual flange hole pattern, crosshead thickness, and load direction. Final bolt lengths should be determined from the CAD stack-up rather than copied from another example.

### Safety and alignment

The specimen load should be centered to reduce bending. A practical machine should include travel limits, accessible grips, and guards for exposed rotating parts.

![Reference bearing bracket and T-slot mounting](Screenshot%202026-11-11%20230446.png)

*Figure 24. Reference bearing bracket and T-slot mounting.*

![Alternative frame layout used as an assembly reference](Screenshot%202026-11-11%20230452.png)

*Figure 25. Alternative frame layout used as an assembly reference.*

## 7. FEA reference and crosshead optimization

The A10 report includes results from a **reference FEA study**, not a completed independent verification of my final CAD assembly. The study applies a **2,000 N** load near the center of an aluminum 6061 crosshead and restrains the screw/nut mounting regions. It compares an initial crosshead to an example with added curved support features.

| Reference configuration | Max. von Mises stress | Max. deflection | Reported safety factor |
|---|---:|---:|---:|
| Initial, coarse mesh | 15.31 MPa | 0.003619 mm | 3.6 |
| Initial, fine mesh | 17.90 MPa | ≈0.003656 mm | 3.1 |
| Modified, intermediate | Inconsistent reported stress exponent | 0.003561 mm | 4.2 |
| Modified, fine mesh | 15.70 MPa | 0.003579 mm | Not clearly documented |

The initial design did **not** meet the safety-factor requirement of 4. Although the modified intermediate result reported a factor of 4.2, the final minimum safety factor was not clearly documented and mesh convergence was incomplete.

![Initial reference von Mises stress plot](Screenshot%202026-11-11%20230415.png)

*Figure 18. Initial reference von Mises stress plot.*

![Initial reference displacement plot](Screenshot%202026-11-11%20230419.png)

*Figure 19. Initial reference displacement plot.*

![Curved support feature for one optimization concept](Screenshot%202026-11-11%20230424.png)

*Figure 20. Curved support feature for one optimization concept.*

![Revised crosshead stress plot from reference analysis](Screenshot%202026-11-11%20230427.png)

*Figure 21. Revised crosshead stress plot from reference analysis.*

![Refined-mesh stress plot after reference optimization](Screenshot%202026-11-11%20230431.png)

*Figure 22. Refined-mesh stress plot after reference optimization.*

### Mesh verification

The initial reference study showed a stress increase from 15.31 to 17.90 MPa after refinement, or about **16.9%**. This suggests more refinement and closer investigation of peak stress are needed. A reliable final analysis should report three mesh sizes, their element counts, peak stress and location, displacement at the grip line, and minimum factor of safety.

![Example mesh details from an alternative crosshead](Screenshot%202026-11-11%20230457.png)

*Figure 26. Example mesh details from an alternative crosshead.*

![Second mesh settings and element counts](Screenshot%202026-11-11%20230501.png)

*Additional figure. Mesh details for the alternative crosshead reference.*

![Example refined mesh and corresponding stress plot](Screenshot%202026-11-11%20230505.png)

*Figure 27. Example refined mesh and corresponding stress plot.*

### Alternative optimization approach

Another reference concept removes roughly 1/8 inch from each side of a different crosshead to reduce mass and then reruns FEA. It is an **alternative** to adding curved reinforcement, not another stage of the same CAD model. The two designs should not be combined without new dimensions and simulation checks.

![Alternative material-removal optimization sketch](Screenshot%202026-11-11%20230513.png)

*Figure 28. Alternative material-removal optimization sketch.*

![Alternative optimized FEA stress and displacement images](Screenshot%202026-11-11%20230518.png)

*Figure 29. Alternative optimized FEA stress and displacement images.*

## 8. Material costs

The following amounts are **historical reference prices copied from the A10 report**, not new supplier quotes. The selection must be reconciled with the final CAD part numbers before ordering.

| Part number | Qty | Component | Unit cost | Extended cost |
|---|---:|---|---:|---:|
| 99030A005 | 2 | 1018 steel Acme screw | $17.84 | $35.68 |
| 95072A147 | 2 | Precision Acme externally threaded nut | $36.39 | $72.78 |
| 1329K102 | 2 | Precision Acme flange | $62.74 | $125.48 |
| 47065T107 | 1 | T-slot frame, 1 ft | $12.68 | $12.68 |
| 47065T108 | 3 | T-slot frame, 1.5 ft | $15.73 | $47.19 |
| 47065T109 | 2 | T-slot frame, 2 ft | $12.69 | $25.38 |
| 3487N299 | 1 | Force sensor / load cell | $2,587.06 | $2,587.06 |
| 91268A190 | 1 | Pack of 10 bolts | $9.21 | $9.21 |
| 90499A029 | 1 | Pack of 100 nuts | $6.48 | $6.48 |
| Stock estimate | 1 | Aluminum crosshead stock (2.34 lb) | $4.75/lb | $11.12 |
| | | **Reference total** | | **$2,933.06** |

The load cell represents $2,587.06 of this estimate. The remaining listed items total **$346.00**. Bearings, brackets, synchronization components, and hardware not included in this table would add cost.

An alternative A10 configuration reports a $1,496.03 estimate, but it uses different components and geometry and is not interchangeable with this baseline.

## 9. Challenges and design decisions

The main challenge was keeping the calculations consistent with the components selected in CAD. I needed to convert between metric and inch units, especially when calculating screw lead and crosshead motion. I also learned that axial stress alone is not enough to select a long lead screw because buckling and end supports affect its performance. Another issue was comparing FEA results when the mesh sizes and geometry were not identical.

## 10. Lessons learned

Throughout the assignment, I learned how the different mechanical components need to work together for a tensile tester to function. The relationship between lead screw rotation and crosshead movement helped me understand how thread lead controls speed. I also became more familiar with using stress, deflection, and torque equations when selecting machine components.

One challenge was making sure dimensions and calculations matched the available parts. Switching between metric and imperial units made some calculations more complicated. Working with SolidWorks also helped me see why the placement of holes, mates, and mounting features matters.

Overall, I learned that the hand calculations, actual material selection, CAD files, and simulation results all need to describe the same design before I can call it verified.

## 11. Engineering drawing

The reference drawing shows a third-angle crosshead layout with overall dimensions, hole dimensions, a material field, and a title block. The finished drawing for a build must match the current CAD part and include the required tolerances and interface details.

![Crosshead engineering drawing reference](Screenshot%202026-11-11%20230439.png)

*Figure 23. Crosshead engineering drawing reference.*

## 12. Project time

**Total reported time: 56 hours.**

## 13. CAD files

The SolidWorks package contains the tensile tester assembly, the crosshead-and-nut assembly, and associated parts.

- [Download full SolidWorks CAD ZIP](Kaleb_Dedrick_A10_All_SolidWorks_CAD.zip)
- Main assembly: `tensile_test_part_1v2.SLDASM`
- Crosshead/nut assembly: `crosshead_and_nut KD.SLDASM`
