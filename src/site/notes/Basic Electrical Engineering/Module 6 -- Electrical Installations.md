---
{"dg-publish":true,"permalink":"/basic-electrical-engineering/module-6-electrical-installations/","tags":["Basic-Electrical-Engineering","Semester-1"],"created":"2026-03-11T13:03:46.194+05:30","updated":"2026-04-08T11:33:24.184+05:30"}
---


---
# The Big Picture First

Every electrical installation — a home, a factory, a college building — needs three things to work safely: **protection devices** (to stop things going wrong), **wiring** (to carry current safely), and **earthing** (to protect people). Then there's the energy management side — batteries for backup, and calculations for consumption and power factor.

That's the entire unit in one sentence. Let's unpack each part.

---
# LT Switchgear: Protection Devices

==**LT** stands for **Low Tension** — meaning low voltage systems== (up to $1000V$), ==which is everything in normal buildings==.

==**Switchgear** = the collection of protective devices that detect faults and disconnect the circuit before damage or injury occurs==.

---
## SFU — Switch Fuse Unit

==The simplest protection. A switch combined with a fuse. The fuse is a thin wire that **melts and breaks** the circuit when current exceeds a safe level. Once blown, it must be physically replaced==.

Think of it as a sacrificial element — it destroys itself to save the rest of the circuit.

---
## MCB — Miniature Circuit Breaker

An upgrade over the fuse. ==It does the same job== — breaks the circuit on over-current — ==but uses an **electromagnetic or bimetallic trip mechanism** instead of melting wire. Key advantage: it can be **reset** by just flipping it back — no replacement needed==.

Two trip mechanisms inside an MCB:

- **Thermal (bimetallic strip)** — ==for sustained overloads. Current heats a bimetallic strip which bends and trips the breaker==.
- **Magnetic (electromagnet)** — ==for sudden short circuits. Large current creates a strong magnetic field that instantly trips the breaker==.

This is what you see as individual breakers in your home's distribution board.

---
## ELCB — Earth Leakage Circuit Breaker

==MCBs protect against over-current. But what if current is leaking to earth through a _person_? That might not be enough current to trip an MCB, but it's enough to kil==l.

==The ELCB detects **current leaking to earth** and trips almost instantly — in milliseconds. It continuously compares current going out through live wire vs returning through neutral. If there's a difference (meaning current leaked elsewhere — possibly through a human), it trips==.

This is your primary protection against electric shock.

---
## MCCB — Moulded Case Circuit Breaker

==Essentially a heavy-duty MCB for industrial/commercial settings. Handles much higher current ratings and can be adjusted for different trip thresholds. Used at the main incoming supply level of large installations==.

---

### Quick Comparison

|Device|Protects Against|Reusable?|Where Used|
|---|---|---|---|
|SFU|Overcurrent|No (fuse replacement)|Simple installations|
|MCB|Overcurrent, short circuit|Yes (reset)|Home distribution boards|
|ELCB|Earth leakage (shock protection)|Yes (reset)|Anywhere humans touch equipment|
|MCCB|Overcurrent (high current)|Yes (reset)|Industrial/commercial mains|

---
# Wires vs Cables — The Distinction First

These terms are often used interchangeably in casual speech but mean different things technically:

**Wire** — a single conductor (solid or stranded). Just the conducting material, possibly with basic insulation.

**Cable** — one or more insulated wires bundled together with an outer protective sheath. A cable is a complete, protected assembly ready for installation.

---
## Types of Wires

**Solid wire** — one single conductor. Rigid, holds shape, used in fixed permanent wiring inside walls. Can't bend repeatedly without breaking.

**Stranded wire** — multiple thin wires twisted together. Flexible, handles vibration and repeated bending well. Used in appliance cords, motor connections, anywhere movement occurs.

**Material:** Almost universally **copper** (high conductivity, flexible) or **aluminium** (cheaper, lighter but lower conductivity — used in overhead transmission lines).

---
## Types of Cables

**Single core cable** — one insulated conductor. Used for simple point-to-point connections.

**Multicore cable** — multiple insulated conductors inside one outer sheath. Your standard home wiring cable has three cores: **Live (Red/Brown), Neutral (Black/Blue), Earth (Green-Yellow)**.

**Armoured cable** — has an additional steel wire armour layer between insulation and outer sheath. Protects against mechanical damage — used underground or in industrial settings where cables might be physically stressed.

**Coaxial cable** — a central conductor surrounded by insulation, then a braided shield, then outer jacket. Used for signal transmission (TV, internet) rather than power.

---
## How Cables are Rated

Two key ratings for any cable:

**Current rating** — maximum current it can carry continuously without overheating. Exceeding this degrades insulation and causes fire risk.

**Voltage rating** — maximum voltage the insulation can withstand. Exceeding this causes insulation breakdown.

Choosing a cable means matching both ratings to the application — undersized cable is a fire hazard.

---
## Earthing — Why It Exists

Here's the physical reasoning: in a healthy circuit, current flows from Live → through load → back through Neutral. The metal body of equipment (a washing machine, a motor casing) is not supposed to carry any current.

But if insulation fails inside the equipment, the live wire can touch the metal body — making the entire casing live at 230V. Anyone touching it becomes the path to ground. Fatal.

