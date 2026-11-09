# A9 – Pulley System Design

## Objective

The objective of this assignment was to design a belt-driven pulley system that transfers power between two parallel shafts. The work required selecting a polyurethane belt, calculating its tight-side and loose-side tensions, sizing shafts made from 1060 hardened steel, selecting journal bearings using pressure–velocity (PV) analysis, and designing a frame to support the assembly.

The assignment established the following constraints:

| Requirement | Specification |
|---|---:|
| Number of pulleys | 2 |
| Pulley diameter | 3.000 in each |
| Center distance | 4–6 in |
| Rotational speed | 1,000–2,000 rpm |
| Static belt tension | 4–6 lbf |
| Pulley material | Aluminum, ABS, or steel |
| Belt material | Polyurethane rubber |
| Belt yield strength at 20% strain | 3.25 MPa (471 psi) |
| Shaft material | 1060 hardened steel |
| Minimum design safety factor | 3 |

I selected an **open-belt arrangement** using two equal-diameter pulleys. This produces a theoretical **1:1 speed ratio**, so the input and output shafts rotate at the same speed when there is no slip. Rather than designing the belt, shaft, bearings, and frame separately, I used a single set of loads throughout the analysis.

---

## Analyze

### Operating Conditions and Design Assumptions

I chose values near the middle of the allowed ranges to provide a straightforward starting configuration.

| Parameter | Symbol | Selected value |
|---|---|---:|
| Pulley diameter | $D$ | 3.000 in |
| Pulley radius | $r$ | 1.500 in |
| Shaft center distance | $C$ | 5.000 in |
| Shaft speed | $n$ | 1,500 rpm |
| Initial static tension **in each span** | $T_0$ | 5.000 lbf |
| Belt wrap angle on each pulley | $\theta$ | $180^\circ=\pi$ rad |
| Assumed effective belt/pulley friction coefficient | $\mu$ | 0.30 |
| Required safety factor | $N$ | 3 |
| Pulley and frame material | — | 6061-T6 aluminum |

The **5 lbf** is interpreted as the pretension in *each* belt span before torque is transmitted. The friction coefficient of **0.30** is an explicit, conservative design assumption for the idealized friction calculation, **not a measured property** of the selected belt/pulley pair. The no-slip result is conditional on the actual contact having at least the calculated required friction coefficient.

> **Figure 1 – Proposed two-pulley arrangement showing two Ø3.000 in pulleys, their open belt path, and 5.000 in shaft center distance**

<img src="../../assets/images/95.png" alt="A9 two-pulley geometry and belt path, dimensioned sketch" style="width:80%; height:auto;">

---

### Belt Design

#### Knowns, Unknowns, and Free-Body Diagram

**Knowns:** $T_0=5$ lbf per span, $\theta=\pi$ rad, $\mu=0.30$ (assumed), $D=3$ in, $S_{y,b}=471$ psi, and $N=3$.

**Unknowns:** Tight-side tension $T_1$, loose-side tension $T_2$, torque capacity, minimum cross-sectional area $A_{\min}$, minimum round-belt diameter $d_{b,\min}$, and suitable belt circumference.

The pulley free-body diagram includes two tangential belt forces: $T_1$ on the tight side and $T_2$ on the loose side. Their **difference** transmits torque, while their approximate **sum** produces the radial load on each shaft.

> **Figure 2 – Belt and pulley free-body diagram showing the tight and loose spans, 1.500 in pulley radius, and 180° contact angle**

<img src="../../assets/images/96.png" alt="A9 belt pulley free-body diagram showing T1, T2, radius, wrap angle, and rotation" style="width:75%; height:auto;">

#### Tight-Side and Loose-Side Tensions

For an idealized drive where the sum of the two running tensions remains equal to twice the initial tension:

$$
T_1+T_2=2T_0
$$

At the threshold of belt slip, the capstan equation gives:

$$
\frac{T_1}{T_2}=e^{\mu\theta}
$$

Solving both equations symbolically:

