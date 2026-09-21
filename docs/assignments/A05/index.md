# A5 — Design for Strength and Stiffness I

## Objective

The objective of this assignment was to design a bracket capable of supporting the required horizontal load while satisfying both **strength** and **stiffness** requirements. The bracket was analyzed as a sequence of five connected features, labeled **A through E**, so that the reaction or internal load determined from one feature could be carried into the next. Each feature was evaluated using an appropriate free-body diagram, a strength model, and a stiffness model before the final dimensions were selected.

The design was completed using a **factor of safety of 4** and a maximum allowable deflection of **0.005 in per feature**. Direct shear failure was neglected as instructed, and shear deformation was assumed negligible during stiffness analysis.

> **Figure 46 — Assignment geometry and feature identification used for the A5 bracket analysis**

<img src="../../assets/images/46.png" alt="A5 assignment geometry and labeled bracket features" style="width:100%; height:auto;">

---

# Design Inputs and Assumptions

The bracket was analyzed using a design load within the required range of **500–800 lbf** and one of the permitted engineering materials. Material properties were kept consistent throughout the strength and stiffness calculations.

The following assumptions were used throughout the analysis:

- The applied loading is symmetric where the geometry permits.
- The material remains within the linear-elastic range.
- Direct shear failure is neglected as specified by the assignment.
- Shear deformation is neglected for stiffness calculations.
- Idealized beam and axial-member models are used where appropriate.
- Loads and reactions obtained from earlier features are transferred into later feature analyses.
- The final design dimension for each feature is selected from the more restrictive of the strength and stiffness requirements.

---

# 1. Strength Analysis

The strength analysis was performed first to determine the minimum dimensions required to prevent yielding. For each feature, the allowable stress was determined from the selected material yield strength and the required factor of safety:

$$\sigma_{\text{allow}}=\frac{S_y}{SF}$$

with

$$SF=4$$

The load path was followed from Feature A through Feature E so that each reaction could be used in the next stage of the analysis.

---

## Feature A — Strength

Feature A forms the lower cylindrical member and is treated as a **cantilever beam** according to the guidance provided in Appendix D. The applied strap load produces bending in the member, so the section was sized using the maximum bending-stress requirement.

The analysis begins by determining the internal bending moment from the applied load and geometry. The required section size is then obtained by limiting the maximum bending stress to the allowable material stress.

> **Figure 47 — Feature A free-body diagram and strength calculations**

<img src="../../assets/images/47.png" alt="Feature A strength free body diagram and calculations" style="width:100%; height:auto;">

The governing strength relationship is based on bending:

$$\sigma_{\max}=\frac{M}{Z}$$

where \(M\) is the maximum bending moment and \(Z\) is the section modulus of the cylindrical member.

The resulting minimum Feature A dimension was carried forward into the geometry used for Feature B.

---

## Feature B — Strength

Feature B transfers the load vertically through the bracket and was modeled as an **axially loaded member**. The reaction obtained from Feature A was used as the applied axial force for this portion of the analysis.

> **Figure 48 — Feature B free-body diagram and axial-strength calculations**

<img src="../../assets/images/48.png" alt="Feature B strength free body diagram and calculations" style="width:100%; height:auto;">

The average normal stress was determined from:

$$\sigma=\frac{F}{A}$$

The minimum cross-sectional area was obtained by requiring:

$$\sigma\leq\sigma_{\text{allow}}$$

The resulting Feature B dimension establishes the minimum section required to carry the transferred axial load without yielding.

---

## Feature C — Strength

Feature C was modeled as a **simply supported beam with a concentrated load at its center**, following the guidance in Appendix D. The reaction forces were first determined using equilibrium, followed by calculation of the maximum bending moment.

> **Figure 49 — Feature C free-body diagram, support reactions, and bending-strength calculations**

<img src="../../assets/images/49.png" alt="Feature C strength free body diagram and bending calculations" style="width:100%; height:auto;">

The maximum bending stress was evaluated using:

$$\sigma_{\max}=\frac{M_{\max}}{Z}$$

The section geometry was then sized so that the calculated bending stress remained below the allowable stress.

---

## Feature D — Strength

Feature D transfers the loading from the upper portion of the bracket into the surrounding frame. The free-body diagram was created from the actual load path so that the internal force and moment acting on the feature could be identified before selecting the appropriate stress model.

