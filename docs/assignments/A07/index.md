# A7 – FEA on Bracket

## Objective

The objective of A7 was to use **Finite Element Analysis (FEA)** to evaluate and improve the bracket developed in A5 and A6.

The optimization process used two repeated loops:

- **Outer Loop:** modify the bracket geometry based on the previous FEA results.
- **Inner Loop:** refine the finite element mesh until the results changed by less than **7%**, or until the third mesh attempt was reached.

Three bracket designs were evaluated while keeping the material fixed as **ASTM A36 steel**.

The performance of each design was compared using:

- Maximum von Mises stress and location
- Maximum displacement and location
- Minimum factor of safety
- Mass
- Number of finite elements

The goal was to improve the bracket's strength and stiffness while keeping the design lightweight.

---

# Simulation Setup

A static SolidWorks Simulation study was used for all three designs.

The same material, fixtures, and applied loading were maintained between designs so that the effect of the geometry changes could be compared directly.

| Simulation Parameter | Value |
|---|---:|
| Material | ASTM A36 Steel |
| Applied Force | 1300 lbf |
| Force Direction | Vertically downward |
| Load Location | Upper curved surface of cylinder |
| Mesh Type | Blended curvature-based solid mesh |
| Mesh Quality | High |
| Convergence Requirement | 7% |

## Fixtures

The bracket was fixed on the lower horizontal surfaces of the two upper arms where the bracket is supported by the T-beam.

> **Figure A7-1 — Fixed geometry used for the bracket simulations**

<img src="../../assets/images/64.png" alt="Fixed geometry applied to the upper bracket support surfaces" style="width:100%; height:auto;">

## Applied Load

The cylinder was split so that the strap force could be applied only to the upper curved surface.

A total force of:

$$
P=1300\text{ lbf}
$$

was applied vertically downward.

Using a selected direction prevented the force from acting radially normal to the cylindrical surface.

> **Figure A7-2 — 1300 lbf downward load applied to the upper cylinder surface**

<img src="../../assets/images/65.png" alt="1300 lbf downward force applied to upper cylinder surface" style="width:100%; height:auto;">

---

# Outer Loop 1 — Design I

Design I was the original bracket geometry from A5 and A6 and served as the baseline for the optimization.

The original front-view width of Feature B was:

$$
w_B=0.498\text{ in}
$$

and its axial thickness was:

$$
T_B=0.375\text{ in}
$$

The initial simulation showed that the most critical region was around **Feature B and its connection to the cylinder**.

---

## Inner Loop 1 — Design I Mesh Convergence

The mesh was refined by reducing the element size.

| Mesh | Max Element Size | Min Element Size | Elements |
|---|---:|---:|---:|
| Mesh 1 | 0.212024 in | 0.212024 in | 9,073 |
| Mesh 2 | 0.150 in | 0.075 in | 26,231 |
| Mesh 3 | 0.100 in | 0.050 in | 78,607 |

### Mesh 1 Results

The first mesh predicted:

$$
\sigma_{\max}=6.209\times10^8\text{ Pa}
$$

or:

$$
\sigma_{\max}=620.9\text{ MPa}
$$

The maximum stress occurred around the **Feature B-to-cylinder connection**.

> **Figure A7-3 — Design I Mesh 1 von Mises stress**

<img src="../../assets/images/66.png" alt="Design I Mesh 1 von Mises stress result" style="width:100%; height:auto;">

The minimum factor of safety was:

$$
N_{\min}=0.4027
$$

> **Figure A7-4 — Design I Mesh 1 factor of safety**

<img src="../../assets/images/67.png" alt="Design I Mesh 1 factor of safety result" style="width:100%; height:auto;">

The maximum displacement was:

$$
\delta_{\max}=0.2893\text{ mm}
$$

The largest displacement occurred at the lower/free portion of the cylinder.

> **Figure A7-5 — Design I Mesh 1 displacement**

<img src="../../assets/images/68.png" alt="Design I Mesh 1 displacement result" style="width:100%; height:auto;">

