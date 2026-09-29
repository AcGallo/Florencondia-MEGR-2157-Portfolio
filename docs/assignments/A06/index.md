# A6 - Bracket Drawing and Parametric Design

## Objective

The objective of A6 was to continue the bracket developed in A5 by turning the final design into a **parametrically controlled SolidWorks model** and a **fully dimensioned engineering drawing**.

A5 established the final bracket geometry from the strength, stiffness, and T-beam fit requirements. A6 focused on carrying those design decisions into CAD in a more controlled way and then communicating the final part with a professional drawing.

The main goals were to:

- convert the important A5 design dimensions into SolidWorks global variables and equations,
- preserve the final A5 bracket geometry,
- verify the material and final parametric model,
- create a **third-angle multiview drawing**,
- fully dimension the part without unnecessary duplicate dimensions,
- apply engineered tolerances to the critical T-beam sliding interfaces,
- and export the final engineering drawing as a PDF.

> **Figure A6-1 - Final bracket geometry used as the starting point for A6**
>
> <img src="../../assets/images/56.png" alt="Final A5 bracket geometry used as the starting point for A6" style="width:100%; height:auto;">

---

## Analyze

### Starting from the A5 Design

The A6 bracket uses the same final geometry selected during A5. The previous analysis showed that **stress governed the final size of all five features**, and the analytical minimums were rounded upward to practical CAD dimensions.

| Feature | Stress Minimum | Stiffness Minimum | Governing Requirement | Final A5 Dimension |
|---|---:|---:|---|---:|
| A - diameter | 0.9027 in | 0.3887 in | Stress | 1.000 in |
| B - thickness | 0.2900 in | 0.01350 in | Stress | 0.375 in |
| C - height | 0.7500 in | 0.3398 in | Stress | 0.875 in |
| D - thickness | 0.6580 in | 0.4096 in | Stress | 0.750 in |
| E - thickness | 0.6580 in | 0.2615 in | Stress | 0.750 in |

The final dimensions carried into A6 were:

| Parameter | Final Value |
|---|---:|
| Material | ASTM A36 Steel |
| Feature A diameter, \(D_A\) | 1.000 in |
| Feature A overall length, \(L_A\) | 1.000 in |
| Feature B width, \(w_B\) | 0.498 in |
| Feature B length, \(L_B\) | 0.750 in |
| Feature B thickness, \(T_B\) | 0.375 in |
| Feature C inside span, \(L_C\) | 2.5964 in |
| Feature C depth, \(w_C\) | 1.000 in |
| Feature C height, \(T_C\) | 0.875 in |
| Feature D opening height, \(L_D\) | 1.599 in |
| Feature D depth, \(w_D\) | 1.000 in |
| Feature D thickness, \(T_D\) | 0.750 in |
| Feature E reach, \(L_E\) | 0.9992 in |
| Feature E depth, \(w_E\) | 1.000 in |
| Feature E thickness, \(T_E\) | 0.750 in |
| Top center opening | 0.5980 in |

The A6 work therefore did not require a new structural design. The main engineering task was to make the CAD model and drawing communicate the existing design more clearly.

---

### T-Beam Fit Geometry

The bracket slides over the same rigid T-beam used in A5.

| T-Beam Dimension | Nominal Size | Given Tolerance |
|---|---:|---:|
| \(a\) | 0.498 in | \(+0.000/-0.001\) in |
| \(b\) | 0.9992 in | \(+0.0000/-0.0005\) in |
| \(c\) | 1.499 in | \(+0.000/-0.001\) in |

Because the given T-beam tolerances only allow the beam dimensions to become smaller, the nominal dimensions represent the largest fit condition.

The horizontal bracket opening is:

$$
L_C=a+2b+0.100
$$

$$
L_C=0.498+2(0.9992)+0.100
$$

$$
\boxed{L_C=2.5964\text{ in}}
$$

The vertical opening is:

$$
L_D=c+0.100
$$

$$
L_D=1.499+0.100
$$

$$
\boxed{L_D=1.599\text{ in}}
$$

The upper-arm reach is:

$$
\boxed{L_E=b=0.9992\text{ in}}
$$

The top center opening is:

$$
\text{Top Opening}=L_C-2L_E
$$

$$
\text{Top Opening}=2.5964-2(0.9992)
$$

