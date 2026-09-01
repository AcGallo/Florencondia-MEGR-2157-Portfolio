# A2 – Truss Stress Analysis

## Objective

The objective of this assignment was to design a lightweight planar truss and determine the required member and pin sizes using basic stress equations. I used statics to calculate the support reactions and internal member forces, then used the largest calculated force to size the common truss-member cross-section. The final design was modeled in SolidWorks so the CAD mass could be compared with the analytical mass.


> **Figure #1 — Assignment constraints**
![Picture #1: Assignment constraints and selected truss geometry](../../assets/images/1.png)

---

## Analyze

The first part of the assignment was to determine the forces acting through the truss before choosing the final member and pin sizes. I used the given geometry, a selected load of 25 kN, equilibrium equations, and the method of joints. These results were then used to determine the minimum cross-sectional area required for the truss members and the minimum diameter required for the pins.

### Truss Geometry

The final design uses:

- **P = 25 kN**
- **a = 0.4 m**
- **b = 0.3 m**
- **A = pin support**
- **B = roller support**

The five joints are **A, B, C, D, and E**.

The seven truss members are:

**BE, EA, BC, CE, ED, AD, and CD**

The final member lengths are:

| Member | Length |
|---|---:|
| BE | 0.600 m |
| EA | 0.600 m |
| BC | 0.500 m |
| AD | 0.500 m |
| CE | 0.3606 m |
| ED | 0.3606 m |
| CD | 0.400 m |

The total centerline length of the seven members is approximately:

**L<sub>total</sub> = 3.3211 m**


> **Figure #2 — Final truss geometry dimensions with a = 0.4 m and b = 0.3 m**
![Figure #2: Final truss geometry dimensions](../../assets/images/2.png)

### Free-Body Diagrams

The overall free-body diagram shows the two applied loads and the support reactions at A and B. At joint A, the unknown support reactions are A<sub>x</sub> and A<sub>y</sub>, while the roller at B has the reaction B<sub>y</sub>. The reaction arrows were initially assumed before solving, so a negative calculated result means the true force acts in the opposite direction.

Separate free-body diagrams were also made for joints A, B, C, D, and E. When solving the joints, the unknown member-force arrows were initially assumed to be in tension and were drawn away from the joint. A negative result therefore indicates compression.


> **Picture #3 — Overall truss free-body diagram**
> *Insert Picture #3 here.*
<!-- IMAGE #3 GOES HERE. Example: ![Picture #3](../../assets/images/your-image-file.png) -->


> **Picture #4 — Joint A and Joint B free-body diagrams**
> *Insert Picture #4 here.*
<!-- IMAGE #4 GOES HERE. Example: ![Picture #4](../../assets/images/your-image-file.png) -->


> **Picture #5 — Joint C, Joint D, and Joint E free-body diagrams**
> *Insert Picture #5 here.*
<!-- IMAGE #5 GOES HERE. Example: ![Picture #5](../../assets/images/your-image-file.png) -->


### Support Reactions

Taking moments about B:

**ΣM<sub>B</sub> = 0**

**A<sub>y</sub>(3a) + P(a) - P(2a) = 0**

**A<sub>y</sub> = P / 3**

**A<sub>y</sub> = 8.333 kN**

Using vertical equilibrium:

**ΣF<sub>y</sub> = 0**

**A<sub>y</sub> + B<sub>y</sub> + P - P = 0**

**B<sub>y</sub> = -8.333 kN**

The negative sign means the actual reaction at B acts downward relative to the initially assumed upward direction.

Using horizontal equilibrium:

**ΣF<sub>x</sub> = 0**

**A<sub>x</sub> = 0**

### Member Forces

The method of joints was used to solve the force in every truss member.

| Member | Force | Result |
|---|---:|---|
| BE | 11.111 kN | Tension |
| EA | -11.111 kN | Compression |
| BC | -13.889 kN | Compression |
| CE | -20.031 kN | Compression |
| ED | 20.031 kN | Tension |
| AD | 13.889 kN | Tension |
| CD | 0 kN | Zero-force member |

The largest internal-force magnitude is:

**F<sub>max</sub> = 20.031 kN**

This occurs in members CE and ED. Because every member must use the same cross-sectional area, this maximum value was used to size the truss.


> **Picture #6 — S<sub>y</sub>mbolic and numerical truss calculations from Overleaf**
> *Insert Picture #6 here.*
<!-- IMAGE #6 GOES HERE. Example: ![Picture #6](../../assets/images/your-image-file.png) -->


### Material Selection

The truss was modeled using **ASTM A500 Grade C** material properties. The values used for the calculations and custom SolidWorks material were:

- **Yield strength = 345 MPa**
- **Ultimate tensile strength = 425 MPa**
- **Elastic modulus = 200,000 MPa**
- **Poisson's ratio = 0.29**
- **Density = 7800 kg/m<sup>3</sup>**

Material-property source:

[BeamDimensions - ASTM A500](https://beamdimensions.com/materials/Steel/ASTM/ASTM_A500/)


> **Picture #7 — ASTM A500 Grade C material-property source**
> *Insert Picture #7 here.*
<!-- IMAGE #7 GOES HERE. Example: ![Picture #7](../../assets/images/your-image-file.png) -->


> **Picture #8 — Custom ASTM A500 Grade C material in SolidWorks**
> *Insert Picture #8 here.*
<!-- IMAGE #8 GOES HERE. Example: ![Picture #8](../../assets/images/your-image-file.png) -->


### Member Cross-Section

The required member safety factor is:

**FS<sub>member</sub> = 3.5**

The allowable normal stress is:

**σ<sub>allow</sub> = S<sub>y</sub> / FS**

**σ<sub>allow</sub> = 345 / 3.5 = 98.57 MPa**

The minimum required member area is:

**A<sub>min</sub> = (F<sub>max</sub> × FS) / S<sub>y</sub>**

**A<sub>min</sub> = (20,030.84 N × 3.5) / 345 N/mm<sup>2</sup>**

**A<sub>min</sub> = 203.21 mm<sup>2</sup>**

I selected a **15 mm × 15 mm** solid cross-section:

**A<sub>member</sub> = 15 × 15 = 225 mm<sup>2</sup>**

Because:

**225 mm<sup>2</sup> > 203.21 mm<sup>2</sup>**

the selected cross-section satisfies the required area.

The actual maximum normal stress is:

**σ<sub>max</sub> = 20,030.84 / 225 = 89.03 MPa**

The actual member safety factor is:

**FS<sub>actual</sub> = 345 / 89.03 = 3.88**

Since **3.88 > 3.5**, the selected member cross-section satisfies the required safety factor.


> **Picture #9 — Member-area and safety-factor calculations**
> *Insert Picture #9 here.*
<!-- IMAGE #9 GOES HERE. Example: ![Picture #9](../../assets/images/your-image-file.png) -->


### Pin Design

The assignment specifies hardened tool-steel pins with:

- **Yield shear strength = 170 ksi = 1172.11 MPa**
- **Density = 0.278 lb/in<sup>3</sup>**
- **Required pin safety factor = 4**
- **Single-shear connection**

The critical pin load used for the design is:

**F<sub>pin</sub> = 25 kN**

For a single-shear pin:

**A<sub>pin,min</sub> = (F<sub>pin</sub> × FS<sub>pin</sub>) / S<sub>sy</sub>**

**A<sub>pin,min</sub> = (25,000 × 4) / 1172.11**

**A<sub>pin,min</sub> = 85.32 mm<sup>2</sup>**

For a circular pin:

**A = πd² / 4**

Solving for diameter gives:

**d<sub>min</sub> = 10.42 mm**

I selected:

**Pin diameter = 11 mm**

The actual area of the 11 mm pin is:

**A<sub>pin</sub> = 95.03 mm<sup>2</sup>**

The actual average shear stress is:

**τ = 25,000 / 95.03 = 263.07 MPa**

The actual pin safety factor is:

**FS<sub>pin</sub>,actual = 1172.11 / 263.07 = 4.46**

Since **4.46 > 4**, the selected 11 mm pin satisfies the required safety factor.

The final flat truss body is 15 mm thick, so the final pin was modeled as:

- **Diameter = 11 mm**
- **Length = 15 mm**


> **Picture #10 — Critical-pin free-body diagram**
> *Insert Picture #10 here.*
<!-- IMAGE #10 GOES HERE. Example: ![Picture #10](../../assets/images/your-image-file.png) -->


> **Picture #11 — Pin sizing calculations**
> *Insert Picture #11 here.*
<!-- IMAGE #11 GOES HERE. Example: ![Picture #11](../../assets/images/your-image-file.png) -->


### Pin Joint Geometry

The pin holes remove material from the member at each joint, so the joint areas were widened in the final CAD model. A 26 mm circular joint region was used around each 11 mm hole so that the net section across the center of the hole remained at least as large as the selected 225 mm<sup>2</sup> member area.

Using the 15 mm truss thickness:

**A<sub>net</sub> = (D<sub>joint</sub> - d<sub>hole</sub>) × t**

**225 = (D<sub>joint</sub> - 11) × 15**

**D<sub>joint</sub> = 26 mm**

The final joint geometry therefore uses:

- **Joint-pad diameter = 26 mm**
- **Hole diameter = 11 mm**
- **Truss thickness = 15 mm**


> **Picture #12 — 26 mm joint pads and 11 mm pin holes**
> *Insert Picture #12 here.*
<!-- IMAGE #12 GOES HERE. Example: ![Picture #12](../../assets/images/your-image-file.png) -->


### Analytical Mass Estimate

Using the selected 225 mm<sup>2</sup> cross-sectional area and the total centerline member length:

**V<sub>truss</sub> ≈ A × L<sub>total</sub>**

**V<sub>truss</sub> ≈ (225 × 10<sup>-6</sup>)(3.3211)**

**V<sub>truss</sub> ≈ 7.4725 × 10<sup>-4</sup> m<sup>3</sup>**

Using the A500 Grade C density:

**m<sub>truss,calc</sub> ≈ 5.82855 kg**

The calculated mass of one 11 mm diameter, 15 mm long pin is approximately:

**m<sub>one pin,calc</sub> ≈ 0.01097 kg**

For five pins:

**m<sub>pins,calc</sub> ≈ 0.05485 kg**

The final analytical estimate is:

**m<sub>total,calc</sub> ≈ 5.8834 kg**

---

## Decide

The final design was selected based on the calculated member and pin requirements rather than only on appearance. The 15 mm × 15 mm member section exceeds the minimum required area, and the 11 mm pin exceeds the minimum required pin diameter. The design was then recreated in SolidWorks as a flat one-part truss body with five separate identical pins.

### Final Design

| Item | Final Value |
|---|---:|
| Applied load P | 25 kN |
| a | 0.4 m |
| b | 0.3 m |
| Member size | 15 mm × 15 mm |
| Member area | 225 mm<sup>2</sup> |
| Truss thickness | 15 mm |
| Joint-pad diameter | 26 mm |
| Pin-hole diameter | 11 mm |
| Pin diameter | 11 mm |
| Pin length | 15 mm |
| Number of pins | 5 |

### CAD Process

The truss was modeled in SolidWorks using MMGS units. I first created construction geometry and located the five joint centers using the correct 400 mm, 600 mm, and 300 mm dimensions. I connected the joint centers, offset the member centerlines by 7.5 mm on each side, converted the original centerlines to construction geometry, and cleaned the intersections until the profile was fully defined.

The completed truss profile was extruded to 15 mm. The five 26 mm joint pads were then added, followed by the five 11 mm pin holes. Finally, one 11 mm diameter by 15 mm long pin was modeled and inserted five times into the final assembly.


> **Picture #13 — Construction lines and joint locations**
> *Insert Picture #13 here.*
<!-- IMAGE #13 GOES HERE. Example: ![Picture #13](../../assets/images/your-image-file.png) -->


> **Picture #14 — Seven-member centerline skeleton**
> *Insert Picture #14 here.*
<!-- IMAGE #14 GOES HERE. Example: ![Picture #14](../../assets/images/your-image-file.png) -->


> **Picture #15 — 7.5 mm offset used on both sides of each member**
> *Insert Picture #15 here.*
<!-- IMAGE #15 GOES HERE. Example: ![Picture #15](../../assets/images/your-image-file.png) -->


> **Picture #16 — Centerlines converted to construction geometry**
> *Insert Picture #16 here.*
<!-- IMAGE #16 GOES HERE. Example: ![Picture #16](../../assets/images/your-image-file.png) -->


> **Picture #17 — Trimmed and cleaned joint geometry**
> *Insert Picture #17 here.*
<!-- IMAGE #17 GOES HERE. Example: ![Picture #17](../../assets/images/your-image-file.png) -->


> **Picture #18 — Fully defined final truss sketch**
> *Insert Picture #18 here.*
<!-- IMAGE #18 GOES HERE. Example: ![Picture #18](../../assets/images/your-image-file.png) -->


> **Picture #19 — Truss extruded to 15 mm**
> *Insert Picture #19 here.*
<!-- IMAGE #19 GOES HERE. Example: ![Picture #19](../../assets/images/your-image-file.png) -->


> **Picture #20 — Final truss body with joint pads and holes**
> *Insert Picture #20 here.*
<!-- IMAGE #20 GOES HERE. Example: ![Picture #20](../../assets/images/your-image-file.png) -->


> **Picture #21 — 11 mm × 15 mm pin model**
> *Insert Picture #21 here.*
<!-- IMAGE #21 GOES HERE. Example: ![Picture #21](../../assets/images/your-image-file.png) -->


> **Picture #22 — Final SolidWorks assembly with five pins**
> *Insert Picture #22 here.*
<!-- IMAGE #22 GOES HERE. Example: ![Picture #22](../../assets/images/your-image-file.png) -->


### CAD Mass Results

The SolidWorks mass of the final truss body was:

**m<sub>CAD,truss</sub> = 5.77144 kg**

The SolidWorks mass of one pin was:

**m<sub>CAD,pin</sub> = 11.12 g**

The final SolidWorks assembly containing the truss and all five pins had a mass of:

**m<sub>CAD,total</sub> = 5.82704 kg**


> **Picture #23 — Truss-body mass properties - 5771.44 g**
> *Insert Picture #23 here.*
<!-- IMAGE #23 GOES HERE. Example: ![Picture #23](../../assets/images/your-image-file.png) -->


> **Picture #24 — One-pin mass properties - 11.12 g**
> *Insert Picture #24 here.*
<!-- IMAGE #24 GOES HERE. Example: ![Picture #24](../../assets/images/your-image-file.png) -->


> **Picture #25 — Final assembly mass properties - 5827.04 g**
> *Insert Picture #25 here.*
<!-- IMAGE #25 GOES HERE. Example: ![Picture #25](../../assets/images/your-image-file.png) -->


### Weight Comparison

The analytical total mass was:

**m<sub>calc</sub> = 5.8834 kg**

The SolidWorks assembly mass was:

**m<sub>CAD</sub> = 5.82704 kg**

The absolute difference is:

**Difference = 0.05636 kg**

The percent difference is approximately:

**Percent difference = 0.96%**

The two results are very close. The analytical calculation treats the members using simplified centerline lengths and constant area, while the CAD model includes the actual trimmed joints, circular joint pads, holes, arcs, and merged geometry. This explains why the final CAD mass is slightly different from the analytical estimate.

---

## Communicate

The completed analysis showed that the selected member and pin dimensions satisfy the required safety factors for the simplified design model. The CAD model also produced a mass within about one percent of the analytical estimate, which shows that the analytical model and final geometry are reasonably consistent. The failure-mode review also showed that a member can be safe against simple axial yielding while still having other possible failure concerns such as buckling in compression.

### MEGR 2157 – Truss Member Failure Modes

ASTM A500 Grade C is treated as a ductile steel. For the tension members, yielding is expected before tensile fracture because the yield strength used in the design is lower than the ultimate tensile strength. For compression members, buckling becomes an important possible failure mode when the assignment's simplified no-buckling assumption is removed.

For the 15 mm × 15 mm solid section:

**I = bh³ / 12 = 4218.75 mm<sup>4</sup>**

Using the ideal pinned-column Euler relation:

**P<sub>cr</sub> = π²EI / L²**

the failure-mode screening gives the following results:

| Member | Loading | Stress | Expected Failure Mode | Material Behavior | Possible Improvement |
|---|---|---:|---|---|---|
| BE | Tension | 49.38 MPa | Yielding before fracture | Ductile | Increase common member area |
| EA | Compression | 49.38 MPa | Buckling | Ductile material | Increase moment of inertia or reduce unsupported length |
| BC | Compression | 61.73 MPa | Buckling | Ductile material | Increase moment of inertia or reduce unsupported length |
| CE | Compression | 89.03 MPa | Buckling | Ductile material | Increase moment of inertia |
| ED | Tension | 89.03 MPa | Yielding before fracture | Ductile | Increase common member area |
| AD | Tension | 61.73 MPa | Yielding before fracture | Ductile | Increase common member area |
| CD | Zero force | 0 MPa | None under this ideal load case | Ductile | Retain for stability and other possible load cases |

The main sizing portion of the assignment specifically allowed compression-member buckling to be ignored. The table above is a separate MEGR 2157 failure-mode review and does not replace the required basic-stress sizing calculation.


> **Picture #26 — Truss-member failure-mode analysis**
> *Insert Picture #26 here.*
<!-- IMAGE #26 GOES HERE. Example: ![Picture #26](../../assets/images/your-image-file.png) -->


### MEGR 2157 – Pin Failure Mode

The pin was designed for direct single shear. At the critical 25 kN load, the 11 mm diameter pin has an average shear stress of approximately **263.07 MPa**, compared with the specified shear yield strength of **1172.11 MPa**. The resulting safety factor is **4.46**, so shear yielding is not expected at the design load.

If the applied load were increased enough, the most directly applicable failure mode for this pin design would be shear yielding across the single shear plane. Increasing the pin diameter would increase its shear area and reduce the average shear stress. A double-shear connection could also reduce the load carried by each shear plane, but this assignment specifically requires a single-shear connection.


> **Picture #27 — Pin failure-mode analysis**
> *Insert Picture #27 here.*
<!-- IMAGE #27 GOES HERE. Example: ![Picture #27](../../assets/images/your-image-file.png) -->


### Engineering Lessons Learned

One of the biggest lessons from this assignment was that checking the original dimensions before beginning detailed CAD work is extremely important. The truss can have the correct shape and force ratios while still having completely incorrect member lengths and weight if the scale is wrong. I also learned that the joint design matters because adding a pin hole removes material from the member and can reduce the net cross-sectional area.

The comparison between analytical mass and CAD mass also showed why both methods are useful. The calculations provide a fast estimate and help size the structure, while CAD represents the final geometry more accurately. Having only about a 0.96% difference between the two results gave me confidence that the final corrected model was consistent with the calculations.

### Mistakes and Improvements

My largest mistake was initially reading the assignment dimensions as **a = 4 m** and **b = 3 m** instead of **a = 0.4 m** and **b = 0.3 m**. I completed most of the first CAD model before catching the error and then rebuilt the truss using the correct 400 mm and 300 mm dimensions. Because the corrected design is a uniform scale change, the truss angles and internal-force results remained the same, but all member lengths and weight calculations had to be corrected.

If I repeated the assignment, I would write the problem constraints and units in a short table before starting the calculations or CAD model. I would also check the overall span and height immediately after creating the first SolidWorks sketch. This would prevent a dimension-reading mistake from carrying through the rest of the design.


> **Picture #28 — Incorrect first CAD model at the wrong scale**
> *Insert Picture #28 here.*
<!-- IMAGE #28 GOES HERE. Example: ![Picture #28](../../assets/images/your-image-file.png) -->


> **Picture #29 — Corrected final CAD model**
> *Insert Picture #29 here.*
<!-- IMAGE #29 GOES HERE. Example: ![Picture #29](../../assets/images/your-image-file.png) -->


### Time Spent

**Total Time Spent: [ENTER ACTUAL TOTAL TIME]**

The assignment included calculations, CAD modeling, a complete CAD rebuild after correcting the dimensions, pin modeling, material setup, assembly work, mass-property comparison, failure-mode analysis, and documentation.

---

## CAD Download

**[ADD FINAL CAD DOWNLOAD LINK HERE]**

The final download should include the truss part, pin part, and assembly so the model can be reviewed and reproduced.

---

## References

1. BeamDimensions. **ASTM A500 Steel Material Properties.**  
   <https://beamdimensions.com/materials/Steel/ASTM/ASTM_A500/>

2. Steel Tube Institute. **ASTM A500.**  
   <https://steeltubeinstitute.org/resources/astm-a500/>

3. Purdue University, ME 323 Mechanics of Materials. **Lecture 39 – Buckling of Columns.**  
   <https://web.ics.purdue.edu/~gonza226/ME323/Lecture-39.pdf>

4. Purdue University, ME 323 Mechanics of Materials. **Lecture 3 – Shear Stress and Strain.**  
   <https://web.ics.purdue.edu/~gonza226/ME323/Lecture-03.pdf>

5. Course handout. **Shear on a Pin.**