---

## Design I Convergence Calculations

The percent change between consecutive meshes was calculated using:

$$
\%\text{ Change}
=
\frac{|\text{Previous Result}-\text{New Result}|}
{\text{New Result}}
\times100
$$

### Mesh Results

| Result | Mesh 1 | Mesh 2 | Mesh 3 |
|---|---:|---:|---:|
| Elements | 9,073 | 26,231 | 78,607 |
| Max Stress | 620.9 MPa | 548.1 MPa | 608.1 MPa |
| Max Displacement | 0.2893 mm | 0.2933 mm | 0.2964 mm |
| Minimum FOS | 0.4027 | 0.4561 | 0.4111 |

### Mesh 1 → Mesh 2

Stress:

$$
\frac{|620.9-548.1|}{548.1}(100)
=
\boxed{13.28\%}
$$

Displacement:

$$
\frac{|0.2893-0.2933|}{0.2933}(100)
=
\boxed{1.36\%}
$$

Factor of safety:

$$
\frac{|0.4027-0.4561|}{0.4561}(100)
=
\boxed{11.73\%}
$$

Only displacement was below the 7% convergence requirement, so the mesh was refined again.

### Mesh 2 → Mesh 3

Stress:

$$
\frac{|548.1-608.1|}{608.1}(100)
=
\boxed{9.87\%}
$$

Displacement:

$$
\frac{|0.2933-0.2964|}{0.2964}(100)
=
\boxed{1.05\%}
$$

Factor of safety:

$$
\frac{|0.4561-0.4111|}{0.4111}(100)
=
\boxed{10.96\%}
$$

The stress and factor-of-safety results were still above the 7% convergence requirement.

However, this was the **third mesh attempt**, so the finer Mesh 3 results were used as the final Design I values according to the assignment procedure.

---

## Final Design I Results

> **Figure A7-6 — Design I final Mesh 3 von Mises stress**

<img src="../../assets/images/69.png" alt="Design I Mesh 3 final von Mises stress" style="width:100%; height:auto;">

> **Figure A7-7 — Design I final Mesh 3 displacement**

<img src="../../assets/images/70.png" alt="Design I Mesh 3 final displacement" style="width:100%; height:auto;">

> **Figure A7-8 — Design I final Mesh 3 factor of safety**

<img src="../../assets/images/71.png" alt="Design I Mesh 3 final factor of safety" style="width:100%; height:auto;">

Final Design I:

| Result | Value |
|---|---:|
| Maximum Stress | 608.1 MPa |
| Maximum Displacement | 0.2964 mm |
| Minimum FOS | 0.4111 |
| Mass | 2.70 lb |
| Elements | 78,607 |

The high stress around Feature B indicated that this part of the geometry should be modified during the next outer loop.

---

# Outer Loop 2 — Design II

The first geometry modification increased the **front-view width of Feature B**.

The width was changed from:

$$
0.498\text{ in}
\rightarrow
0.625\text{ in}
$$

The axial thickness remained:

$$
T_B=0.375\text{ in}
$$

This distinction was important because the cylinder must retain sufficient usable length for the **3/4 in strap**.

Increasing the axial thickness would reduce that strap-clearance space.

Increasing the front-view width instead added material directly to the critical load path while preserving the strap interface.

> **Figure A7-9 — Design II Feature B increased to 0.625 in**

<img src="../../assets/images/72.png" alt="Design II Feature B width increased to 0.625 inches" style="width:100%; height:auto;">

---

# Inner Loop 2 — Design II Mesh Convergence

| Result | Mesh 1 | Mesh 2 |
|---|---:|---:|
| Elements | 9,350 | 26,636 |
| Max Stress | 331.5 MPa | 352.8 MPa |
| Max Displacement | 0.2323 mm | 0.2362 mm |
| Minimum FOS | 0.7541 | 0.7087 |

## Mesh 1 → Mesh 2

Stress:

