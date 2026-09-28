# Project D.E.C.A. Subsystem Specification
## Decaborane (B₁₀H₁₄) Thermal Sublimation & Fuel Delivery Module

> **Component Code:** DECA-FDS-01  
> **Lead Theoretical Author:** Neeraj Bhupendra Patekar  
> **Design Philosophy:** Minimalist, zero-moving-parts thermal sublimation with hydrogen carrier sweep. (Zero over-engineering).

---

### 1. The Fuel Challenge

Decaborane (B₁₀H₁₄) is the ideal solid chemical carrier for proton–Boron-11 (p-¹¹B) aneutronic fusion:
* It naturally contains 10 Boron atoms and 14 Hydrogen atoms per molecule.
* At room temperature (25°C), it is a stable, non-pyrophoric white crystalline solid.
* **Physical constants:**
  - Melting point: 99.7°C
  - Boiling point: 213°C (at atmospheric pressure)
  - Sublimation temperature under reduced pressure: **115°C to 125°C**
  - Thermal decomposition threshold: Begins pyrolyzing into higher non-volatile boranes above **170°C**.

**The Engineering Constraint:** We must vaporize the powder cleanly and feed it into the supersonic nozzle without:
1. Jamming mechanical augers or powders in valves.
2. Overheating it past 170°C (which deposits sticky brown boron polymers and clogs lines).
3. Allowing the vapor to hit cold metal walls and re-crystallize (clogging the injection orifice).

---

### 2. The Solution: Heated Sublimation Ampoule + Carrier Sweep

Instead of complex pumps or screw feeders, the DECA-FDS-01 uses a **passive thermal sublimation reservoir** swept by pure Hydrogen (H₂) gas:

```
                      DECA-FDS-01 FUEL SCHEMATIC
                      
  Pure H2 Gas In
  (1.5 bar)
      │
      ▼
 ┌─────────┐
 │ Needle  │
 │  Valve  │
 └────┬────┘
      │
      ▼
┌───────────────────────────────────────────────┐
│  HEATED SUBLIMATION CELL (316L Stainless)     │
│  Temperature: 120°C (Controlled by band heater)│
│                                               │
│   H2 Gas Sweeps Over Surface                  │
│   ════════════════════════════════════════>   │
│                                               │
│    [ B10H14 Solid Crystals / Pellets ]        │
└───────────────────────┬───────────────────────┘
                        │ Saturated B10H14 + H2 Vapor
                        ▼
           ┌────────────────────────┐
           │ Trace-Heated Feed Line │  (Maintained at 135°C
           │ (1/4" Swagelok 316L)   │   to prevent re-solidifying)
           └────────────┬───────────┘
                        │
                        ▼
           ┌────────────────────────┐
           │ Piezo Fast Pulse Valve │  (Mounted directly on
           │ (Piezomechanik PST-150)│   anode breech)
           └────────────┬───────────┘
                        │ Supersonic Gas Puff
                        ▼
             [ Reactor Anode Breech ]
```

---

### 3. Hardware Architecture & Components

| Subsystem Component | Specification / Commercial Standard | Operational Function |
| :--- | :--- | :--- |
| **Sublimation Ampoule** | 100 ml 316L Stainless Steel mini-cylinder with CF 40 top flange | Holds 50 grams of solid B₁₀H₁₄ crystals. Easy to unbolt and reload inside a fume hood. |
| **Thermal Jacket** | 150 W external mica band heater with K-type thermocouple | Heats the cell to exactly **120°C ± 2°C** via an inexpensive PID temperature controller. |
| **Carrier Sweep Line** | 1/8" stainless line regulated at 1.2 to 1.5 bar H₂ | Bubbles or sweeps across the crystals. Saturated vapor pressure of B₁₀H₁₄ at 120°C provides optimal 1:1.4 Boron-to-Hydrogen stoichiometric fuel ratio. |
| **Transfer Line** | 30 cm length of 1/4" 316L seamless tube with silicone heat wrap | Electrically trace-heated to **135°C** (15°C above the cell) to ensure zero condensation on tube walls. |
| **Fast Injection Valve** | Piezoelectric poppet valve (response time: < 50 microseconds) | Fires a 200-microsecond gas burst into the hollow anode breech synchronized with the 50 Hz capacitor discharge. |

---

### 4. Operational Sequence (Firing Cycle)

1. **Pre-Heat (T - 10 minutes):**
   - The PID controller brings the sublimation cell to 120°C and the transfer line to 135°C.
   - Decaborane crystals sublimate into dense vapor filling the headspace.
2. **Carrier Pressurization:**
   - Ultra-high purity Hydrogen (H₂) is admitted at 1.5 bar, mixing with the Decaborane vapor.
3. **Pulsed Injection (At 50 Hz):**
   - The piezo valve pulses open for 200 microseconds.
   - Saturated fuel gas expands through the converging-diverging nozzle into the electrode breech at Mach 2.4.
4. **Shutdown & Purge:**
   - The heater is de-energized.
   - A pure H₂ purge flushes any remaining vapor from the lines into the vacuum exhaust, leaving the lines clean.

---

### 5. Why This Design Eliminates Over-Engineering

* **Zero mechanical moving parts in the hot zone:** No pistons, no gears, no screw augers.
* **Self-regulating stoichiometry:** Operating at 120°C keeps vapor pressure stable without risking polymer decomposition (which only occurs at >170°C).
* **Standard off-the-shelf parts:** Entirely constructed from standard Swagelok fittings, a mini CF-40 sampling cylinder, and commercial silicone heating tape.

---

### 6. The Three Foolproof Workshop Safeguards (Lab Traps Neutralized)

1. **The "Shiny Grey Only" Material Rule (No Copper / Brass):**
   - *Trap:* Hot Decaborane (B₁₀H₁₄) vapor reacts aggressively with Copper (Cu), Brass, or Silver, catalytically forming shock-sensitive, explosive metal-borane complexes and sticky polymer clogs.
   - *Fix:* Enforce the strict workshop rule: **Zero copper or yellow brass anywhere in the fuel path.** Standardize 100% on **Swagelok 316L Stainless Steel**, PTFE (Teflon) ferrules, and Kalrez seals.

2. **The Valve Dual-Wrap & PTFE Thermal Break (No Flash-Freezing):**
   - *Trap:* The massive room-temperature vacuum chamber acts as a heat sink, cooling the piezo valve body down to ~50°C. Saturated B₁₀H₁₄ vapor instantly flash-freezes into solid crystals on the cold valve seat, gluing the poppet shut.
   - *Fix:* Extend the flexible silicone heating tape from the tube by 2 extra wraps directly around the piezo valve body (maintaining it at 135°C), and insert a **2 mm thick PTFE/Macor thermal standoff washer** between the valve and the chamber flange.

3. **Inline 4A Molecular Sieve Trap (No Boric Glass Crusts):**
   - *Trap:* Trace moisture (humidity) in commercial Hydrogen reacts at 120°C to form Boric Acid (H₃BO₃) and Boron Trioxide (B₂O₃), coating the Mach 2.4 nozzle with a sticky, glassy crust.
   - *Fix:* Install an inexpensive inline 6-inch stainless cylinder packed with **4A Molecular Sieve beads** on the H₂ supply line to scrub water vapor down to < 1 ppm before it enters the sublimation cell.
