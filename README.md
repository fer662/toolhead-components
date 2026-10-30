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

| Component | File | Calculated mass | Contents |
| --- | --- | --- | --- |
| MGN12H linear-rail carriage | [MGN12H.f3d](MGN12H.f3d) | 49.518 g | Assigned materials, 60 bearing balls, calculated COM point, orange reference marker |

Download the `.f3d` file and open it in Autodesk Fusion. Select the root component and open **Properties** to inspect its combined mass. The archive is standalone; it does not require the original toolhead assembly.

## MGN12H provenance and preparation

The source is **[MGN12H – Full detail](https://grabcad.com/library/mgn12h-full-detail-1)** by **Steven de Roos**, published on GrabCAD. Credit for the source carriage geometry belongs to its author. This is a representative carriage model; it is not a manufacturer-certified model of a particular tested unit.

The Fusion version was prepared from the saved display meshes in the source SolidWorks files, preserving assembly placements. Mesh payload integrity was checked, and all seven unique source mesh shapes were closed and consistently wound. The bearing-ball mesh was replaced with an exact native Fusion sphere of the same 2.3 mm diameter, shared across all 60 ball instances. The other six unique parts retain their source mesh representation; this is a mixed mesh/BRep model, without the original SolidWorks feature history.

Our changes include assigning explicit material densities, centering and orienting the standalone assembly, replacing the faceted ball geometry with spheres, calculating native Fusion physical properties, and adding a COM reference. Geometry was not scaled and mass was not normalized to a target weight.

### Parts and materials

There are **73 physical instances** across seven unique parts, plus a separate reference component for the COM marker.

| Part | Instances | Assigned density (g/cm³) | Basis |
| --- | ---: | ---: | --- |
| Main body | 1 | 7.68 | Assumed steel density |
| Bearing ball, Ø2.3 mm | 60 | 7.68 | Assumed steel density |
| End cap P1 | 2 | 1.02 | ABS density stored in the source files |
| End cap P2 | 2 | 1.02 | ABS density stored in the source files |
| Retainer | 2 | 8.00 | 304 stainless steel density stored in the source files |
| End seal | 2 | 1.20 | Assumed elastomer density |
| Internal M2×8 end-cap screw | 4 | 7.85 | Assumed steel density |

These assignments describe the calculation scenario. They do not establish the actual material grades of a physical carriage. External carriage mounting screws are not included.

### Calculated mass and COM

Fusion's native physical-properties calculation gives **49.517916 g**, displayed as **49.518 g** in Properties. The exported archive was reopened to verify the material assignments, mass, COM point, and visible geometry.

The COM follows the mass-weighted centroid, `COM = Σ(mᵢ × rᵢ) / Σmᵢ`, using each part's geometry, placement, and assigned density.

The standalone coordinate system places the source steel body's geometric midpoint at the origin:

- **X:** along the rail.
- **Y:** through the block thickness; the mounting face is at **Y = +5 mm**.
- **Z:** across the block width.

Calculated COM, in millimeters in that coordinate system:

| X | Y | Z |
| ---: | ---: | ---: |
| +0.010247 | +0.768323 | +0.013402 |

The COM lies approximately **4.231677 mm behind the mounting face**. The `REFERENCE - carriage COM orange crosshair` component contains the named construction point and three orange surface markers. These surfaces have zero enclosed volume and add no mass to the calculation.

The permanent COM reference is included in the file. Its visibility through opaque parts on the preparation computer is provided by a separate local Fusion display add-in; that show-through behavior is not bundled into the `.f3d` archive.

### Limits and measured mass

- The model contains four straight ball rows, with 15 balls per row. Balls in the turnaround arcs and grease are omitted.
- Internal dimensions and actual material grades have not been verified against the tested carriage.
- Most parts use saved display meshes, so their volume and centroid depend on the source tessellation.
- Agreement with a plausible mass range is a useful check, but does not validate the internal mass distribution or physical COM.

Our test carriage was measured at **48 g**. That measured value remains the carriage mass used in the toolhead assembly's COM calculation; the carriage is excluded from the separately reported toolhead weight. The **49.518 g** value here is the standalone model estimate and does not replace the measurement.

## Attribution and reuse

The upstream CAD geometry is credited above. This repository does not claim authorship of that geometry or apply a new license to it. Refer to the original GrabCAD listing and its applicable terms for reuse of the source and derived geometry. No repository-wide license is asserted for third-party assets.

For future components, include the original author and source, changes made, material assumptions, coordinate frame, validation performed, and known limitations alongside each model.