**Earthing** connects the metal body of equipment directly to the earth (literally the ground) through a low resistance path. Now if insulation fails and live touches the casing — the current rushes to earth through the earth wire (not through a person), the current is large, and it trips the MCB or blows the fuse immediately.

Earthing doesn't prevent the fault — it makes the fault **visible to protection devices** so they can act before anyone is harmed.

---
## Types of Earthing

**Plate earthing** — a copper or galvanised iron plate buried vertically in the ground, connected to the earth wire. Most common for buildings.

**Pipe earthing** — a galvanised iron pipe driven into the ground. Simpler, used in areas with moist soil.

**Rod earthing** — copper rods driven into the ground. Used in rocky terrain where deep burial isn't possible.

The soil moisture matters enormously — dry soil has high resistance and makes a poor earth. That's why earthing pits are often kept moist with water and salt.

---
## The Three Wires in Every Installation

|Wire|Colour (IS standard)|Role|
|---|---|---|
|Live|Red (old) / Brown (new)|Carries current to load|
|Neutral|Black (old) / Blue (new)|Returns current from load|
|Earth|Green-Yellow|Safety path to ground|

Neutral is at near-zero voltage and returns current normally. Earth carries no current during normal operation — it only activates during a fault. This distinction is exam-relevant.

---
# Batteries -- The Basics First

A battery converts chemical energy into electrical energy. For this syllabus, what matters is understanding the key characteristics and types — not the chemistry.

---
## Important Battery Characteristics

**EMF (Open Circuit Voltage)** — the voltage a battery produces when nothing is connected. No current flowing, no internal voltage drop.

**Terminal Voltage** — the actual voltage available at the terminals when current is being drawn. Always less than EMF because of internal resistance:

$$
V_{terminal} \ = \ EMF \ - \ I \ \cdot \ r
$$

where r is the internal resistance. This is exactly the practical voltage source model from Unit 1.

**Capacity** — measured in **Ampere-hours (Ah)**. Tells you how much total charge the battery can deliver. A 100Ah battery can deliver 10A for 10 hours, or 1A for 100 hours.

**Energy stored** — in Watt-hours (Wh):

$$
E \ = \ V \ \times \ Ah
$$

So a 12V, 100Ah battery stores 1200 Wh = 1.2 kWh of energy.

---
### Types of Batteries

**Primary (non-rechargeable)** — chemical reaction is irreversible. Use once, discard. Example: standard AA alkaline cells.

**Secondary (rechargeable)** — reaction is reversible. Can be recharged by pushing current back through. Examples:

|Type|Voltage/cell|Use|
|---|---|---|
|Lead-acid|2V/cell|Car batteries, UPS|
|Lithium-ion|3.6V/cell|Phones, laptops, EVs|
|Nickel-MH|1.2V/cell|Rechargeable AA batteries|

**Lead-acid** is the most exam-relevant for this syllabus — it's used in UPS systems and backup power, which directly connects to electrical installations.

---
## Series vs Parallel Battery Connections

**Series** — voltages add, capacity stays same:

$$
V_{total} \ = \ V_1 \ + \ V_2 \ + \ \cdots \ , \  Ah_{total} \ = \ Ah_{onecell}
$$


**Parallel** — voltage stays same, capacity adds:

$$
V_{total} \ = \ V_{onecell}, \ Ah_{total} \ = \ Ah_1 \ + \ Ah_2 \ + \ \cdots 
$$

Real battery banks (like in a UPS or solar installation) combine both to get the required voltage AND capacity simultaneously.

---
## Energy Consumption Calculations

This is the "electricity bill" part of the unit. The unit of electrical energy for billing is the **kilowatt-hour (kWh)**, commonly called a **unit** of electricity.

$$
E \ = \ P \ \times \ t
$$

where $P$ is power in kW and $t$ is time in hours.

**Example:** A 1500W air conditioner running for 8 hours:

$$
E \ = \ 1.5 kW \ \times \ 8h \ = \ 12 \ kWh \ = \ 12 \ \text{units}
$$

If electricity costs ₹6 per unit:

$$
\text{Cost} \ = \ 12 \ \times\ 6 \ = \ 72
$$

That's the entire calculation framework — straightforward multiplication.

---
## Power Factor Improvement

We covered power factor in Unit 2. Here's the practical problem it causes in installations:

A low power factor (say 0.6) means the supply current is much larger than what's actually doing useful work. Larger current means:

- Thicker, more expensive cables needed
- Higher $I^2 R$ losses in wiring
- Electricity board penalises industrial consumers with low PF

**Why does low PF occur?** Most industrial loads — motors, transformers, fluorescent lights — are inductive. Inductive loads cause current to lag voltage, pulling PF below 1.

**How to fix it:** Connect **capacitors in parallel** with the load. Capacitors draw leading current, which cancels the lagging current from inductors. The net effect is the current drawn from the supply reduces and PF improves toward unity.

$$
Q_C \ = \ P(\tan{\phi_1} \ - \ \tan{\phi_2})
$$

where $\phi_1$, is the original power factor angle, and $\phi_2$ is the desired power factor angle. This gives the reactive power the capacitor bank must supply.

**Key point:** You're not changing the load — the motor still does the same work. You're just stopping the reactive current from travelling all the way from the supply. It now circulates locally between the capacitor and the motor.

---
