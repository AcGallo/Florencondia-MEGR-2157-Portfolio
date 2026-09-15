# A4 – Motor Mount

## Objective

The objective of A4 is to design a motor mount for a **Brushed 24V DC Gear Motor** subjected to a load of **300 N**. The mount must remain below the material yield strength with a required **safety factor of 3** and must not exceed a maximum deflection of **0.30 mm**.

The design is separated into two structural features:

- **Feature 1:** the portion of the mount attached to and supporting the motor.
- **Feature 2:** the portion of the mount attached to the rigid wall.

Both features are analyzed using beam bending equations for **maximum stress** and **maximum deflection**. The resulting dimensions are then used to create a parametric SolidWorks model.

---

## Analyze

### Design Requirements

The design requirements used for the motor mount are:

| Requirement | Value |
|---|---:|
| Applied Load, \(P\) | 300 N |
| Maximum Deflection | 0.30 mm |
| Required Safety Factor | 3 |
| Mount Width, \(b\) | 50 mm |
| Motor Shaft Offset | 18 mm |

The motor weight is neglected as allowed by the assignment.

> **Figure #1 — A4 motor dimensions and applied-load diagram**
<img src="../../assets/images/37.png" alt="A4 motor dimensions and applied load diagram" style="width:100%; height:auto;">

### Material Selection

The selected material is **PETG**.

The supplied PETG material data gives:

$$\boxed{E=3.03\text{ GPa}=3030\text{ MPa}}$$

$$\boxed{S_y=51.4\text{ MPa}}$$

PETG was selected because the supplied material data provides a useful combination of stiffness and yield strength for the static stress and deflection requirements of this motor mount.

> **Figure #2 — PETG material properties used for the design**
<img src="../../assets/images/38.png" alt="PETG material properties" style="width:100%; height:auto;">

### Allowable Stress

The allowable stress is determined using the required safety factor:

$$\sigma_{\text{allow}}=\frac{S_y}{SF}$$

$$\sigma_{\text{allow}}=\frac{51.4}{3}$$

$$\boxed{\sigma_{\text{allow}}=17.13\text{ MPa}}$$

### Justifiable Assumptions

The following assumptions are used to simplify the analysis:

- The motor weight is neglected.
- The wall is treated as perfectly rigid.
- PETG is treated as a linear elastic material for the beam calculations.
- Each feature is modeled as a rectangular beam.
- The mount width is fixed at **50 mm**.
- The 300 N load acts at the end of the motor shaft.
- Stress concentrations around bolt holes are neglected in the preliminary beam analysis.
- The wall mounting bolts are positioned symmetrically on Feature 2.

### Motor Mount Research

Before creating the final design, examples of existing motor mounts were reviewed to understand common mounting geometry and bolt placement.

<!-- Add 1–2 motor mount research links here before submission. -->

---

# Feature 1

## Feature 1 – Knowns and Unknowns

Feature 1 is the portion of the bracket that supports the motor.

Known values:

$$P=300\text{ N}$$

$$e_1=18\text{ mm}$$

$$b=50\text{ mm}$$

$$L_1=50\text{ mm}$$

$$E=3030\text{ MPa}$$

$$S_y=51.4\text{ MPa}$$

$$SF=3$$

$$\delta_{\max}=0.30\text{ mm}$$

Unknown:

$$h_1=?$$

> **Figure #3 — Feature 1 free-body diagram and knowns/unknowns**
<img src="../../assets/images/39.png" alt="Feature 1 free-body diagram and knowns and unknowns" style="width:100%; height:auto;">

## Feature 1 – Applied Moment

The 300 N force acts 18 mm from the motor mounting face.

$$M_1=Pe_1$$

$$M_1=(300)(18)$$

$$\boxed{M_1=5400\text{ N}\cdot\text{mm}=5.40\text{ N}\cdot\text{m}}$$

## Feature 1 – Stress Analysis

For a rectangular cross section:

$$I=\frac{bh^3}{12}$$

and:

$$c=\frac{h}{2}$$

The bending stress equation is:

$$\sigma=\frac{Mc}{I}$$

Substituting the rectangular section equations:

$$\sigma=\frac{6M}{bh^2}$$

Including the required safety factor:

$$\frac{6M_1}{bh_1^2}\leq\frac{S_y}{SF}$$

Solving symbolically for \(h_1\):

$$h_1=\sqrt{\frac{6M_1SF}{bS_y}}$$

Numerically:

$$h_1=\sqrt{\frac{6(5400)(3)}{(50)(51.4)}}$$

$$\boxed{h_{1,\text{stress}}=6.15\text{ mm}}$$

> **Figure #4 — Feature 1 handwritten bending-stress calculation**
<img src="../../assets/images/40.png" alt="Feature 1 handwritten bending stress calculation" style="width:100%; height:auto;">

## Feature 1 – Deflection Analysis

For a cantilever subjected to an end moment:

$$\delta=\frac{ML^2}{2EI}$$

Using:

$$I=\frac{bh^3}{12}$$

