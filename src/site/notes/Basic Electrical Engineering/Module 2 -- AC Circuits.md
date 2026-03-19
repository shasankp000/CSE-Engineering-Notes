---
{"dg-publish":true,"permalink":"/basic-electrical-engineering/module-2-ac-circuits/","tags":["Basic-Electrical-Engineering","Semester-1"],"created":"2026-02-14T13:57:23.558+05:30","updated":"2026-03-19T06:18:53.323+05:30"}
---

---
# Index

1. [[#Representation of Sinusoidal Waveforms]]
2. [[#Phase Difference]]
3. [[#Peak and RMS values]]
4. [[#Phasor Representation]]
5. [[#Complex Number forms]]
6. [[#AC Circuit analysis using Phasors]]
7. [[#Impedances]]
8. [[#Three types of power in AC circuits]]
9. [[#1. Real Power (Active Power)]]
10. [[#2 Reactive Power]]
11. [[#3. Apparent Power]]
12. [[#Analysis of Single Phase AC Circuits]]
13. [[#Resonance in single phase AC circuits]]
14. [[#Three Phase AC Circuits]]
15. [[#The Connection Methods]]
16. [[#Power in Three-Phase Systems]]

---
# Representation of Sinusoidal Waveforms

## Sinusoids

https://www.youtube.com/watch?v=YhpOZcjrvQM

What exactly are these sinusoids?

![Pasted image 20251108000701.png](/img/user/media/Pasted%20image%2020251108000701.png)

==**Sinusoids** are signals that look like sine or cosine functions==.

A sinusoid is represented by an equation like:

$$
V(t) \ = \ V_m \ \sin(\omega \ \times \ t)
$$

And a sinusoidal (AC) voltage or current varies with time according to:

$$
V(t) \ = \ V_m \ \sin{(\omega \ t \ + \ \phi)}
$$

where:

- $V(t)$ is the instantaneous voltage at time $t$ seconds.
  
- $V_m$ is the amplitude or maximum value of the voltage. (The maximum arc, a crest or trough can stretch to in the signal).

![Pasted image 20250916122232.png](/img/user/media/Pasted%20image%2020250916122232.png)

- $\omega$ is ==the angular frequency in radians per second==. The angular frequency of a wave is ==a measure of how quickly a wave's phase changes over time, representing the angular displacement per unit of time==. 
  
  ==The phase of a wave is basically any point in the wave within a single cycle==.
  
  ==The phase difference would mean the difference between any two chosen points on the wave in a single cycle==.
  
  ![Pasted image 20251108001706.png](/img/user/media/Pasted%20image%2020251108001706.png)


- $t$ is the time.

- $f$ is the frequency in Hertz (Hz)

- $T$ is the time period which is $\frac{1}{f}$ seconds.

- $\phi$ is the phase angle (in radians or degrees)

---
### Periodicity

- ==Sinusoids are **periodic signals**, meaning their waveform repeats itself==.

- ==The **fundamental time period (T)** is the minimum time after which the signal repeats==.

Assuming you already did DC circuits before getting here, ==think of AC as voltage/current that changes magnitude and direction periodically==.

---
### Essential Relationships

Time Period & Frequency:

$$
\omega \ = \ 2\pi f \ = \ \frac{2\pi}{T}
$$


For example: If $f \ = \ 50 \ \text{Hz}$ then:

- $T \ = \ \frac{1}{50} \ = \ 0.02 \ \text{s} \ = \ 20 \ \text{ms}$

- $\omega \ = \ 2\pi \ \times \ 50 \ = \ 314.16 \ \text{rad/s}$.

---
### Phase Difference

When comparing two sinusoids of the same frequency:

- $v_1(t) \ = \ V_{m_1} \ \sin{(\omega t)}$
- $v_2(t) \ = \ V_{m_2} \ \sin{(\omega \ t \ + \ \phi)}$

The second waveform leads by $\phi$ if $\phi \ > \ 0$ or lags if $\phi \ < \ 0$.

---
### Quick Practice

A voltage $v(t) \ = \ 325 \sin{(314t \ + \ 30^{\circ})} \ V$.

Find:

- The Peak value
- Frequency
- Time Period.

Using the formula: $V(t) \ = \ V_m \ \sin{(\omega \ t \ + \ \phi)}$, 

The $V_m \ = \ 325$, $\omega \ = \ 314$ and $\phi \ = \ 30^{\circ}$


- The peak value (we will learn more about it in the next section), $V_m \ = \ 325$

- The Frequency is given by: 
  
  $\omega \ = \ \frac{2\pi}{f} \ \implies \ f \ = \ \frac{\omega}{2\pi} \ = \ \frac{314}{2\pi} \ = \ 50 \ \text{Hz}$ 

- The Time period is given by:
  
  $T \ = \ \frac{1}{f} \ = \ \frac{1}{50} \ = \ 0.02 \ \text{s} \ = \ 20 \ \text{ms}$.

---
# Peak and RMS values

## Peak Value

The **peak value** ($V_m$ or $I_m$) is the maximum value reached by an AC quantity (==maximum value the amplitude can reach==) ==in one cycle==.

For the sinusoid $v(t) \ = \ V_m \ \sin(\omega \ t)$, the peak value is simply $V_m$.

---
### Visual Understanding

If you imagine a sine wave oscillating up and down:

- It starts at zero
- Rises to it's **peak value** at $90^{\circ}$ (==positive maximum or positive peak==)
- Returns to zero at $180^{\circ}$.
- Drops to it's **negative peak** at $270^{\circ}$ (==which has the same magnitude as the positive peak==)
- Returns to zero at $360^{\circ}$, cycle complete.


**Peak-to-Peak Value**: The total swing from negative to positive peak is $2 V_m$.

---
## RMS Value

The RMS value of alternating current is defined as: ==**the steady DC current which, when passed through a given resistance for a given time, produces the same amount of heat as produced by the alternating current through the same resistance for the same time**==.

### Think of it this way

Imagine two scenarios with the same resistor:

1. **AC Scenario**: An AC current $i(t) \ = \ 10\sin(\omega \ t) \ \text{A}$ flows through a resistor for 1 minute.

2. **DC Scenario**: A steady DC current of $7.07 \ \text{A}$ flows through the same resistor for 1 minute.

==Both produces **exactly the same amount of heat!** That 7.07 A DC value **is the RMS value of the AC current**==.

### Why This Matters

- ==The RMS value is also called the **"effective value"** because it represents the effective heating capability of AC​==
    
- All electrical instruments (ammeters, voltmeters) measure RMS values
  
- When you see "230V AC" on your appliances, that's the RMS voltage, not peak.

- Power calculations in AC circuits use RMS values: $P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos\phi$.

**Quick Example**

If an AC produces the same heat as a steady DC of 4A, then the **RMS value** of that AC is 4A (not the resistance). The peak value would then be: $I_m \ = \ 1.414 \ \times \ 4 \ = \ 5.656 \ \text{A}$

---
### RMS Formulae

For a sinusoidal waveform:

- $V_{rms} \ = \ \frac{V_m}{\sqrt{2}} \ = \ 0.707 \ \times \ V_m$
- $I_{rms} \ = \ \frac{I_m}{\sqrt{2}} \ = \ 0.707 \ \times \ I_m$

The inverse relationship will be:

$V_m \ = \ \sqrt{2} \ \times \ V_{rms} \ = \ 1.414 \ \times \ V_{rms}$

$I_m \ = \ \sqrt{2} \ \times \ I_{rms} \ = \ 1.414 \ \times \ I_{rms}$

---
## Some examples to understand Peak and RMS values

**Problem 1**: A sinusoidal voltage has a peak value of 340V. Find the RMS value.

**Solution**:

$$
V_{rms} \ = \ 0.707 \ \times \ 340 \ = \ 240.38 \ V
$$

---

**Problem 2**: The domestic AC supply is 230V, 50Hz. Find: (a) Peak voltage, (b) Equation of voltage.

**Solution**:

Here, the 230 V is not voltage, but the RMS voltage.

So, we need to find the amplitude of the sinusoidal equation of this supply, which will be the peak voltage.

(a) Peak voltage: $V_{m} \ = \ 1.414 \ \times \ 230 \ = \ 325.22 \ V$.
(b) Now we need to find the angular frequency of the wave, which is given by:

$\omega \ = \ 2\pi \ \times \ 50 \ = \ 314.16 \ \text{rad/s}$

Now the equation of voltage is given by:

$V(t) \ = \ V_m \ \sin(\omega \ t \ + \ \phi) \ V$

since we don't have $\phi$ here, we are just going to write:

$V(t) \ = \ V_m \ \sin(\omega \ t) \ V$

or: $V(t) \ = \ 352.22 \ \sin(314.16 \ t) \ V$

---
**Problem 3**: An AC current is given by $i(t) \ = \ 10 \sin(314 \ t) \ A$. Find the RMS current (it's DC equivalent for the heating effect in a resistor).


From the given sinusoidal equation:

$$
i(t) \ = \ 10 \sin(314 \ t) \ \text{A}
$$


We have:

The peak current value (amplitude) as: $I_m \ = \ 10 \ \text{A}$.
The angular frequency, $\omega \ = \ 314 \ \text{rad/s}$.

So, the RMS current value would be:

$$
I_{rms} \ = \ 0.707 \ \times \ 10 \ = \ 7.07 \ \text{A}
$$

---
# Phasor Representation

https://www.youtube.com/watch?v=qyKEw9X-yHQ

A phasor is a **complex number** that represents two key pieces of information about a sinusoid: its **amplitude** and its **phase angle**. 

## Conversion: Time Domain to Phasor Domain

For a sinusoid that's in the time domain: $v(t) \ = \ V_m \ \sin(\omega \ t \ + \ \phi)$ 

The equivalent phasor form(using RMS) would be:

$$
\bar{V} \ = \ V_{rms} \ \angle{\phi}
$$

where $V_{rms} \ = \ \frac{V_m}{\sqrt{2}} \ = \ 0.707 \ \times \ V_m$

Say, if we have a sinusoidal wave equation:

$$
v(t) \ = \ 3\cos(\omega \ + \ 30^{\circ})
$$

where the amplitude is 3 and the phase angle is 30 degrees

It can be represented with a phasor as:

$$
\bar{v} \ = \ 3 \ \angle{30^{\circ}}
$$

For it's phasor representation using RMS:

$$
\bar{V} \ = \ 2.121 \ \angle{30^{\circ}}
$$



==**Time Independence**==: A crucial aspect of phasors is that they are **time-independent**. ==The time involved components are suppressed when a sinusoid is converted to a phasor and that simplifies analysis==.

---
## Complex Number forms

Phasors are expressed as complex numbers, most commonly in:

### 1. Polar Form

The standard form that we just explored:

$$
\bar{V} \ = \ V_m \ \angle{\phi}
$$

or with RMS:

$$
\bar{V} \ = \ V_{rms} \ \angle{\phi}
$$

### 2. Rectangular (Complex) Form

$$
\bar{V} \ = \ V_x \ + \ jV_y
$$

where:

- $V_x \ = \ V_m \ \cos{\phi}$ (Real part)
- $V_y \ = \ V_m \sin{\phi}$ (imaginary part)
- $j \ = \ \sqrt{-1}$

Example: $100 \angle{30^{\circ}} \ = \ 86.6 \ + \ j50 \ \text{V}$

### Conversion between forms

#### Polar to Rectangular:

$$
V_m \ \angle{\phi} \ = \ V_m \ \cos{\phi} \ + \ j \ V_m \ \sin{\phi}
$$

#### Rectangular to Polar:

$$
V_x \ + \ jV_y \ = \ \sqrt{V_x^2 \ + \ V_y^2} \ \angle{\tan^-1{(\frac{V_y}{V_x})}}
$$

---
### Quick Example

Problem: Convert $v(t) \ = \ 220 \sqrt{2} \ \sin(314 \ t \ + \ 60^{\circ})$ V to phasor form (RMS)

For phasor form:

$$
\bar{V} \ = \ \frac{220\sqrt{2}}{\sqrt{2}} \ \angle{60^{\circ}}
$$

Thus the phasor is: $\bar{V} \ = \ 200 \ \angle{60^{\circ}} \ \text{V}$ in polar form.

where:

- $V_{rms} \ = \ 220$
- $\phi \ = \ 60$

For the rectangular form:

$V_x \ = \ 220 \cos{60^{\circ}} \ = \ 110 \ \text{V}$
$V_y \ = \ 220 \ \sin{60^{\circ}} \ = \ 190.52 \ \text{V}$

$\bar{V} \ = \ 110 \ + \ j190.52 \ \text{V}$, is the phasor in the rectangular form.

---
## AC Circuit analysis using Phasors

https://www.youtube.com/watch?v=YrtZgA05MBI

### Example 1

![Pasted image 20251108194352.png](/img/user/media/Pasted%20image%2020251108194352.png)

#### Impedances

Quick pause before we proceed with the solving.

Impedance ($Z$) ==is the total opposition to alternating current (AC) flow in a circuit, measured in ohms. It is the AC equivalent of the resistance in a DC circuits==, combining both resistance ($R$) from resistors and reactance ($X$) from inductors and capacitors.

Now that we are done, let's get back to the problem.

We have been given:

- A source in phasor form: $V \ = \ 10 \ \angle{30^{\circ}}$.

- Two resistors in series, both $1 \ohm$ each.

- Current arrow $I$ flows clockwise (through the top $1\ohm$ resistor then down the right $1\ohm$).


So, firstly what we will do is combine the impedances(resistances) which are in series.

Total impedance $Z \ = \ 2 \ohm$.

Using ohm's law we can find out the total current in the circuit:

$$
I \ = \ \frac{V_{rms}}{R} \ = \ \frac{10 \ \angle{30^{\circ}}}{2} \ \text{A}
$$

$$
I \ = \ 5 \ \angle{30^{\circ}} \ \text{A}
$$

Optionally we can convert to the rectangular form as well (for better practice):

$\cos{30} \ = \ 0.866$ , $\sin{30} \ = \ 0.5$

$$
I_{rect} \ = \ (5 \ \times \ 0.866) \ + \ (5 \ \times \ j \ 0.5) \ \approx \ 4.33 \ + \ j \ 0.25  \ \text{A} 
$$

We can further verify our own answer.

For each resistor, there will be a voltage drop.

Voltage drop for each $1\ohm$ resistor would be:

$V_{drop} \ = \ 5 \ \angle{30^{\circ}} \ \times \ 1 \ = \ 5 \ \angle{30^{\circ}} \ \text{V}$.

A KVL check would result in: $V_{source} \ = \ V_{R1} \ + \ V_{R2} \ = 10 \ \angle{30^{\circ}}$ which matches the source voltage.

Final answer: Convert back to sinusoid (time domain)

Here be careful about your phasor convention:

- If the voltage (or current) is given in the phasors form, which are given in polar forms, the numeric part are the **RMS values**, by default convention.

- If the voltage (or current) is given in sinusoidal form, you would get the phasor in peak voltage form, not RMS, thus converting it back to the resulting sinusoidal would just directly fit in the sinusoid equations.

In our case, we have RMS values.

So,

$$
I \ = \ 5 \ \angle{30^{\circ}} \ \text{A}
$$


will be converted to it's peak value equivalent in the sinusoid for the instantaneous current.

So the instantaneous current is:

$$
i(t) \ = \ (\sqrt{2} \ \times \ 5) \ (\sin{\omega} \ t \ + \ 30^{\circ}) \ \text{A}
$$

or:

$$
i(t) \ = \ 7.07 \ (\sin{\omega} \ t \ + \ 30^{\circ}) \ \text{A}
$$

(Textbooks commonly use RMS phasors; confirm from your course which convention they use. ==If nothing is said, RMS is safest==.)

And that's exactly what it is in the video:

![Pasted image 20251108202339.png](/img/user/media/Pasted%20image%2020251108202339.png)

---
### Example 2

![Pasted image 20251108203912.png](/img/user/media/Pasted%20image%2020251108203912.png)

Given here is a sinusoidal voltage.

$$V \ = \ 6 \sin(\omega \ t \ + \ 10^{\circ}) \ \text{V}$$

The resistances are the same and the current is the same as the previous problem.

So the total impedance ($Z$) is $2\ohm$

Converting the voltage to a phasor form:

$$
\bar{V} \ = \ 6 \ \angle{10} \ \text{V}
$$

The current would be:

$$I \ = \ \frac{6\angle{10}}{2} \ = \ 3\angle{10}$$

Converting back to sinusoidal form:

$$
i(t) \ = \ 3 \ \sin(\omega t \ + \ 10 ) \ \text{A}
$$

https://www.youtube.com/watch?v=47hGRVA3K98 

This video contains even more examples related to phasors


---
## Key Advantage of using phasors

**Addition/subtraction of AC quantities**: Instead of adding complex sine functions, just add phasors as vectors!

Example:

$v_1(t) \ + \ v_2 \ = \ 10 \ \sin{\omega \ t} \ + \ 15 \ \sin{\omega \ t \ + \ 30^{\circ}}$

Using phasors:

$\bar{V}_{total} \ = \ 10 \ \angle{0^{\circ}} \ + \ 15 \ \angle{30^{\circ}}$, as simple as that.

---
# Power in AC Circuits

In DC circuits, power was simple: $P \ = \ VI$. ==In AC circuits, it's more complex because voltage and current may not be in phase==.

Now hold on a minute.

## What does it mean to be "in phase" and "not in phase"?

For that, let's just wind back to our definition of phase in a wave:

 ==The phase of a wave is basically any point in the wave within a single cycle==.
  
  ==The phase difference would mean the difference between any two chosen points on the wave in a single cycle==.
  
  ![Pasted image 20251108001706.png](/img/user/media/Pasted%20image%2020251108001706.png)

For a general sinusoidal signal:

$$
x(t) \ = \ X_m \ \sin(\omega \ t \ + \ \phi)
$$

- $\omega \ t$ : tells you where you are in time within a cycle (A cycle starts when $\phi \ = \ 0^{\circ}$ and ends when $\phi \ = \ 360^{\circ}$).

- $\phi$ : tells how much the wave is shifted horizontally (left or right) compared to a reference.


So, if two waves have different $\phi$, one wave starts earlier (leads) and the other starts later (lags behind)

---
### What "in phase" means:

==If two sinusoids of the **same frequency** rise, peak, cross zero, and fall **at the same time**, they are **in phase**==.

Mathematically:

$v(t) \ = \ V_m \ \sin(\omega \ t)$
$i(t) \ = \ I_m \ \sin(\omega \ t)$

Here $\phi \ = \ 0^{\circ}$ (or multiples of 360).
Their peak lines up perfectly.

An example would be:

Imagine two sinusoids on top of each other:

```python
v(t):    ~~~~~~~~^^^^~~~~~~~^^^^~~~~
i(t):    ~~~~~~~~^^^^~~~~~~~^^^^~~~~
```

- Both cross zero and reach peaks simultaneously.
- $\phi \ = \ 0^{\circ}$
- This happens in **pure resistive** circuits — no energy stored, all power converted to heat.

That's what being "in phase" means.

---
### What being "out of phase" or "not in phase means"

Now imagine:

$v(t) \ = \ V_m \ \sin(\omega \ t)$
$i(t) \ = \ I_m \ \sin(\omega \ t \ - \ \phi)$

If $\phi \ \neq\ 0$, their peaks no longer line up.

This is called a **phase difference** (or **phase shift**).

- $i$ lags behind $v$ if $\phi \ > \ 0$ (current occurs later). This happens in **inductive** circuits.

- $i$ leads $v$ if $\phi \ < \ 0$ (current occurs earlier). This happens in **capacitive** circuits.

Example:

```python
v(t):    ~~~~~~~~^^^^~~~~~~~^^^^~~~~
i(t):      ~~~~~~~~^^^^~~~~~~~^^^^~~
```

- Current wave is shifted to the right(lags).
- Same frequency, different timing.

---
### The phase angle $\phi$ and what it really represents.

Think of $\phi$ as ==the **angular time delay** between voltage and current within one cycle==.

- One full cycle is $360^{\circ}$ or $2\pi$ radians
- So a $90^{\circ}$ phase difference means the second wave reaches its peak $\frac{1}{4}$ of a cycle later.

In AC analysis:

$$
\phi \ = \ \text{angle between voltage phasor and current phasor}
$$

- For a resistor: $\phi \ = \ 90^{\circ}$
- For an inductor: $\phi \ = \ +90^{\circ}$ (current lags)
- For a capacitor: $\phi \ = \ -90^{\circ}$ (current leads)
- For any R-L-C combo: $\phi$ lies between $-90^{\circ}$ and $+90^{\circ}$


Imagine **voltage** as “effort” and **current** as “resulting motion.”  
If both are synchronized (in phase), all your effort goes into useful motion (real work).  
If not, part of your effort goes into _pushing and pulling energy back and forth_ — that’s reactive power.

>For people who have learnt machine learning, specifically cosine similarity and how vector embeddings work here's a neat connection build up the full intuition:
>
>Like in vectors, specifically while performing cosine similarity we can tell how similar a vector is to another based on their angle, with the most similar for the angle being 1 .
>
In cases of sinusoids and their phase angles, the sinusoids are literally similar to each other since they overlap on each other due to their phase angle, i.e. angular time delay between them being zero. They start together and end together. 
>
That's what it means to be in phase.
>
Now, dissimilar vectors have an angle of zero. 
>
Similarly when two sinusoids' phase angle is not equals to zero, then they are not that similar to each other, in wave terms, one started earlier and the other lagged behind it by a certain time delay, which is the phase angle. 
>
That's what it means to be out of phase.

---
## Three types of power in AC circuits

### 1. Real Power (Active Power)

**Definition**: ==The **actual power consumed** by the circuit that does useful work (produces heat, light, motion)==.

Symbol: $P$
Unit: Watts $W$.

Formula: $P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos{\phi}$

where $\phi$ is the phase angle between voltage and current.


**Key Point**: Only the component of current **in phase** with voltage contributes to real power. Real power is consumed by resistive elements (R)

---
### 2 Reactive Power

**Definition**: ==Power that **oscillates back and forth** between the source and reactive elements (inductors and capacitors) without doing any useful work==.

**Symbol**: $Q$
**Unit**: VAR (Volt-Ampere Reactive)

Formula:

$$
Q \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \sin{\phi}
$$


**Key Point**: The component of current **90° out of phase** with voltage contributes to reactive power.

---
### 3. Apparent Power

**Definition**: ==The **total power** supplied by the source, combining both real and reactive power==.

Symbol: $S$
Unit: $VA$ (Volt-Ampere)

Formula:

$S \ = \ V_{rms} \ \times \ I_{rms}$

**Relationship with P and Q**:

$S \ = \ \sqrt{P^2 \ + \ Q^2}$

or in complex form:

$S \ = \ P \ + \ jQ$

Apparent power is used to rate electrical equipment like transformers and generators.

---
### Power Triangle 

The relationship between these three powers forms a **right-angled triangle**:​

![Pasted image 20251109131732.png](/img/user/media/Pasted%20image%2020251109131732.png)


- **Horizontal side** (adjacent): Real Power (P)
- **Vertical side** (opposite): Reactive Power (Q)
- **Hypotenuse**: Apparent Power (S)

From the triangle:

- $P \ = \ S \cos{\phi}$ ($\cos{\phi} \ = \ \frac{\text{Base}}{\text{Hypotenuse}}$)
- $Q \ = \ S \sin \phi$ ($\sin{\phi} \ = \ \frac{\text{Vertical Side}}{\text{Hypotenuse}}$)
- $S \ = \ \sqrt{P^2 \ + \ Q^2}$ (Pythagoras's Theorem)
- $\tan{\phi} \ = \ \frac{Q}{P}$ $\tan{\phi} \ = \ \frac{\text{Vertical Side}}{\text{Base}}$

---
### Power Factor

Definition: The ratio of real power to apparent power

$$
\text{Power Factor} \ = \ \cos{\phi} \ = \ \frac{P}{S} \ = \ \frac{\text{Real Power}}{\text{Apparent Power}}
$$

Range: 0 to 1 (or 0% to 100%)

**Significance**:

- **Power factor = 1** (unity): Purely resistive circuit, all power is real power
    
- **Power factor = 0**: Purely reactive circuit, no real power consumed
    
- **Leading power factor**: Capacitive load (current leads voltage)
    
- **Lagging power factor**: Inductive load (current lags voltage)
  
---
## Essential Formulae Summary


| Power Type     | Symbol       | Unit                       | Formula                                     |
| -------------- | ------------ | -------------------------- | ------------------------------------------- |
| Real Power     | $P$          | W (Watts)                  | $V_{rms}I_{rms}\cos{\phi}$ or $S\cos{\phi}$ |
| Reactive Power | $Q$          | VAR (Volt-Ampere Reactive) | $V_{rms}I_{rms}\sin{\phi}$ or $S\sin{\phi}$ |
| Apparent Power | $S$          | VA (Volt-Ampere)           | $V_{rms}I_{rms}$ or $\sqrt{P^2 \ + \ Q^2}$  |
| Power Factor   | $\cos{\phi}$ | -                          | $\frac{P}{S}$                               |

And $\tan{\phi} \ = \ \frac{Q}{P}$ or $\phi \ = \ \tan^{-1}{\frac{Q}{P}}$

---
## Why $\phi$, the phase angle matters when it comes to the the different types of power

When we learned power:

$$
P \ = \ VI \cos{\phi}
$$

and

$$
Q \ = \ VI \ \sin{\phi}
$$


This $\phi$ **is the same phase angle between voltage and current phasors**.

| Case                     | $\phi$                                       | Effect                              | Behaviour         |
| ------------------------ | -------------------------------------------- | ----------------------------------- | ----------------- |
| $\phi \ = \ 0^{\circ}$   | In phase                                     | All power converted to heat/work    | Purely resistive  |
| $\phi \ = \ +90^{\circ}$ | Voltage leads by $90^{\circ}$ (Current lags) | No real power transfer (Q positive) | Purely inductive  |
| $\phi \ = \ -90^{\circ}$ | Current leads by $90^{\circ}$ (Voltage lags) | No real power transfer (Q negative) | Purely capacitive |
| $0^{\circ} \ <$          | $\phi$                                       | $< 90^{\circ}$                      | Partial alignment |

So, $\phi$ literally tells you _how effectively_ voltage and current work together to deliver real power.

---
# Analysis of Single Phase AC Circuits

## Pre-requisites

### 1. Inductors

![Pasted image 20251109182149.png](/img/user/media/Pasted%20image%2020251109182149.png)


An inductor is ==a passive electrical component that stores energy in a magnetic field when an electric current flows through it==. It is typically made of a coil of insulated wire and opposes any change in the current passing through it, a property known as inductance.


#### Time-Domain Relationships

$$
v_l (t) \ = \ L \frac{di(t)}{dt}
$$

- Voltage **leads** current (because voltage depends on the _rate of change_ of current).

- Constant current: $\frac{di}{dt} \ = \ 0 \ \implies \ v_l \ = \ 0$

- Sudden current change: large voltage spike

### For Sinusoidal signals

Let $v(t) \ = \ V_m{\sin(\omega t)}$

Therefore, the current will be:

$$
i(t) \ = \ \frac{1}{\omega \ L} V_m \sin(\omega t \ - \ 90^{\circ})
$$

current lags voltage by $90^{\circ}$

---
### 2. Capacitors

A capacitor is ==an electronic component that stores electrical energy in an electric field, made of two parallel conducting plates separated by an insulating material called a dielectric==. When a voltage is applied, it accumulates opposite charges on the plates, and it can release this energy quickly, unlike a battery which releases energy slowly.

![Pasted image 20251109185731.png](/img/user/media/Pasted%20image%2020251109185731.png)

The equation of a capacitor is:

$$
i_C(t) \ = \ C \ \frac{dv(t)}{dt}
$$


- Current **leads** voltage (because current depends on the _rate of change_ of voltage).

- Constant voltage: $\frac{dv}{dt} \ = \ 0 \ \implies \ i_C \ = \ 0$

- Sudden voltage change: large current spike

For sinusoidal signals:

$$
i(t) \ = \ \omega C V_m \ \sin(\omega t \ + \ 90^{\circ})
$$


current leads voltage by $90^{\circ}$

---
### Impedance and Reactance

#### Impedance

- Resistor: $Z_R \ = \ R$
- Inductor: $Z_L \ = \ j \omega \ L$
- Capacitor: $Z_C \ = \ -j \ \frac{1}{\omega \ C}$

S.I unit: ohms

#### Reactance

Reactance is the _magnitude_ of impedance (ignoring the sign/phase):

##### Inductance

$$
X_L \ = \ \omega L
$$

Inductance increases with the frequency, since they block high-frequency signals.

S.I unit: ohms

##### Capacitance

$$
X_C \ = \ \frac{1}{\omega C}
$$


The capacitance of a capacitor decreases with the frequency, since they allow high frequency signals.

---
## Example 1 - Pure Resistor circuit


![Pasted image 20251109192818.png](/img/user/media/Pasted%20image%2020251109192818.png)

We need to calculate all three types of power and the power factor here as well.

Starting off with the given voltage. When nothing is said about the amplitude type, it's safe to assume that it's RMS.

Given voltage:

$$
V_{rms} \ = \ 120 \ \angle{0^{\circ}}
$$

Total impedance ($Z$): $15 \ \ohm$
The phase angle $\phi$ is $0^{\circ}$

By ohm's law the current will be:

$$
I_{rms} \ = \ \frac{120 \ \angle{0^{\circ}}}{15}
$$

$$
I_{rms} \ = \ 8 \ \angle{0^{\circ}}
$$ 
### Quick note — about _multiplying phasors_

- When you multiply two phasors: $A\angle{\alpha} \times B\angle{\beta} \ = \ (\text{AB})\angle{(\alpha \ + \ \beta)}$

**However while calculating power**:

We use the _complex conjugate_ of the current: $S \ = \ VI^*$
because instantaneous power depends on $v(t)i(t)$ and in phasor math, that conjugate ensures we capture the real (average) part correctly.

In short, while calculating power, **subtract the angles**.


Remembering our formula table for power:

| Power Type     | Symbol       | Unit                       | Formula                                     |
| -------------- | ------------ | -------------------------- | ------------------------------------------- |
| Real Power     | $P$          | W (Watts)                  | $V_{rms}I_{rms}\cos{\phi}$ or $S\cos{\phi}$ |
| Reactive Power | $Q$          | VAR (Volt-Ampere Reactive) | $V_{rms}I_{rms}\sin{\phi}$ or $S\sin{\phi}$ |
| Apparent Power | $S$          | VA (Volt-Ampere)           | $V_{rms}I_{rms}$ or $\sqrt{P^2 \ + \ Q^2}$  |
| Power Factor   | $\cos{\phi}$ | -                          | $\frac{P}{S}$                               |


Now, let's find out the real power (P) first:

Real power:

$$
P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos{0}
$$


$$
P \ = \ 960 \ \angle{0^{\circ}} \ \text{W}
$$

(The angle stays the same since $0 \ - \ 0 \ = \ 0$)

Now, the apparent power(Q):

$$
Q \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \sin{0}
$$


is also:

$$
Q \ = \ P \ = \ 0 \ \angle{0^{\circ}} \ \text{VAR}
$$



Next, the reactive power (S):

$$
S \ = \ \sqrt{P^2 \ + \ Q^2}
$$

$$ 
S \ = \ 960 \ \angle{0^{\circ}} \ \text{VA}
$$


Lastly, the power factor:

$$
\text{Power factor} \ = \ \frac{P}{S} \ = \ \frac{960 \ \angle{0^{\circ}}}{960 \ \angle{0^{\circ}}} \ = \ 1
$$

Since the power factor is 1, it's a purely resistive circuit.

Final answer in time domain:

The instantaneous circuit is:

$$
i(t) \ = \ 8\sqrt{2} \ \sin{(\omega t \ + \ 0^{\circ})}
$$

or:

$$
i(t) \ = \ 11.31 \ \sin{(\omega t \ + \ 0^{\circ})}
$$

---
## Example 2 -- Pure Inductor Circuit

![Pasted image 20251109204624.png](/img/user/media/Pasted%20image%2020251109204624.png)

Same voltage, however we have an inductor now of $j20 \ \ohm$ 

In inductance terms that would translate to:

$$
X_L \ = \ 20 \ \angle{+90^{\circ}}
$$

This means that the current is lagging behind the voltage by 90 degrees and the voltage is leading ahead of the current by 90 degrees, which is what inductors do.

Now that that's out of the way, 

The impedance will be:

$$
Z \ = \ X_L \ = \ 20 \ \angle{+90^{\circ}} \ \ohm
$$


Thus the current will be:

$$
I_{rms} \ = \ \frac{V_{rms}}{Z}
$$

$$
I_{rms} \ = \ \frac{120 \ \angle{0}}{20 \ \angle{90}}
$$

$$
I_{rms} \ = \ 6 \ \angle {-90^{\circ}} \ \text{A}
$$

Now, for the power calculations

>In power calculations, the phase angle **always means the phase difference between voltage and current**, not their individual phasor angles.

So, here:

$\angle{V} \ = \ 0$, $\angle{I} \ = \ -90$

So, $\phi \ = \ \angle{V} \ - \ \angle{I} \ = \ +90^{\circ}$

This calculated phase angle will be the angle for the voltage, and the current in this power calculation, so we don't need to write them again in the phasor format while calculating. 

Real power:

$$
P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos{90}
$$

$$
P \ = \ 120 \ \times \ 6 \ \times \ 0
$$

$$
P \ = \ 0 \text{W}
$$


Now, for the apparent power:

$$
q \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \sin{90}
$$

$$
Q \ = \ 120 \ \times \ 6 \ \times \ \sin{90}
$$

$$
Q \ = \ 720 \ \text{VAR}
$$


Next, for the reactive power:

$$
S \ = \ \sqrt{P^2 \ + \ Q^2} \ = \ 720 \ \text{VA}
$$

And the power factor:

$$
\text{P.F} \ = \ \frac{P}{S} \ = \ 0
$$

which means that this is a purely reactive circuit, no real power consumed. The current just bounces back from the inductor and other sources. All energy is temporarily stored in the inductor’s magnetic field and returned to the source each cycle — no net work is done.

Final instantaneous current in sinusoidal form:

$$
i(t) \ = \ 6\sqrt{2} \ \sin(\omega t \ - \ 90^{\circ})
$$

or:

$$
i(t) \ = \ 8.484 \ \sin(\omega t \ - \ 90^{\circ}) \ \text{A}
$$

---
## Example 3 -- Pure Capacitor Circuit


![Pasted image 20251109234446.png](/img/user/media/Pasted%20image%2020251109234446.png)


Same voltage, but now we have a capacitor of $-j20 \ohm$

which translates to:

$$
X_C \ = \ 20 \angle{-90^{\circ}} \ \ohm
$$

This means that the current is leading ahead of the voltage by 90 degrees and the voltage is lagging behind the current by 90 degrees, which is how capacitors work.

So the total impedance, Z, will be:

$$
Z \ = \ X_C \ = \ 20 \angle{-90^{\circ}} \ \ohm
$$


Thus, the current will be:

$$
I_{rms} \ = \ \frac{V_{rms}}{Z}
$$

$$
I_{rms} \ = \ \frac{120 \ \angle{0}}{20 \ \angle{-90}}
$$

$$
I_{rms} \ = \ 6 \ \angle {90^{\circ}} \ \text{A}
$$

Now, for the power calculations:


$\angle{V} \ = \ 0$, $\angle{I} \ = \ 90$

So, $\phi \ = \ \angle{V} \ - \ \angle{I} \ = \ -90^{\circ}$

Real power:

$$
P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos{-90}
$$

$$
P \ = \ 120 \ \times \ 6 \ \times \ 0
$$

$$
P \ = \ 0 \text{W}
$$


Now, for the apparent power:

$$
q \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \sin{-90}
$$

$$
Q \ = \ 120 \ \times \ 6 \ \times \ \sin{-90}
$$

$$
Q \ = \ -720 \ \text{VAR}
$$

You might be concerned as to what's with the negative power here?

==Negative reactive power means the circuit is **supplying** reactive energy back to the source over each cycle (the capacitor charges and discharges), rather than absorbing it==. That’s why capacitors are associated with negative $Q$, and inductors with positive $Q$.


Next, for the reactive power:

$$
S \ = \ \sqrt{P^2 \ + \ Q^2} \ = \ 720 \ \text{VA}
$$

And the power factor:

$$
\text{P.F} \ = \ \frac{P}{S} \ = \ 0
$$

which means that this is a purely reactive circuit, no real power consumed.

Final instantaneous current in sinusoidal form:

$$
i(t) \ = \ 6\sqrt{2} \ \sin(\omega t \ + \ 90^{\circ})
$$

or:

$$
i(t) \ = \ 8.484 \ \sin(\omega t \ + \ 90^{\circ}) \ \text{A}
$$


---
## Example 4 -- Series RLC circuit

![Pasted image 20251110013503.png](/img/user/media/Pasted%20image%2020251110013503.png)

This is the same process, just we have to add up the total impedances.

For parallel impedances:

- Find the reciprocal of each impedance (they are called admittances).
- Convert each admittances to rectangular form and add them up.
- Convert back the total admittance to polar form.
- Get total impedance ($Z$) by inverting this total admittance.
- The final impedance angle sign tells you whether the overall network is inductive (+ angle → current lags) or capacitive (− angle → current leads).

The total impedance will be:

$$
Z_{total} \ = \ 10 \ + \ j12 \ - j5
$$

$$
Z_{total} \ = \ 10 \ + \ 7j
$$

$$
Z_{total} \ = \ 10 \ + \ 7\angle{90^{\circ}}
$$


The inductance is greater than the capacitance, so the current is lagging behind the voltage (as evidenced by the sign of the phase angle)

This looks like it's a rectangular phasor.

For ease of calculations we need to convert this to a polar phasor.

From:

$$
Z_{total} \ = \ 10 \ + \ 7j
$$

$V_x \ = \ 10$
$V_y \ = \ 7$

So,

$$
Z_{polar} \ = \ \sqrt{10^2 \ + \ 7^2} \ \angle{\tan^{-1}{\frac{7}{10}}}
$$

$$
Z_{polar} \ = \ 12.206 \ \angle{34.99} \ \ohm
$$

Thus, the current will be:


$$
I_{rms} \ = \ \frac{V_{rms}}{Z}
$$

$$
I_{rms} \ = \ \frac{120 \ \angle{0}}{12.206 \ \angle{34.99}}
$$

$$
I_{rms} \ = \ 9.831 \ \angle {-34.99^{\circ}} \ \text{A}
$$


So, the current lags behind the voltage by 34.99 degrees

Now, for the power calculations:

So, here:

$\angle{V} \ = \ 0$, $\angle{I} \ = \ -34.99$

So, $\phi \ = \ \angle{V} \ - \ \angle{I} \ = \ +34.99^{\circ}$

Real power:

$$
P \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \cos{34.99}
$$

$$
P \ = \ 120 \ \times \ 9.831 \ \times \ 0.819
$$

$$
P \ = \ 966.4 \text{W}
$$


Now, for the apparent power:

$$
Q \ = \ V_{rms} \ \times \ I_{rms} \ \times \ \sin{90}
$$

$$
Q \ = \ 120 \ \times \ 9.831 \ \times \ 0.573
$$

$$
Q \ = \ 676.4 \ \text{VAR}
$$


Next, for the reactive power:

$$
S \ = \ \sqrt{P^2 \ + \ Q^2} \ = \ 1179.72 \ \text{VA}
$$

And the power factor:

$$
\text{P.F} \ = \ \frac{P}{S} \ = \ 0.819
$$


Very close to 1, almost purely resistive circuit.

Final instantaneous current in sinusoidal form:

$$
i(t) \ = \ 9.831\sqrt{2} \ \sin(\omega t \ - \ 34.99^{\circ})
$$

or:

$$
i(t) \ = \ 13.901 \ \sin(\omega t \ - \ 34.99^{\circ}) \ \text{A}
$$

---
# Resonance in single phase AC circuits

==In a single-phase AC circuit, resonance occurs when the inductive reactance== ($X_L$) ==equals the capacitive reactance== $X_C$
==causing the circuit's impedance to be at its minimum and the phase angle between the voltage and current to be zero==. This condition results in maximum current flow for a given voltage and ==causes the circuit to behave like a purely resistive circuit at that specific resonant frequency==.

At resonance, $Z \ = \ R$. (impedance = resistance)

The resonant frequency $f_0$ in a single-phase AC circuit, typically an [RLC circuit](https://www.google.com/search?q=RLC+circuit&sca_esv=79231a2a76414654&source=hp&ei=hHoRae6mGqif4-EPqfrb2AI&iflsig=AOw8s4IAAAAAaRGIlPB9WUY4mSxeotCmf5qTvSsPLc2e&oq=what+is+resonance+in+single+p&gs_lp=Egdnd3Mtd2l6Ih13aGF0IGlzIHJlc29uYW5jZSBpbiBzaW5nbGUgcCoCCAAyBhAAGBYYHjILEAAYgAQYhgMYigUyCxAAGIAEGIYDGIoFMgsQABiABBiGAxiKBTILEAAYgAQYhgMYigUyCBAAGIAEGKIEMggQABiABBiiBDIIEAAYgAQYogQyCBAAGIAEGKIEMggQABiABBiiBEjAJlAAWMUbcAB4AJABAZgBlwKgAY0lqgEGMC4yNS4zuAEDyAEA-AEBmAIboALvI8ICERAuGIAEGLEDGNEDGIMBGMcBwgILEAAYgAQYsQMYgwHCAggQABiABBixA8ICDhAAGIAEGLEDGIMBGIoFwgIIEC4YgAQYsQPCAgsQABiABBixAxiKBcICBRAAGIAEwgILEAAYgAQYsQMYxwOYAwCSBwYwLjI1LjKgB4SuAbIHBjAuMjUuMrgH7yPCBwgwLjQuMjIuMcgHXA&sclient=gws-wiz&mstk=AUtExfAYYO-Lmwu0NOgbjXcXFrRyb8TJovm1TjE8Hoc08sAHUFmyiad-eqXqM66e7niM_3_GCnG0bo_1CkDehimBO9OPXjXnXure2UQCFtYeX4hzxnPpy8KQUf4NbIpc5FFAzXEKZ9EYNrkxrBk4DBzCH8s85clKcElQHIsRRRsQ_P3mlVyT4aF1Le5KC8ogXvYJ-6vL&csui=3&ved=2ahUKEwj1qNC-9-aQAxVXR-sIHa7eIBkQgK4QegQIARAC), is the specific frequency at which capacitive and inductive reactances are equal, resulting in minimum impedance for a series circuit.

It is given by:

$$
f_0 \ = \ \frac{1}{2\pi\sqrt{LC}}
$$

The new impedance, $Z_{new})$ at a different frequency, is given by:

$$
Z_{new} \ = \ \sqrt{R^2 \ + \ (X_L \ - \ X_C)^2}
$$

The inductive reactance, $X_L$ is given by:

$$
X_L \ = \ \frac{2\pi \ f}{L}
$$

The capacitative reactance, $X_C$ is given by:

$$
X_C \ = \ 2 \pi f \ \times \ C
$$


The quality factor,

$$
Q \ = \ \frac{\omega L}{R} \ = \ \frac{1}{R} \ \times \ \sqrt{\frac{L}{C}} 
$$

Bandwidth:

$$
BW \ = \ \frac{f_0}{Q} \ = \ \frac{R}{2\pi L}
$$



---
# Three Phase AC Circuits

==A three-phase system consists of **three AC voltages of equal magnitude and frequency**, but displaced from each other by **120°** in phase==. This is the standard for power generation and distribution because ==it's more efficient than single-phase==.

**Phase sequence**: R-Y-B (or A-B-C), meaning voltage in R leads Y by 120°, and Y leads B by 120°.

---
## A better explanation of why 3-phase AC systems are needed

In a single-phase AC system, you have:

- **Two wires:** one “live” (carrying alternating voltage) and one “return” (or neutral).
- The voltage between them is the **supply voltage** (e.g. 230 V in homes).
- The current through the wire is the same as the current through the load.

So voltage and current are straightforward — one voltage, one current, one path.

Now imagine a generator that makes three AC voltages

In a **three-phase alternator**, there are **three coils** placed 120° apart on the stator.  

Each coil produces its own sinusoidal voltage, equal in magnitude but shifted in phase:

$$
v_R(t) \ = \ V_m \sin{\omega t}
$$

$$
v_Y(t) \ = \ V_m \ \sin{\omega t \ - \ 120^{\circ}}
$$

$$
v_B (t) \ = \ V_m \ \sin(\omega \ t \ - \ 240^{\circ})
$$

In a **three-phase alternator**, there are **three coils** placed 120° apart on the stator.  
==Each coil produces its own sinusoidal voltage, equal in magnitude but shifted in phase==.

---
## The Connection Methods

### 1. Star(Y or Wye) Connection.


![Pasted image 20251110151947.png](/img/user/media/Pasted%20image%2020251110151947.png)

**Structure**: ==We tie one end of all three windings together at a common point (called the **neutral**).  
The other ends go out as the **line terminals**==.

**Wiring**: 4-wire system (3 phase wires + 1 neutral) or 3-wire system (without neutral).

**Key Characteristics**:

- Has a neutral point
- Used for power transmission over long distances
- Used in low and medium voltage distribution (like household supply - 230V phase, 400V line)

- 3 outer terminals: **R, Y, B** → called **Line wires**
- 1 central point: **Neutral (N)**

Each winding (wire/coil/impedance) (between line and neutral) is a **phase**.

---
### 2. Delta $(\Delta)$ connection.

![Pasted image 20251110162444.png](/img/user/media/Pasted%20image%2020251110162444.png)

**Structure**: Three windings are connected in a closed loop (forming a triangle/delta shape).

**Wiring**: 3-wire system only (no neutral wire).

**Key Characteristics**:

- No neutral point
- Used for shorter distances
- More common in industrial and high-power applications

No neutral point exists — just three junctions R, Y, B (the **lines**).

### What's Line vs Phase then?

Think of it this way:

| Term      | Means (in Star)                                                         | Means (in Delta)                                 | Analogy                                            |
| --------- | ----------------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------- |
| **Phase** | Each individual winding of the generator/load (between Line & Neutral). | Each side of the delta loop (between two Lines). | One “sub-circuit” per phase.                       |
| **Line**  | The external wires that connect the system to the load (R, Y, B).       | Same: external wires R, Y, B.                    | The “mains” wires carrying current to the outside. |

So the **phase** is an internal quantity (inside the machine or load).  

The **line** is what you can measure from outside — between the terminals.

### Final mental picture that should click:

```python
       [ R-phase ] → voltage = 230∠0°
       [ Y-phase ] → voltage = 230∠−120°
       [ B-phase ] → voltage = 230∠−240°
```

- Each one is its own “phase” (coil or load branch).
- Each produces an AC voltage 120° out of phase with the others.
- The **line wires** carry those voltages outward.    
- The **neutral (if star)** or shared points (if delta) **tie them together** electrically.


---
## Voltage and Current Relations

### Star Connection

#### Voltage Relation

$$
V_L \ = \ \sqrt{3} \ \times \ V_{ph}
$$

where:

- $V_L$ is the line voltage (voltage between any two lines) 
- $V_{ph}$ is the phase voltage (voltage between any line and neutral)

#### Current Relation:

$$
I_L \ = \ I_{ph}
$$

where:

- $I_L$ is the line current (current in the line conductor)
- $I_{ph}$ is the phase current (current through each winding)

---
### Delta Connection

#### Voltage Relation

$$
V_L \ = \ V_{ph}
$$

Line voltage equals phase voltage.

#### Current Relation:

$$
I_L \ = \ \sqrt{3} \ \times \ I_{ph}
$$


---
### Why two kinds of voltages and currents?

It all comes from **how the three coils (phases)** are connected to the external circuit.

When we join the coils **inside the generator or load**, some terminals become **shared**, and some go **outward** to the lines.  
That’s why we end up with:

- internal quantities → **phase voltage/current**
    
- external, measurable quantities → **line voltage/current**

---
## Power in Three-Phase Systems

### Total Power

For a **balanced three-phase system**, total power is:

$$
P \ = \ 3 \ \times \ V_{ph} \ \times \ I_{ph} \ \cos{\phi}
$$

or in terms of line quantities:

$$
P \ = \ \sqrt{3} \ \times \ V_L \ \times \ I_L \ \times \ \cos{\phi}
$$

### Reactive Power

$$
Q \ = \ 3 \ \times \ V_{ph} \ \times \ I_{ph} \ \times \ \sin{\phi}
$$

### Apparent Power

$$
S \ = \ 3 \ \times \ V_{ph} \ \times \ I_{ph}
$$

### Power Factor

$$
\text{P.F} \ = \ \frac{P}{S} \ = \ \cos{\phi}
$$

---
## Practice Numericals

### Question 1

A balanced star-connected load has phase voltage of 230V and phase current of 10A with power factor 0.8 lagging. Find: (a) Line voltage, (b) Line current, (c) Total power.

Solution:

Given $I_{ph} \ = \ 10 \ \text{A}$, $V_{ph} \ = \ 230 \ \text{V}$, $\text{P.F} \ = \ \cos{\phi} \ = \ 0.8$ 

(a) Line Voltage:

$$
V_L \ = \ \sqrt{3} \ \times \ V_{ph}
$$

or:

$$
V_L \ = \ 1.732 \ \times \ 230 \ = \ 398.36 \ \text{V}
$$

(b) Line current (in star phase, line current = phase current).

$$
I_{L} \ = \ I_{ph} \ = \ 10 \ \text{A}
$$

(c) Total power:

$$
P \ = \ 3 \ \times \ V_{ph} \ \times \ I_{ph} \ \times \ \cos{\phi}
$$

$$
P \ = \ 3 \ \times \ 230 \ \times \ 10 \ \times \ 0.8
$$

$$
P \ = \ \ 5520 \ \text{W}
$$

---
### Question 2

A balanced delta-connected load draws line current of 20A with line voltage of 400V and power factor 0.9. Find: (a) Phase voltage, (b) Phase current, (c) Total power.

**Solution**:

Given power factor $\cos{\phi} \ = \ 0.9$
 
(a) Phase voltage: (in delta connection, phase voltage = line voltage)

$$
V_{ph} \ = \ V_L \ = \ 400 \ \text{V}
$$

(b) Phase current: 

$$
I_{ph} \ = \ \frac{I_L}{\sqrt{3}} \ = \ 11.55 \ \text{A}
$$

(c) Total power:

$$
P \ = \ \sqrt{3} \ \times \ V_L \ \times \ \cos{\phi} \ = \ 1.732 \ \times \ 400 \ \times \ 0.9 \ = \  12470 \ \text{W}
$$


---
## Important Points to Remember

- $\sqrt{3}$ factor: In star, it appears in voltage relation; in delta, it appears in current relation.
- **Power formula is same** for both connections: $P \ = \ \sqrt{3} \ V_L \ I_L \ \cos{\phi}$
- **Balanced load**: All three phases have equal impedance and equal phase angle.
- **Phase sequence**: Always assume R-Y-B unless stated otherwise.
- **Neutral current in balanced star**: Zero (because three equal currents 120° apart cancel out)

---