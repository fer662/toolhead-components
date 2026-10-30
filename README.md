# Toolhead components

Reusable CAD references for 3D printer toolhead design, with explicit material assignments, mass estimates, center-of-mass (COM) references, and source attribution.

This repository will collect:

- Standalone Fusion component files that can be reused in toolhead assemblies.
- Material and density assumptions so calculated mass can be inspected in Fusion Properties.
- COM markers, coordinate conventions, and notes on how each estimate was obtained.
- Provenance for third-party geometry, including links to its authors and a description of our changes.
- Known omissions and validation notes, keeping measured values distinct from model estimates.
- Additional exchange formats and supporting calculation data as they become available.

## Available components

| Component | File | Calculated mass | Contents | Provenance |
| --- | --- | --- | --- | --- |
| MGN12H linear-rail carriage | [MGN12H.f3d](MGN12H.f3d) | 49.518 g | Assigned materials, 60 bearing balls, calculated COM point, orange reference marker | [MGN12H – Full detail](https://grabcad.com/library/mgn12h-full-detail-1) by Steven de Roos; adapted for Fusion with materials and COM reference. |
| CHUBE Air / Conduction | [CHUBE_INTEGRATION_REVA.step](CHUBE_INTEGRATION_REVA.step) | — | Combined integration reference, including supplied COM references | [CHUBE / Luke's Laboratory](https://www.chubehotends.com/integrations); original manufacturer STEP, unchanged. |
| CHUBE Compact | [Chube_Compact_integration_assembly.step](Chube_Compact_integration_assembly.step) | — | Integration assembly | [CHUBE / Luke's Laboratory](https://www.chubehotends.com/integrations); original manufacturer STEP, unchanged. |

Download the `.f3d` file and open it in Autodesk Fusion. Select the root component and open **Properties** to inspect its combined mass. The archive is standalone; it does not require the original toolhead assembly.