the equation becomes:

$$\delta=\frac{6ML^2}{Ebh^3}$$

Solving symbolically for \(h_1\):

$$h_1=\sqrt[3]{\frac{6M_1L_1^2}{Eb\delta_{\max}}}$$

Numerically:

$$h_1=\sqrt[3]{\frac{6(5400)(50)^2}{(3030)(50)(0.30)}}$$

$$\boxed{h_{1,\text{deflection}}=12.124\text{ mm}}$$

The deflection requirement controls because:

$$12.124>6.15$$

The final Feature 1 thickness is rounded upward to:

$$\boxed{h_1=12.2\text{ mm}}$$

### Feature 1 Cross-Sectional Area

$$A_1=bh_1$$

$$A_1=(50)(12.2)$$

$$\boxed{A_1=610\text{ mm}^2}$$

### Feature 1 Verification

Stress:

$$\sigma_1=\frac{6(5400)}{(50)(12.2)^2}$$

$$\boxed{\sigma_1=4.35\text{ MPa}}$$

Actual safety factor:

$$FS_1=\frac{51.4}{4.35}$$

$$\boxed{FS_1=11.8}$$

Deflection:

$$\delta_1=\frac{6(5400)(50)^2}{(3030)(50)(12.2)^3}$$

$$\boxed{\delta_1=0.294\text{ mm}}$$

Since:

$$0.294<0.300\text{ mm}$$

Feature 1 satisfies the deflection requirement.

> **Figure #5 — Feature 1 handwritten deflection calculation and final thickness**
<img src="../../assets/images/41.png" alt="Feature 1 handwritten deflection calculation and final thickness" style="width:100%; height:auto;">

---

# Feature 2

## Feature 2 – Knowns and Unknowns

Feature 2 is the vertical portion of the bracket attached to the rigid wall.

The 50 mm plate is divided approximately into thirds for the wall bolt placement. The outer bolt line is therefore approximately:

$$33.33\text{ mm}$$

from the edge.

The distance from this bolt line to the end of the plate is:

$$50-33.33=16.67\text{ mm}$$

Adding the 18 mm motor shaft offset gives the Feature 2 moment arm:

$$e_2=16.67+18$$

$$\boxed{e_2=34.67\text{ mm}}$$

Known values:

$$P=300\text{ N}$$

$$b=50\text{ mm}$$

$$L_2=50\text{ mm}$$

$$E=3030\text{ MPa}$$

$$S_y=51.4\text{ MPa}$$

$$SF=3$$

$$\delta_{\max}=0.30\text{ mm}$$

Unknown:

$$h_2=?$$

> **Figure #6 — Feature 2 free-body diagram and knowns/unknowns**
<img src="../../assets/images/42.png" alt="Feature 2 free-body diagram and knowns and unknowns" style="width:100%; height:auto;">

## Feature 2 – Applied Moment

$$M_2=Pe_2$$

$$M_2=(300)(34.67)$$

$$\boxed{M_2=10401\text{ N}\cdot\text{mm}\approx10.40\text{ N}\cdot\text{m}}$$

## Feature 2 – Stress Analysis

The same bending stress relation is used:

$$h_2=\sqrt{\frac{6M_2SF}{bS_y}}$$

Numerically:

$$h_2=\sqrt{\frac{6(10401)(3)}{(50)(51.4)}}$$

$$\boxed{h_{2,\text{stress}}=8.54\text{ mm}}$$

> **Figure #7 — Feature 2 handwritten bending-stress calculation**
<img src="../../assets/images/43.png" alt="Feature 2 handwritten bending stress calculation" style="width:100%; height:auto;">

## Feature 2 – Deflection Analysis

Using the cantilever deflection relation:

$$h_2=\sqrt[3]{\frac{6M_2L_2^2}{Eb\delta_{\max}}}$$

Numerically:

$$h_2=\sqrt[3]{\frac{6(10401)(50)^2}{(3030)(50)(0.30)}}$$

$$\boxed{h_{2,\text{deflection}}=15.085\text{ mm}}$$

The deflection requirement controls because:

$$15.085>8.54$$

The final Feature 2 thickness is rounded upward to:

$$\boxed{h_2=15.1\text{ mm}}$$

### Feature 2 Cross-Sectional Area

$$A_2=bh_2$$

$$A_2=(50)(15.1)$$

$$\boxed{A_2=755\text{ mm}^2}$$

### Feature 2 Verification

Stress:

$$\sigma_2=\frac{6(10401)}{(50)(15.1)^2}$$

$$\boxed{\sigma_2=5.47\text{ MPa}}$$

Actual safety factor:

$$FS_2=\frac{51.4}{5.47}$$

$$\boxed{FS_2=9.39}$$

Deflection:

$$\delta_2=\frac{6(10401)(50)^2}{(3030)(50)(15.1)^3}$$

$$\boxed{\delta_2=0.299\text{ mm}}$$

Since:

$$0.299<0.300\text{ mm}$$

Feature 2 satisfies the deflection requirement.

