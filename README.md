# Brake Pedal Lever Using Generative Design

An Autodesk Fusion project exploring a lightweight brake pedal lever for a PDR course project. The design uses an open, ribbed geometry around its mounting and connection features, and is evaluated through two static structural load cases using Titanium 6Al-4V.

This repository contains the exported lever mesh, a Fusion study report, and two safety-factor animations. The report's setup, material data, figures, and findings are included below so the project can be read directly from this README.

**Author:** Pranav Adhithya · **Software:** Autodesk Fusion · **Study:** Static Stress

![Brake pedal lever geometry exported in the Autodesk Fusion study report](assets/readme/model-overview.png)

[View the 3D model](Brake%20Stem%201%20GD3%20copy.stl) · [Original HTML report](Reports/Study%20Report%20for%20Brake%20Pedal_PDR.html) · [Load-case animations](#load-case-animations)

## Contents

- [Project objective and geometry](#project-objective-and-geometry)
- [Embedded study report](#embedded-study-report)
- [Results and interpretation](#results-and-interpretation)
- [Report figure gallery](#report-figure-gallery)
- [Load-case animations](#load-case-animations)
- [Further design work](#further-design-work)
- [Repository files and viewing instructions](#repository-files-and-viewing-instructions)

## Project objective and geometry

The project investigates how a brake pedal lever can carry its applied loads while reducing unnecessary material. Its geometry combines a pedal pad at one end, circular connection features, and curved ribs surrounding large internal openings. The openings illustrate the project's lightweight design intent; the surrounding ribs provide the remaining structural paths between the connection regions.

The supplied material documents the resulting geometry and its structural evaluation. It does not include a baseline mass, a final mass, or the original generative-design study settings, so a percentage weight reduction or an optimal-design claim cannot be established from these files.

The documented evaluation consists of assigning the material, defining constraints and loads for two cases, generating a solid finite-element mesh, and reviewing safety factor, stress, and displacement. The second case adds an X-direction component to the primary force, allowing a comparison with the first case's Z-direction loading.

## Embedded study report

The following tables and figure gallery present the content of the uploaded Fusion report in README form. All unique model and result images were extracted directly from its embedded PNGs. Repeated images in the original report are reused here. The [original HTML export](Reports/Study%20Report%20for%20Brake%20Pedal_PDR.html) is retained unchanged.

### Report and study identification

| Field | Reported value |
| --- | --- |
| Report title | Studies |
| Author | Pranav Adhithya |
| Analyzed file | Brake Stem 1 GD3 |
| Software version | Autodesk Fusion 2705.1.30 |
| Report creation | 2026-10-13, 18:49:32 |
| Simulation model | Simulation Model 1 |
| Study name | Study 1 - Structural Component |
| Study type | Static Stress |
| Study last modified | 2026-10-13, 11:23:03 |

The timestamps above are reproduced from the export; its timezone is unspecified.

### Material: Titanium 6Al-4V

The report assigns **Titanium 6Al-4V** to component **Body13**, with **yield strength** used as the strength criterion.

| Property | Value from the report |
| --- | ---: |
| Density | 4.430 × 10⁻⁶ kg/mm³ |
| Young's modulus | 113,763.35 MPa |
| Poisson's ratio | 0.35 |
| Yield strength | 882.528 MPa |
| Ultimate tensile strength | 1,034.213 MPa |
| Thermal conductivity | 0.007 W/(mm·K) |
| Thermal expansion coefficient | 8.600 × 10⁻⁶ /K |
| Specific heat | 526.30 J/(kg·K) |

Young's modulus controls the elastic stiffness used in the structural calculation, while yield strength provides the material reference for assessing yielding. The thermal properties are included because they appear in the material export; this report documents a static stress study rather than a thermal analysis.

### Solver and mesh settings

| Setting | Exported value |
| --- | --- |
| Contact tolerance | 0.10 mm |
| Remove rigid body modes | No |
| Mesh type | Solids |
| Nodes | 71,168 |
| Elements | 45,363 |
| Average element size, relative to model size | 10% |
| Scale mesh size per part | No |
| Absolute average element size | Not provided (`-` in export) |
| Element order | Parabolic |
| Create curved mesh elements | Yes |
| Maximum turn angle on curves | 60° |
| Maximum adjacent mesh-size ratio | 1.5 |
| Maximum aspect ratio | 10 |
| Minimum element size, relative to average size | 20% |
| Adaptive refinement steps | 0 |
| Configured results convergence tolerance | 20% |
| Configured portion of elements to refine | 10% |
| Baseline accuracy result | von Mises stress |

The contacts table in the original report contains no entries. The convergence settings are configuration values, not evidence of a completed convergence study: the exported number of adaptive refinement steps is zero.

### Constraints and load cases

Force components use the report's global X, Y, and Z axes. Both cases include gravity and two force definitions.

| Definition | Load Case 1 | Load Case 2 |
| --- | --- | --- |
| Fixed constraint | `Fixed1` | `Fixed2` |
| Constrained translations | Ux, Uy, Uz fixed | Ux, Uy, Uz fixed |
| Gravity, (X, Y, Z) | (0, 0, −9.807) m/s² | (0, 0, −9.807) m/s² |
| Primary load name | `Force1` | `Force3` |
| Primary force, (X, Y, Z) | (0, 0, −900) N | (+250, 0, −900) N |
| Primary force per entity | No | No |
| Secondary load name | `Force2` | `Force4` |
| Secondary force, (X, Y, Z) | (0, 0, +800) N | (0, 0, +800) N |
| Secondary force per entity | Yes | Yes |

**The secondary +800 N force is defined per selected entity.** The report text does not specify how many entities are selected, so it cannot be treated as a confirmed total 800 N force or combined into a net −100 N load. The exported setup images below preserve the available visual context; exact face selections must be checked in the native Fusion study.

<details>
<summary>View the report's load-setup images</summary>

**Gravity** — the same image is exported for both cases.

![Gravity definition visualization from the Fusion report](assets/readme/gravity.png)

**Load Case 1: Force1** — 900 N in the negative Z direction.

![Load Case 1 primary vertical force applied to the pedal region](assets/readme/vertical-force.png)

**Load Case 2: Force3** — +250 N in X and −900 N in Z.

![Load Case 2 primary force with X and Z components](assets/readme/case-2-combined-force.png)

**Both cases: Force2 / Force4** — +800 N in Z per selected entity, shown at the central circular feature.

![Secondary upward force at the central circular feature, shared by both load cases](assets/readme/secondary-force.png)

The report's fixed-constraint images are identical to the model overview and do not visibly distinguish the fixed faces. Verify the exact constrained entities in Fusion before rebuilding the study.

</details>

## Results and interpretation

The HTML report's numerical result-summary tables are empty. The stress and displacement values below are therefore **transcribed from the visible legends in its result images**. Safety-factor minima are **read separately from the uploaded WebM animations**; they are not populated values from the HTML summary tables.

| Result and source | Load Case 1 | Load Case 2 |
| --- | ---: | ---: |
| von Mises stress, minimum — report image | 0.044 MPa | 0.025 MPa |
| von Mises stress, maximum — report image | 134.348 MPa | 126.850 MPa |
| First principal stress, minimum — report image | −21.201 MPa | −16.769 MPa |
| First principal stress, maximum — report image | 118.066 MPa | 99.599 MPa |
| Third principal stress, minimum — report image | −142.014 MPa | −133.816 MPa |
| Third principal stress, maximum — report image | 20.799 MPa | 13.225 MPa |
| Total displacement, minimum — report image | 0 mm | No readable value exported |
| Total displacement, maximum — report image | 1.305 mm | No readable value exported |
| Minimum safety factor displayed in WebM | 6.569 | 6.957 |

**What the result types mean:** von Mises stress supports comparison with the yield strength of this ductile material; first and third principal stresses describe the largest and smallest principal stress components, including tensile and compressive regions. Total displacement describes movement from the original geometry. A deformation animation visualizes the result and does not establish the physical displacement scale unless its scale settings are known.

### Load Case 1

The report's guided result states:

> With the analysis criteria in this study setup, there is opportunity to reduce the volume of material and cost of this design.

The exported von Mises plot reaches **134.348 MPa**, and the displacement plot reaches **1.305 mm**, with the largest visible displacement toward the pedal end. The corresponding WebM displays a minimum safety factor of **6.569**. These exports support investigating further material removal under this particular setup, subject to checking the loads, constraints, mesh, and design requirements.

### Load Case 2

The report's guided result states:

> With the analysis criteria in this study setup, the design is expected to bend permanently or break.

However, its stress image shows a maximum von Mises stress of **126.850 MPa**, below the exported **882.528 MPa** yield strength, while the corresponding WebM displays a minimum safety factor of **6.957** and predominantly blue, above-target regions. The HTML safety-factor image is also predominantly blue. **The Case 2 guided warning and these numerical/visual exports do not agree.**

This README preserves both observations. The native study and a fresh solve/export are needed to determine which result state or guidance is applicable. A lower displayed stress in Case 2 does not resolve that inconsistency or establish that the design is ready for service. Its exported displacement image is uncolored and has no readable numerical legend, so no Case 2 displacement value is asserted here.

## Report figure gallery

These are the original report images, including incomplete result captures. Expand each case to inspect its safety factor, stress components, and displacement directly within the README. Click an image to inspect it at full resolution.

<details>
<summary>Load Case 1 — all exported result figures</summary>

### Safety factor

The report uses this same image for its guided safety-factor result and its safety-factor result table. It contains no visible contour scale or numerical safety-factor legend; the numerical minimum listed above comes from the WebM instead.

![Load Case 1 safety-factor capture, exported without a colored contour or numerical legend](assets/readme/case-1-safety-factor.png)

### von Mises stress

![Load Case 1 von Mises stress, 0.044 to 134.348 MPa](assets/readme/case-1-von-mises.png)

### First principal stress

![Load Case 1 first principal stress, minus 21.201 to 118.066 MPa](assets/readme/case-1-first-principal.png)

### Third principal stress

![Load Case 1 third principal stress, minus 142.014 to 20.799 MPa](assets/readme/case-1-third-principal.png)

### Total displacement

![Load Case 1 total displacement, 0 to 1.305 mm](assets/readme/case-1-displacement.png)

</details>

<details>
<summary>Load Case 2 — all exported result figures</summary>

### Safety factor

The report reuses this image for its guided result and its safety-factor result table. The marked values **1.442** and **3.225** identify the displayed target-range boundaries, not the minimum and maximum solved safety factors.

![Load Case 2 safety-factor plot with above-target, in-range, and below-target display bands](assets/readme/case-2-safety-factor.png)

### von Mises stress

![Load Case 2 von Mises stress, 0.025 to 126.850 MPa](assets/readme/case-2-von-mises.png)

### First principal stress

![Load Case 2 first principal stress, minus 16.769 to 99.599 MPa](assets/readme/case-2-first-principal.png)

### Third principal stress

![Load Case 2 third principal stress, minus 133.816 to 13.225 MPa](assets/readme/case-2-third-principal.png)

### Total displacement

This is the displacement capture as exported; the missing contour and legend have not been reconstructed.

![Load Case 2 displacement capture, exported without a colored contour or numerical legend](assets/readme/case-2-displacement.png)

</details>

## Load-case animations

Both uploaded WebM files show **Static Stress — Safety Factor** results. The GIF previews below are derived from those files so they display directly in a GitHub README. The original WebM files remain available at their original resolution.

### Load Case 1

[![Animated Load Case 1 safety-factor result](assets/readme/load-case-1.gif)](Reports/LoadCase1.webm)

[Open or download the original LoadCase1.webm](Reports/LoadCase1.webm)

### Load Case 2

[![Animated Load Case 2 safety-factor result](assets/readme/load-case-2.gif)](Reports/Loadcase2.webm)

[Open or download the original Loadcase2.webm](Reports/Loadcase2.webm)

## Further design work

The report recommends checking the setup and other result types before changing the geometry. Its Case 1 guidance suggests lightweighting regions above the safety-factor limit; its Case 2 guidance additionally recommends strengthening weak areas and increasing stiffness. Resolving the Case 2 export discrepancy is the first step before deciding which changes are justified.

<details>
<summary>Study-report recommendations</summary>

**Validate the study setup**

- Check that the applied loads are appropriate and are not set too high.
- Check mesh refinement, especially in high-stress areas.
- Confirm the required safety factor.
- If displacement is high, consider a nonlinear study.

**Check other results**

- Inspect the below-target visualization for weak regions.
- Inspect stress for possible yielding.
- Inspect displacement for movement from the original alignment.
- Review reaction forces to check the setup and strain to assess material performance.

**Lightweight regions above the safety-factor limit**

- Set a safety-factor upper limit to identify potential material-removal regions.
- Remove material from regions above that limit.
- Explore design modifications in the Generative Design workspace.
- Consider a Shape Optimization study to identify unnecessary material.

**Strengthen regions below target, as recommended in Case 2**

- Add material to weak areas.
- Consider a material with higher yield strength.
- Stiffen the design.
- Modify the geometry through a Generative Design study and evaluate alternatives.

</details>

The supplied files do not document the original optimization objectives, preserved/obstacle geometry, manufacturing constraints, alternative generated designs, a mesh-convergence study, fatigue assessment, or physical testing. These would be useful additions for extending the project and assessing repeated braking loads. This remains an educational prototype rather than a manufacturing-ready design.

## Repository files and viewing instructions

| File or directory | Purpose |
| --- | --- |
| [Brake Stem 1 GD3 copy.stl](Brake%20Stem%201%20GD3%20copy.stl) | Exported triangle mesh of the lever; open the repository file to inspect its 3D preview where supported, or import it into a CAD/mesh viewer. |
| [Study Report for Brake Pedal_PDR.html](Reports/Study%20Report%20for%20Brake%20Pedal_PDR.html) | Original Fusion study report, including its embedded images. Download and open it in a browser to use the original report layout. |
| [LoadCase1.webm](Reports/LoadCase1.webm) | Original Load Case 1 safety-factor animation. |
| [Loadcase2.webm](Reports/Loadcase2.webm) | Original Load Case 2 safety-factor animation. |
| [assets/readme/](assets/readme/) | PNG figures extracted from the report and GIF previews derived from the original WebM files for inline display. |

GitHub displays HTML repository files as source rather than embedding their interactive report layout in a README. The report content is therefore included above as Markdown tables and inline figures, with expandable sections for the detailed exports.

To continue the CAD work, import the STL into Autodesk Fusion or another compatible application and verify the intended units on import: STL does not encode a unit system. The repository does not contain a native Fusion design file, parametric history, or an editable simulation study. Rebuilding the analysis requires reconstructing the material assignment, mesh, exact constrained faces, and force selections from the report and then solving and validating the study again.
