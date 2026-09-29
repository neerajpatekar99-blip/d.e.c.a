# Project D.E.C.A. - Phase I Mechanical & Vacuum Chamber Engineering Blueprint
## 3D CAD Assembly, Tolerancing, and Vacuum-Electromagnetic Hardware Specification

**Author:** Neeraj Bhupendra Patekar  
**Domain:** Mechanical CAD Design, Ultra-High Vacuum (UHV) Systems, Pulsed-Power Hardware Engineering  
**Document Classification:** Mechanical & Vacuum Architecture Blueprint (Rev 1.0)  
**Date of Formulation:** September 25, 2026  

---

### 1. Coordinate System & Structural Envelope

To maintain absolute dimensional consistency across SolidWorks, FreeCAD, and OpenFOAM simulation meshes, all components are referenced to a unified Cartesian coordinate frame:

* **Z-Axis (Axial):** Aligned with the central cylindrical axis of the hollow anode. 
  * `Z = 0.00 mm`: Triple-junction interface (knife-edge lip of the Boron Nitride insulator).
  * `Z = -35.00 mm`: Rear base flange / stripline transition.
  * `Z = +160.00 mm`: Tip of the W-25Re anode (pinch ignition plane).
  * `Z = +160.00 to +460.00 mm`: Faraday induction stator ceramic duct.
* **R-Axis (Radial):** Cylindrical radius from the central bore centerline (`R = 0.00 mm`).
* **Theta-Axis (Azimuthal):** 360-degree rotational symmetry.

```
                            CROSS-SECTIONAL ELEVATION VIEW
                            
    Port 3: Piezo Gas Injector (Top, CF 40)
       │
       ▼
   ┌───────┐
   │ ┌───┐ │  Cathode Rods (x16, PCD 100 mm)
───┼─┼───┼─┼─────────────────────────────────────────┬───────────────────────────
   │ │   │ │                                         │
   │ │   │ │   ┌───────────────────────────────┐     │  Ceramic Duct (Si3N4)
   │ │hBN│ │   │ Anode Barrel: W-25Re          │     │  ═════════════════════════►
Stripline ─┼───┤                               ├─────┼──[Coil 1] [Coil 2] [Coil 3]
Feedthru   │   │  Hollow Bore (ID: 18 mm)      │     │  ═════════════════════════►
   │ │hBN│ │   │                               │     │   (Faraday Stator Stages)
   │ │   │ │   └───────────────────────────────┘     │
   │ │   │ │                                         │
───┼─┼───┼─┼─────────────────────────────────────────┴───────────────────────────
   │ └───┘ │
   └───────┘
       ▲
       │
    Port 4: Turbomolecular Vacuum Port (Bottom, CF 150)
```

---

### 2. Vacuum Chamber Architecture & Port Layout

The reactor vessel is engineered from low-magnetic permeability **AISI 316LN Stainless Steel** to prevent magnetic field distortion and eddy current damping during the 3.8 MA pulse.

#### 2.1 Main Chamber Geometry
* **Vessel Type:** Modified 6-Way Cross with ConFlat (CF) knife-edge metal gasket flanges.
* **Main Bore Diameter:** 150 mm (CF 150 Flange size).
* **Wall Thickness:** 6.0 mm (rated for 10^-8 Torr base pressure and violent acoustic pressure pulses).
* **Interior Surface Finish:** Electro-polished to `Ra < 0.2 micrometers` to minimize gas desorption and outgassing under hard X-ray illumination.

#### 2.2 Six-Way Port Assignment Matrix:

