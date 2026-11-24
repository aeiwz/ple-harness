# Phased Data-Center Campus BIM Model (`p6_002`) — Summary Report

### Deliverable
- **File**: `submission/model.ifc`
- **Format**: ISO-10303-21 STEP Physical File, Schema IFC4
- **Verification Status**: **FEASIBLE** (17 / 17 binding requirements satisfied)

---

### Campus Layout & Architecture

The site layout accommodates the two delineated wetlands (`WET1` and `WET2`) and utilizes the upland corridor centered around $x = 180\,\text{m}$ for primary access and distribution.

1. **`DH_P1` (Phase 1 Data Hall)**:
   - Footprint: $[80, 170] \times [20, 70]\,\text{m}$ ($4,500\,\text{m}^2$, aspect ratio $1.8 \le 2.5$).
   - Height: $8.0\,\text{m}$, 2 Storeys (Elevations $0.0\,\text{m}$ and $4.0\,\text{m}$, floor-to-floor $4.0\,\text{m} \in [3.2, 5.5]\,\text{m}$).
   - Gross Floor Area: $9,000\,\text{m}^2 \ge 7,200\,\text{m}^2$.
   - Road Separation: $10.0\,\text{m} \le 18.0\,\text{m}$ apparatus access.

2. **`DH_P2` (Phase 2 Data Hall)**:
   - Footprint: $[80, 170] \times [200, 250]\,\text{m}$ ($4,500\,\text{m}^2$, aspect ratio $1.8 \le 2.5$).
   - Height: $8.0\,\text{m}$, 2 Storeys (Elevations $0.0\,\text{m}$ and $4.0\,\text{m}$, floor-to-floor $4.0\,\text{m} \in [3.2, 5.5]\,\text{m}$).
   - Gross Floor Area: $9,000\,\text{m}^2 \ge 7,200\,\text{m}^2$.
   - Road Separation: $10.0\,\text{m} \le 18.0\,\text{m}$ apparatus access.

3. **`SUB` (Phase 1 Substation)**:
   - Footprint: $[190, 245] \times [168, 201]\,\text{m}$ ($1,815\,\text{m}^2 \ge 1,000\,\text{m}^2$).
   - Height: $4.0\,\text{m}$, 1 Storey.
   - Dual function: acts as a 3D line-of-sight acoustic barrier shielding Receptor R1 from the Generator Yard and Receptor R2 from the Cooling Plant.

4. **`GEN` (Phase 1 Generator Yard, Hazard Class H-1)**:
   - Footprint: $[274, 301] \times [174, 194]\,\text{m}$ ($540\,\text{m}^2 \ge 500\,\text{m}^2$).
   - Height: $3.0\,\text{m}$, 1 Storey.
   - Separation: $29.0\,\text{m}$ to `SUB`, $31.0\,\text{m}$ to `CTP`, $>100\,\text{m}$ to `DH_P1`/`DH_P2` (all $\ge 28.0\,\text{m}$).

5. **`CTP` (Phase 1 Cooling Plant)**:
   - Footprint: $[240, 280] \times [225, 245]\,\text{m}$ ($800\,\text{m}^2 \ge 800\,\text{m}^2$).
   - Height: $4.0\,\text{m}$, 1 Storey.

6. **`BRM` (Phase 1 Landscape Berm)**:
   - Footprint: $[250, 302] \times [166, 172]\,\text{m}$ ($312\,\text{m}^2 \ge 300\,\text{m}^2$).
   - Height: $4.5\,\text{m}$, placed south of `GEN`.
   - Blocks 100% of 3D lines of sight from Receptor R2 to `GEN`.

7. **`RET` (Phase 1 Stormwater Retention Basin)**:
   - Footprint: $[20, 65] \times [20, 60]\,\text{m}$ ($1,800\,\text{m}^2 \ge 1,641.7\,\text{m}^2$ required).
   - Modeled as an extruded solid below grade ($-0.3\,\text{m}$ to $0.0\,\text{m}$).

---

### Infrastructure Networks & Connectivity

- **Road Network**:
  - `ROAD_TRUNK` (Phase 1): Centerline $[[180.0, 0.0], [180.0, 208.0]]$, width $6.0\,\text{m}$, length $208.0\,\text{m}$. Enters within $0.0\,\text{m} \le 2.0\,\text{m}$ of South frontage ($y=0$) and passes cleanly through the upland corridor.
  - `ROAD_EAST` (Phase 1): Centerline $[[180.0, 208.0], [265.0, 208.0]]$, width $6.0\,\text{m}$, length $85.0\,\text{m}$.
  - Total road length: $293.0\,\text{m}$.