$$
\boxed{\text{Top Opening}=0.5980\text{ in}}
$$

These fit-controlled dimensions were kept separate from the structural thicknesses so that the drawing could clearly distinguish between **fit requirements** and **strength-controlled dimensions**.

---

## Parametric CAD Model

### Global Variables and Equations

The original A5 bracket was modeled mostly with directly entered dimensions. For A6, the important design values were organized using SolidWorks **global variables and equations**.

The main parameter set included:

```text
a = 0.498 in
b = 0.9992 in
c = 1.499 in
Clearance = 0.100 in

DA = 1.000 in
LA = 1.000 in

wB = 0.498 in
LB = 0.750 in
TB = 0.375 in

wC = 1.000 in
TC = 0.875 in

wD = 1.000 in
TD = 0.750 in

wE = 1.000 in
TE = 0.750 in
```

The fit-controlled dimensions were then related to the T-beam variables:

$$
L_C=a+2b+\text{Clearance}
$$

$$
L_D=c+\text{Clearance}
$$

$$
L_E=b
$$

$$
\text{TopGap}=L_C-2L_E
$$

The overall geometry can also be checked from:

$$
W_{\text{overall}}=L_C+2T_D
$$

$$
W_{\text{overall}}=2.5964+2(0.750)
$$

$$
\boxed{W_{\text{overall}}=4.0964\text{ in}}
$$

and:

$$
H=T_C+L_D+T_E
$$

$$
H=0.875+1.599+0.750
$$

$$
\boxed{H=3.224\text{ in}}
$$

> **Figure A6-2 - SolidWorks global variables and equation table**
>
> <img src="../../assets/images/57.png" alt="SolidWorks global variables and equations controlling the A6 bracket" style="width:100%; height:auto;">

---

### Linking the Main Sketch

The main bracket profile in Sketch1 was updated so that the important dimensions were tied to the named design parameters rather than remaining as isolated numerical values.

Examples include:

- Feature A diameter controlled by \(D_A\),
- Feature B width controlled by \(w_B\),
- Feature B length controlled by \(L_B\),
- Feature C height controlled by \(T_C\),
- Feature D thickness controlled by \(T_D\),
- Feature E thickness controlled by \(T_E\),
- Feature E reach controlled by \(L_E\),
- and the fit-controlled opening dimensions tied back to the T-beam geometry.

The Feature A sketch uses a radius, so the circular dimension was related to the diameter parameter using:

$$
R_A=\frac{D_A}{2}
$$

With:

$$
D_A=1.000\text{ in}
$$

the sketch radius remains:

$$
\boxed{R_A=0.500\text{ in}}
$$

> **Figure A6-3 - Main parametric sketch with the A5 design dimensions**
>
> <img src="../../assets/images/58.png" alt="Main A6 SolidWorks sketch showing the parametric bracket dimensions" style="width:100%; height:auto;">

---

### Analysis Equation Used in the Parameter Set

One of the useful connections between the A5 calculations and the A6 CAD model is Feature B.

For Feature B:

$$
\sigma=\frac{P_B}{w_BT_B}
$$

Solving for the minimum thickness gives:

$$
T_{B,\text{stress}}
=
\frac{P_B}{w_B\sigma_{\text{allow}}}
$$

Using:

$$
P_B=1300\text{ lbf}
$$

$$
w_B=0.498\text{ in}
$$

and:

$$
\sigma_{\text{allow}}
=
\frac{36,000}{4}
=
9000\text{ psi}
$$

gives:

$$
T_{B,\text{stress}}
=
\frac{1300}
{(0.498)(9000)}
$$

$$
\boxed{T_{B,\text{stress}}\approx0.290\text{ in}}
$$

The parameter table retained this analytical result while the final Feature B thickness remained the practical A5 selection:

$$
\boxed{T_B=0.375\text{ in}}
$$

This is an example of how the analytical result and the selected manufacturing dimension can exist together in the parametric design instead of being treated as unrelated values.

---

### Material

The final part material was set to **ASTM A36 Steel**, matching the material used in the A5 analysis.

The important A5 material properties were:

$$
S_y=36,000\text{ psi}
$$

$$
E\approx29\times10^6\text{ psi}
$$