| Port | Orientation | Flange Size | Subsystem Mounted | Function |
| :--- | :--- | :--- | :--- | :--- |
| **Port 1** | Axial Rear (`-Z`) | **CF 200** | High-Current Stripline Header | Clamps anode and cathode baseplates to capacitor stripline with sub-nanohour inductance. |
| **Port 2** | Axial Forward (`+Z`) | **CF 100** | Faraday Stator Duct Coupling | Transitions from metal chamber to the 25 mm non-conductive ceramic induction duct. |
| **Port 3** | Vertical Top (`+Y`) | **CF 40** | Piezo Gas-Puff Injector | Houses the 40-micron piezo stack and heated Decaborane (B10H14) vapor nozzle. |
| **Port 4** | Vertical Bottom (`-Y`) | **CF 150** | Turbomolecular Pump Station | Connected via LN2/dry-ice cold trap chevron baffle to a 300 L/s turbopump; pulls down to `10^-6 Torr` while shielding pump blades from abrasive boron dust. |
| **Port 5** | Lateral Left (`-X`) | **CF 63** | Optical Interferometer Port | Optical-grade Fused Silica viewport for 532 nm laser Schlieren / shadowgraphy of sheath. |
| **Port 6** | Lateral Right (`+X`) | **CF 40** | Rogowski Diagnostic Feedthrough | High-bandwidth differential Rogowski coil and capacitive voltage divider (`dV/dt`). |

---

### 3. Precision Electrode Subassembly & Tolerances

```
                      ANODE TIP & INSULATOR LIP DETAIL
                      
                W-25Re Anode (OD 40 mm, ID 18 mm)
                ┌───────────────────────────────────────────────┐
                │                                            45°│ Chamfered
                │   Hollow Axial Exhaust Canal (ID 18 mm)       │ Nozzle
                │                                            45°│ (Tip)
                └───────────────────────────────────────────────┘
                 ▲
   h-BN Sleeve   │ 0.05 mm Precision Slip-Fit
   ┌─────────────┴─┐
   │30° Knife-Edge │ Triple Junction (Local E-field > 150 kV/cm)
   └───────────────┘
```

#### 3.1 Central Anode (W-25Re Alloy)
* **Part Number:** `DECA-ANO-W25RE-001`
* **Material Composition:** 75.0 wt% Tungsten, 25.0 wt% Rhenium (vacuum arc remelted).
* **Outer Diameter (OD):** `40.00 mm (+0.00 mm / -0.02 mm)`.
* **Inner Bore Diameter (ID):** `18.00 mm (+0.02 mm / -0.00 mm)`.
* **Overall Length:** `195.00 mm` (160 mm exposed active length + 35 mm rear clamping stalk).
* **Tip Profile:** 45.0° ± 0.2° chamfer machined inward to a depth of 2.5 mm to anchor the magnetic flux compression at the hollow entrance.
* **Surface Roughness:** Ground and honed to `Ra = 0.4 µm` along the outer cylindrical barrel; interior bore polished to `Ra = 0.2 µm` to ensure zero boundary-layer drag for expanding alpha ions.

#### 3.2 Peripheral Cathode Array (Squirrel Cage)
* **Part Number:** `DECA-CAT-ROD-016` (Qty: 16)
* **Material:** Oxygen-Free High-Conductivity Copper (C10100 OFHC), vacuum-annealed.
* **Rod Dimensions:** Diameter `8.00 mm (± 0.01 mm)`, Length `175.00 mm`.
* **Pitch Circle Diameter (PCD):** `100.00 mm (± 0.05 mm)`.
* **Surface Plating:** Inner facing 180° arc of each rod is electro-plated with `50.0 µm` Tungsten to resist plasma sputtering.
* **Alignment Ring:** Forward cathode ends are rigidly braced by a circular OFHC copper tie-ring (`OD 116 mm, ID 92 mm, thickness 6 mm`) with radiused edges to eliminate parasitic corona arcing.

#### 3.3 Hexagonal Boron Nitride Insulator Sleeve
* **Part Number:** `DECA-INS-HBN-001`
* **Material:** Grade AX05 Hot-Pressed Hexagonal Boron Nitride (HP-BN, 99.5% purity, zero binder).
* **Outer Diameter:** `44.00 mm (± 0.02 mm)`.
* **Inner Diameter:** `40.05 mm (+0.02 mm / -0.00 mm)` (precision slip-fit over the anode).
* **Length:** `35.00 mm` extending forward from the cathode header plane.
* **Triple-Junction Knife-Edge:** Forward lip beveled at `30.0°` terminating in a sharp `0.10 mm` flat. This geometrically magnifies the electrostatic field gradient, triggering sub-1.5 ns Townsend breakdown.