> **Figure #8 — Feature 2 handwritten deflection calculation and final thickness**
<img src="../../assets/images/44.png" alt="Feature 2 handwritten deflection calculation and final thickness" style="width:100%; height:auto;">

---

## Decide

### Final Calculated Dimensions

The final calculated dimensions are:

| Parameter | Final Value |
|---|---:|
| Material | PETG |
| Width | 50 mm |
| Feature 1 Design Length | 50 mm |
| Feature 1 Thickness | 12.2 mm |
| Feature 2 Design Length | 50 mm |
| Feature 2 Thickness | 15.1 mm |
| Feature 1 Deflection | 0.294 mm |
| Feature 2 Deflection | 0.299 mm |
| Required Safety Factor | 3 |
| Feature 1 Calculated Safety Factor | 11.8 |
| Feature 2 Calculated Safety Factor | 9.39 |

### Isometric Design Sketch

An isometric sketch will be completed on paper using the calculated dimensions before creating the CAD model.

> **Figure #9 — Final hand-drawn isometric motor-mount sketch**
<img src="../../assets/images/45.png" alt="Final hand drawn isometric motor mount sketch" style="width:100%; height:auto;">

### Parametric CAD Model

The motor mount will be modeled in SolidWorks using global variables and equations so that the geometry is controlled parametrically.

The main variables will include:

- Load \(P\)
- PETG Modulus of Elasticity \(E\)
- PETG Yield Strength \(S_y\)
- Safety Factor
- Maximum Deflection
- Mount Width
- Feature 1 Thickness
- Feature 2 Thickness

> **Figure #10 — SolidWorks global variables and parametric equations**
<img src="../../assets/images/46.png" alt="SolidWorks global variables and parametric equations" style="width:100%; height:auto;">

### Final CAD Geometry

The final CAD model will include:

- Feature 1 horizontal motor-support plate
- Feature 2 vertical wall-mounting plate
- Motor clearance feature
- Four M3 motor mounting clearance holes
- Wall mounting holes
- Parametric dimensions based on the calculated geometry

> **Figure #11 — Feature 1 parametric sketch**
<img src="../../assets/images/47.png" alt="Feature 1 parametric sketch" style="width:100%; height:auto;">

> **Figure #12 — Feature 1 extrusion**
<img src="../../assets/images/48.png" alt="Feature 1 extrusion" style="width:100%; height:auto;">

> **Figure #13 — Feature 2 parametric sketch**
<img src="../../assets/images/49.png" alt="Feature 2 parametric sketch" style="width:100%; height:auto;">

> **Figure #14 — Completed L-bracket geometry before holes**
<img src="../../assets/images/50.png" alt="Completed L bracket geometry before holes" style="width:100%; height:auto;">

> **Figure #15 — Motor opening and M3 mounting-hole layout**
<img src="../../assets/images/51.png" alt="Motor opening and M3 mounting hole layout" style="width:100%; height:auto;">

> **Figure #16 — Wall-mounting hole layout**
<img src="../../assets/images/52.png" alt="Wall mounting hole layout" style="width:100%; height:auto;">

> **Figure #17 — Final parametric motor-mount CAD model**
<img src="../../assets/images/53.png" alt="Final parametric motor mount CAD model" style="width:100%; height:auto;">

---

## Communicate

### Design Summary

Both Feature 1 and Feature 2 were sized using bending stress and beam deflection equations.

For both features, the **maximum deflection requirement controlled the final thickness**, rather than the yield stress requirement.

Feature 1 required:

$$\boxed{h_1=12.2\text{ mm}}$$

Feature 2 required:

$$\boxed{h_2=15.1\text{ mm}}$$

Using these dimensions, both calculated deflections remain below the required maximum of 0.30 mm.

### Design Reflection

The calculations show that stiffness is more restrictive than material yielding for this design. Although both features have calculated stresses well below the PETG yield strength, substantially more thickness is required to keep the deflection below 0.30 mm.

The parametric CAD model allows the main design dimensions to update from the governing equations rather than being entered as unrelated fixed dimensions.

### Mistakes and Improvements

<!-- Complete this section after finishing the assignment. Include any calculation, sketching, or CAD mistakes and how they were corrected. -->

### Lessons Learned

<!-- Complete after CAD. Briefly explain what you learned from beam bending, parametric design, and creating the motor mount. -->

### Time Spent

<!-- Replace with actual total time before submission. -->

The total time spent completing A4 was approximately:

$$\boxed{\text{TBD hours}}$$

---

## CAD Download

<!-- Add the final SolidWorks part file to docs/assets/files/ and replace the placeholder below. -->

[Download A4 Motor Mount SolidWorks Part](../../assets/files/A4_Motor_Mount_Florencondia.SLDPRT)

---

## References

1. Course A4 Motor Mount assignment instructions.
2. MatWeb — Overview of materials for PETG Copolyester.
3. Machinery's Handbook — Beam calculations and bending equations.
4. Motor mount design references used during the research portion of the assignment.
