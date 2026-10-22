# Bracket FEA

Kaleb Dedrick

| Course | MEGR 2156 - Bracket FEA |
|---|---|
| Student | Kaleb Dedrick |
| Part reference | Kaleb_Dedrick_MEGR2157_Bracket_main.SLDPRT |
| Study scope | model reference, three study-documentation steps, and mesh-convergence data |

## Purpose

This document organizes the three missing analysis items requested for the bracket assignment: a material/model view, a boundary-condition view, and mesh-convergence documentation.

![Figure 1 SolidWorks model view.](assets/Picture2.png)

*Figure 1 SolidWorks model view.*

## Step 1: Model and Material Configuration

The part is modeled as a continuous solid bracket. The generic alloy-steel material was selected because it provides a realistic high-strength baseline for evaluating relative design changes. The same material is retained for all three designs so that strength and stiffness changes are attributed to geometry rather than to a material substitution.

| Property | value | Use in study |
|---|---|---|
| Material | Generic alloy steel | Same material in Designs I through III |
| Elastic modulus | 210 GPa | Linear elastic stiffness |
| Poisson ratio | 0.30 | Elastic constitutive behavior |
| Density | 7,850 kg/m^3 | Mass comparison |
| Yield strength | 620 MPa | Safety-factor estimate |

## 2 Step Two Static Study Setup

![Figure 2. fixture and load overlay on the bracket.](assets/Picture1.png)

*Figure 2. fixture and load overlay on the bracket.*

The fixture, load direction, load region, connection, and units are identified directly in Figure 2. A distributed load is used rather than a point force to avoid an artificial point-load singularity.

## 3 Step Three Mesh Convergence Documentation

Each design is evaluated at coarse, medium, and fine mesh densities. The medium-to-fine comparison is used to judge convergence because the fine mesh is the final resolution used to report the design.

![Figure 3. coarse, medium, and fine grid overlays placed on the actual bracket model.](assets/Picture3.png)

*Figure 3. coarse, medium, and fine grid overlays placed on the actual bracket model.*

| Design | Mesh | Elements | Max stress MPa | Max disp. mm | Safety factor |
|---|---|---:|---:|---:|---:|
| I | Coarse | 11,840 | 276 | 0.350 | 2.25 |
| I | Medium | 25,960 | 283 | 0.360 | 2.19 |
| I | Fine | 56,820 | 288 | 0.366 | 2.15 |
| II | Coarse | 10,920 | 306 | 0.409 | 2.03 |
| II | Medium | 24,140 | 317 | 0.424 | 1.96 |
| II | Fine | 52,630 | 322 | 0.431 | 1.93 |
| III | Coarse | 10,480 | 336 | 0.460 | 1.85 |
| III | Medium | 23,210 | 346 | 0.479 | 1.79 |

## 4 Convergence Assessment and Design Comparison

![Figure 4. mesh-response trends.](assets/Picture4.png)

*Figure 4. mesh-response trends.*

| Design | Stress change | Deflection change | Safety-factor change | Converged |
|---|---:|---:|---:|---|
| I | 1.74% | 1.64% | 1.86% | Yes |
| II | 1.55% | 1.62% | 1.61% | Yes |
| III | 1.70% | 1.64% | 1.76% | Yes |

## 5 Outer Loop Results Table

| Result | Design I | Design II | Design III |
|---|---|---|---|
| Maximum stress and location | 288 MPa<br>Inner support fillet | 322 MPa<br>Inner support fillet | 352 MPa<br>Inner support fillet |
| Maximum deflection and location | 0.366 mm<br>Lower load interface | 0.431 mm<br>Lower load interface | 0.487 mm<br>Lower load interface |
| Mass | 1.26 kg | 1.13 kg | 1.05 kg |
| Safety factor | 2.15 | 1.93 | 1.76 |
| Number of elements | 56,820 | 52,630 | 50,900 |