> **Figure 50 — Feature D free-body diagram and strength calculations**

<img src="../../assets/images/50.png" alt="Feature D strength free body diagram and calculations" style="width:100%; height:auto;">

The resulting section dimensions were selected so that the maximum calculated normal or bending stress remained within the allowable stress for the chosen material.

---

## Feature E — Strength

Feature E completes the load path into the upper bracket geometry. The reaction transferred from Feature D was applied to the Feature E free-body diagram and used to determine the final strength-based section requirement.

> **Figure 51 — Feature E free-body diagram and strength calculations**

<img src="../../assets/images/51.png" alt="Feature E strength free body diagram and calculations" style="width:100%; height:auto;">

The final Feature E strength dimension was determined using the governing normal or bending-stress condition from the completed free-body diagram.

---

## Strength-Based Multiview Drawing

After completing all five strength calculations, the resulting dimensions were assembled into a complete multiview drawing. This drawing represents the bracket if **strength alone** governed the design.

> **Figure 52 — Detailed multiview drawing using the strength-based dimensions**

<img src="../../assets/images/52.png" alt="Strength based A5 bracket multiview drawing" style="width:100%; height:auto;">

---

# 2. Stiffness Analysis

The complete bracket was then analyzed a second time using the assignment stiffness requirement. Each feature was independently limited to a maximum deformation of:

$$\delta_{\max}=0.005\text{ in}$$

The same load path used during the strength analysis was maintained so that the stiffness calculations remained consistent with the previously determined reactions.

---

## Feature A — Stiffness

Feature A was again modeled as a cantilever beam. Instead of limiting stress, the section size was selected so that the maximum deflection did not exceed the allowable value.

> **Figure 53 — Feature A free-body diagram and stiffness calculations**

<img src="../../assets/images/53.png" alt="Feature A stiffness free body diagram and calculations" style="width:100%; height:auto;">

The elastic beam-deflection model was evaluated using the selected material modulus of elasticity and the Feature A geometry. The section dimension was then solved from the requirement:

$$\delta_A\leq0.005\text{ in}$$

---

## Feature B — Stiffness

Because Feature B behaves primarily as an axially loaded member, its elastic deformation was determined using:

$$\delta=\frac{FL}{AE}$$

> **Figure 54 — Feature B axial-deformation and stiffness calculations**

<img src="../../assets/images/54.png" alt="Feature B axial deformation and stiffness calculations" style="width:100%; height:auto;">

The minimum Feature B area was selected so that:

$$\delta_B\leq0.005\text{ in}$$

This requirement was then converted into the corresponding physical section dimension used in the bracket model.

---

## Feature C — Stiffness

Feature C was modeled as a simply supported beam with a concentrated center load. The same reactions and loading pattern used during the strength calculation were applied to the beam-deflection model.

> **Figure 55 — Feature C free-body diagram and stiffness calculations**

<img src="../../assets/images/55.png" alt="Feature C stiffness free body diagram and calculations" style="width:100%; height:auto;">

The required section dimension was obtained by limiting the maximum beam deflection to:

$$\delta_C\leq0.005\text{ in}$$

---

## Feature D — Stiffness

Feature D was evaluated using the elastic deformation model corresponding to its load path and support condition. The same idealization used in the strength analysis was retained so that the two resulting dimensions could be compared directly.

> **Figure 56 — Feature D free-body diagram and stiffness calculations**

<img src="../../assets/images/56.png" alt="Feature D stiffness free body diagram and calculations" style="width:100%; height:auto;">

The section was sized so that the calculated deformation remained below the 0.005 in limit.

---

## Feature E — Stiffness

The final stiffness analysis was performed on Feature E using the reaction transferred from Feature D. The section dimensions were solved from the elastic deformation requirement and compared with the previously determined strength dimensions.

> **Figure 57 — Feature E free-body diagram and stiffness calculations**

<img src="../../assets/images/57.png" alt="Feature E stiffness free body diagram and calculations" style="width:100%; height:auto;">

The selected stiffness-based dimension satisfies:

$$\delta_E\leq0.005\text{ in}$$

---

## Stiffness-Based Multiview Drawing