> **Figure A6-4 - ASTM A36 Steel assigned to the final bracket model**
>
> <img src="../../assets/images/60.png" alt="SolidWorks material window showing ASTM A36 Steel assigned to the bracket" style="width:100%; height:auto;">

---

### Sketch2 Correction

During the conversion to the A6 model, Sketch2 became **over-defined** because two coincident relations conflicted with the revised geometry.

Rather than rebuilding the entire feature, the conflicting relations were identified, removed, and the sketch was reconstructed with only the necessary constraints.

This preserved the original bracket geometry while removing the sketch error.

> **Figure A6-5 - Secondary bracket sketch after correcting the conflicting relations**
>
> <img src="../../assets/images/61.png" alt="Corrected secondary SolidWorks sketch used in the A6 bracket" style="width:100%; height:auto;">

---

## Engineering Drawing

### Third-Angle Multiview

The final engineering drawing uses **third-angle projection**.

The primary views are:

- Front view
- Top view
- Right-side view

An isometric view was also included as a visual reference.

The drawing scale is **1:2**, while all written dimensions represent the true part dimensions.

The final drawing includes:

- the main bracket dimensions,
- centerlines and center marks,
- Feature A diameter,
- Feature B dimensions,
- the T-beam fit openings,
- critical engineered tolerances,
- material identification,
- a general tolerance block,
- drawing title and number,
- and a third-angle projection note.

---

### Dimensioning Strategy

The drawing was dimensioned so that the critical geometry could be manufactured without unnecessary duplicate dimensions.

For example, the vertical geometry is defined using:

$$
T_E=0.750\text{ in}
$$

$$
L_D=1.599\text{ in}
$$

$$
T_C=0.875\text{ in}
$$

instead of also adding the redundant overall height of 3.224 in.

Likewise, the internal horizontal opening \(L_C\) was dimensioned directly instead of requiring the manufacturer to calculate it from the overall bracket width and the two side-wall thicknesses.

This is especially important because \(L_C\) is a functional fit dimension.

---

### Engineered Fit Tolerances

Three dimensions directly control the sliding interface between the bracket and the T-beam:

$$
\boxed{L_C=2.596\pm0.005\text{ in}}
$$

$$
\boxed{L_D=1.599\pm0.005\text{ in}}
$$

$$
\boxed{\text{Top Opening}=0.598\pm0.005\text{ in}}
$$

These dimensions were explicitly toleranced because they control whether the bracket can physically slide onto the rail.

The minimum possible bracket openings are:

$$
L_{C,\min}=2.596-0.005=2.591\text{ in}
$$

$$
L_{D,\min}=1.599-0.005=1.594\text{ in}
$$

$$
\text{Top Opening}_{\min}=0.598-0.005=0.593\text{ in}
$$

The corresponding maximum T-beam dimensions are the nominal values:

$$
a+2b
=
0.498+2(0.9992)
=
2.4964\text{ in}
$$

$$
c=1.499\text{ in}
$$

$$
a=0.498\text{ in}
$$

Therefore, even at the minimum bracket dimensions:

$$
2.591-2.4964
=
\boxed{0.0946\text{ in}}
$$

$$
1.594-1.499
=
\boxed{0.095\text{ in}}
$$

$$
0.593-0.498
=
\boxed{0.095\text{ in}}
$$

The specified tolerances therefore preserve approximately **0.095 in of minimum total clearance** at each critical fit condition.

---

### General Tolerance Block

The final drawing also includes the required general tolerance block:

```text
UNLESS OTHERWISE SPECIFIED:
DIMENSIONS ARE IN INCHES

TOLERANCES:
X.X   ± .02
X.XX  ± .01
X.XXX ± .005
```

Critical fit dimensions were given their own explicit tolerances, while the remaining dimensions use the general block where applicable.

The drawing title block identifies:

- **Material:** ASTM A36 Steel
- **Title:** A6 BRACKET
- **Drawing Number:** A6-BRACKET-001
- **Scale:** 1:2
- **Projection:** Third Angle
- **Date:** 09/29/2026

> **Figure A6-6 - Final A6 third-angle engineering drawing**
>
> <img src="../../assets/images/63.png" alt="Final A6 bracket engineering drawing with dimensions, tolerances, title block, and third-angle views" style="width:100%; height:auto;">

---

## Decide

