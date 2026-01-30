---
{"dg-publish":true,"permalink":"/physics-1/module-4-quantum-mechanics/","tags":["Semester-1","Physics"],"created":"2025-10-17T21:00:47.157+05:30","updated":"2026-01-31T02:28:22.855+05:30"}
---

---
# Index

1. [[#Black body radiation]]
2. [[#The Photo-electric effect]]
3. [[#The Compton Effect]]
4. [[#The De Broglie Hypothesis]]
5. [[#Heisenberg's uncertainty principle]]
6. [[#Schrodinger Wave Equation]]

---
# Black body radiation

![Pasted image 20251106233713.png](/img/user/media/Pasted%20image%2020251106233713.png)

Black body radiation is the ==electromagnetic radiation emitted by a theoretical object that absorbs all incident radiation and, at thermal equilibrium, emits radiation dependent only on its temperature==.

## What is a black body?

- ==A black body is an idealized object that absorbs all electromagnetic radiation incident upon it, with no reflection or transmission==.

- ==While no real object is a perfect black body, an opening in a hollow enclosure is a good approximation, as is a furnace or the sun==.

### Explaining the black body radiation using the photon concept.

#### The Problem

==Classical physics (specifically the Rayleigh-Jeans law) assumed that energy was continuous and that vibrating charged particles within a heated object could have any energy value==. This led to ==a formula that accurately described radiation at long wavelengths but predicted that an infinite amount of energy would be emitted at high frequencies (short wavelengths), a clear contradiction== of experimental results known as the ==ultraviolet catastrophe==.

### Quantum Explanation: The Photon Concept

==Max Planck resolved this paradox in 1900== by proposing a radical hypothesis that laid the foundation for quantum mechanics:

- **Energy Quantization:** ==Planck suggested that energy exchange between the walls of a black body cavity and the electromagnetic radiation (photons) could only occur in discrete amounts, or quanta==.

- **Photon Energy**: ==The energy== ($E$) ==of a single quantum(photon) is directly proportional to it's frequency== $\mu$, as defined by the equation:
  
$$E \ = \ h\mu$$

where $h$ is ==Planck's constant== (approximately $6.626 \times \ 10^{-34} \text{J.s}$)

- **Discrete Energy Levels**: The vibrating oscillators (atoms/electrons) in the black body walls ==can only exist in specific, equally spaced energy states== (e.g. $E_1 \ = \ h\mu$, $E_2 \ = \ 2h\mu$, etc.) ==They absorb energy to jump to a higher state or emit a photon to drop to a lower state. (same concept behind a 3-phase, 4-phase LASER where the electrons gain more energy on jumping to a higher state and emit photons when dropping to a lower state.==)

---
# The Photo-electric effect

The **photoelectric effect** is ==the phenomenon where electrons, called **photoelectrons**, are emitted from a material's surface when light shines on it==. ==This effect provides key evidence for the **particle nature of light**== (photons) and was successfully explained by Albert Einstein using Max Planck's quantum theory, earning Einstein the Nobel Prize in Physics in 1921.

### Classical Physics vs. Experimental Results

==Before Einstein's explanation, classical wave theory predicted that a brighter light (higher intensity) should result in higher-energy electrons==, and any frequency of light should eventually cause emission if the intensity was high enough or given enough time. However, experiments revealed:

- ==Electron emission only occurred if the light's frequency was above a certain minimum (threshold frequency)==.
  
- ==The kinetic energy of the emitted electrons depended only on the light's frequency, not its intensity==.
  
- ==Emission was instantaneous, with no time delay for even very dim light, as long as the frequency condition was met==

### Einstein's Explanation: The Photon Concept

==Einstein's theory reconciled these observations by extending Planck's idea that light energy comes in discrete packets (photons)==. The explanation is based on a one-to-one collision between a single photon and a single electron:

- **Energy Transfer**: ==When a photon strikes the metal surface, it transfers all of it's energy== ($E \ = \ h\mu$) ==to a single electron==.

- **Work Function** ($\phi$): ==A portion of this energy is used by the electron to overcome the attractive forces that bind it to the metal's surface, known as the work function==.

- **Kinetic Energy:** ==The remaining energy is converted into the kinetic energy of the ejected electron==.

![Pasted image 20251107000235.png](/img/user/media/Pasted%20image%2020251107000235.png)

### The Photoelectric Equation

Einstein's photoelectric equation mathematically describes this interaction:

$$\text{Energy of incident photon \ = \ Work function  \ + \ Maximum kinetic energy of electron}$$

or:

$$
h\mu \ = \ \phi \ + \ KE_{max}
$$

$$
KE_{max} \ = \ h\mu \ - \ \phi
$$

where:

- $h$ is Planck's constant (approximately $6.626 \times \ 10^{-34} \text{J.s}$).
- $\mu$ is the frequency of incident light.
- $\phi$ is the work function of the specific metal.
- $KE_{max}$ is the maximum kinetic energy of the emitted photoelectron.

---
# The Compton Effect

The **Compton effect** (or Compton scattering) is ==the phenomenon where a high-energy photon, typically an X-ray or gamma ray, collides with a free or loosely bound electron, resulting in a decrease in the photon's energy and an increase in its wavelength==.

==This effect cannot be explained by classical wave theory, which predicts that the scattered radiation should have the same wavelength as the incident radiation==. In 1923, Arthur Compton explained the effect by applying the **photon concept** and treating the interaction as a collision between two particles: a photon and an electron.

### Explanation using the Photon Concept

The explanation of the Compton effect relies on two fundamental principles: the conservation of energy and the conservation of momentum.

- **Photon as a Particle with Momentum:** Unlike classical waves, photons are treated as discrete packets of energy that also possess momentum. The momentum ($\rho$) of a photon is related to its wavelength ($\lambda$) by the equation $\rho \ = \ \frac{h}{\lambda}$ where $h$  is Planck's constant.
  
- **The Collision:** ==When an incident photon collides with an electron (assumed to be at rest or loosely bound), it behaves like a cue ball hitting another ball. The photon transfers a portion of its energy and momentum to the electron==.
  
  
- **Energy Transfer and Wavelength Shift:** ==Because the incident photon gives away some of its energy to the recoiling electron, the scattered photon has less energy==. According to the energy-frequency relationship ($E \ = \ h \mu$),
  ==lower energy corresponds to a lower frequency and, consequently, a **longer wavelength**==.
  
  
- **Conservation Laws:** Compton used relativistic mechanics to analyze the collision, applying the conservation of both energy and momentum (which is a vector quantity, accounting for direction) to derive a formula that accurately predicts the change in wavelength based on the angle at which the photon is scattered.

---
### The Compton Shift Formula

![Pasted image 20251107032445.png](/img/user/media/Pasted%20image%2020251107032445.png)

==The change in wavelength== ($\Delta \lambda$), ==or the Compton shift==, is given by the Compton scattering equation.

$$
\Delta \lambda \ = \ \lambda' \ - \ \lambda \ = \ \frac{h}{m_ec} \ (1 \ - \ \cos\theta)
$$

or:

$$
\Delta \lambda \ = \ \lambda_C(1 \ - \ \cos\theta)
$$

The term $\lambda_C \ = \ \frac{h}{m_ec} \ = \ 2.43 \ \times \ 10^{-12} \ \text{m}$ is ==also known as the **Compton wavelength** of the electron==.

### Constants to remember:

- $h \ = \ 6.626 \times \ 10^{-34} \text{J.s}$ (Planck's constant)
- $c \ = \ 3 \times \ 10^8 \text{m/s}$ (speed of light)
- $m_e \ = \ 9.11 \ \times \ 10^{-31} \text{kg}$ (mass of the electron)
- $\lambda_C \ = \ 2.43 \ \times \ 10^{-12} \text{m}$ (or $0.0243  \ \mathring{A}$) (in angstroms) (important)
- $\theta$ is the scattering angle of the photon (will be given).
- $m_e \ c^2 \ = \ 0.511 \text{MeV}$ (for energy related calculations)
- $hc \ = \ 1240 \text{eV-nm}$ (for energy related calculations)

---
# Practice Numericals for the Compton Effect

## Numerical 1: Calculating scattered wavelength and the electron kinetic energy

An X-ray photon with an initial wavelength of $\lambda \ = \ 0.100 \ \text{nm}$ collides with a free electron and is scattered at an angle of $\phi \ = \ 90^{\circ}$ relative to it's original direction. Calculate:

- The wavelength of the scattered photon $\lambda'$
- The kinetic energy $KE$ imparted to the recoiling electron.

Constants:

- Planck's constant: $h \ = \ 6.626 \ \times \ 10^{-34} \ \text{J.s}$
- Speed of light: $c \ = \ 3 \times \ 10^8 \ \text{m/s}$
- $m_e \ = \ 9.11 \ \times \ 10^{-31} \text{kg}$ (mass of the electron)
- $\lambda_C \ = \ \frac{h}{m_e \ c} \ = \ 2.43 \ \times \ 10^{-12} \ \text{m}$

$\cos{\phi} \ = \ \cos{90} \ = \ 0$

(a) The wavelength of the scattered photon $\lambda'$

Firstly the Compton shift:


$$
\Delta \lambda \ = \ \lambda_C \ (1 \ - \ \cos{\phi})
$$

$$
\Delta \ \lambda \ = \ 2.43 \ \times \ 10^{-12} \ \times 1
$$

$$
\Delta \lambda \ = \ 2.43 \ \times \ 10^{-12}
$$

Next, 

So, 

$$
\Delta \ \lambda \ = \ \lambda' \ - \ \lambda
$$

$$
\lambda' \ = \ \Delta \lambda \ + \ \lambda
$$

$$
\lambda' \ = \ (2.43 \ \times \ 10^{-12} \ + \ 1 \ \times \ 10^{-9}) \ \text{m}
$$

$$
\lambda' \ = \ (2.43 \ \times \ 10^{-9} \ \times 10^{-3} \ + \ 1 \ \times\ 10^{-9}) \ \text{m}
$$

$$
\lambda' \ = \ (0.00243 \ \times \ 10^{-9} \ + \ 1 \ \times \ 10^{-9}) \ \text{m}
$$

$$
\lambda' \ = \ 1.00243 \ \times \ 10^{-9} \ \text{m}
$$


(b) The Kinetic Energy imparted to the electron will be:

$$
\text{K.E} \ = \ E_{\text{initial photon}} \ - \ E_{\text{scattered photon}}
$$

This is because in cases like the **Compton effect** during collision, the amount of energy lost by the photon is the exact amount of energy the electron gains to get scattered. The energy is conserved.

Thus,

$$
\text{K.E} \ = \ \frac{hc}{\lambda} \ - \ \frac{hc}{\lambda'}
$$

$$
\text{K.E} \ = \ \frac{6.626 \ \times \ 10^{-34} \ \times \ 3 \ \times \ 10^8}{1 \ \times \ 10^{-9}} \ - \ \frac{6.626 \ \times \ 10^{-34} \ \times \ 3 \ \times \ 10^8}{1.00243 \ \times \ 10^{-9}}
$$


$$
\text{K.E} \ = \ \frac{19.878 \ \times \ 10^{-26}}{10^{-9}} \ - \ \frac{19.878 \ \times \ 10^{-26}}{1.00243 \ \times \ 10^{-9}}
$$


$$
\text{K.E} \ = \ 19.878 \ \times \ 10^{-17} \ - \ 19.829 \ \times \ 10^{-17}
$$

$$
\text{K.E} \ = \ 0.049 \ \times \ 10^{-17}
$$

---
## Practice Problem: The Backward Scattering

A beam of X-ray photons with a wavelength of $\lambda = 0.0500 \text{ nm}$ strikes a target. After the collision, the scattered photons are detected with a new wavelength of $\lambda' = 0.05486 \text{ nm}$.

**Calculate:**

1. **The scattering angle ($\phi$):** Through what angle were the photons deflected?
2. **The Kinetic Energy ($K.E.$) of the electron:** How much energy did the electron carry away (in Joules)? 

**Constants for your calculation:**

- $\lambda_C = 2.43 \times 10^{-12} \text{ m}$ (Compton Wavelength)
- $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$
- $c = 3 \times 10^8 \text{ m/s}$
- $hc \ = \ 19.878 \ \times \ 10^{-26} \ \text{ Jm}$

### 1. Scattering Angle

We know that the Compton Shift is given by:

$$
\Delta \lambda \ = \ \lambda' \ - \ \lambda
$$

$$
\Delta \ \lambda \ = \ 0.05486 \ - \ 0.0500
$$

$$
\Delta \ \lambda \ = \ 0.04986 \ \text{nm}
$$

or: 
$$
\Delta \lambda \ = \ 4.986 \ \times \ 10^{-12} \text{ m}
$$

$$
\Delta \ \lambda \ = \ \lambda_C \ (1 \ - \ \cos \phi)
$$

$$
4.986 \ \times \ 10^{-12} \ = \ 2.43 \times 10^{-12} \ \times \ (1 \ - \ \cos \phi)
$$

$$
(1 \ - \ \cos\phi) \ = \ \frac{4.986}{2.43}
$$


$$
(1 \ - \ \cos\phi) \ = \ 2.051
$$

Rounding off for simplicity:

$$
(1 \ - \ \cos\phi) \ = \ 2
$$

$$
\cos \phi \ = \ -1
$$

$$
\phi \ = \ \cos^{-1}(-1)
$$

$$
\phi \ = \ 180^{\circ}
$$


This means that the collision is head on.

### 2. The Kinetic Energy of the scattered electron.

The scattered electron's energy comes directly from the energy difference between the photon before it struck the electron and the photon after it struck the electron.

In this case, since the collision is head-on, the $\text{K.E}$ received will be the maximum.

Given:

$\lambda = 0.0500 \ \times \ 10^{-9} \ \text{ m}$
$\lambda' \ = \ 0.05486 \times 10^{-9} \text{ m}$

So,

$$
\text{KE}_{\text{max}} \ = \ \frac{hc}{\lambda} \ - \ \frac{hc}{\lambda'}
$$

$$
\text{KE}_{\text{max}} \ = \ \frac{hc}{\lambda} \ - \ \frac{hc}{\lambda'}
$$

$$
\text{KE}_{\text{max}} \ = \ \frac{19.878 \ \times \ 10^{-26}}{0.0500 \ \times \ 10^{-9}} \ - \ \frac{19.878 \ \times \ 10^{-26}}{0.05486 \times 10^{-9}}
$$

$$
\text{KE}_{\text{max}} \ = \ 397.56 \ \times \ 10^{-17} \ - \ 362.34 \ \ \times \ 10^{-17}
$$


$$
\text{KE}_{\text{max}} \ = \ 35.22 \ \times \ 10^{-17} \ \text{ J}
$$

---
# The De Broglie Hypothesis

The **De Broglie hypothesis**, proposed by French physicist Louis De Broglie in 1924, is a fundamental tenet of quantum mechanics stating that ==all matter exhibits wave-particle duality==. While classical physics treats matter solely as particles, this hypothesis suggests that moving particles also possess wave-like characteristics.

## Core Principles

- **Matter Waves:** ==Every moving material particle (such as an electron or a proton) has an associated wave, often referred to as a **matter wave** or **de Broglie wave**==.
  
- **Symmetry of Nature:** ==De Broglie’s reasoning was partially based on the idea that if light—traditionally viewed as a wave—could behave like a particle (photon), then nature’s inherent symmetry suggests particles should also behave like waves==.

---
## The De Broglie Equation

The hypothesis relates a particle's wavelength $\lambda$ to it's momentum $\rho$ using the following formula:  

![](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)
$$
\lambda \ = \ \frac{h}{\rho} \ = \ \frac{h}{mv}
$$


where:

 - $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$ (Planck's Constant)
 - $c = 3 \times 10^8 \text{ m/s}$ (Speed of light)
 - $m$ is the mass of the particle
 - $v$ is the velocity of the particle

**Key Implications**

1. **Microscopic vs. Macroscopic:** ==The wave nature is only significant for subatomic particles with very small mass==. For macroscopic objects (like a moving ball), the mass is so large that the wavelength becomes infinitesimally small and undetectable.
   
2. **Bohr's Atomic Model:** ==De Broglie's hypothesis provided a theoretical basis for Bohr's model of the atom. It explained that electrons inhabit specific orbits because only certain circumferences allow the electron's matter wave to form a **standing wave**, preventing energy loss through radiation==.
   
3. **Experimental Proof:** The hypothesis was confirmed in 1927 by the **Davisson-Germer experiment**, which demonstrated that electrons could be diffracted—a property unique to waves—when fired at a nickel crystal.

---
## Difference from Electromagnetic Waves

==Unlike light or radio waves, matter waves are not electromagnetic==. They do not consist of oscillating electric and magnetic fields and cannot propagate through a vacuum without the physical presence of the particle itself.

---
### Practice Problem 1: The Macroscopic World

Calculate the de Broglie wavelength of a **baseball** with a mass of $0.145 \text{ kg}$ thrown at a speed of $40 \text{ m/s}$ (about 90 mph).

- **Constants:** $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$
- **Goal:** See just how small the wavelength is for everyday objects.

Given:

- $m \ = \ 0.145 \ \text{ kg}$ 
- $v \ = \ 40 \ \text{ m/s}$
- $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$

The de Broglie wavelength for this:

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{0.145 \ \times 40}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{5.8}
$$

$$
\lambda \ = \ 1.142 \ \times \ 10^{-34} \ \text{ m}
$$


---
### Practice Problem 2: The Microscopic World

Calculate the de Broglie wavelength of an **electron** ($m_e = 9.11 \times 10^{-31} \text{ kg}$) moving at a speed of $2.19 \times 10^6 \text{ m/s}$ (this is the typical speed of an electron in the first orbit of a hydrogen atom).

- **Goal:** Compare this wavelength to the size of an atom ($\approx 0.1 \text{ nm}$).

Given:

- $m \ = \ 9.11 \times 10^{-31} \ \text{ kg}$ 
- $v \ = \ 2.19 \times 10^6 \ \text{ m/s}$
- $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$

The de Broglie wavelength for this:

$$
\lambda \ = \ \frac{h}{mv}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{9.11 \times 10^{-31} \ \times \ 2.19 \times 10^6}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{19.9509 \ \times \ 10^{-25}}
$$

$$
\lambda \ = \ \frac{6.626 \ \times \ 10^{-9}}{19.9509} \ \text {m}
$$

$$
\lambda \ = \ 0.3321 \ \times \ 10^{-9} \ \text{ m}
$$

---
## The Energy-Wavelength Relation

In many lab experiments (like Electron Microscopy), you don't know the **velocity** ($v$) of the electron, but you do know its **Kinetic Energy** ($K.E.$) because you accelerated it using a specific voltage.

We can combine the classical Kinetic Energy formula with de Broglie’s:

1. $K.E. = \frac{1}{2}mv^2$
2. Rearranging for momentum ($p = mv$), we get: $p = \sqrt{2m(K.E.)}$
3. Substituting this into $\lambda = \frac{h}{p}$:

$$\lambda = \frac{h}{\sqrt{2m(K.E.)}}$$

### Example

An electron ($m = 9.11 \times 10^{-31} \text{ kg}$) is accelerated through a potential difference such that it gains a **Kinetic Energy** of $1.6 \times 10^{-17} \text{ J}$ (which is 100 eV).

**Calculate its de Broglie wavelength.**

Given:

-  Mass of electron: $m = 9.11 \times 10^{-31} \text{ kg}$
-  Kinetic Energy of the accelerated electron: $\text{KE} \ = \ 1.6 \times 10^{-17} \text{ J}$
-  $h = 6.626 \times 10^{-34} \text{ J}\cdot\text{s}$ 

The de Broglie wavelength of the accelerated electron:

$$
\lambda = \frac{h}{\sqrt{2m(K.E.)}}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{\sqrt{2 \ \times \ 9.11 \ \times \ 10^{-31} \ \times \ 1.6 \ \times \ 10^{-17}}}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{\sqrt{29.152 \ \times \ 10^{-48}}}
$$

$$
\lambda \ = \ \frac{6.626 \times 10^{-34}}{5.399 \ \times \ 10^{-24}}
$$

$$
\lambda \ = \ \frac{6.626}{5.399} \ \times \ 10^{-10}
$$

$$
\lambda \ = \ 1.227 \ \times \ 10^{-10} \ \text{ m}
$$

---
# Heisenberg's uncertainty principle

https://www.youtube.com/watch?v=BNYz5EKXVeI

![Pasted image 20260104171335.png](/img/user/media/Pasted%20image%2020260104171335.png)

Heisenberg's Uncertainty Principle, given by Werner Heisenberg in 1927, this principle only works on the microscopic scale, on the subatomic level. ==It states that, it is impossible to simultaneously measure certain pairs of physical properties, such as **position== ($x$)** ==and **momentum== ($\rho$)**, ==with infinite precision==.

The principle reveals that ==at the subatomic level, the more accurately you determine a particle's position, the less accurately you can know its momentum, and vice versa==.

## Key Concepts

- **Wave-Particle Duality**: The principle arises because quantum objects (like electrons) behave like waves. A perfectly localized wave has an indeterminate wavelength (momentum), while a wave with a precise wavelength is spread out over space.
  
- **Intrinsic Limit**: ==This uncertainty is not due to clumsy measurement tools or experimental error; it is an inherent property of nature==.

---
## Practice Problem 1

![Pasted image 20260104175749.png](/img/user/media/Pasted%20image%2020260104175749.png)

1 > (a): 

Given:

- Velocity of electron $\Delta v$: $0.15 \ \text{ m/s}$ 
- Mass of electron is $m = 9.11 \times 10^{-31} \text{ kg}$

The uncertainty in the momentum of the electron is:

$$
\Delta \rho \ = \ m \Delta v \ = \ 1.3665 \ \times \ 10^{-31} \ \text{ kg m/s}
$$

The uncertainty in the position of the electron is:

$$
\Delta x \ \cdot \ \Delta \rho \ \geq \ \frac{h}{4\pi}
$$

or: (removing the inequality for solving purposes)

$$
\Delta x \ = \ \frac{h}{4\pi} \ \times \ \frac{1}{\Delta p}
$$
$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-34}}{4 \ \times \ 3.14} \ \times \ \frac{1}{1.3665 \ \times \ 10^{-31}}
$$

$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-34}}{12.56 \ \times \ 1.3665 \ \times \ 10^{-31}}
$$

$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-3}}{17.16324}
$$

$$
\Delta x \ = \ 0.38605 \ \times \ 10^{-3}
$$

$$
\Delta x \ = \ 3.86 \ \times \ 10^{-4} \ \text{ m}
$$

1> (b):

Given mass of ball: $m \ = \ 2 \ \text{kg}$
Given uncertainty value of velocity of the ball: $\Delta v \ = \ 0.15 \ \text{m/s}$

The uncertainty in the momentum is given by:

$\Delta \rho \ = \ m \ \cdot \ \Delta v \ = \ 0.3 \ \text{ kg m/s}$

The uncertainty in the position of the electron is given by:

$$
\Delta x \ \cdot \ \Delta \rho \ \geq \ \frac{h}{4\pi}
$$

$$
\Delta x \ \cdot \ 0.3 \ \geq \ \frac{6.626 \ \times \ 10^{-34}}{4\pi}
$$

(Removing the inequality for simplification purposes)

$$
\Delta x \ \cdot \ 0.3 \ = \ \frac{6.626 \ \times \ 10^{-34}}{4\pi}
$$

$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-34}}{0.3 \ \times \ 4 \pi}
$$

$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-34}}{0.3 \ \times\ 12.56}
$$

$$
\Delta x \ = \ \frac{6.626 \ \times \ 10^{-34}}{3.768}
$$

$$
\Delta x \ = \  1.7584 \ \times \ 10^{-34}
$$


---
# Schrodinger Wave Equation

## The Concept

Think of it this way: ==In classical physics, we use **Newton’s Second Law**== ($F=ma$) ==to predict the path of a ball. In quantum mechanics, particles don't have a single path—they have a **Wavefunction**, represented by the Greek letter== $\Psi$ ==(psi)==.


==The Schrödinger equation is the "law of motion" for this wavefunction. It doesn't tell you exactly where the particle _is_; it tells you how the **probability wave** of that particle evolves over time and space==.

---
### The Equation (Time-Independent)

For a particle moving in one dimension, the most common form of the equation is:

$$- \frac{\hbar^2}{2m} \frac{d^2\Psi}{dx^2} + V(x)\Psi = E\Psi$$

#### Breaking down the terms:

- **$\Psi$ (The Wavefunction):** ==Contains all the information about the particle==.

- **$- \frac{\hbar^2}{2m} \frac{d^2\Psi}{dx^2}$ (Kinetic Energy):** ==This part represents the energy of the particle's motion==. The $d^2/dx^2$ is a derivative that measures how much the wave "curves."

- **$V(x)\Psi$ (Potential Energy):** ==This represents the environment (like an electric field or a "box") pushing on the particle==.   

- **$E\Psi$ (Total Energy):** $E$ is ==the total energy of the system==.

- **$\hbar$ (Reduced Planck's Constant):** Defined as $\hbar = \frac{h}{2\pi}$.

---
### Why is this equation so important?

1. **Quantization:** It explains why electrons only live in specific energy levels.9 The math only "works" for certain values of $E$—much like a guitar string only vibrates at specific notes.
    
2. **Probability Density:** While $\Psi$ can be a complex number, its square, $|\Psi|^2$, tells you the **probability** of finding the particle at a specific spot.
    
3. **The End of Certainty:** It officially replaces the idea of "orbits" with "orbitals" (clouds of probability).

---
## Detailed Explanation

### 1. What is the "Wave"?

When we talk about the wave in the Schrödinger equation, ==it is **not** a physical wave emitted by the electron (like a radio wave coming off an antenna)==. Instead:

- The electron **is** the wave.
  
- It is a **mathematical wave** of "possibility."
  
- This is the heart of **wave-particle duality**: ==In transit, the electron acts like a spread-out wave (it can interfere with itself, go through two slits at once, etc.). But when you look at it, the wave "collapses," and you find a particle at a specific point==.

### 2. Probability vs. Path

Earlier, I was confused, if the equation gives the probability of a "path." In quantum mechanics, the idea of a "path" (like a ball flying through the air) actually disappears. ==Instead, the Schrödinger equation gives you the **probability of finding the particle at a specific point** at a specific time== (on being observed).

### 3. How it relates to Heisenberg

- **Heisenberg** tells you the _limit_: "You cannot sharpen your focus on position and momentum at the same time."
    
- **Schrödinger** gives you the _map_: It tells you the **precise probability** for every single point in space.

==If Heisenberg says the electron is somewhere in a range of 1 nanometer, Schrödinger’s equation will tell you, "There is a 10% chance it's at the left edge, a 50% chance it's in the middle, and a 5% chance it's already tunneled slightly outside the wall."==

---
### The Schrödinger Equation: A Visual Breakdown

Think of the wavefunction $\Psi$ as a "cloud." ==Where the cloud is thick, the probability is high. Where the cloud is thin, the probability is low==.

The equation explains how that cloud moves:

1. **Kinetic Energy term:** ==Tells us how the cloud spreads out or "wiggles." (Fast electrons have more "wiggles" or higher frequency)==. 
2. **Potential Energy term:** ==Tells us how the environment (like a nucleus) pulls on or traps the cloud==.

---
## The "Particle in a Box" thought experiment.

Imagine an electron trapped between two invisible walls.

![Pasted image 20260108022740.png](/img/user/media/Pasted%20image%2020260108022740.png)

Imagine that the electron is denoted by the blue arrows and that it is moving back and forth by crashing against the orange and the green walls.

The orange "cloud of probabilities" is the **wavefunction** $\Psi$ (it might look a bit different in the drawing), which **until observed** **is just probabilities of where the electron may be given a certain instant, since we do know the momentum of electron, but we cannot know it's position too at the same time in the same instant, as Heisenberg said**.

The moment **an observer observes the electron**, only the does the cloud of probabilities collapse and the electron instantly collapses to a specific position, with the probability as given by Schrodinger's Equation.

The way we can know the velocity of the electron is because in this model, the **Infinite Square Well model**, when unobserved, this **cloud of probabilities is actually a wave**. (Coming from the wave-particle duality, that until observed the electron is a wave and once observed it collapses to a particle.)

So, ==when we compress the free area available to the electron by pushing the walls closer, we reduce the wavelength of the electron, causing it to have a higher frequency==, thus achieving more momentum, and thus more Kinetic Energy.

![Pasted image 20260108023645.png](/img/user/media/Pasted%20image%2020260108023645.png)


(Since wavelength is inversely related to frequency in any consistent medium).

As:

The speed of a wave $v$ is given by $v \ = \ \lambda \ \times \ f$ (for light/EM waves in vacuum that's $c \ = \ 3 \ \times \ 10^8 \ \text{ m/s}$)

---