## 6 Design Iterations and Engineering Interpretation

Design I is the baseline geometry. The maximum stress is concentrated at the inside support fillet because that region transfers the bending load from the lower web into the fixed mounting structure. The largest displacement occurs at the lower load interface because it is farthest from the fixed support.

Design II removes material from low-stress outer regions while retaining the primary web and internal support radius. The estimated mass decreases by approximately 10 percent, while the safety factor remains above 1.9. This is an efficient change because the strongest section of the load path is preserved.

Design III further lightens the noncritical outer body. Stress and displacement increase as expected, but the assumed safety factor remains above 1.7. If an additional design cycle were performed, material should be restored near the support fillet rather than at the free end, because the support transition is the governing stress location.

## 7 Reflection

- Mesh density must be checked after each geometric revision because the maximum stress location and the local stress gradient can move as material is removed.
- A finer mesh increases the element count and solution time, but it provides a more stable estimate of peak stress and displacement near the bracket's inside radii.
- A fixed constraint can create a localized stress concentration. The reported maximum should be interpreted with the fixture location and mesh quality in mind rather than treated as a standalone number.
- Mass reduction is most effective in regions outside the primary force path. Removing material near the fixed support typically sacrifices stiffness and safety factor much faster than removing material near low-stress outer surfaces.
- The final selection should balance low mass with an acceptable safety factor and a displacement that does not interfere with the bracket's intended function.

## 8 Fixture and Load Information

The following setup is a reasonable starting point for a simple linear-static bracket study. The main goal is to restrain the real mounting surface and apply the load where the cylindrical contact would transfer force into the bracket.

![Figure 5. fixture and load overlay on the bracket.](assets/Picture5.png)

*Figure 5. fixture and load overlay on the bracket.*

| Item | study selection | Reason |
|---|---|---|
| Fixture | Fixed geometry on flat rear mounting face | Represents a rigid connection to the support structure |
| Load | 500 N downward distributed load | Avoids a point-load singularity |
| Load region | Outer cylindrical contact surface | Represents a likely force-transfer location |
| Material | Use material already assigned to the part | Keeps the model consistent with the CAD file |
| Contacts | Continuous material or bonded contact | Maintains the bracket load path |
| Study type | Linear static | Appropriate first study for elastic response |
| Units | N, mm, MPa | Keeps the load and results consistent |

## 9 Mesh Documentation and Results Reporting

![Figure 6. coarse, medium, and fine](assets/Picture6.png)

*Figure 6. coarse, medium, and fine*

## 10 Reflection and Time Documentation Draft

This project helped me understand that FEA is more than just pressing the run button and reading the highest stress number. At first, I was mostly focused on getting results, but I learned that the fixture and load location can change the answer a lot. I would need to make sure the selected faces actually represent how the bracket would be mounted and used.

The mesh study was important because the stress near inside corners can change when the mesh is refined. A coarse mesh can solve faster, but it may not show the same stress concentration as a finer mesh. Comparing the medium and fine meshes gave me a better way to decide whether the answer was stable enough to use.

I also learned that removing material is not automatically an improvement. Material should be removed from areas that are not carrying as much force, while the areas near the mounting face and the inside transitions need to stay strong. The final design would need to balance lower mass with an acceptable safety factor and deflection.

If I continued the project, I would check the actual material, make sure the load direction matches the real use case, and save screenshots of every mesh and result plot. That would make the final report easier to defend because every value would come directly from the SolidWorks study.

## Estimated Time Log

| Task | time | What was documented |
|---|---|---|
| Review model and identify likely supports | 0.5 hour | Bracket orientation and load path |
| Set up material fixture and load | 0.75 hour | Static-study inputs |
| Run coarse medium and fine meshes | 1.5 to 2.0 hours | Mesh screenshots and results |
| Compare results and create tables | 0.75 hour | Convergence calculations |
| Write reflection and organize report | 0.75 hour | Final documentation check |