$$
\frac{|331.5-352.8|}{352.8}(100)
=
\boxed{6.04\%}
$$

Displacement:

$$
\frac{|0.2323-0.2362|}{0.2362}(100)
=
\boxed{1.65\%}
$$

Factor of safety:

$$
\frac{|0.7541-0.7087|}{0.7087}(100)
=
\boxed{6.41\%}
$$

All three values changed by less than 7%.

Therefore:

$$
\boxed{\text{Design II converged at Mesh 2}}
$$

A third mesh was not required.

---

## Final Design II Results

> **Figure A7-10 — Design II final Mesh 2 von Mises stress**

<img src="../../assets/images/73.png" alt="Design II Mesh 2 final von Mises stress" style="width:100%; height:auto;">

> **Figure A7-11 — Design II final Mesh 2 displacement**

<img src="../../assets/images/74.png" alt="Design II Mesh 2 final displacement" style="width:100%; height:auto;">

> **Figure A7-12 — Design II final Mesh 2 factor of safety**

<img src="../../assets/images/75.png" alt="Design II Mesh 2 final factor of safety" style="width:100%; height:auto;">

Final Design II:

| Result | Value |
|---|---:|
| Maximum Stress | 352.8 MPa |
| Maximum Displacement | 0.2362 mm |
| Minimum FOS | 0.7087 |
| Mass | 2.71 lb |
| Elements | 26,636 |

Compared with Design I, the maximum stress decreased by:

$$
\frac{608.1-352.8}{608.1}(100)
=
\boxed{42.0\%}
$$

The displacement decreased by:

$$
\frac{0.2964-0.2362}{0.2964}(100)
=
\boxed{20.3\%}
$$

The mass increased by only approximately:

$$
2.71-2.70
=
\boxed{0.01\text{ lb}}
$$

The widened Feature B therefore produced a major improvement in both stress and stiffness with very little increase in total mass.

The Design II stress plot showed localized high stress on the **front face of Feature B near its sharp upper transitions into the bracket**, with a smaller stress concentration near the lower cylinder transition.

This stress pattern motivated the next geometry change.

---

# Outer Loop 3 — Design III

Design III retained the wider Feature B from Design II and added **fillets to the upper and lower front transitions of Feature B**.

The goal was to remove the sharp transitions visible in the Design II stress plot and create a smoother load path.

The material, loading, fixtures, cylinder geometry, and Feature B axial thickness remained unchanged.

---

# Inner Loop 3 — Design III Mesh Convergence

| Result | Mesh 1 | Mesh 2 | Mesh 3 |
|---|---:|---:|---:|
| Elements | 9,366 | 27,852 | 78,494 |
| Max Stress | 325.9 MPa | 367.1 MPa | 369.4 MPa |
| Max Displacement | 0.2148 mm | 0.2183 mm | 0.2189 mm |
| Minimum FOS | 0.7671 | 0.6811 | 0.6767 |

## Mesh 1 → Mesh 2

Stress:

$$
\frac{|325.9-367.1|}{367.1}(100)
=
\boxed{11.22\%}
$$

Displacement:

$$
\frac{|0.2148-0.2183|}{0.2183}(100)
=
\boxed{1.60\%}
$$

Factor of safety:

$$
\frac{|0.7671-0.6811|}{0.6811}(100)
=
\boxed{12.63\%}
$$

Stress and factor of safety were not below the 7% criterion, so another refinement was required.

## Mesh 2 → Mesh 3

Stress:

$$
\frac{|367.1-369.4|}{369.4}(100)
=
\boxed{0.62\%}
$$

Displacement:

$$
\frac{|0.2183-0.2189|}{0.2189}(100)
=
\boxed{0.27\%}
$$

Factor of safety:

$$
\frac{|0.6811-0.6767|}{0.6767}(100)
=
\boxed{0.65\%}
$$

All three results were below 7%.

Therefore:

$$
\boxed{\text{Design III converged at Mesh 3}}
$$

---

## Final Design III Results