---

### 4. Faraday Stator Duct & Coil Assembly

The Faraday stator extracts electrical energy directly from the supersonic alpha beam through a ceramic vacuum pipe without physical contact.

```
                      FARADAY INDUCTION DUCT CROSS-SECTION
                      
        Liquid Nitrogen Cooling Jackets
        ┌───┐       ┌───┐       ┌───┐       ┌───┐       ┌───┐       ┌───┐
        │ C1│       │ C2│       │ C3│       │ C4│       │ C5│       │ C6│
   ═════╧═══╧═══════╧═══╧═══════╧═══╧═══════╧═══╧═══════╧═══╧═══════╧═══╧═════►
    Alpha Beam ──► Silicon Nitride Ceramic Duct (ID: 20 mm, OD: 25 mm)
   ═════╤═══╤═══════╤═══╤═══════╤═══╤═══════╤═══╤═══════╤═══╤═══════╤═══╤═════►
        │ C1│       │ C2│       │ C3│       │ C4│       │ C5│       │ C6│
        └───┘       └───┘       └───┘       └───┘       └───┘       └───┘
        ◄── 35 mm ──► Pitch Spacing between Induction Stages
```

#### 4.1 Ceramic Exhaust Duct Specification
* **Material:** Gas-Pressure Sintered Silicon Nitride (`Si3N4`) or Ultra-Pure Fused Quartz.
  * *Why Si3N4:* Zero electrical conductivity, high mechanical hoop tensile strength (> 800 MPa), and zero magnetic permeability (`mu_r = 1.000`).
* **Outer Diameter:** `25.00 mm (± 0.05 mm)`.
* **Inner Diameter:** `20.00 mm (± 0.05 mm)` (wall thickness: 2.5 mm).
* **Length:** `300.00 mm`.
* **Vacuum Coupling:** Brazed Kovar transition rings on both ends, welded to CF 100 mating flanges with Viton / Helicoflex metal seals.

#### 4.2 Multi-Stage Stator Pick-Up Coils
* **Number of Stages:** 6 independent, sequential coaxial induction stages.
* **Axial Pitch:** `35.0 mm` center-to-center spacing.
* **Coil Conductor:** Hollow OFHC Copper tubing (`OD 4.0 mm, ID 2.0 mm`).
  * *Internal Cooling:* Chilled de-ionized water or liquid nitrogen (LN2) circulating continuously through the hollow conductor bore to maintain ultra-low electrical resistance.
* **Turns per Stage:** 4 tight concentric turns per stage (mean radius `R = 15.5 mm`).
* **DC Magnetic Bias:** Each stage is bracketed by a pair of Neodymium-Iron-Boron (NdFeB, Grade N52) permanent ring magnets producing a static `2.0 Tesla` transverse magnetic bias field across the ceramic bore.

---

### 5. High-Current Stripline & Header Clamping

At 3.8 MA, magnetic repulsion forces (`Lorentz bursting pressure`) between the stripline plates exceed **30 MPa (300 atmospheres)**. Any mechanical flexing increases loop inductance and reduces current rise time.

```
                    PARALLEL-PLATE STRIPLINE DIELECTRIC SANDWICH
                    
    Top Ground Plate (OFHC Copper, 3.0 mm)
    ════════════════════════════════════════════════════════════════════════════
    Multi-layer Kapton Film (1.5 mm total, 6 x 250 µm sheets) [Breakdown > 220 kV/mm]
    ────────────────────────────────────────────────────────────────────────────
    Bottom High-Voltage Plate (OFHC Copper, 3.0 mm, Charging: +50 kV DC)
    ════════════════════════════════════════════════════════════════════════════
    ▲
    │ High-Torque Non-Magnetic Titanium Clamping Bolts with Belleville Washers
```