### Final A6 Design

The final A6 design retained the structural dimensions selected during A5 because those dimensions had already been verified against the allowable stress and maximum-deflection requirements.

The controlling final dimensions remained:

$$
\boxed{
D_A=1.000,\;
T_B=0.375,\;
T_C=0.875,\;
T_D=0.750,\;
T_E=0.750\text{ in}
}
$$

The fit-controlled dimensions remained:

$$
\boxed{
L_C=2.5964,\;
L_D=1.599,\;
L_E=0.9992\text{ in}
}
$$

with:

$$
\boxed{\text{Top Opening}=0.5980\text{ in}}
$$

The important change in A6 was not the bracket shape. The improvement was in how the design was **controlled and communicated**.

Using global variables and equations makes the CAD model easier to understand and modify, while the engineering drawing communicates the final dimensions and tolerances required to manufacture the part.

---

## Communicate

### Parametric Modeling

The main lesson from the parametric portion of A6 was that a CAD model can have the correct dimensions without necessarily being easy to control.

The original A5 model had the correct geometry, but most values were entered directly into the sketches. Moving the important dimensions into named parameters made the design intent more visible.

This was especially useful for the dimensions that depend directly on the T-beam geometry, such as:

$$
L_C=a+2b+\text{Clearance}
$$

and:

$$
L_D=c+\text{Clearance}
$$

These relationships show where the final dimensions came from instead of treating them as unexplained numbers.

---

### Tolerancing Decisions

The drawing also reinforced the difference between a **nominal dimension** and a **functional manufactured dimension**.

The three fit dimensions were intentionally given explicit ±0.005 in tolerances because they directly control the bracket-to-T-beam interface.

Other dimensions, such as the structural thicknesses, can use the general tolerance block because small variations in those dimensions do not control whether the bracket can slide onto the rail.

This avoids applying unnecessarily tight tolerances to every dimension while still protecting the dimensions that matter most for function.

---

### Problems Encountered

A6 took longer than expected because several SolidWorks issues appeared while converting the model.

The first problem occurred while entering the global-variable equations. SolidWorks froze while an incomplete equation was being evaluated, forcing the program to be closed and reopened.

The second problem occurred in Sketch2. After the main sketch dimensions were changed, Sketch2 became over-defined because two coincident relations conflicted with the revised geometry.

The sketch was repaired by identifying the conflicting relations and removing them rather than rebuilding the complete part.

These problems showed that parametric modeling is not only about writing equations. Existing sketch relations also have to remain compatible with the new parameter relationships.

---

### Lessons Learned

A5 focused mainly on determining whether the bracket was strong and stiff enough. A6 showed that the next part of the engineering process is making the final design **controllable, manufacturable, and understandable to another person**.

The biggest lessons from A6 were:

- A correct CAD shape is not automatically a good parametric model.
- Named parameters make the connection between calculations and CAD easier to follow.
- Fit dimensions should be dimensioned directly instead of relying on tolerance stack-ups from unrelated dimensions.
- Critical tolerances should protect function without making every dimension unnecessarily precise.
- Sketch relations can conflict when dimensions are converted to equations, so changes need to be checked carefully.
- A completed engineering drawing communicates information that the 3D model alone does not show.

---

### Time Spent

The total time spent completing A6 was approximately:

$$
\boxed{5\text{ hours}}
$$

The work was completed on and off. A significant portion of the time was spent converting the existing A5 model into a parametric model, troubleshooting the SolidWorks equation and sketch-relation problems, and cleaning up the final engineering drawing.

---

## CAD and Drawing Downloads

The final A6 files are linked below.

[Download A6 Parametric Bracket SolidWorks Part](../../assets/files/A6_Bracket_Florencondia.SLDPRT)

[Download A6 Bracket SolidWorks Drawing](../../assets/files/A6_Bracket_Florencondia.SLDDRW)

[Download A6 Engineering Drawing PDF](../../assets/files/A6_Bracket_Florencondia.pdf)

---

## References

1. MEGR 2156 A6 assignment instructions.
2. MEGR 2156 A5 Bracket Design calculations and final dimensions.
3. *Machinery's Handbook*, 32nd Edition - standard drafting and dimensioning practices.
4. SolidWorks global variables, equations, parametric modeling, and engineering drawing tools.