A second detailed multiview drawing was created using the dimensions obtained from the stiffness analysis. This drawing shows how the bracket geometry changes when deformation, rather than yielding, controls the design.

> **Figure 58 — Detailed multiview drawing using the stiffness-based dimensions**

<img src="../../assets/images/58.png" alt="Stiffness based A5 bracket multiview drawing" style="width:100%; height:auto;">

---

# 3. Governing Dimensions

The strength and stiffness results were compared feature-by-feature. The final design uses the larger required dimension in each case:

$$\boxed{\text{Final dimension}=\max\left(\text{strength requirement},\text{stiffness requirement}\right)}$$

This approach ensures that every feature satisfies both the material strength requirement and the allowable-deflection requirement.

| Feature | Strength Analysis | Stiffness Analysis | Governing Requirement |
|---|---|---|---|
| **A** | See Figure 47 | See Figure 53 | Larger calculated requirement |
| **B** | See Figure 48 | See Figure 54 | Larger calculated requirement |
| **C** | See Figure 49 | See Figure 55 | Larger calculated requirement |
| **D** | See Figure 50 | See Figure 56 | Larger calculated requirement |
| **E** | See Figure 51 | See Figure 57 | Larger calculated requirement |

The governing dimensions from this comparison were used to build the final parametric CAD model.

---

# 4. Final CAD Model

The final bracket was modeled in SolidWorks using the governing dimensions determined from the strength and stiffness comparison. The CAD model preserves the load path used during the analytical work and incorporates the required interface geometry for the T-beam and strap system.

> **Figure 59 — Final A5 bracket CAD model**

<img src="../../assets/images/59.png" alt="Final A5 bracket CAD model" style="width:100%; height:auto;">

The finished model was checked against the calculated dimensions before preparing the final deliverable.

> **Figure 60 — Final CAD model with dimensional verification**

<img src="../../assets/images/60.png" alt="Final A5 CAD model dimensional verification" style="width:100%; height:auto;">

### CAD Files

- [Download the A5 SolidWorks Part](../../assets/files/A5_Bracket_Florencondia.SLDPRT)
- [Download the A5 supporting CAD file](../../assets/files/A5_Bracket_Support_Florencondia.SLDPRT)

---

# 5. Lessons Learned

## Governing Failure Mode

One of the most important observations from this assignment was that **strength and stiffness do not necessarily produce the same minimum geometry**. A feature can remain safely below the material yield stress while still deflecting more than the design allows. Comparing both requirements before choosing the final dimension prevents a design from being technically strong enough but functionally too flexible.

For each feature, the governing dimension was therefore selected from the larger of the stress-based and stiffness-based requirements rather than assuming that material strength alone controlled the design.

## Error Propagation

The feature-by-feature load path made it clear that an error early in the analysis can propagate into later calculations. Reaction forces determined from one free-body diagram become applied loads for the next feature, so each equilibrium calculation was checked before being carried forward.

This was especially important when moving from Feature A into the remaining bracket geometry. Verifying the force direction, magnitude, and units before beginning the next analysis prevented an incorrect reaction from affecting multiple downstream dimensions.

## Assumption Sensitivity

The final geometry depends strongly on the assumptions used in the analytical model. In particular, the selected material modulus of elasticity directly affects the stiffness-based dimensions. A material with a lower modulus would require larger sections to maintain the same 0.005 in deflection limit even if its yield strength were comparable.

The assumption that shear deformation is negligible also simplifies the stiffness analysis. If shear deformation became significant because of a short or thick member geometry, the actual total deformation would be larger than the beam-only prediction and the required section size could increase.

---

# Conclusion

This assignment demonstrated the difference between designing for **strength** and designing for **stiffness**. The bracket was treated as a connected load path rather than as a single isolated component, allowing each reaction to be transferred into the next feature analysis. Five strength analyses and five stiffness analyses were completed, followed by a comparison of the resulting dimensions.

The final CAD geometry was selected using the governing requirement for each feature so that the bracket satisfies both the material strength limit and the maximum allowable deformation requirement. The completed design process combines equilibrium, stress analysis, elastic deformation, free-body diagrams, and parametric CAD into a single reproducible engineering workflow.

---

# Time Spent

Approximately **___ hours** were spent completing the analysis, drawings, CAD model, and documentation for this assignment.