#### 5.1 Stripline Busbar Parameters
* **Conductor Plates:** Precision cold-rolled OFHC Copper sheets (`Width: 600 mm, Thickness: 3.0 mm`).
* **Dielectric Insulation:** 6 layers of `250 µm` DuPont Kapton HN polyimide film interleaved with `50 µm` Mylar film (total thickness `1.8 mm`).
* **Dielectric Overhang:** Kapton insulation extends `60.0 mm` past the copper sheet perimeter on all sides to eliminate edge surface tracking and Paschen breakdown in ambient air.

#### 5.2 Header Clamping Mechanism
* **Fasteners:** Grade 5 Titanium (Ti-6Al-4V) non-magnetic bolts spaced on a `40 mm x 40 mm` grid.
* **Spring Loading:** Every bolt includes a pair of Belleville disc spring washers torqued to `45 N-m`, guaranteeing a constant, uniform interfacial clamping pressure of `> 18 MPa` across the entire stripline area to suppress micro-gap arcing.

---

### 6. Piezo-Electric Gas Injector Subassembly

* **Part Number:** `DECA-GAS-PZT-001`
* **Actuator:** High-force pre-stressed Piezo-electric stack actuator (PZT-5H).
  * Actuation Voltage: 0 to 150 V DC.
  * Stroke Length: `40.0 µm (± 1 µm)`.
  * Response Time: `< 25 microseconds`.
* **Poppet Valve Head:** Kalrez 7090 perfluoroelastomer tip seated into a polished 60° conical orifice (`throat diameter: 1.20 mm`).
* **Decaborane Vaporizer Reservoir:**
  * Solid Decaborane (`B10H14`) crystals sit in an auxiliary stainless steel chamber heated to `85°C` by an external PID silicone heating band (vapor pressure: ~15 Torr).
  * Ultra-pure Hydrogen carrier gas (`H2`) sweeps through the sublimation chamber, delivering a 1:1 proton-to-boron ratio into the valve throat.
* **Puff Timing:** The valve opens `180 microseconds` before capacitor discharge, creating a localized `3.0 Torr` gas bubble over the insulator lip while keeping the main chamber at `< 10^-4 Torr`.

---

### 7. CAD Bill of Materials (BOM) & Parametric Hierarchy

```
[DECA-ASM-001: COMPLETE REACTOR CORE ASSEMBLY]
├── [DECA-VAC-CHAMBER-001] 6-Way CF 150 316LN Stainless Chamber Body
│   ├── [FLG-CF150-BLIND] Bottom Turbopump Adapter Flange
│   ├── [FLG-CF100-TRANS] Forward Stator Transition Flange
│   └── [WND-CF63-QUARTZ] Laser Interferometry Optical Viewport
├── [DECA-ELC-SUBASM-001] Coaxial Electrode Subassembly
│   ├── [DECA-ANO-W25RE-001] Hollow Central Anode (40 mm OD, 18 mm ID, W-25Re)
│   ├── [DECA-CAT-ROD-016] Peripheral Cathode Rods (Qty 16, OFHC + W-plated)
│   ├── [DECA-CAT-RING-001] Forward Cathode Reinforcement Ring
│   └── [DECA-INS-HBN-001] Hexagonal Boron Nitride Knife-Edge Sleeve
├── [DECA-STR-STATOR-001] Faraday Induction Energy Recovery Subassembly
│   ├── [DECA-DCT-SI3N4-001] 25 mm Silicon Nitride Vacuum Duct Tube
│   ├── [DECA-COIL-OFHC-006] 4-Turn Coaxial Stator Coils (Qty 6, LN2 cooled)
│   └── [MAG-N52-RING-012] 2.0 Tesla Permanent Bias Magnets (Qty 12)
├── [DECA-PROT-SUBASM-001] Hard-Stop Prevention & Reliability Subassembly
│   ├── [DECA-VAC-CRYO-001] Liquid Nitrogen/Dry-Ice Cold Trap Chevron Baffle (Port 4)
│   ├── [DECA-BEL-316L-001] CF 100 Edge-Welded Stainless Steel Anode Expansion Bellows
│   ├── [DECA-SW-PSEUDO-004] Quad-Parallel Sealed Pseudospark Plasma Switch Array (50 Hz)
│   └── [DECA-CTL-FIBER-001] Multi-Channel Optical Fiber Trigger & Telemetry Transceivers
└── [DECA-PWR-BUS-001] Ultra-Low Inductance Parallel Stripline
    ├── [BUS-CU-HV-001] 50 kV Bottom High-Voltage Copper Plate (600 mm)
    ├── [BUS-CU-GND-001] Ground Return Top Copper Plate (600 mm)
    └── [INS-KAPTON-006] Multi-Layer Dielectric Sandwich (1.8 mm)
```