- **Medium-Voltage Network**:
  - `MV_UTIL_SUB` (Phase 1): $[[320.0, 195.0], [245.0, 195.0]]$, length $75.0\,\text{m}$. Connects directly at utility point $(320, 195)$.
  - `MV_SUB_DH1` (Phase 1): $[[190.0, 168.0], [170.0, 70.0]]$, length $100.02\,\text{m}$.
  - `MV_SUB_DH2` (Phase 2): $[[190.0, 201.0], [170.0, 201.0]]$, length $20.0\,\text{m}$.
  - Total MV length: $195.02\,\text{m}$ ($175.02\,\text{m}$ in Phase 1).
- **Topology Graph**:
  - Embedded in `DCD_Networks` pset on `IfcSite`.
  - Typed edges: `utility_feed` (`GRID` $\rightarrow$ `SUB`), `power_feed` (`SUB` $\rightarrow$ `DH_P1`, `DH_P2`), and `vehicle_access` (`GATE` $\rightarrow$ `DH_P1`, `DH_P2`, `SUB`, `GEN`, `CTP`).

---

### Key Requirements & Verification Matrix

| # | Requirement | Brief Threshold | Model Value | Status |
|---|---|---|---|---|
| 1 | Program Footprints & Aspect Ratios | Per schedule; aspect $\le 2.5$ | Aspect 1.8; all areas $\ge$ min | **PASS** |
| 2 | Gross Floor Area & Storeys | GFA $\ge 7,200\,\text{m}^2$; f2f $\in [3.2, 5.5]\,\text{m}$ | $9,000\,\text{m}^2$; f2f $4.0\,\text{m}$ | **PASS** |
| 3 | Maximum Building Height | $\le 13.8\,\text{m}$ above grade | Max $8.0\,\text{m}$ | **PASS** |
| 4 | Lot Boundary Setbacks | $\ge 18.0\,\text{m}$ all lot lines | All $\ge 18.0\,\text{m}$ | **PASS** |
| 5 | Aggregate Footprint Cap | $\le 15.1\%$ of lot ($13,529.6\,\text{m}^2$) | $12,155.0\,\text{m}^2$ ($13.57\%$) | **PASS** |
| 6 | Wetland Separation & Buffers | $\ge 8.0\,\text{m}$ buffer to structures & roads | All structures & road edges $\ge 8.0\,\text{m}$ | **PASS** |
| 7 | Hazardous Material Separation | $\ge 28.0\,\text{m}$ (`GEN` to occupied) | Min separation $29.0\,\text{m}$ (`GEN`–`SUB`) | **PASS** |
| 8 | Fire Apparatus Access | Within $18.0\,\text{m}$ of access road | All within $17.0\,\text{m}$ | **PASS** |
| 9 | Frontage Entrance & Continuity | Within $2.0\,\text{m}$ of frontage; continuous | $0.0\,\text{m}$ from frontage; 100% continuous | **PASS** |
| 10 | Stormwater Retention Basin Sizing | $\ge 11.8\%$ of total impervious area | $1,800.0\,\text{m}^2 \ge 1,641.7\,\text{m}^2$ | **PASS** |
| 11 | Noise Limit (Phase 1 & Full Buildout) | $\le 42.35\,\text{dB(A)}$ at R1 & R2 | R1: $37.34\,\text{dB(A)}$; R2: $39.35\,\text{dB(A)}$ | **PASS** |
| 12 | Visual Screening of Generator Yard | Screened from R1 and R2 ($1.7\,\text{m}$ eye) | 100% shielded by `SUB` and `BRM` | **PASS** |
| 13 | Medium-Voltage System Bus & Reach | Line endpoints within $5.0\,\text{m}$ of target | $0.0\,\text{m}$ offset to targets | **PASS** |
| 14 | Graph Topology & Typed Edges | Valid schema, node set, typed edges | Fully connected, valid JSON payload | **PASS** |
| 15 | Design-to-Cost Full Buildout | $\le 473.0$ reference cap | **$282.92$** ($1.0 \times 195.02 + 0.3 \times 293.0$) | **PASS** |
| 16 | Phasing Scope & Allocation | P1: 6 buildings; P2: 1 building | Correctly phased and tagged in pset | **PASS** |
| 17 | Phase 1 Cost Cap & Standalone | $\le 314.0$; no cross-phase routing | **$262.92$**; zero cross-phase routing | **PASS** |

The resulting BIM model is fully compliant with IFC4 schema specifications and satisfies all statutory conditions of approval.