$$
\boxed{T_1=\frac{2T_0e^{\mu\theta}}{1+e^{\mu\theta}}}
$$

$$
\boxed{T_2=\frac{2T_0}{1+e^{\mu\theta}}}
$$

First, the tension ratio at impending slip is:

$$
e^{\mu\theta}=e^{(0.30)(\pi)}=2.5663
$$

The limiting tight-side force is:

$$
T_1=\frac{2(5)(2.5663)}{1+2.5663}
$$

$$
\boxed{T_{1,\mathrm{limit}}=7.196\text{ lbf}}
$$

The limiting loose-side force is:

$$
T_2=\frac{2(5)}{1+2.5663}
$$

$$
\boxed{T_{2,\mathrm{limit}}=2.804\text{ lbf}}
$$

These values represent the **maximum tension difference before predicted slip** under the assumed friction condition. They are not measured operating loads.

#### Design Torque and No-Slip Check

I selected a **design transmitted torque of 5.000 in·lbf**. The force difference needed to transmit this torque is:

$$
M_t=r(T_1-T_2)
$$

$$
\Delta T=\frac{M_t}{r}=\frac{5.000}{1.500}=3.333\text{ lbf}
$$

Combining this with $T_1+T_2=10$ lbf:

$$
T_{1,\mathrm{design}}=\frac{10+3.333}{2}
=\boxed{6.667\text{ lbf}}
$$

$$
T_{2,\mathrm{design}}=\frac{10-3.333}{2}
=\boxed{3.333\text{ lbf}}
$$

The required coefficient of friction to avoid slipping at this torque is:

$$
\mu_{\mathrm{required}}=
\frac{\ln(T_{1,\mathrm{design}}/T_{2,\mathrm{design}})}{\theta}
$$

$$
\mu_{\mathrm{required}}=\frac{\ln(6.667/3.333)}{\pi}
$$

$$
\boxed{\mu_{\mathrm{required}}=0.221}
$$

Since $0.221<0.30$, the belt **does not slip in the assumed friction model**. The corresponding maximum friction-limited torque is:

$$
M_{\mathrm{slip}}=r(T_{1,\mathrm{limit}}-T_{2,\mathrm{limit}})
$$

$$
M_{\mathrm{slip}}=1.5(7.196-2.804)
$$

$$
\boxed{M_{\mathrm{slip}}=6.588\text{ in}\cdot\text{lbf}}
$$

Thus, the 5.000 in·lbf design torque is below the calculated slip threshold. The belt strength and shaft strength are checked against the **higher, limiting tension and torque** to remain conservative within this model.

For reference, the nominal belt speed is:

$$
V_b=\frac{\pi Dn}{12}
=\frac{\pi(3)(1500)}{12}
=\boxed{1178.1\text{ ft/min}}
$$

The ideal transmitted power at the selected design torque is:

$$
P=\frac{M_tn}{63025}
=\frac{(5)(1500)}{63025}
=\boxed{0.119\text{ hp}}
$$

This power calculation neglects losses and is not a manufacturer's power rating for the belt.

#### Minimum Belt Cross-Section and Diameter

The allowable belt tensile stress, using the specified yield-strength reference and a safety factor of 3, is:

$$
\sigma_{\mathrm{allow}}=\frac{S_{y,b}}{N}
=\frac{471}{3}=157\text{ psi}
$$

The largest belt tension controls the cross-sectional area:

$$
\sigma=\frac{T_{1,\mathrm{limit}}}{A}\leq\sigma_{\mathrm{allow}}
$$

Rearranging:

$$
\boxed{A_{\min}=\frac{NT_{1,\mathrm{limit}}}{S_{y,b}}}
$$

$$
A_{\min}=\frac{3(7.196)}{471}
$$

$$
\boxed{A_{\min}=0.04583\text{ in}^2}
$$

For a solid circular belt, $A=\pi d_b^2/4$. Solving for the minimum diameter:

$$
\boxed{d_{b,\min}=\sqrt{\frac{4A_{\min}}{\pi}}}
$$

$$
d_{b,\min}=\sqrt{\frac{4(0.04583)}{\pi}}
$$