> **Figure A7-13 — Design III final Mesh 3 von Mises stress**

<img src="../../assets/images/76.png" alt="Design III Mesh 3 final von Mises stress" style="width:100%; height:auto;">

> **Figure A7-14 — Design III final Mesh 3 displacement**

<img src="../../assets/images/77.png" alt="Design III Mesh 3 final displacement" style="width:100%; height:auto;">

> **Figure A7-15 — Design III final Mesh 3 factor of safety**

<img src="../../assets/images/78.png" alt="Design III Mesh 3 final factor of safety" style="width:100%; height:auto;">

Final Design III:

| Result | Value |
|---|---:|
| Maximum Stress | 369.4 MPa |
| Maximum Displacement | 0.2189 mm |
| Minimum FOS | 0.6767 |
| Mass | 2.71 lb |
| Elements | 78,494 |

Design III had the **smallest displacement of the three designs**, making it the stiffest configuration tested.

However, the final peak stress was slightly higher than Design II.

---

# Design II vs. Design III Stress Distribution

A close comparison of the stress plots showed that the fillets changed how the stress was distributed through Feature B.

> **Figure A7-16 — Design III stress distribution around Feature B**

<img src="../../assets/images/79.png" alt="Close-up Design III stress distribution around Feature B and cylinder" style="width:100%; height:auto;">

In Design III, the high-stress region was more spread out across the transition between Feature B and the surrounding geometry.

The stress was no longer concentrated into as small of an area as it was in Design II.

> **Figure A7-17 — Design II localized Feature B stress**

<img src="../../assets/images/80.png" alt="Close-up Design II localized stress distribution around Feature B" style="width:100%; height:auto;">

Design II had smaller, more localized red regions near the sharp Feature B transitions.

The fillets therefore **redistributed the stress**, but they did not lower the numerical peak stress.

The maximum stress changed from:

$$
352.8\text{ MPa}
$$

in Design II to:

$$
369.4\text{ MPa}
$$

in Design III.

At the same time, the maximum displacement decreased from:

$$
0.2362\text{ mm}
$$

to:

$$
0.2189\text{ mm}
$$

Therefore, the fillets improved stiffness and produced a smoother stress distribution, but did not improve the peak-stress result.

---

# Final Required Design Comparison

| Required Result | Design I | Design II | Design III |
|---|---|---|---|
| **Max Stress and Location** | **608.1 MPa** — Feature B / cylinder junction | **352.8 MPa** — front face of Feature B near sharp transitions | **369.4 MPa** — front face of Feature B near filleted transition |
| **Max Deflection and Location** | **0.2964 mm** — lower/free end of cylinder | **0.2362 mm** — lower/free end of cylinder | **0.2189 mm** — lower/free end of cylinder |
| **Mass** | **2.70 lb** | **2.71 lb** | **2.71 lb** |
| **Safety Factor** | **0.4111** | **0.7087** | **0.6767** |
| **Number of Elements** | **78,607** | **26,636** | **78,494** |

---

# Final Design Decision

Design II was selected as the **best overall design of the three configurations tested**.

Design III was stiffer.

The improvement in displacement from Design II to Design III was:

$$
\frac{0.2362-0.2189}{0.2362}(100)
=
\boxed{7.32\%}
$$

However, Design III also increased peak stress relative to Design II:

$$
\frac{369.4-352.8}{352.8}(100)
=
\boxed{4.71\%}
$$

Design III also had a lower factor of safety:

$$
0.6767<0.7087
$$

Both designs had essentially the same mass:

$$
m=2.71\text{ lb}
$$

Therefore, Design II provided the better overall balance between:

- Maximum stress
- Stiffness
- Factor of safety
- Mass

The most effective change during the optimization was therefore the increase in Feature B width from **0.498 in to 0.625 in**.

---

# Safety Evaluation

Although Design II was the best design tested, the FEA results also revealed an important limitation.

The A36 yield strength shown in the simulations was approximately:

