---
{"dg-publish":true,"permalink":"/mathematics-1-a/module-1-calculus-integration/","tags":["Semester-1","Mathematics-1A"],"created":"2026-03-01T12:01:58.849+05:30","updated":"2026-03-16T03:34:49.014+05:30"}
---

---
# Index

## Class 12 level recap 

1. [[#Integral Calculus Recap]]
2. [[#Basic Integral Formulae]]
3. [[#Some basic trigonometric identities]]
4. [[#Methods of integration]]
5. [[#1. U-substitution]]
6. [[#2. Integration by Parts -- The easy method.]]
7. [[#3. Integration by partial fractions -- An easy method]]

---
## College Stuff (Calculus - 1)

1. [[#Evolutes and Involutes]]
2. [[#1. Indefinite vs Definite Integrals]]
3. [[#2. Even and Odd Functions (Symmetry Rules)]]
4. [[#3. Improper Integrals]]
5. [[#Applications of definite integrals to evaluate surface areas and volumes of revolutions]]
6. [[# DEFINITE INTEGRALS — MASTER ALGORITHM]]
7. [[#Area under Curves]]
8. [[#Volumes of Revolution]]
9. [[#1. Disk Method (When there is no hollow region)]]
10. [[#2. Washer Method (When there is a hollow region)]]
11. [[#Gamma Functions]]
12. [[#Beta Functions]]

---
# Integral Calculus Recap

Taken from [[Calculus-3 stuff/Integral Calculus\|Integral Calculus]]

## **A problem well defined, is a problem half solved -- Charles Kettering**

https://www.youtube.com/watch?v=hXOrQ0Ao4UE&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=1&pp=gAQBiAQB

The above link points to a full comprehensive recap of class 12 recap. Watch it only if you have time.

---
## Basic Integral Formulae

![WhatsApp Image 2024-11-06 at 11.09.36_8ab79753.jpg](/img/user/media/WhatsApp%20Image%202024-11-06%20at%2011.09.36_8ab79753.jpg)

![WhatsApp Image 2024-11-06 at 11.09.36_a529dee3.jpg](/img/user/media/WhatsApp%20Image%202024-11-06%20at%2011.09.36_a529dee3.jpg)

---
## Some basic trigonometric identities

https://www.youtube.com/watch?app=desktop&v=m1OitPmkydY

![Pasted image 20241106111131.png](/img/user/media/Pasted%20image%2020241106111131.png)

https://www.geeksforgeeks.org/trigonometric-identities/

![Trigonometry-Identities.webp](/img/user/media/Trigonometry-Identities.webp)


https://www.geeksforgeeks.org/trigonometry-table/

![Trogonometry-2.png](/img/user/media/Trogonometry-2.png)

---
## Methods of integration 

### 1. U-substitution 

So let's say we have an integral 

$$\int{f(x) dx}$$

To solve this using **u-substitution**, we need to: 
1. set $x = g(t)$.
2. Differentiate both sides
3. So, we get : $${dx} = g'(t).dt$$
And then we replace the value of $x$ and $dx$ in the original equation to get:

$$\int{f(g(t)).g'(t)dt}$$
#### Example 1 :

1. $$\int{sin(mx)dx}$$
Let us set $mx = t$ and differentiate both sides w.r.t $x$, we get :

$$\frac{d}{dx}(mx) = \frac{d(t)}{dx}$$

$$\implies m . \frac{d(x)}{dx} = \frac{dt}{dx}$$
$$\implies m = \frac{dt}{dx}$$
$$\implies dx = \frac{dt}{m}$$

And thus we replace $dx$ in the original equation to get:

$$\int{sin(t)\frac{dt}{m}}$$
$$\frac{1}{m}.\int{sin(t)}dt$$
$$\frac{1}{m}.(-cos(t)) + C$$
or , $$\frac{-cos(mx)}{m} + C$$

---
#### Example 2

$$\int{\frac{2x}{1+x^2}dx}$$

Let $$1+x^2 = t$$
$$\therefore \frac{d(1)}{dx} + \frac{d(x^2)}{dx} = \frac{d(t)}{dx}$$

or $$\implies 0 + 2x = \frac{dt}{dx}$$
or, $$2x dx = dt$$
Replacing this in the original equation, 

$$\int{\frac{dt}{t}}$$

$$= log|t| + C$$
or , 

$$log|1 + x^2| + C$$
---
## 2. Integration by Parts -- The easy method.

https://www.youtube.com/watch?v=2I-_SV8cwsw&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=2

This is called the D-I method. Differentiate-Integrate. (also known as the LIATE method)

---
### Example 1.

So let's say we have this integral here :

$$\int{x^2.sin(3x)dx}$$
We need to make a small table.

| Sign | D   | I   |
| ---- | --- | --- |
|      |     |     |

The D column represents differentiation and I column represents integration.

Now we choose each term to be either differentiated or integrated.

Here the easy choice seems to differentiate $x^2$ and integrate $sin(3x)$


| D     | I         |
| ----- | --------- |
| $x^2$ | $sin(3x)$ |

Now we continue the respective operations on both sides for a while.

| Sign | D     | I                    |
| ---- | ----- | -------------------- |
| +    | $x^2$ | $sin(3x)$            |
| -    | $2x$  | $\frac{-cos(3x)}{3}$ |
| +    | 2     | $-\frac{sin(3x)}{9}$ |
| -    | 0     | $\frac{cos(3x)}{27}$ |

Each column having alternating signs.

---
### What to differentiate and what to integrate?

- **Inverse trigonometric functions** (like $tan^{-1}$, $sin^{-1}$) — _differentiate_ these if present.
- **Logarithmic functions** (like ln(x)) — _differentiate_ these if present.
- **Algebraic functions** (like $x^2$, $x$, constants) — _differentiate_ these if no inverse or logarithmic terms are present.
- **Trigonometric functions** (like $sin(x)$, $cos(x)$) — _differentiate_ these if there are no inverse, logarithmic, or algebraic terms to use.
- **Exponential functions** (like $e^x$, $a^x$) — these are typically _integrated_ as a last choice.


**When to stop the operations**:

1. If the column of **D** reaches `0`.
2. If the products of a row (product of both the value of **D** and **I**) can be integrated.
3. If any the products of any row (product of both the value of **D** and **I**) result in the original integral.

So here we see that the column of **D** has reached `0`.

So we multiply downwards, diagonally, along with each respective sign, and write them together for the final answer.

![Pasted image 20241106211308.png](/img/user/media/Pasted%20image%2020241106211308.png)

Like this.

So the final answer becomes, 

$$\int{x^2.sin(3x)dx} = \boxed{\frac{-x^{2}.cos(3x)}{3}+\frac{2sin(3x)}{9}+\frac{2cos(3x)}{27}}$$

![Pasted image 20241106211458.png](/img/user/media/Pasted%20image%2020241106211458.png)

---
### Example 2

Let's say we have another integral 

$$x^4.log(x)dx$$ or $x^4.ln(x)dx$

$ln(x)$ is the same as $log(x)$

So, we make the table, 

| Sign | D                | I                |
| ---- | ---------------- | ---------------- |
| +    | $ln(x)$          | $x^4$            |
| -    | $\frac{1}{x}$    | $\frac{x^5}{5}$  |
| +    | $-\frac{1}{x^2}$ | $\frac{x^6}{30}$ |

So here we see firstly, that columns of **D** and **I** keep going on with no near end in sight. And the product of their second row which results in $-\frac{x^4}{5}$ can be integrated.

So we stop at the second row itself, since the third row makes the math complicated.

And we make the diagonal products.

![Pasted image 20241106213018.png](/img/user/media/Pasted%20image%2020241106213018.png)

So the final answer would be : $$x^4.log(x)dx = \boxed{\frac{x^5.ln(x)}{5} - \int{\frac{x^4}{5}}}$$. **Yes, in such instances of a row being possible to integrate, we write it in the answer**.

Now we will have to solve the remaining integral to get the complete answer.

Thus we get the complete answer as : $$\int{x^4.log(x)dx} = \boxed{\frac{x^5.ln(x)}{5} - \frac{x^5}{25}}$$

---
### Example 3:

Let's say we have another integral, $$e^x.sin(x)dx$$

Remembering our rules, we differentiate $e^x$, since functions like $e^x$ are integrated as a last choice. And the remaining $sin(x)$ will be differentiated.

So , 


| Sign | D     | I         |
| ---- | ----- | --------- |
| +    | $e^x$ | $sin(x)$  |
| -    | $e^x$ | $-cos(x)$ |
| +    | $e^x$ | $-sin(x)$ |
In the third row we see that our original question has appeared.


![Pasted image 20241106213952.png](/img/user/media/Pasted%20image%2020241106213952.png)


So we stop the operations and write diagonal products first. 

$$\int{e^x.sin(x)dx} = \boxed{-e^{x}.cos(x) + e^{x}sin(x) - \int{e^x.sin(x)}}$$


or $$2\int{e^x.sin(x)dx} = e^{x}.[sin(x)-cos(x)]$$
or, $$\int{e^x.sin(x)dx} = \boxed{\frac{e^{x}.[sin(x)-cos(x)]}{2}}$$

---

## 3. Integration by partial fractions -- An easy method

https://www.youtube.com/watch?v=OFEfGtCsVKg&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=4&pp=gAQBiAQB

**This method can only be applied if the denominator can be factorized into linear factors**

or that in denominator power of $x$ is 1, or it is a product of terms in which power of $x$ is 1.

### Example 1

So let's say we have an integral : 

$$\int{\frac{(2x-1)}{(x-1)(x+2)(x-3)} dx}$$

We can see that it's denominator is in the form of a product of linear factors.

So the **way to tackle this**, is to **take one term at a time**.

We first select $(x-1)$.

Equate this term to `0`. We get $x = 1$.

Now we apply this value back in the original equation, but there's a twist.

We modify this part of the process by removing the selected term from denominator, but instead placing it in the form of a natural log (log or $ln$), and we don't substitute the value of $x$ in that log term.

1. So, for $(x-1)$

$$\frac{2(1) -1}{(1+2)(1-3)}.ln(x-1)$$

or $$\frac{-ln(x-1)}{6}$$
2. For $(x+2)$, we get $x = -2$

or $$\frac{2(-2) - 1}{(-2-1)(-2-3)}ln(x+2)$$

or $$\frac{-5.ln(x+2)}{15} = \frac{-ln(x+2)}{3}$$
3. For $(x-3)$, we get $x = 3$.

or $$\frac{2(3) - 1}{(3-1)(3+2)}.ln(x-3)$$
or $$\frac{5.ln(x-3)}{10} = \frac{ln(x-3)}{2}$$
Finally we put all the obtained terms together along with their signs.

$$\int{\frac{(2x-1)}{(x-1)(x+2)(x-3)} dx} = \boxed{\frac{-ln(x-1)}{6} + \frac{-ln(x+2)}{3} + \frac{ln(x-3)}{2}}$$

as our complete answer.

The given video link has another example on this.

---
# Evolutes and Involutes

## Evaluation of definite and improper integrals

### 1. Indefinite vs Definite Integrals

#### Indefinite Integral

Indefinite Integral (the integral we are used to by default)

$$
\int {f(x) \ dx} \ = \ F(x) \ + \ C
$$

- Reverse of differentiation
- Gives a function
- Always include $+ \ C$

---
#### Definite Integral

An integral which has defined specific upper and lower limits.

$$
\int_a^b{f(x) \ dx} \ = \ F(b) \ - \ F(a)
$$

- Gives a number
- No $+ \ C$ (constants cancel)
- Represents net area

---
### 2. Even and Odd Functions (Symmetry Rules)

#### Odd Function

$$
f(-x) \ = \ -f(x)
$$

Examples of such odd functions:

$x^3$, $x$, $\sin(x)$

$$
\int_{-a}^{a} {f(x) \ dx} \ = \ 0
$$

Reason: Areas cancel.

For dissimilar limits:

$$
\int_{-b}^{-a} {f(x) \ dx} \ = \ \int_{a}^{b} {f(x) \ dx}
$$


---
#### Even Function

$$
f(-x) \ = \ f(x)
$$

Examples: $x^2$, $\cos(x)$.

$$
\int_{-a}^{a} {f(x) \ dx} \ = \ 2 \int_{0}^{a} {f(x) \ dx}
$$

Reason: Graph is symmetric about y-axis.

For dissimilar limits:

$$
\int_{-b}^{-a} {f(x) \ dx} \ = \ - \int_{a}^{b} {f(x) \ dx}
$$

---
### 3. Improper Integrals

An improper integral is ==a definite integral that extends the concept of integration to cases where the interval of integration is unbounded (infinite) or the integrand has an infinite discontinuity==.

![Pasted image 20260301124006.png](/img/user/media/Pasted%20image%2020260301124006.png)

---
#### The Case of Infinity

For:

$$
\int_{1}^{\infty} {\frac{1}{x^p} \ dx}
$$

or

$$
\int_{1}^{\infty} {x^{-p} \ dx}
$$

The integral:

- **Converges** if $p \ > \ 1$
- **Diverges** if $p \leq \ 1$

Key idea:  If $p \ > \ 1$ then the integral shrinks, but shrinks slowly, enough so that it can be 
integrated. If $p \ \leq\ 1$, then the integral shrinks too fast to be integrated.

Powers even as close to 1 as:

$$
\int_{1}^{\infty} {\frac{1}{x^{1.0001}} \ dx}
$$

will converge, because that tiny extra power makes the function shrink _just fast enough_.

However the moment $p \ = \ 1$, the function will diverge.


Example:

**Exhibit A**:

$$
\int_{1}^{\infty} {\frac{1}{x^2} \ dx} \ = \ 1
$$

**Exhibit B**:

$$
\int_{1}^{\infty} {\frac{1}{x} \ dx} \ = \ \infty
$$


---
#### Near-Zero Case

For:

$$
\int_{0}^{1} {\frac{1}{x^p} \ dx}
$$

or

$$
\int_{0}^{1} {x^{-p} \ dx}
$$

The integral:

- **Converges** if $p \ < \ 1$
- **Diverges** if $p \geq \ 1$

Key idea:  If $p \ < \ 1$ then the integral blows up, but blows up slowly, enough so that it can be 
integrated. If $p \ \geq \ 1$, then the integral blows up too fast to be integrated.

Powers even as close as $0.99$, will converge, but the moment $p \ = \ 1$, the function will diverge.

The boundary is sharp.

Example:

**Exhibit A**:

$$
\int_{0}^{1} {\frac{1}{x^{\frac{1}{2}}} \ dx} \ = \ 2
$$

or:

$$
\int_{0}^{1} {\frac{1}{\sqrt{x}} \ dx} \ = \ 2
$$


or:

$$
\int_{0}^{1} {{x^{-\frac{1}{2}}} \ dx} \ = \ 2
$$

**Exhibit B**:


$$
\int_{0}^{1} {\frac{1}{x} \ dx} \ = \ \infty
$$


---
### 5. Why Conditions Flip

| Location      | Condition for Convergence |
| ------------- | ------------------------- |
| Near $\infty$ | ( $p \ > \ 1$ )           |
| Near $0$      | ( $p \ < \ 1$ )           |

At $\infty$ → concerned about shrinking  
At $0$ → concerned about explosion

![Pasted image 20260301135847.png](/img/user/media/Pasted%20image%2020260301135847.png)

---
## Practice examples for the evaluation of definite and improper integrals.

### 1. Even and Odd Functions

#### (A)

$$
\int_5^5{x^5 \ dx}
$$

$$
= 0
$$

Since $x^5$ is odd.

---
#### (B)

$$
\int_{-4}^{4} {x^4 \ dx}
$$

$$
= \ 2 \int_{0}^{4} \ {x^4 \ dx}
$$

$$
= \ 2 [\frac{x^5}{5}]^4_0
$$

$$
= \ 2 \ {(\frac{4^5}{5} \ - \ \frac{0^5}{5})}
$$

$$
= \ 2 \ (\frac{1024}{5} \ - \ 0)
$$

$$
= \ \frac{2048}{5}
$$

---
#### (C) 

$$
\int_{-\pi}^{\pi} {(x^3 \ +  \ x^2) \ dx}
$$

$$
= \ \int_{-\pi}^{\pi} {x^3 \ dx} \ + \ \int_{-\pi}^{\pi} {x^2} \ dx
$$

$$
= 0 \ + \ \int_{-\pi}^{\pi} {x^2 \ dx}
$$

$$
= 2 \int_{0}^{\pi} {x^2 \ dx}
$$

$$
= \ 2 [\frac{x^3}{3}]_{0}^{\pi}
$$

$$
= \ 2 [\frac{\pi^3}{3} \ - \ \frac{0}{3}]
$$

$$
= \frac{2 \pi^3}{3}
$$

---
### 2. Improper Integrals -- The Case of Infinity

#### (A)

$$
\int_{1}^{\infty} {\frac{1}{x^3} \ dx}
$$


Here: $p \ = \ 3 \ > \ 1$.

So the function will converge.

$$
= \ \int_{1}^{\infty} { x^{-3} \ dx}
$$


$$
= \ [\frac{x^{-2}}{-2}]_1^{\infty}
$$

$$
= \ [0 \ - \ (- \frac{1^{-2}}{2})]
$$

$$
= [0 \ + \ \frac{1}{2}]
$$

$$
= \ \frac{1}{2}
$$

---
#### (B)

$$
\int_{1}^{\infty} {\frac{1}{\sqrt{x}} \ dx}
$$

Since $p \ = \ \frac{1}{2} \ = \ 0.5 \ < \ 1$,

The function diverges.

The value is:

$$
\int_{1}^{\infty} {\frac{1}{\sqrt{x}} \ dx} \ = \ \infty
$$

---
#### (C)

$$
\int_{1}^{\infty} {\frac{1}{x^{1.2}} \ dx}
$$

Since $p \ = \ 1.2 \ > \ 1$,

The function converges.

$$
= \ \int_{1}^{\infty} {x^{-1.2} \ dx}
$$

$$
= \ [\frac{x^{-0.2}}{-0.2}]_1^{\infty}
$$

$$
= \ [0 \ - \ (-\frac{1^{-0.2}}{0.2})]
$$

$$
= \ [0 \ + \ (\frac{1}{0.2})]
$$

$$
= \ 5
$$

---
### 3. Improper Integrals -- Near Zero

#### (A)

$$
\int_0^1{\frac{1}{x^{0.7}} \ dx}
$$

Here, 

$p \ = \ 0.7 \ < \ 1$, so the function will converge.

$$
= \ \int_0^1{x^{-0.7} \ dx}
$$

$$
= \ [\frac{x^{-1.7}}{-1.7}]_0^1
$$

$$
= \ [- \ \frac{1^{-1.7}}{1.7} \ + \ 0]
$$

$$
= \ - \frac{1}{1.7}
$$

---
#### (B)

$$
\int_0^1{\frac{1}{x^2} \ dx}
$$

Here, $p \ = \ 2 \ > \ 1$, so the function will diverge.

Value:

$$
\int_0^1{\frac{1}{x^2} \ dx} \ = \ \infty
$$


---
#### (C) 

$$
\int_0^1{\frac{1}{x^{0.99}} \ dx}
$$

Since $p \ = \ 0.99 \ < \ 1$, the function will converge.

I am not going to solve this one, since the concept is already clear at this point.

---
# Applications of definite integrals to evaluate surface areas and volumes of revolutions

Before we proceed, let's sum up definite integrals in one master algorithm

## DEFINITE INTEGRALS — MASTER ALGORITHM

We separate everything into three layers:

1. Orientation
2. Symmetry (Parity)
3. Sign / Area Type

---
### PART 1 — ORIENTATION RULE (Always Check First)

### Rule:

$$
\int_{-b}^{-a} {f(x) \ dx} \ = \ - \int_{a}^{b} {f(x) \ dx}
$$

or

$$
\int_{b}^{a} {f(x) \ dx} \ = \ - \int_{a}^{b} {f(x) \ dx}
$$

(limits were swapped manually here).

### When to use:

- Whenever limits appear reversed.
- Whenever you swap limits manually.

### When NOT to use:

- If limits are already in increasing order.

This has nothing to do with symmetry or sign.  
It is purely about direction.

---
### PART 2 — SYMMETRY / PARITY RULE (Only When 0 is Structurally Present, i.e present among the limits)

Is interval symmetric around 0?  
If yes → use parity.  
If no → ignore parity.

or,

**Trigger condition**:

- Interval is $[-a, a]$, or
- You are converting $[-b, \ -a]$ to $[a, \ b]$


#### Odd Function

$$
f(-x) \ = \ -f(x)
$$

Examples of such odd functions:

$x^3$, $x$, $\sin(x)$

$$
\int_{-a}^{a} {f(x) \ dx} \ = \ 0
$$

#### Even Function

$$
f(-x) \ = \ f(x)
$$

Examples: $x^2$, $\cos(x)$.

$$
\int_{-a}^{a} {f(x) \ dx} \ = \ 2 \int_{0}^{a} {f(x) \ dx}
$$

---
###  PART 3 — SIGN ANALYSIS (Determines Area Sign)

This determines whether the integral is:

- Positive
- Negative    
- Zero


### Ask:

Is function positive, negative, or changing sign?

This determines:

- Net area sign
- Whether splitting is needed
- Whether absolute value is needed

This is done is as follows:

Suppose we have three range brackets (or zeroes):

Let's say from $-2$ to $2$.

And we get the zeroes as:

$$
[-2, -1],\ [-1, 1], \ [1, 2] 
$$


The rule to test whether the function $f(x)$ is positive or negative between each bracket, is:

- **Always check with values between the ends of the bracket.**

In the case of zeroes where you cannot find any middle value, you can use either end, like for example $-2$ in $[-2, -1]$ or $2$ in $[1, 2]$.

However in the case of the bracket of $[-1, 1]$, we can find a middle value, which is $0$.

So, we can test if the function $f(x)$ is positive or negative at $x \ = \ 0$, which will tell us whether the function is positive or negative in $[-1, 1]$.

---
# Area under Curves

Are we asked for:

- Net area? → use integral normally.
- Total/geometric area? → integrate absolute value.

### 1. Net Area (Standard Definite Integral)

$$
\int_a^b{f(x) \ dx}
$$

This calculates:

Signed area.

- Area above x-axis → positive.
- Area below x-axis → negative.
- Opposite sides cancel.

Odd symmetry cancellation happens here.

---
### 2. Geometric Area (Total Area)

$$
\int_a^b{ |f(x)| \ dx}
$$

This calculates:

Total physical area.

Everything becomes positive.

No cancellation.

---
## 🔵 When To Split the Integral

Split when:

- The function changes sign in the interval.
- You are calculating geometric area.
- The interval crosses 0 and you want symmetry benefits.

Example:

$$
\int_{-5}^{2} {f(x) \ dx} \ = \ \int_{-5}^{0} {f(x) \ dx} \ + \ \int_{0}^{2} {f(x) \ dx}
$$

---
## Quick Summary Table

| Situation                   | Tool               |
| --------------------------- | ------------------ |
| Limits reversed             | Orientation rule   |
| Interval symmetric around 0 | Parity             |
| Interval ordinary           | Sign analysis only |
| Asking total area           | Use absolute value |
| Function crosses x-axis     | Split integral     |


---

## Example

Let's say we have:

$$
\int_{-3}^{3} {x^2 \ dx}
$$

We have to find the:

- Net Area
- Geometric Area

### For Net Area

The limits go from -3 to 3, so the integral has to be split:

$$
= \ \int_{-3}^{0} {x^2 \ dx} \ + \ \int_{0}^{3} { x^2 \ dx}
$$

Now we solve:

$$
= [\frac{x^3}{3}]_{-3}^{0} \ + \ [\frac{x^3}{3}]_0^{3}
$$

$$
= \ [0 \ + \ \frac{27}{3}] \ + \ [\frac{27}{3} \ - \ 0]
$$

$$
= \ 18
$$

This could also have been directly solved by just:

$$
\int_{-3}^{3} {x^2 \ dx} \ = \ 2 \int_0^{3} {x^2} \ dx
$$

$$
= \ 2 \ \times \ [\frac{x^3}{3}]_0^{3}
$$

$$
= \ 2 \ \times \ \frac{27}{3}
$$

$$
= \ 2 \ \times \ 9 \ = \ 18
$$

### For Geometric Area

For the integrand, 

$$
x^2
$$

Set  $x^2 \  = \ 0$

Thus $x^2 \ = \ 0$.

$x \ = \ 0$.

So we going from $-3$ to $3$, we get three range brackets:

$$
[-3, \ 0], \ [0,\ 0], \ [0, \ 3]
$$


The function would be: $x^2 \ = \ 0$

So,  for any $x \ \neq \ 0$, $x^2 \ > \ 0$

For the first bracket, $x^2 \ = \ 9$
For the second bracket, $x^2 \ = \ 0$
For the third bracket: $x^2 \ = \ 0$

So the function is positive for all three range brackets

So the geometric area would be:

$$
= \ \int_{-3}^{0} {x^2 \ dx} \ + \ \int_{0}^{3} { x^2 \ dx}
$$


We can technically ignore the middle bracket of $[0,0]$ since the end output would be just zero. Adding or subtracting that won't make any difference.

Solving these integrals,

$$
= \ [0 \ + \ \frac{27}{3}] \ + \ [\frac{27}{3} \ - \ 0]
$$

$$
= \ 18
$$


Thus, the net and geometric area are the same.

---
## Practice Problems

### 1. Find net and geometric area of

$$
\int_{-2}^{2} {x^3} dx
$$

Net area = $0$.

For geometric area, 

Setting, $x^3 \ = \ 0$,  $x \ = \ 0$.

Then we split the integral:

$$
[-2, 0], \ [0, 0],  \  [0, 2]
$$


At:

- $x \ = \ -2$, $x^3 \ = \ -8$, $[-2, \ 0]$
- $x \ = \ 0$, $x^3 \ = \ 0$, $[0, \ 0]$
- $x \ = \ 0, \ x^3 \ = \ 0$., $[0, 2]$


So, the function is negative between $[-2, 0]$ and positive for $[0,2]$

So, the geometric area:

$$
- \int_{-2}^{0} {x^3} dx \ + \ \int_{0}^{2} {x^3} dx 
$$

$$
= \ - [\frac{x^4}{4}]^{0}_{-2} \ + \ [\frac{x^4}{4}]_0^2 
$$

$$
= \ - \ [0 \ - \ 4] \ + \ [4 \ - \ 0]
$$

$$
= \ 4 \ + \ 4
$$

$$
= \ 8
$$


---
### 2. Find the net and geometric area of

$$
\int_{-2}^{2} {(x^2 \ - \ 1)} \ dx
$$

First, we split the integral:

$$
\int_{-2}^{2} {x^2 \ dx} \ - \ \int_{-2}^{2} {1 \ dx} 
$$

Both are even functions, so by rule of parity:

$$
= \ 2 \int_{0}^{2} \ {x^2 \ dx} \ - \ 2 \int_{0}^{2} {dx}
$$

$$
= \ 2 \ [\frac{x^3}{3}]_0^2 \ - \ 2 [x]_0^2
$$

$$
= \ 2 \ [\frac{8}{3}] \ - \ 4
$$

$$
= \ \frac{16}{3} \ - \ \frac{4}{1}
$$

$$
= \ \frac{16 \ - \ 12}{3}
$$

$$
= \ \frac{4}{3}
$$



Now, for the geometric area:

The limits go from $-2$ to $2$.

Now, setting $x^2 \ - \ 1 \ = \ 0$,

$x \ = \ \pm 1$.

So the zeroes are:

$$
[-2, -1],\ [-1, 1], \ [1, 2] 
$$

At:

- $x \ = \ -2$, $x^2 \ - \ 1 \ = \ 3$
- $x \ = \ 0$, $x^2 \ - \ 1 \ = \ -1$
- $x \ = \ 1$, $x^2 \ - \ 1 \ = \ 0$

So the function is positive for the range brackets of $[-2, -1], \ [1, 2]$, but negative for $[-1, 1],$

Now, we will split the integral accordingly:

$$
= \int_{-2}^{-1} {(x^2 \ - \ 1)} \ dx \ - \ \int_{-1}^{1} {(x^2 \ - \ 1)} \ dx \ + \ \int_{1}^{2} {(x^2 \ - \ 1)} \ dx
$$

$$
= (\int_{-2}^{-1} {x^2 \ dx} \ - \ \int_{-2}^{-1} {dx} )\ - \ (\int_{-1}^{1} {x^2 \ dx} \ - \ \int_{-1}^{1} {dx}) \ + \ (\int_{1}^{2} {x^2 \ dx} \ - \ \int_{1}^{2} {dx})  
$$

$$
= \int_{-2}^{-1} {x^2 \ dx} \ - \ \int_{-2}^{-1} {dx} \ - \ 2 \int_{0}^{1} {x^2 \ dx} \ + \ 2 \int_{0}^{1} {dx} \ + \ \int_{1}^{2} {x^2 \ dx} \ - \ \int_{1}^{2} {dx}  
$$

$$
= [\frac{x^3}{3}]_{-2}^{-1} \ - \ [x]_{-2}^{-1} \ - \ 2[\frac{x^3}{3}]_{0}^{1} \ + \ 2[x]_{0}^{1} \ + \ [\frac{x^3}{3}]_{1}^{2} \ - \ [x]_{1}^{2}
$$

$$
= \ [-\frac{1}{3} \ + \ \frac{8}{3}] \ - \ [-1 \ + \ 2] \ - \ 2[\frac{1}{3} \ - \ 0] \ + \ 2[1 \ - \ 0] \ + \ [\frac{8}{3} \ - \ \frac{1}{3}] \ - \ [2 \ - \ 1]
$$

$$
= \ \frac{7}{3} \ - \ 1 \ - \ \frac{2}{3} \ + \ 2 \ + \ \frac{7}{3} \ - \ 1
$$

$$
= \ \frac{12}{3} \ - \ 2 \ + \ 2
$$

$$
= \ \frac{12}{3}
$$

$$
= \ 4
$$

---
# Volumes of Revolution

This is where definite integrals stop being just “area under a curve” and start becoming **3D geometry**.

We revolve a curve around an axis → it sweeps out a solid → we compute its volume using integration.

There are **two primary methods** you must master:

1. Disk / Washer Method
2. Shell Method

## 1. Disk Method (When there is no hollow region)

### Situation:

You rotate a curve around an axis and it creates a **solid disk** (like stacking coins).

If a function  $y \ = \ f(x)$, is rotated about the **x-axis** then, 

![Pasted image 20260303134857.png](/img/user/media/Pasted%20image%2020260303134857.png)

$$
V \ = \ \pi \int_{a}^{b} {[f(x)]^2 \ dx}
$$

**Why is function squared?**

Because:

- At each x, the radius = $f(x)$
- Area of circular cross-section = $\pi r^2$.

So, a small volume element will equal:

$$
dV \ = \ \pi[f(x)]^2 \ dx
$$

Then we can integrate it to find the volume.

### Example 1.

Find volume formed by rotating:

$$
y \ = \ x
$$

from $x \ = \ 0$ to $x \ = \ 2$ about the $x$-axis.

#### Step 1: Find radius.

At each $x$, the radius is $f(x)$ which is $y \ = \ x$. (just $x$).

#### Step 2: Apply formula:

$$
V \ = \ \pi \int_{0}^{2} {x^2} \ dx
$$

$$
= \ \pi \ \times \ [\frac{x^3}{3}]_0^2 
$$

$$
= \ \pi \ \times \ [\frac{8}{3} \ - \  0] 
$$

$$
\implies \ V \ = \ \frac{8\pi}{3}
$$

---
## 2. Washer Method (When there is a hollow region)

Now suppose you rotate the region between two curves:

$$
y \ = \ f(x)
$$

and

$$
y \ = \ g(x)
$$

with $f(x) \ > \ g(x)$.

You get a hollow solid, like a washer.

![Pasted image 20260303140828.png](/img/user/media/Pasted%20image%2020260303140828.png)


The formula for the volume is:

$$
V \ = \ \pi \ \int_{a}^{b} {([R(x)]^2 \ - \ [r(x)]^2) \ dx}
$$

where:

- $R(x)$ = outer radius
- $r(x)$ = inner radius


## WASHER METHOD — PURE ALGORITHM

We assume:

- Region between two curves
- Rotated about a horizontal or vertical line

---
### STEP 1 — Identify Axis of Rotation

Is it:

- y = 0 (x-axis)?
- x = 0 (y-axis)?
- y = k ?
- x = k ?

Write it down clearly.

Everything depends on this.

---
###  STEP 2 — Decide Variable of Integration

If axis is horizontal (like y = something):

→ Use vertical slices  
→ Integrate with respect to dx

If axis is vertical (like x = something):

→ Use horizontal slices  
→ Integrate with respect to dy

(Exam shortcut: washers use slices perpendicular to axis.)

![Pasted image 20260304034214.png](/img/user/media/Pasted%20image%2020260304034214.png)


---
### STEP 3 — Identify Outer and Inner Radius

Radius = distance from axis.

Always compute distance using:

$$
\text{Distance} \ = \ |\text{axis} \ - \ \text{curve} |
$$


Then:

- Outer radius = farther curve from axis
- Inner radius = closer curve to axis

Do NOT think “which function is bigger.”

Think “which is farther from axis.”

---
### STEP 4 -- Apply Washer Formula

$$
V \ = \ \pi \ \int{(R^2 - r^2)}
$$

Where:

- R = outer radius
- r = inner radius

---
# Gamma Functions

## What is it?

The Gamma function is an extension of the factorial to all real numbers, including fractions.

Formally defined as:


$$
Γ(n) \ = \ \int_{0}^{\infty} e^{−t} \ \cdot \  t^{n \ - \ 1} \ dt
$$



- The $e^{-t}$ term forces convergence despite the infinite upper limit — it kills the function fast enough as $t \ \rightarrow \ \infty$

- Defined for all n > 0

---
## The Reduction Formula

$$
Γ(n \ + \ 1) \ = \ n \ \cdot \ Γ(n)  
$$

This is the core property. Every Gamma value connects to the previous one by simple multiplication — same unwinding pattern as a factorial.

$$
Γ(n \ + \ 1) \ = \ n! 
$$

So Gamma is the factorial function, shifted by 1:

- Γ(5) = 4! = 24
- Γ(6) = 5! = 120

> ⚠️ Watch the shift — Γ(5) = 4!, not 5!

---
## Base Values

$$
Γ(1) \ = \ 1 
$$


$$
Γ(\frac{1}{2}) \ = \ \sqrt{\pi} 
$$

---
## Half-Integer Values

Derived using the reduction formula starting from $Γ(\frac{1}{2}) \ = \ \sqrt{\pi}$ .

| n                | $Γ(n)$                   |
| ---------------- | ------------------------ |
| $Γ(\frac{1}{2})$ | $\sqrt{\pi}$             |
| $Γ(\frac{3}{2})$ | $\frac{\sqrt{\pi}}{2}$   |
| $Γ(\frac{5}{2})$ | $\frac{3\sqrt{\pi}}{4}$  |
| $Γ(\frac{7}{2})$ | $\frac{15\sqrt{\pi}}{8}$ |


**Pattern:**

- Numerator: 1, 1, 3, 15 → each multiplies by the next odd number
- Denominator: 1, 2, 4, 8 → powers of 2

> 💡 If you blank in the exam, just re-derive on the spot using the reduction formula. Takes 20 seconds.

---
# Beta Functions

## What is it?

A function of **two** inputs that measures a weighted interaction between two exponents.

$$
B(m, n) \ = \ \int_{0}^{1} {(x^{m \ - \ 1}) \ \cdot \ (1 \ - \ x)^{n \ - \ 1} \ dx}
$$

- Limits are **0 to 1** (unlike Gamma which goes 0 to ∞)
- Two parameters m and n

---
## Key Properties

**Symmetry:**

$$
B(m, n) \ = \ B(n, m)
$$

Bridge Formula:

$$
B(m, n) \ = \ \frac{Γ(m) \ \cdot \ Γ(n)}{Γ(m \ + \ n)}
$$

This connects Beta back to Gamma. Almost every exam question uses this.

> ⚠️ Denominator is Γ(m+n) — add the arguments FIRST, then take Gamma. Not Γ(m) + Γ(n).

---
## Trigonometric Form

$$
B(m, n) \ = \ 2 \int_{0}^{\frac{\pi}{2}} {\sin^{2m \ - \ 1}\theta \ \cdot \ \cos^{2n \ - \ 1}\theta \ d \theta}
$$

Which means:

$$
\int_{0}^{\frac{\pi}{2}} {\sin^{p}\theta \ \cdot \ \cos^{q}\theta \ d \theta} \ = \ \frac{B(\frac{p+1}{2}, \frac{q+1}{2})}{2}
$$

$$
\int_{0}^{\frac{\pi}{2}} {\sin^{p}\theta \ \cdot \ \cos^{q}\theta \ d \theta} \ = \ \frac{B(m, n)}{2}
$$

since:

- $\frac{p+1}{2} \ = \ m$
- $\frac{q+1}{2} \ = \ n$


---
## Algorithm for Trig Integrals

1. Read off **p** and **q** from the powers of sin and cos
2. Compute **m = (p+1)/2** and **n = (q+1)/2**
3. Extend the half-integer Gamma table as far as needed using Γ(n+1) = n·Γ(n)
4. Plug into bridge formula
5. Let **√π cancel** — keep everything as pure fractions, never decimals
6. Simplify fraction to final answer

---
## Worked Example

$$
\int_{0}^{\frac{\pi}{2}} {\sin^{5}\theta \ \cdot \ \cos^{4}\theta \ d \theta}
$$

- p = 5, q = 4
- m = $\frac{5+1}{2} \ = \ 3$, n = $\frac{4 \ + \ 1}{2} \ = \ \frac{5}{2}$
- Γ(3) = $2! \ = \ 2$
- Γ(5/2) = $\frac{3 \pi}{4}$
- Γ(11/2) = 9/2 · Γ(9/2) = 9/2 · $\frac{105\pi}{16}$ = $\frac{945 \pi}{32}$

$$
= \frac{2 \ \times \ \frac{3\pi}{4}}{2 \ \times \ \frac{945 \pi}{32}}
$$

$$
= \ \frac{\frac{3\pi}{4}}{\frac{945 \pi}{32}}
$$

$$
= \frac{3\pi \ \times \ 32}{4 \ \times \ 945 \ \pi}
$$

$$
= \ \frac{3 \ \times \ 8}{945}
$$

$$
= \ \frac{24}{945}
$$

$$
= \ \frac{8}{315}
$$


---