$$
\boxed{d_{b,\min}=0.2416\text{ in}}
$$

I selected the next practical size, a **5/16 in (0.3125 in) round polyurethane belt**.

The area of the selected belt is:

$$
A_b=\frac{\pi(0.3125)^2}{4}
=\boxed{0.07670\text{ in}^2}
$$

The tensile stress at the slip-limiting load is:

$$
\sigma_b=\frac{7.196}{0.07670}
=\boxed{93.82\text{ psi}}
$$

The corresponding tensile-yield safety factor is:

$$
N_b=\frac{471}{93.82}
=\boxed{5.02>3}
$$

The 5/16 in belt satisfies the assigned **static tensile-yield calculation**. This simplified check does not establish fatigue life, splice strength, creep resistance, or performance at operating speed.


#### Belt Circumference and Product Selection

I designed a shallow round-belt groove so the **belt centerline is approximately at the pulley’s specified 3.000 in diameter**. This defines the belt's effective pitch diameter for the length calculation.

For two equal pulleys with an open belt:

$$
L_{\mathrm{pitch}}=2C+\pi D
$$

$$
L_{\mathrm{pitch}}=2(5)+\pi(3)
$$

$$
\boxed{L_{\mathrm{pitch}}=19.4248\text{ in}}
$$

The catalog describes belt length by **outer circumference**, not centerline circumference. For round belting of diameter $d_b$, the geometric outer circumference of the installed loop is approximately:

$$
L_{\mathrm{outer,installed}}=L_{\mathrm{pitch}}+\pi d_b
$$

$$
L_{\mathrm{outer,installed}}=19.4248+\pi(0.3125)
$$

$$
\boxed{L_{\mathrm{outer,installed}}=20.4065\text{ in}}
$$

I selected **McMaster-Carr 9462T58**, a made-to-order polyurethane round belt with a 5/16 in diameter. Its stated minimum pulley diameter is **2.5 in**, so our **3.0 in pulleys** meet that geometric limitation.

For the proposed adjustable frame, I specified a **nominal unstretched outer circumference of 19.75 in**. At the nominal 5.000 in center distance, the corresponding geometric installed extension is approximately:

$$
\varepsilon_{\mathrm{install}}=
\frac{20.4065-19.75}{19.75}
=\boxed{3.32\%}
$$

This is a **geometric stretch estimate**, not a calculated 5-lbf tension. The given 471 psi stress at 20% strain does not provide a complete elastic stress–strain curve. Therefore, the actual installed pretension would be set with the adjustable support and checked if the design were physically assembled.


---

### Shaft Diameter Design

#### Knowns, Unknowns, and Shaft FBD

The problem specifies **1060 hardened steel**. For this calculation I used a documented reference condition: AISI 1060 steel oil-quenched at 845°C and tempered at 480°C. MatWeb lists a **yield strength of 89,500 psi** for a 50 mm round specimen in that condition. This is a **condition-specific reference value**, not a guarantee for every product sold as 1060 steel.

**Knowns:** $S_{y,s}=89{,}500$ psi (selected reference condition), $M_t=6.588$ in·lbf at the assumed friction limit, $N=3$, $T_1+T_2=10$ lbf, and a selected bearing center-to-center span of $L_s=1.250$ in.

**Unknowns:** Minimum shaft diameter under torsion, bending moment, minimum diameter under combined stress, and the safety factor of the chosen shaft.

The model uses **two journal bearings per shaft**, with the pulley centered between them. This allows the bearing reactions and maximum bending moment to be determined from a simple free-body diagram.

> **Figure 3 – Shaft free-body diagram showing a centered 10 lbf belt load, 1.250 in bearing span, 5 lbf reactions, and applied torque**

<img src="../../assets/images/97.png" alt="A9 shaft free-body diagram with a centered pulley load and two bearing reactions" style="width:80%; height:auto;">

#### Transmitted Torque and Bending Moment

To size the shaft conservatively, I used the maximum torque just before predicted slip:

$$
\boxed{M_t=6.588\text{ in}\cdot\text{lbf}}
$$

The approximate radial load on either pulley is:

$$
F_r=T_{1,\mathrm{limit}}+T_{2,\mathrm{limit}}
=7.196+2.804
=\boxed{10.000\text{ lbf}}
$$

For a centered point load on a simply supported shaft:

$$
R_A=R_B=\frac{F_r}{2}
=\boxed{5.000\text{ lbf}}
$$

The maximum bending moment occurs at the pulley location:

$$
M_b=\frac{F_rL_s}{4}
$$

$$
M_b=\frac{(10)(1.250)}{4}
$$

$$
\boxed{M_b=3.125\text{ in}\cdot\text{lbf}}
$$

#### Minimum Diameter for Pure Torsion

For a solid circular shaft:

$$
\tau_{\max}=\frac{16M_t}{\pi d_s^3}
$$

Using the von Mises criterion for ductile steel in pure torsion:

$$
\sqrt{3}\,\tau_{\max}\leq\frac{S_{y,s}}{N}
$$

Substituting and solving symbolically:

$$
\boxed{d_{s,\min}=\left(\frac{16\sqrt{3}\,M_tN}{\pi S_{y,s}}\right)^{1/3}}
$$

$$
d_{s,\min}=\left(\frac{16\sqrt{3}(6.588)(3)}{\pi(89{,}500)}\right)^{1/3}
$$

$$
\boxed{d_{s,\min,\mathrm{torsion}}=0.1249\text{ in}}
$$

#### Minimum Diameter with Bending and Torsion

The pulley load also bends the shaft, so the practical sizing check includes both stress components:

$$
\sigma_b=\frac{32M_b}{\pi d_s^3}
\qquad
\tau=\frac{16M_t}{\pi d_s^3}
$$

The combined von Mises stress is:

$$
\sigma_{\mathrm{VM}}=\sqrt{\sigma_b^2+3\tau^2}
$$

Setting the combined stress equal to the allowable yield stress and rearranging gives:

$$
\boxed{
d_{s,\min}=\left[
\frac{N\sqrt{(32M_b)^2+3(16M_t)^2}}{\pi S_{y,s}}
\right]^{1/3}}
$$

$$
d_{s,\min}=\left[
\frac{3\sqrt{(32\times3.125)^2+3(16\times6.588)^2}}{\pi(89{,}500)}
\right]^{1/3}
$$

$$
\boxed{d_{s,\min,\mathrm{combined}}=0.1305\text{ in}}
$$

**Combined bending and torsion governs** over the torsion-only calculation because it produces the larger minimum diameter.

I selected a **nominal 3/8 in (0.375 in) shaft** rather than the theoretical minimum because it fits a commonly available journal bearing and provides greater rigidity.

At $d_s=0.375$ in, the nominal stresses are:

$$
\sigma_b=\frac{32(3.125)}{\pi(0.375)^3}
=603.6\text{ psi}
$$

$$
\tau=\frac{16(6.588)}{\pi(0.375)^3}
=636.3\text{ psi}
$$

$$
\sigma_{\mathrm{VM}}=\sqrt{603.6^2+3(636.3)^2}
=\boxed{1256.5\text{ psi}}
$$

$$
N_s=\frac{89{,}500}{1256.5}
=\boxed{71.2>3}
$$

This is the **nominal static shaft safety factor** for the stated loading and material model. A real manufactured shaft would also require proper bearing-journal finish, pulley attachment, and consideration of fatigue and local stress concentrations.


---

### Journal Bearing Design

#### Knowns, Unknowns, and Bearing FBD

I chose a **sintered, oil-impregnated bronze sleeve bearing** because this system operates continuously at 1,500 rpm and requires a material with sufficient pressure, surface-speed, and PV capacity.

Each shaft is supported by two bearings, so the proposed complete two-shaft assembly has **four bearings**.