---

### 8. Manufacturing & Assembly Protocol

1. **Ultrasonic Degreasing:** All stainless steel, tungsten-rhenium, and copper components undergo 45-minute ultrasonic cleaning in semiconductor-grade acetone, followed by isopropyl alcohol (IPA), and are baked in a vacuum oven at 120°C for 4 hours.
2. **h-BN Sleeve Cleanliness:** Boron Nitride parts are handled strictly with powder-free nitrile gloves and stored in a nitrogen desiccator box; h-BN is never exposed to liquid water to prevent micro-delamination.
3. **Helium Leak Rate Check:** The assembled vacuum envelope must demonstrate a global helium leak rate of less than `1.0 x 10^-9 mbar-L/second` before high-voltage electrical connection.
4. **Stripline Hi-Pot Test:** The parallel stripline busbar is tested with a 75 kV DC hipot tester for 60 seconds with zero dielectric leakage (< 10 µA) prior to coupling with the capacitor bank.

---

### 9. Hard-Stop Prevention Subsystems (Eliminating Lab Showstoppers)

To prevent catastrophic experimental shutdowns during continuous 50 Hz operation, four specialized mechanical protections are integrated directly into the hardware stack:

#### 9.1 Fiber-Optic Trigger & Telemetry Isolation (`DECA-CTL-FIBER-001`)
* **Hazard:** 3.8 MA discharge with `dI/dt > 10^12 A/s` generates severe EMP, inducing hundreds of volts in metallic signal cables and frying digital logic.
* **Architecture:** Control signals between the diagnostic control PC and the reactor high-voltage deck travel exclusively over **Avago HFBR-1521 / standard plastic optical fiber (POF)** lines. Zero copper data cables cross the high-voltage perimeter, providing > 100 kV galvanic isolation.

#### 9.2 Cryogenic Cold-Trap Chevron Baffle (`DECA-VAC-CRYO-001`)
* **Hazard:** Sputtered tungsten particles and unburned Decaborane dust entering the turbomolecular pump at 80,000 RPM will shred titanium rotor blades.
* **Architecture:** Mounted directly between Chamber Port 4 and the turbopump gate valve. An optically-dense stainless steel chevron baffle cooled by liquid nitrogen or dry ice freezes out unreacted boranes and intercepts metallic particulates via impaction, protecting pump bearings and blades.

#### 9.3 Sealed Pseudospark Plasma Switch Array (`DECA-SW-PSEUDO-004`)
* **Hazard:** Traditional spark gaps erode and pit within minutes under 50 Hz continuous pulsing (180,000 shots/hour).
* **Architecture:** Utilizes a quad-parallel bank of sealed cold hollow-cathode **Pseudospark switches** (gas-filled ceramic envelopes). Current conduction occurs via a broad diffuse plasma discharge rather than a localized spark arc, achieving an operating lifetime exceeding **100 million pulses**.

#### 9.4 Anode Axial Expansion Bellows (`DECA-BEL-316L-001`)
* **Hazard:** Repetitive 50 Hz thermal pulsing causes the central W-25Re anode to expand axially by up to 1.5 mm. Rigid mechanical mounting would exert destructive shear force on the brittle h-BN insulator sleeve.
* **Architecture:** An edge-welded 316LN stainless steel flexible bellows is integrated into the rear CF 100 mounting flange. The bellows accommodates up to 2.5 mm of axial thermal displacement while maintaining UHV vacuum seal integrity (`< 10^-9 mbar-L/s`).