$$
S_y=2.50\times10^8\text{ Pa}
$$

or:

$$
S_y=250\text{ MPa}
$$

The maximum Design II stress was:

$$
\sigma_{\max}=352.8\text{ MPa}
$$

and its minimum factor of safety was:

$$
N_{\min}=0.7087
$$

Since:

$$
N_{\min}<1
$$

the simulation predicts **local yielding under the modeled 1300 lbf load**.

The same is true for all three designs because each produced a factor of safety below 1.

Therefore, Design II should be considered the **best of the three designs evaluated in this optimization**, but additional redesign would still be required before considering the bracket fully elastic under this loading condition.

---

# Lessons Learned

## Mesh Convergence

One of the most important lessons from this assignment was that different FEA results can converge at different rates.

For Design I, displacement changed by only:

$$
1.05\%
$$

between Mesh 2 and Mesh 3, while stress still changed by:

$$
9.87\%
$$

This showed that a stable displacement result does not automatically mean that the stress result has converged.

Stress concentrations can remain highly sensitive to mesh density.

---

## Geometry Should Follow the Load Path

Increasing Feature B from 0.498 in to 0.625 in added material directly to the region carrying the load from the cylinder into the bracket.

This change reduced the final maximum stress by approximately:

$$
\boxed{42.0\%}
$$

while increasing total mass by only approximately:

$$
\boxed{0.01\text{ lb}}
$$

This demonstrated that strategically adding a small amount of material can be more effective than increasing the size of the entire bracket.

---

## Fillets Do Not Automatically Lower Peak Stress

The Design III fillets produced a visibly smoother and more distributed stress field.

However, the maximum stress increased slightly from 352.8 MPa to 369.4 MPa.

This showed that a smoother-looking stress plot does not automatically mean that the maximum numerical stress is lower.

The actual converged values must still be compared.

---

## Strength and Stiffness Can Favor Different Designs

Design III produced the smallest displacement, while Design II produced the lowest stress and highest factor of safety.

Therefore, selecting the best design required evaluating multiple performance measures rather than optimizing only one quantity.

---

## FEA and Hand Calculations Serve Different Purposes

The analytical work from A5 modeled individual features using simplified axial and beam equations.

The FEA model evaluated the complete three-dimensional bracket and revealed local stress concentrations around Feature B that were difficult to represent using the simplified calculations alone.

The two methods are therefore complementary:

- Hand calculations provide initial sizing and physical understanding.
- FEA shows how the complete geometry actually transfers load and where local stress concentrations occur.

---

# Conclusion

Three outer-loop bracket designs were evaluated using static FEA.

Each design was checked using its own inner mesh-convergence loop.

### Design I

The original bracket produced:

$$
\sigma_{\max}=608.1\text{ MPa}
$$

and:

$$
N_{\min}=0.4111
$$

with a major stress concentration around Feature B.

### Design II

Increasing the Feature B width from:

$$
0.498\text{ in}
\rightarrow
0.625\text{ in}
$$

reduced maximum stress to:

$$
352.8\text{ MPa}
$$

and increased the minimum factor of safety to:

$$
0.7087
$$

with almost no increase in mass.

### Design III

Adding fillets around the Feature B transitions reduced maximum displacement to:

$$
0.2189\text{ mm}
$$

but increased the maximum stress slightly to:

$$
369.4\text{ MPa}
$$

Therefore:

$$
\boxed{\text{Design II was selected as the best overall tested design}}
$$

Its final results were:

$$
\boxed{\sigma_{\max}=352.8\text{ MPa}}
$$

$$
\boxed{\delta_{\max}=0.2362\text{ mm}}
$$

$$
\boxed{N_{\min}=0.7087}
$$

$$
\boxed{m=2.71\text{ lb}}
$$

Further redesign would still be required to obtain a factor of safety greater than 1 under the modeled 1300 lbf load.

---

# Time Spent

The total time spent completing A7 was approximately:

$$
\boxed{2\text{ hours}}
$$