| Parameter | Symbol | Value |
|---|---|---:|
| Shaft nominal diameter | $d_s$ | 0.375 in |
| Bearing inside diameter, nominal | $d_b$ | 0.375 in |
| Bearing outside diameter, nominal | $D_b$ | 0.500 in |
| Bearing length | $L_b$ | 0.500 in |
| Shaft speed | $n$ | 1,500 rpm |
| Total pulley radial load | $F_r$ | 10.000 lbf |
| Number of bearings per shaft | — | 2 |
| Load on one bearing | $F_b$ | 5.000 lbf |

**Unknowns:** Projected bearing area, pressure $P$, surface speed $V$, PV value, and acceptable bearing material.

> **Figure 4 – Journal-bearing geometry and free-body diagram showing the 5 lbf radial load, Ø0.375 in shaft, and 0.500 in bearing length**

<img src="../../assets/images/98.png" alt="A9 journal bearing sectional sketch and five pound radial load diagram" style="width:75%; height:auto;">

#### Bearing Pressure

For a journal bearing, the projected area is the shaft diameter multiplied by the bearing length:

$$
A_p=d_sL_b
$$

$$
A_p=(0.375)(0.500)
=\boxed{0.1875\text{ in}^2}
$$

The average pressure on one bearing is:

$$
P=\frac{F_b}{d_sL_b}
$$

$$
P=\frac{5}{(0.375)(0.500)}
$$

$$
\boxed{P=26.67\text{ psi}}
$$

#### Surface Velocity

For a shaft diameter in inches and speed in revolutions per minute:

$$
V=\frac{\pi d_sn}{12}
$$

$$
V=\frac{\pi(0.375)(1500)}{12}
$$

$$
\boxed{V=147.26\text{ ft/min}}
$$

#### Pressure–Velocity Product

$$
PV=P\,V
$$

$$
PV=(26.67)(147.26)
$$

$$
\boxed{PV=3927\text{ psi}\cdot\text{ft/min}}
$$

#### Bearing Material Selection

I compared the calculated value with **Table 4, Application Limits—Sintered Metal and Nonmetallic Bearings**, referenced by the assignment in *Machinery's Handbook* (p. 2440). The reference table gives the following values relevant to this design:

| Candidate material | Table pressure limit | Table speed limit | Table PV limit | Decision |
|---|---:|---:|---:|---|
| Acetal | 1,000 psi | 1,000 ft/min | 3,000 psi·ft/min | PV limit below calculated value |
| Reinforced Teflon | 2,500 psi | 1,000 ft/min | 10,000–15,000 psi·ft/min | Possible, but less PV margin |
| **Porous bronze** | **4,500 psi** | **1,500 ft/min** | **50,000 psi·ft/min** | **Selected** |

> **Reference excerpt – *Machinery's Handbook*, Table 4: bearing pressure, surface speed, and PV limits**

<img src="../../assets/images/100.png" alt="Machinery's Handbook Table 4 bearing material limits; source screenshot" style="width:80%; height:auto;">

The porous-bronze PV margin is:

$$
N_{PV}=\frac{PV_{\mathrm{limit}}}{PV_{\mathrm{calculated}}}
=\frac{50{,}000}{3927}
$$

$$
\boxed{N_{PV}=12.73>3}
$$


#### Selected Commercial Bearing

I selected the **Oilite AA502- sleeve bearing**, made from **SAE 841 sintered bronze** with an impregnated lubricant. The manufacturer's published dimensions and limits are:

| Oilite AA502- specification | Published value |
|---|---:|
| Nominal ID | 0.375 in |
| Nominal OD | 0.500 in |
| Length | 0.500 in |
| Maximum bearing pressure | 2,000 psi |
| Maximum surface speed | 1,200 ft/min |
| Maximum PV | 50,000 psi·ft/min |

Using the **more restrictive published manufacturer pressure and speed limits** rather than the broad handbook material values:

$$
\frac{P_{\max}}{P}=\frac{2000}{26.67}=75.0
$$

$$
\frac{V_{\max}}{V}=\frac{1200}{147.26}=8.15
$$

$$
\frac{PV_{\max}}{PV}=\frac{50{,}000}{3927}=12.73
$$

