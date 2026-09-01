# A2 – Truss Stress Analysis

## Objective

The objective of this assignment was to design a lightweight planar truss and determine the required member and pin sizes using basic stress equations. I used statics to calculate the support reactions and internal member forces, then used the largest calculated force to size the common truss-member cross-section. The final design was modeled in SolidWorks so the CAD mass could be compared with the analytical mass.

> **Figure #1 — Assignment constraints**
![Figure #1: Assignment constraints](../../assets/images/1.png)

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
- **Member safety factor = 3.5**
- **Pin safety factor = 4**

The joint coordinates are:

$$
B=(0,b)
$$

$$
C=(a,0)
$$

$$
E=\left(\frac{3a}{2},b\right)
$$

$$
D=(2a,0)
$$

$$
A=(3a,b)
$$

The five joints are **A, B, C, D, and E**. The seven truss members are **BE, EA, BC, CE, ED, AD, and CD**.

> **Figure #2 — Final truss geometry dimensions with a = 0.4 m and b = 0.3 m**
![Figure #2: Final truss geometry dimensions](../../assets/images/2.png)

The diagonal member lengths are:

$$
L_1=\sqrt{a^2+b^2}
$$

$$
L_1=\sqrt{(0.4)^2+(0.3)^2}
$$

$$
\boxed{L_1=0.500\text{ m}}
$$

and

$$
L_2=\sqrt{\left(\frac{a}{2}\right)^2+b^2}
$$

$$
L_2=\sqrt{\left(\frac{0.4}{2}\right)^2+(0.3)^2}
$$

$$
\boxed{L_2=0.3606\text{ m}}
$$

Therefore:

| Member | Length |
|---|---:|
| BE | 0.600 m |
| EA | 0.600 m |
| BC | 0.500 m |
| AD | 0.500 m |
| CE | 0.3606 m |
| ED | 0.3606 m |
| CD | 0.400 m |

The total centerline length is:

$$
L_{\text{total}}=4a+2L_1+2L_2
$$

$$
L_{\text{total}}=4(0.4)+2(0.5)+2(0.360555)
$$

$$
\boxed{L_{\text{total}}=3.3211\text{ m}}
$$

### Free-Body Diagrams

The overall free-body diagram shows the two applied loads and the support reactions at A and B. At joint A, the unknown reactions are $A_x$ and $A_y$, while the roller at B has reaction $B_y$. The reaction arrows were initially assumed before solving, so a negative result means the true force acts in the opposite direction.

Separate free-body diagrams were also made for joints A, B, C, D, and E. Unknown member forces were initially assumed to be in tension and drawn away from each joint. A negative result therefore indicates compression.

> **Figure #3 — Overall truss free-body diagram**
![Figure #3: Overall truss free-body diagram](../../assets/images/3.png)

> **Figure #4 — Joint A and Joint B free-body diagrams**
![Figure #4: Joint A and Joint B free-body diagrams](../../assets/images/4.png)

> **Figure #5 — Joint C, Joint D, and Joint E free-body diagrams**
![Figure #5: Joint C, Joint D, and Joint E free-body diagrams](../../assets/images/5.png)

### Support Reactions

Taking moments about B:

$$
\sum M_B=0
$$

$$
A_y(3a)+P(a)-P(2a)=0
$$

$$
3aA_y-aP=0
$$

$$
A_y=\frac{P}{3}
$$

$$
A_y=\frac{25}{3}
$$

$$
\boxed{A_y=8.333\text{ kN}}
$$

Using vertical equilibrium:

$$
\sum F_y=0
$$

$$
A_y+B_y+P-P=0
$$

$$
B_y=-A_y=-\frac{P}{3}
$$

$$
\boxed{B_y=-8.333\text{ kN}}
$$

The negative sign means the actual reaction at B acts downward relative to the initially assumed upward direction.

Using horizontal equilibrium:

$$
\sum F_x=0
$$

$$
\boxed{A_x=0}
$$

### Symbolic Member Forces

Tension is taken as positive.

#### Joint B

$$
\sum F_y=0
$$

$$
B_y-\frac{b}{L_1}F_{BC}=0
$$

$$
-\frac{P}{3}-\frac{b}{L_1}F_{BC}=0
$$

$$
\boxed{F_{BC}=-\frac{PL_1}{3b}}
$$

$$
\sum F_x=0
$$

$$
F_{BE}+\frac{a}{L_1}F_{BC}=0
$$

$$
\boxed{F_{BE}=\frac{aP}{3b}}
$$

#### Joint A

$$
\sum F_y=0
$$

$$
A_y-\frac{b}{L_1}F_{AD}=0
$$

$$
\frac{P}{3}-\frac{b}{L_1}F_{AD}=0
$$

$$
\boxed{F_{AD}=\frac{PL_1}{3b}}
$$

$$
\sum F_x=0
$$

$$
-F_{EA}-\frac{a}{L_1}F_{AD}=0
$$

$$
\boxed{F_{EA}=-\frac{aP}{3b}}
$$

#### Joint C

$$
\sum F_y=0
$$

$$
P+\frac{b}{L_1}F_{BC}+\frac{b}{L_2}F_{CE}=0
$$

$$
P-\frac{P}{3}+\frac{b}{L_2}F_{CE}=0
$$

$$
\boxed{F_{CE}=-\frac{2PL_2}{3b}}
$$

$$
\sum F_x=0
$$

$$
-\frac{a}{L_1}F_{BC}+F_{CD}+\frac{a}{2L_2}F_{CE}=0
$$

$$
\boxed{F_{CD}=0}
$$

#### Joint D

$$
\sum F_y=0
$$

$$
-P+\frac{b}{L_1}F_{AD}+\frac{b}{L_2}F_{ED}=0
$$

$$
-P+\frac{P}{3}+\frac{b}{L_2}F_{ED}=0
$$

$$
\boxed{F_{ED}=\frac{2PL_2}{3b}}
$$

$$
\sum F_x=0
$$

$$
\frac{a}{L_1}F_{AD}-F_{CD}-\frac{a}{2L_2}F_{ED}=0
$$

$$
\boxed{F_{CD}=0}
$$

#### Joint E Check

$$
\sum F_x=0
$$

$$
-F_{BE}+F_{EA}-\frac{a}{2L_2}F_{CE}+\frac{a}{2L_2}F_{ED}=0
$$

$$
\boxed{\sum F_x=0}
$$

$$
\sum F_y=0
$$

$$
-\frac{b}{L_2}F_{CE}-\frac{b}{L_2}F_{ED}=0
$$

$$
\boxed{\sum F_y=0}
$$

### Numerical Member Forces

$$
F_{BC}=-\frac{(25)(0.500)}{3(0.300)}
$$

$$
\boxed{F_{BC}=-13.889\text{ kN}}
$$

$$
F_{BE}=\frac{(0.400)(25)}{3(0.300)}
$$

$$
\boxed{F_{BE}=11.111\text{ kN}}
$$

$$
F_{AD}=\frac{(25)(0.500)}{3(0.300)}
$$

$$
\boxed{F_{AD}=13.889\text{ kN}}
$$

$$
F_{EA}=-\frac{(0.400)(25)}{3(0.300)}
$$

$$
\boxed{F_{EA}=-11.111\text{ kN}}
$$

$$
F_{CE}=-\frac{2(25)(0.360555)}{3(0.300)}
$$

$$
\boxed{F_{CE}=-20.031\text{ kN}}
$$

$$
F_{ED}=\frac{2(25)(0.360555)}{3(0.300)}
$$

$$
\boxed{F_{ED}=20.031\text{ kN}}
$$

$$
\boxed{F_{CD}=0}
$$

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

$$
\boxed{F_{\max}=20.031\text{ kN}}
$$

This occurs in members CE and ED. Because every member must use the same cross-sectional area, this maximum value was used to size the truss.

### Material Selection

The truss was modeled using **ASTM A500 Grade C** material properties:

- **Yield strength, $S_y$ = 345 MPa**
- **Ultimate tensile strength = 425 MPa**
- **Elastic modulus, $E$ = 200,000 MPa**
- **Poisson's ratio = 0.29**
- **Density, $\rho_{\text{truss}}$ = 7800 kg/m³**

Material-property source:

[BeamDimensions - ASTM A500](https://beamdimensions.com/materials/Steel/ASTM/ASTM_A500/)

> **Figure #6 — ASTM A500 Grade C material-property source**
![Figure #6: ASTM A500 Grade C material-property source](../../assets/images/6.png)

> **Figure #7 — Custom ASTM A500 Grade C material in SolidWorks**
![Figure #7: Custom ASTM A500 Grade C material in SolidWorks](../../assets/images/7.png)

### Member Cross-Section

The required member safety factor is:

$$
FS_{\text{member}}=3.5
$$

The allowable normal stress is:

$$
\sigma_{\text{allow}}=\frac{S_y}{FS_{\text{member}}}
$$

$$
\sigma_{\text{allow}}=\frac{345}{3.5}
$$

$$
\boxed{\sigma_{\text{allow}}=98.57\text{ MPa}}
$$

Using $\sigma=F/A$:

$$
\frac{F_{\max}}{A_{\min}}=\frac{S_y}{FS_{\text{member}}}
$$

Therefore:

$$
\boxed{A_{\min}=\frac{F_{\max}FS_{\text{member}}}{S_y}}
$$

Numerically:

$$
A_{\min}=\frac{(20\,030.84)(3.5)}{345}
$$

$$
\boxed{A_{\min}=203.21\text{ mm}^2}
$$

I selected a **15 mm × 15 mm** solid cross-section:

$$
A_{\text{member}}=wt
$$

$$
A_{\text{member}}=15(15)
$$

$$
\boxed{A_{\text{member}}=225\text{ mm}^2}
$$

$$
\boxed{225\text{ mm}^2>203.21\text{ mm}^2}
$$

The actual maximum normal stress is:

$$
\sigma_{\max}=\frac{F_{\max}}{A_{\text{member}}}
$$

$$
\sigma_{\max}=\frac{20\,030.84}{225}
$$

$$
\boxed{\sigma_{\max}=89.03\text{ MPa}}
$$

The actual member safety factor is:

$$
FS_{\text{actual,member}}=\frac{S_y}{\sigma_{\max}}
$$

$$
FS_{\text{actual,member}}=\frac{345}{89.03}
$$

$$
\boxed{FS_{\text{actual,member}}=3.88}
$$

Since:

$$
\boxed{3.88>3.5}
$$

the selected member cross-section satisfies the required safety factor.

### Pin Design

The assignment specifies hardened tool-steel pins with:

- **Yield shear strength = 170 ksi = 1172.11 MPa**
- **Density = 0.278 lb/in³ = 7695.01 kg/m³**
- **Required pin safety factor = 4**
- **Single-shear connection**

The loads considered at the joints are:

$$
F_{\text{pin},A}=\sqrt{A_x^2+A_y^2}=8.333\text{ kN}
$$

$$
F_{\text{pin},B}=|B_y|=8.333\text{ kN}
$$

$$
F_{\text{pin},C}=P=25\text{ kN}
$$

$$
F_{\text{pin},D}=P=25\text{ kN}
$$

Therefore:

$$
\boxed{F_{\text{pin,max}}=25.000\text{ kN}}
$$

> **Figure #8 — Critical-pin free-body diagram**
![Figure #8: Critical-pin free-body diagram](../../assets/images/8.png)

For single shear:

$$
\tau=\frac{F}{A}
$$

and

$$
\tau_{\text{allow}}=\frac{S_{sy,\text{pin}}}{FS_{\text{pin}}}
$$

Therefore:

$$
\boxed{
A_{\min,\text{pin}}
=
\frac{F_{\text{pin,max}}FS_{\text{pin}}}{S_{sy,\text{pin}}}
}
$$

Numerically:

$$
A_{\min,\text{pin}}=\frac{(25\,000)(4)}{1172.11}
$$

$$
\boxed{A_{\min,\text{pin}}=85.32\text{ mm}^2}
$$

For a circular pin:

$$
A_{\text{pin}}=\frac{\pi d^2}{4}
$$

Solving for minimum diameter:

$$
d_{\min}=\sqrt{\frac{4A_{\min,\text{pin}}}{\pi}}
$$

$$
d_{\min}=\sqrt{\frac{4(85.32)}{\pi}}
$$

$$
\boxed{d_{\min}=10.42\text{ mm}}
$$

I selected:

$$
\boxed{d_{\text{pin}}=11\text{ mm}}
$$

The actual pin area is:

$$
A_{\text{pin}}=\frac{\pi(11)^2}{4}
$$

$$
\boxed{A_{\text{pin}}=95.03\text{ mm}^2}
$$

The actual average shear stress is:

$$
\tau_{\text{actual}}=\frac{25\,000}{95.03}
$$

$$
\boxed{\tau_{\text{actual}}=263.07\text{ MPa}}
$$

The actual pin safety factor is:

$$
FS_{\text{actual,pin}}=\frac{1172.11}{263.07}
$$

$$
\boxed{FS_{\text{actual,pin}}=4.46}
$$

Since:

$$
\boxed{4.46>4}
$$

the selected 11 mm pin satisfies the required safety factor.

The final pin dimensions are:

- **Diameter = 11 mm**
- **Length = 15 mm**
- **Number of pins = 5**

### Pin Joint Geometry

The pin holes remove material from each joint, so the joint regions were widened in the final CAD model. The goal was to keep the net cross-sectional area through the pin hole at least as large as the selected member area.

$$
A_{\text{joint,net}}=(D_{\text{joint}}-d_{\text{pin}})t
$$

The required condition is:

$$
A_{\text{joint,net}}\geq A_{\text{member}}
$$

Using $A_{\text{member}}=225\text{ mm}^2$, $d_{\text{pin}}=11\text{ mm}$, and $t=15\text{ mm}$:

$$
(D_{\text{joint}}-11)(15)\geq225
$$

$$
D_{\text{joint}}\geq26\text{ mm}
$$

$$
\boxed{D_{\text{joint,min}}=26\text{ mm}}
$$

The final joint geometry therefore uses:

- **Joint-pad diameter = 26 mm**
- **Hole diameter = 11 mm**
- **Truss thickness = 15 mm**

> **Figure #9 — 26 mm joint pads and 11 mm pin holes**
![Figure #9: 26 mm joint pads and 11 mm pin holes](../../assets/images/9.png)

### Analytical Mass and Weight Estimate

The selected member area is:

$$
A_{\text{member}}=225\text{ mm}^2
$$

$$
A_{\text{member}}=2.25\times10^{-4}\text{ m}^2
$$

The approximate truss volume is:

$$
V_{\text{truss,approx}}=A_{\text{member}}L_{\text{total}}
$$

$$
V_{\text{truss,approx}}=(2.25\times10^{-4})(3.321110)
$$

$$
\boxed{V_{\text{truss,approx}}=7.4725\times10^{-4}\text{ m}^3}
$$

Using $\rho_{\text{truss}}=7800\text{ kg/m}^3$:

$$
m_{\text{truss,approx}}=\rho_{\text{truss}}V_{\text{truss,approx}}
$$

$$
m_{\text{truss,approx}}=(7800)(7.4725\times10^{-4})
$$

$$
\boxed{m_{\text{truss,approx}}=5.829\text{ kg}}
$$

Using $g=9.81\text{ m/s}^2$:

$$
W_{\text{truss,approx}}=m_{\text{truss,approx}}g
$$

$$
\boxed{W_{\text{truss,approx}}=57.18\text{ N}}
$$

For one 11 mm diameter × 15 mm long pin:

$$
V_{\text{one pin}}=\frac{\pi d_{\text{pin}}^2}{4}L_{\text{pin}}
$$

$$
V_{\text{one pin}}=\frac{\pi(0.011)^2}{4}(0.015)
$$

$$
\boxed{V_{\text{one pin}}=1.4255\times10^{-6}\text{ m}^3}
$$

Using $\rho_{\text{pin}}=7695.01\text{ kg/m}^3$:

$$
m_{\text{one pin}}=\rho_{\text{pin}}V_{\text{one pin}}
$$

$$
\boxed{m_{\text{one pin}}=0.01097\text{ kg}}
$$

For five pins:

$$
m_{\text{pins,total}}=5m_{\text{one pin}}
$$

$$
\boxed{m_{\text{pins,total}}=0.05485\text{ kg}}
$$

$$
W_{\text{pins,total}}=m_{\text{pins,total}}g
$$

$$
\boxed{W_{\text{pins,total}}=0.538\text{ N}}
$$

The final analytical estimate is:

$$
m_{\text{total,approx}}
=
m_{\text{truss,approx}}+m_{\text{pins,total}}
$$

$$
m_{\text{total,approx}}=5.82855+0.05485
$$

$$
\boxed{m_{\text{total,approx}}=5.883\text{ kg}}
$$

$$
W_{\text{total,approx}}
=
W_{\text{truss,approx}}+W_{\text{pins,total}}
$$

$$
\boxed{W_{\text{total,approx}}=57.72\text{ N}}
$$

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
| Member area | 225 mm² |
| Truss thickness | 15 mm |
| Joint-pad diameter | 26 mm |
| Pin-hole diameter | 11 mm |
| Pin diameter | 11 mm |
| Pin length | 15 mm |
| Number of pins | 5 |

### CAD Process

The truss was modeled in SolidWorks using MMGS units. I first created construction geometry and located the five joint centers using the correct 400 mm, 600 mm, and 300 mm dimensions. I connected the joint centers, offset the member centerlines by 7.5 mm on each side, converted the original centerlines to construction geometry, and cleaned the intersections until the profile was fully defined.

The completed truss profile was extruded to 15 mm. The five 26 mm joint pads were then added, followed by the five 11 mm pin holes. Finally, one 11 mm diameter by 15 mm long pin was modeled and inserted five times into the final assembly.

> **Figure #10 — Construction lines and joint locations**
![Figure #10: Construction lines and joint locations](../../assets/images/10.png)

> **Figure #11 — Seven-member centerline skeleton**
![Figure #11: Seven-member centerline skeleton](../../assets/images/11.png)

> **Figure #12 — 7.5 mm offset used on both sides of each member**
![Figure #12: 7.5 mm offset used on both sides of each member](../../assets/images/12.png)

> **Figure #13 — Centerlines converted to construction geometry**
![Figure #13: Centerlines converted to construction geometry](../../assets/images/13.png)

> **Figure #14 — Trimmed and cleaned joint geometry**
![Figure #14: Trimmed and cleaned joint geometry](../../assets/images/14.png)

> **Figure #15 — Fully defined final truss sketch**
![Figure #15: Fully defined final truss sketch](../../assets/images/15.png)

> **Figure #16 — Truss extruded to 15 mm**
![Figure #16: Truss extruded to 15 mm](../../assets/images/16.png)

> **Figure #17 — Final truss body with joint pads and holes**
![Figure #17: Final truss body with joint pads and holes](../../assets/images/17.png)

> **Figure #18 — 11 mm × 15 mm pin model**
![Figure #18: 11 mm × 15 mm pin model](../../assets/images/18.png)

> **Figure #19 — Final SolidWorks assembly with five pins**
![Figure #19: Final SolidWorks assembly with five pins](../../assets/images/19.png)

### CAD Mass Results

The SolidWorks mass of the final truss body was:

$$
\boxed{m_{\text{CAD,truss}}=5.77144\text{ kg}}
$$

> **Figure #20 — Truss-body mass properties, 5771.44 g**
![Figure #20: Truss-body mass properties](../../assets/images/20.png)

The SolidWorks mass of one pin was:

$$
\boxed{m_{\text{CAD,pin}}=11.12\text{ g}}
$$

> **Figure #21 — One-pin mass properties, 11.12 g**
![Figure #21: One-pin mass properties](../../assets/images/21.png)

The final SolidWorks assembly containing the truss and all five pins had a mass of:

$$
\boxed{m_{\text{CAD,total}}=5.82704\text{ kg}}
$$

> **Figure #22 — Final assembly mass properties, 5827.04 g**
![Figure #22: Final assembly mass properties](../../assets/images/22.png)

### Weight Comparison

The analytical total mass was:

$$
m_{\text{calc}}=5.8834\text{ kg}
$$

The SolidWorks assembly mass was:

$$
m_{\text{CAD}}=5.82704\text{ kg}
$$

The absolute difference is:

$$
\text{Difference}=|5.8834-5.82704|
$$

$$
\boxed{\text{Difference}=0.05636\text{ kg}}
$$

The percent difference is:

$$
\text{Percent Difference}
=
\frac{0.05636}{5.8834}\times100
$$

$$
\boxed{\text{Percent Difference}=0.96\%}
$$

The two results are very close. The analytical calculation treats the members using simplified centerline lengths and a constant area, while the CAD model includes the actual trimmed joints, circular joint pads, holes, arcs, and merged geometry. This explains why the final CAD mass is slightly different from the analytical estimate.

---

## Communicate

The completed analysis showed that the selected member and pin dimensions satisfy the required safety factors for the simplified design model. The CAD model also produced a mass within about one percent of the analytical estimate, which shows that the analytical model and final geometry are reasonably consistent. The failure-mode review showed that a member can be safe against simple axial yielding while still having another possible failure concern such as buckling in compression.

### MEGR 2157 – Truss Member Failure Modes

ASTM A500 Grade C was treated as a ductile steel for this analysis. For the tension members, yielding is expected before tensile fracture because the yield strength used in the design is lower than the ultimate tensile strength. For compression members, buckling becomes an important possible failure mode when the assignment's simplified no-buckling assumption is removed.

For the 15 mm × 15 mm solid section:

$$
I=\frac{bh^3}{12}
$$

$$
I=\frac{15(15)^3}{12}
$$

$$
\boxed{I=4218.75\text{ mm}^4}
$$

Using the ideal pinned-column Euler relation:

$$
P_{cr}=\frac{\pi^2EI}{L^2}
$$

with:

$$
E=200\,000\text{ N/mm}^2
$$

For the 600 mm compression member EA:

$$
P_{cr,EA}
=
\frac{\pi^2(200\,000)(4218.75)}{600^2}
$$

$$
\boxed{P_{cr,EA}=23.13\text{ kN}}
$$

For the 500 mm compression member BC:

$$
P_{cr,BC}
=
\frac{\pi^2(200\,000)(4218.75)}{500^2}
$$

$$
\boxed{P_{cr,BC}=33.31\text{ kN}}
$$

For the 360.6 mm compression member CE:

$$
P_{cr,CE}
=
\frac{\pi^2(200\,000)(4218.75)}{360.6^2}
$$

$$
\boxed{P_{cr,CE}\approx64.06\text{ kN}}
$$

The failure-mode screening gives:

| Member | Loading | Stress | Expected Failure Mode | Material Behavior | Possible Improvement |
|---|---|---:|---|---|---|
| BE | Tension | 49.38 MPa | Yielding before fracture | Ductile | Increase common member area |
| EA | Compression | 49.38 MPa | Buckling | Ductile material | Increase moment of inertia or reduce unsupported length |
| BC | Compression | 61.73 MPa | Buckling | Ductile material | Increase moment of inertia or reduce unsupported length |
| CE | Compression | 89.03 MPa | Buckling | Ductile material | Increase moment of inertia |
| ED | Tension | 89.03 MPa | Yielding before fracture | Ductile | Increase common member area |
| AD | Tension | 61.73 MPa | Yielding before fracture | Ductile | Increase common member area |
| CD | Zero force | 0 MPa | None under this ideal load case | Ductile | Retain for stability and other possible load cases |

The main sizing portion of the assignment specifically allowed compression-member buckling to be ignored. The analysis above is a separate MEGR 2157 failure-mode review and does not replace the required basic-stress sizing calculation.

### MEGR 2157 – Pin Failure Mode

The pin was designed for direct single shear. At the critical 25 kN load:

$$
\tau_{\text{pin}}=\frac{F}{A}
$$

$$
\tau_{\text{pin}}=\frac{25\,000}{95.03}
$$

$$
\boxed{\tau_{\text{pin}}=263.07\text{ MPa}}
$$

Compared with:

$$
S_{sy,\text{pin}}=1172.11\text{ MPa}
$$

the safety factor is:

$$
FS_{\text{pin}}=\frac{1172.11}{263.07}
$$

$$
\boxed{FS_{\text{pin}}=4.46}
$$

Therefore, shear yielding is not expected at the design load. If the load were increased enough, the most directly applicable failure mode for this pin design would be shear yielding across the single shear plane. Increasing pin diameter would increase shear area and reduce the average shear stress. A double-shear connection could also reduce the load carried by each shear plane, but this assignment specifically uses single shear.

### Engineering Lessons Learned

One of the biggest lessons from this assignment was that checking the original dimensions before beginning detailed CAD work is extremely important. The truss can have the correct shape and force ratios while still having completely incorrect member lengths and weight if the scale is wrong. I also learned that joint design matters because adding a pin hole removes material from the member and can reduce the net cross-sectional area.

The comparison between analytical mass and CAD mass also showed why both methods are useful. The calculations provide a fast estimate and help size the structure, while CAD represents the final geometry more accurately. Having only about a 0.96% difference between the two results gave me confidence that the final corrected model was consistent with the calculations.

### Mistakes and Improvements

My largest mistake was initially reading the assignment dimensions as **a = 4 m** and **b = 3 m** instead of **a = 0.4 m** and **b = 0.3 m**. I completed most of the first CAD model before catching the error and then rebuilt the truss using the correct 400 mm and 300 mm dimensions. Because the corrected design is a uniform scale change, the truss angles and internal-force results remained the same, but all member lengths and weight calculations had to be corrected.

If I repeated the assignment, I would write the problem constraints and units in a short table before starting the calculations or CAD model. I would also check the overall span and height immediately after creating the first SolidWorks sketch. This would prevent a dimension-reading mistake from carrying through the rest of the design.

> **Figure #23 — Incorrect first CAD model at the wrong scale**
![Figure #23: Incorrect first CAD model at the wrong scale](../../assets/images/23.png)

> **Figure #24 — Corrected final CAD model**
![Figure #24: Corrected final CAD model](../../assets/images/24.png)

### Time Spent

**Total Time Spent: 18 Hours**

The assignment included calculations, CAD modeling, a complete CAD rebuild after correcting the dimensions, pin modeling, material setup, assembly work, mass-property comparison, failure-mode analysis, and documentation.

---

## CAD Download

The completed SolidWorks CAD files can be downloaded below:

- [Download Truss_Florencondia.SLDPRT](../../assets/files/Truss_Florencondia.SLDPRT)
- [Download Pin_Florencondia.SLDPRT](../../assets/files/Pin_Florencondia.SLDPRT)
- [Download Assembly_Florencondia.SLDASM](../../assets/files/Assembly_Florencondia.SLDASM)

These files include the final truss part, pin part, and complete assembly used for the CAD mass comparison.

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
