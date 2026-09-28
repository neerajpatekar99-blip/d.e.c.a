# Project D.E.C.A. Subsystem Specification
## Radiation Protection & Passive Shielding Envelope

> **Component Code:** DECA-SHLD-01  
> **Lead Theoretical Author:** Neeraj Bhupendra Patekar  
> **Design Philosophy:** Standard industrial two-layer passive clamshell shield. (Zero exotic liquid cooling, zero toxic materials, zero over-engineering).

---

### 1. Radiation Physics Profile of p-¹¹B Reaction

The primary proton–Boron-11 fusion reaction is completely aneutronic:
```
p + ¹¹B  ───>  3 ⁴He  +  8.7 MeV
```

However, in any real-world pulsed Dense Plasma Focus (DPF), three distinct radiation components must be addressed:

| Radiation Type | Origin | Energy Range | Penetration & Safety Risk |
| :--- | :--- | :--- | :--- |
| **Alpha Particles (⁴He²⁺)** | Primary fusion products (three alphas per reaction) | 2.0 to 4.5 MeV | **Zero external risk.** Alphas are stopped completely within 15 micrometers of solid copper or stainless steel. 100% contained inside the vacuum vessel. |
| **Bremsstrahlung X-Rays** | Intense deceleration of fast electrons in the high-density Boron plasma core | 2 keV to 60 keV (Peak at ~25 keV) | Highly penetrating through thin vacuum viewports. Requires dense high-Z metal attenuation. |
| **Secondary Fast Neutrons** | Parasitic side reactions (e.g., ¹¹B + p ──> ¹¹C + n, branching ratio < 0.1%) | 1.0 to 3.0 MeV | Stray fast neutrons. Requires low-Z hydrogenous moderator + neutron absorber. |

---

### 2. The Solution: Dual-Layer Modular "Clamshell" Shield

Instead of pouring cubic meters of heavy concrete or using exotic liquid lithium tanks, the DECA-SHLD-01 uses a **compact, two-layer split-clamshell enclosure** that rolls directly around the 316LN 6-way cross vacuum chamber:

```
                  CROSS-SECTION: TWO-LAYER SHIELD WALL
                  
      Outer Atmosphere (Safe Personnel Zone: < 0.05 mSv/hr)
    ─────────────────────────────────────────────────────────────
    ▲
    │   LAYER 2: 100 mm (10 cm) Borated HDPE (5% Boron)
    │   * Hydrogen nuclei slow down (thermalize) fast neutrons
    │   * Boron-10 absorbs thermal neutrons without hard gammas
    ▼
    ─────────────────────────────────────────────────────────────
    ▲
    │   LAYER 1: 6 mm Sheet Lead (Pb) Lining
    │   * High-Z electron density absorbs 99.9% of Bremsstrahlung X-rays
    ▼
    ─────────────────────────────────────────────────────────────
    ▲
    │   REACTOR VACUUM CHAMBER WALL: 12 mm 316LN Stainless Steel
    ▼
    ─────────────────────────────────────────────────────────────
      Plasma Core / Vacuum Zone (Pinch & Stator Duct)
```

---

### 3. Material Specifications

#### Layer 1 (Inner X-Ray Stop):
* **Material:** Commercial Grade B Lead Sheet (99.9% Pb).
* **Thickness:** **6.0 mm**.
* **Attenuation Capability:** 
  - The Tenth-Value Layer (TVL) of lead for 50 keV X-rays is just **0.06 mm**.
  - A 6.0 mm lead layer represents **100 Tenth-Value Layers**—reducing Bremsstrahlung escape to mathematically negligible levels (< 0.001%).

#### Layer 2 (Outer Fast-Neutron Absorber):
* **Material:** High-Density Polyethylene with 5% elemental Boron by weight (**5% B-HDPE** - commercial grade *ShieldWEAR* / *Borotron*).
* **Thickness:** **100.0 mm (10 cm)**.
* **Mechanism:**
  1. The high concentration of Hydrogen atoms in polyethylene acts like equal-mass billiard balls, rapidly thermalizing stray 2.5 MeV neutrons down to room temperature (< 0.025 eV).
  2. The 5% Boron-10 captures the thermalized neutrons via:
     ```
     n + ¹⁰B  ───>  ⁷Li  +  ⁴He  +  0.48 MeV (soft gamma)
     ```
  3. The soft 0.48 MeV gamma is safely absorbed within the outer bulk plastic, preventing secondary hard gamma emission.

---

### 4. Mechanical Enclosure Architecture

```
                  TOP VIEW: SPLIT-CLAMSHELL HOUSING
                  
                 ┌────────────────────────────────┐
                 │       LEFT CLAMSHELL HALF      │
                 │   [ 100mm HDPE + 6mm Lead ]    │
                 └──────┬──────────────────┬──────┘
                        │  Stepped Joint   │
                        │ (Prevents Line-  │
                        │  of-Sight Leak)  │
      High-Voltage      │                  │      Faraday Stator
      Stripline In ═════╪   [ 316LN Cross] ╪═════ Duct Out
                        │                  │
                        │  Stepped Joint   │
                 ┌──────┴──────────────────┴──────┐
                 │      RIGHT CLAMSHELL HALF      │
                 │   [ 100mm HDPE + 6mm Lead ]    │
                 └────────────────────────────────┘
                     ▲                        ▲
             Mounted on heavy-duty lockable casters
             (Rolls open in 10 seconds for maintenance)
```

* **Quick-Access Clamshell:** Built as two identical halves mounted on heavy-duty locking swivel casters. 
* **Zero Line-of-Sight Radiation Leaks:** The meeting seams use a **25 mm stepped overlap joint** (ship-lap profile). Radiation cannot travel in a straight line through the seam.
* **Service Penetrations:**
  - **HV Stripline Port:** Stepped lead-lined collar fitting snugly over the parallel-plate feed.
  - **Stator Duct Exit:** 100 mm thick B-HDPE doughnut ring surrounding the ceramic Faraday duct.
  - **Vacuum Pump Port:** Right-angle elbow lined with lead sheet to eliminate straight-path photon escape to the turbo pump.

---

### 5. Why This Design Eliminates Over-Engineering

1. **Standard Off-The-Shelf Materials:** Uses standard commercial 6 mm lead sheets and standard prefabricated 100 mm 5% Borated HDPE plates used in hospital radiotherapy rooms.
2. **Zero Maintenance:** Passive solid-state shielding. No pumps, no cooling fluid loops, no water jackets to freeze or leak.
3. **Ergonomic Maintenance:** Two people can unlock four over-center draw latches and roll the entire shield back in 15 seconds to access the vacuum chamber or replace electrode components.