All three operating values are below the published limits, with a margin greater than 3 even when each limit is compared individually.

For an actual installation, the manufacturer's recommended **housing bore is 0.50015 ± 0.0005 in** and its recommended **finished shaft diameter is 0.37375 ± 0.0002 in**. These fits are separate from the nominal component sizes used in the preliminary strength analysis.


---

### Supporting Frame Design

#### Frame Configuration

I selected **6061-T6 aluminum** for the frame because it is lightweight, readily machined, and has adequate strength for the calculated belt loads. The concept uses **two parallel support rails**, one on either side of the pulley faces, with a pair of journal bearings supporting each shaft.

As a supporting material-selection reference, I also used an **Ashby strength–density chart**. The chart helps visualize why aluminum is a reasonable choice for a lightweight structural frame: it offers much higher specific strength than wood or polymer foams while avoiding the excess density of many steels and cast irons for this low-load application.

> **Reference chart – Ashby strength–density plot used to support the frame material selection**

<img src="../../assets/images/101.png" alt="Ashby strength density chart used as a reference for A9 frame material selection" style="width:80%; height:auto;">

| Frame feature | Design dimension |
|---|---:|
| Support rail quantity | 2 |
| Each rail: length | 7.000 in |
| Each rail: height | 1.500 in |
| Each rail: thickness | 0.500 in |
| Nominal pulley shaft centers along rails | 1.000 and 6.000 in from one end |
| Nominal center-to-center distance | 5.000 in |
| Clear distance between inner rail faces | 0.750 in |
| Proposed pulley face width | 0.500 in |
| Clearance per pulley face side | 0.125 in |
| Bearing support center-to-center span along shaft | 1.250 in |
| Stationary-drive bearing bore | Ø0.500 in nominal seating diameter |
| Driven-end tension adjustment | Sliding bearing carriers, ±0.125 in |

The **driving-shaft station is fixed**, while two matched bearing carriers at the **driven-shaft station** slide together to adjust center distance from **4.875 to 5.125 in**. The moving carriers retain **round bearing bores**; only their **mounting fasteners use slots**. This avoids placing a journal bearing directly in an elongated hole.

The 0.750 in space between the rails accommodates the proposed 0.500 in pulley faces, leaving 0.125 in of axial clearance on each side. With bearings centered in 0.500 in thick rails, the shaft's support-center spacing is:

$$
L_s=0.750+\frac{0.500}{2}+\frac{0.500}{2}
=\boxed{1.250\text{ in}}
$$

This agrees with the span used earlier in the shaft calculation.

The same conceptual figure also shows how the two bearing loads are transmitted to the frame. The frame dimensions and force estimates are checked algebraically below, rather than repeated as handwritten calculations in an image.

> **Figure 5 – Proposed supporting frame concept and loading diagram, showing the 7.000 in rails, 5.000 in pulley spacing, adjustable shaft supports, and 5 lbf bearing loads**

<img src="../../assets/images/99.png" alt="A9 frame design sketch with rail dimensions, adjustable shaft carriers, and loading arrows" style="width:85%; height:auto;">

#### Frame Free-Body Diagram and Stress Checks

Each pulley pulls toward the other pulley with an approximate resultant load of **10 lbf**. For the symmetric, two-support shaft arrangement, each bearing transmits **5 lbf** to its corresponding frame rail. The forces at the left and right shaft stations are equal and opposite under the idealized belt layout.

For a conservative net-section calculation at a fixed bearing bore, the remaining area through a rail with a 0.500 in bore is:

$$
A_{\mathrm{net}}=t(h-D_b)
$$

$$
A_{\mathrm{net}}=(0.500)(1.500-0.500)
$$

$$
\boxed{A_{\mathrm{net}}=0.500\text{ in}^2}
$$

For a 5 lbf force per rail:

$$
\sigma_{\mathrm{net}}=\frac{F_{\mathrm{rail}}}{A_{\mathrm{net}}}
=\frac{5}{0.500}
=\boxed{10.0\text{ psi}}
$$

The aluminum-to-bearing seating pressure, using nominal dimensions as a simple projected-area check, is:

$$
P_{\mathrm{seat}}=\frac{F_b}{D_b t}
=\frac{5}{(0.500)(0.500)}
=\boxed{20.0\text{ psi}}
$$

As an additional conservative frame check, I assumed a 5 lbf load acting with a **1.000 in local lever arm** on one rail:

$$
M_f=F_{\mathrm{rail}}e=(5)(1.000)
=5.000\text{ in}\cdot\text{lbf}
$$

For a rectangular rail section bending in its own plane:

$$
I=\frac{th^3}{12}
=\frac{(0.500)(1.500)^3}{12}
=0.140625\text{ in}^4
$$

$$
\sigma_{\mathrm{bend}}=\frac{M_f(h/2)}{I}
=\frac{(5)(0.750)}{0.140625}
=\boxed{26.67\text{ psi}}
$$

Adding the nominal net-section and illustrative local bending stresses provides a conservative simple comparison:

$$
\sigma_{\mathrm{check}}=10.0+26.67
=\boxed{36.67\text{ psi}}
$$

Using a reference 6061-T6 yield strength of **35,000 psi**:

$$
N_{\mathrm{frame,nominal}}=
\frac{35{,}000}{36.67}
=\boxed{955>3}
$$

The enormous margin indicates that these **simplified static rail stresses do not govern** the design; the rail thickness is instead influenced by the 0.500 in-long bearing and practical assembly. This value is **not an overall frame-system safety factor** because it excludes mounting-fastener effects, local stresses around slots, press-fit stresses, and other geometric details. Those details would require separate checks if a physical frame were manufactured.


---

## Decide

### Selected Pulley System

Based on the belt, shaft, bearing, and frame analysis, I selected the following configuration:

| Component | Final analytical design selection |
|---|---|
| Pulley arrangement | Open belt, 1:1 speed ratio |
| Pulleys | Two Ø3.000 in 6061-T6 aluminum pulleys |
| Effective belt pitch diameter | 3.000 in, from shallow-groove geometry |
| Center distance | 5.000 in nominal; 4.875–5.125 in adjustment |
| Speed | 1,500 rpm |
| Initial belt tension | 5 lbf per span |
| Design transmitted torque | 5.000 in·lbf |
| Assumed effective coefficient of friction | 0.30 |
| Belt | McMaster-Carr 9462T58; Ø5/16 in polyurethane round belt |
| Specified unstretched outer circumference | 19.75 in, made to order |
| Shaft material | AISI 1060 hardened steel, specified heat-treated reference condition |
| Shaft diameter | Ø0.375 in nominal; finished journals to manufacturer fit |
| Bearings | Four Oilite AA502- porous bronze sleeves |
| Bearing size | 0.375 in ID × 0.500 in OD × 0.500 in long |
| Frame | Two 6061-T6 aluminum rails, each 7.000 × 1.500 × 0.500 in |
| Shaft supports | Two bearings per shaft, with adjustable driven-side carriers |

The chosen component sizes were not based only on the theoretical minimum dimensions. Standard bearing compatibility, controlled pulley spacing, sufficient installation clearance, and the ability to set belt tension all influenced the selection.

### Results Summary

| Analysis | Calculated result | Outcome |
|---|---:|---|
| Tight-side tension at assumed slip limit | 7.196 lbf | Used to size belt |
| Loose-side tension at assumed slip limit | 2.804 lbf | Establishes tension difference |
| Minimum belt diameter | 0.2416 in | Selected 0.3125 in |
| Belt tensile-yield safety factor | 5.02 | Exceeds 3 |
| Required friction coefficient at design torque | 0.221 | Below assumed 0.30 |
| Slip-limiting torque | 6.588 in·lbf | Above 5.000 in·lbf design torque |
| Installed belt pitch-line length | 19.4248 in | Based on specified groove geometry |
| Installed belt outer circumference | 20.4065 in | Used to estimate belt extension |
| Minimum shaft diameter, torsion only | 0.1249 in | Does not govern |
| Minimum shaft diameter, bending + torsion | 0.1305 in | Governing shaft calculation |
| Selected shaft diameter | 0.375 in | Practical bearing-compatible size |
| Nominal shaft static safety factor | 71.2 | Exceeds 3 |
| Bearing pressure | 26.67 psi | Below Oilite limit |
| Bearing surface speed | 147.26 ft/min | Below Oilite limit |
| Bearing PV | 3,927 psi·ft/min | Below Oilite limit |
| Bearing PV-limit margin | 12.73 | Exceeds 3 |
| Simplified frame rail stress | 36.67 psi | Below 6061-T6 yield allowance |

**Belt tensile strength, not shaft yield, produces the smallest calculated strength margin in this simplified design.** For the journal bearing, the PV comparison is more restrictive than the pressure comparison; for the shaft, combined bending and torsion controls over pure torsion. The selected dimensions satisfy the numerical checks made under the stated assumptions.

---

## Communicate

### Engineering Lessons Learned

This design showed why a belt-driven system cannot be sized from transmitted torque alone. The **difference** between the tight-side and loose-side tensions transmits torque, but their **sum** still loads the shaft and journal bearings. Even when the transmitted torque is relatively modest, the static belt pretension contributes to bending and bearing pressure.

An important correction during the analysis involved **belt circumference**. The initial belt-path estimate must not be confused with the *outer circumference* used in the supplier's catalog. By defining a groove in which the belt centerline follows the 3.000 in pitch diameter, I could distinguish the 19.4248 in installed pitch-line length from the 20.4065 in installed outer circumference. I also recognized that the specified 471 psi at 20% strain is not enough information to calculate a 5 lbf pretension from belt length alone; the support must be adjustable if the design is built.

The shaft calculations also reinforced the importance of considering **combined loading**. A torsion-only result gave a smaller theoretical diameter, but the belt's radial force creates bending as well. Using the larger combined-loading diameter and then selecting a standard 3/8 in shaft made the journal-bearing selection simpler and created additional strength margin.

Finally, the journal-bearing check showed that **pressure, surface speed, and PV must be evaluated separately**. A material can withstand the bearing pressure while still being unsuitable for the pressure–velocity combination. Selecting porous bronze and cross-checking its handbook limits with the specific Oilite product provided a more defensible choice than relying only on a generic material label.

The frame analysis showed a different design trade-off: the calculated load is small enough that the **bearing installation and support arrangement**, rather than the simple aluminum yield stress, determine a practical rail thickness. The adjustable driven-side support addresses the belt-tension requirement without relying on an elongated bearing bore.

### Time Spent

Approximately **5 hours** were spent completing the engineering calculations, component and material selection, frame design, drawings, and portfolio documentation for this assignment.

---

## References

1. MEGR 2156/2157, *Pulley System* assignment instructions and grading rubric.
2. *Machinery's Handbook*, Table 4, “Application Limits—Sintered Metal and Nonmetallic Bearings,” p. 2440 (table referenced in the assignment).
3. *Simple Stresses*, p. 217, Table 2 (reference identified in the assignment).
4. Cambridge University Press, [belt friction/capstan equation and power transmission](https://assets.cambridge.org/97811070/06232/excerpt/9781107006232_excerpt.pdf).
5. McMaster-Carr, [9462T58 made-to-order 5/16 in polyurethane round belt and minimum pulley diameter](https://www.mcmaster.com/products/conveyor-roller-bands/).
6. MatWeb, [AISI 1060 steel, oil-quenched and tempered, 50 mm round reference properties](https://apm.matweb.com/search/DataSheet.aspx?MatGUID=5fb9954cde754e709944d64233e50d3b&ckck=1).
7. Oilite, [AA502- SAE 841 sintered bronze sleeve-bearing specifications and fit recommendations](https://oilite.com/product/AA502-).
8. Aircraft Materials, [6061-T6 aluminum yield-strength reference data](https://www.aircraftmaterials.com/data/aluminium/6061.html).

