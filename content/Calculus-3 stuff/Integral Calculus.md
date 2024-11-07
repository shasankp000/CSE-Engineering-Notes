---
title: Integral Calculus -- Mathematics III
tags:
  - Semester-3
---

https://www.youtube.com/playlist?list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy (Full playlist link)
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
## College Stuff (Calculus -3)
   
8. [[#Double Integrals]]
9. [[#Changing of order of integration]]
10. [[#What is changing of order of integration?]]
11. [[#When can you NOT change the order of integration.]]
12. [[#Triple Integrals]]
13. [[#Change of variables (Cartesian to Polar)]]
14. [[#When to change from cartesian to polar variables?]]
15. [[#The Jacobian determinant.]]
16. [[#How to calculate the determinant of a 2x2 matrix?]]
17. [[#How to calculate the determinant of a 3x3 matrix?]]
18. [[#Back to conversion of Cartesian to Polar co-ordinates]]
19. [[#Green's Theorem (Statement only)]]

---

# Integral Calculus Recap

## **A problem well defined, is a problem half solved -- Charles Kettering**

https://www.youtube.com/watch?v=hXOrQ0Ao4UE&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=1&pp=gAQBiAQB

The above link points to a full comprehensive recap of class 12 recap. Watch it only if you have time.

---
## Basic Integral Formulae

![[WhatsApp Image 2024-11-06 at 11.09.36_8ab79753.jpg]]

![[WhatsApp Image 2024-11-06 at 11.09.36_a529dee3.jpg]]

---
## Some basic trigonometric identities

https://www.youtube.com/watch?app=desktop&v=m1OitPmkydY

![[Pasted image 20241106111131.png]]

https://www.geeksforgeeks.org/trigonometric-identities/

![[Trigonometry-Identities.webp]]


https://www.geeksforgeeks.org/trigonometry-table/

![[Trogonometry-2.png]]

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

![[Pasted image 20241106211308.png]]

Like this.

So the final answer becomes, 

$$\int{x^2.sin(3x)dx} = \boxed{\frac{-x^{2}.cos(3x)}{3}+\frac{2sin(3x)}{9}+\frac{2cos(3x)}{27}}$$

![[Pasted image 20241106211458.png]]

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

![[Pasted image 20241106213018.png]]

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


![[Pasted image 20241106213952.png]]


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
# Double Integrals

https://www.youtube.com/watch?v=BJ_0FURo9RE&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=5

## Example 1

Let's say we have an integral here, $$\int_{0}^{2}\int_{1}^{3}{xy^2}dydx$$
In double (or triple integrals), **the order of integration matters**. Whether you want to integrate in terms of $y$ or $x$ or $z$ (triple integrals) first, that depends on you.

So here we follow which variable is given first. The first variable is $dy$.

So we integrate with respect to $y$ first.

$$\therefore \int_{0}^{2}x[\frac{y^3}{3}]_{1}^{3}dx$$

or $$\int_{0}^{2}x. [\frac{3^3}{3} - \frac{1^3}{3}]dx$$
or, $$\int_{0}^{2}\frac{2x}{3}. dx$$
or $$\frac{2}{3}.\int_{0}^{2}xdx$$
or, $$\frac{2}{3}.[\frac{x^2}{2}]_{0}^{2}$$
or $$\frac{2}{3}.\frac{4}{2}$$
Thus finally, $$\int_{0}^{2}\int_{1}^{3}{xy^2}dydx = \boxed{\frac{4}{3}}$$

---
## Example 2

![[Pasted image 20241106222205.png]]

So we have this integral right here, 

$$\int\int_R[2y - 3x^2y^2]dA$$

where $R = \{(x,y) | 0 \leq x \leq 1, 0 \leq y \leq 2\}$

So we need to find the upper and lower limits of $x$ and $y$.

Following the given set, we see that $x$ lies between $0$ and $1$.

And $y$ lies between $0$ and $2$.

Therefore the integral becomes, $$\int_{0}^{1}\int_{0}^{2}[2y - 3x^2y^2]dxdy$$
While applying the limits **we follow the order of the variables in the given set**, which in this case, $x$ comes first, followed by $y$

Now it's business as usual. We can solve the integral in the same way we did before.

![[Pasted image 20241106222704.png]]

![[Pasted image 20241106222735.png]]

Yeah, I decided to save a bit of time on this one by taking screenshots. Typing and rendering the equations properly is a really time consuming process.

---
## Changing of order of integration

Sometimes we cannot integrate the given question in the given order of variables as it is.

### What is changing of order of integration?

Suppose we have an integral, 

$$\int_{c}^{d}\int_{a}^{b} f(x) dxdy$$

**To change the order of integration, we need to swap both the dx and dy AND their respective limits**.

So after changing of order of integration, the new integral would appear as:

$$\int_{a}^{b}\int_{c}^{d} f(x) dydx$$

Notice that the **limits  of x and y have swapped respectively when the variables did**.

You **cannot** swap just the variables and keep their limits as they were. This will invalidate the logic of the equation, which will be explained further down the line.

### Why do we change the order in integration?

- Sometimes it's easier to evaluate a double integral by changing the order of integration, especially when the region $R$ is more naturally described in one order than another.
- The process involves identifying the new limits of integration for the variables after switching the order.

---
### When can you NOT change the order of integration.

Suppose we have an integral :


![[Pasted image 20241106222851.png]]

In this question, we see that the limits of $x$ has $y$ entangled in it.

So we if we tried to, let's say write the integral as $$\int_{0}^{2y}\int_{0}^{1}[4+2x - y^2]dydx$$
**This won't work here**.

Since ==the limits of $x$ are interdependent on $y$==. So we need to evaluate $x$ first , apply the limits which contain $y$. Then integrate in terms of $y$.

A better explanation would be :

In the original equation **x relies on the changing value of y, so x is not static**. 

In this equation, where the order is changed $$\int_{0}^{2y}\int_{0}^{1}[4+2x - y^2]dydx$$
**y ranges from 0 to 1 for each fixed x, while x ranges from 0 to 2y**.

This completely changes the region over which the integral expands.


So, in these type of integrals we need to solve the interdependent limits first.

$$\therefore \int_0^1 [4x+x^2-y^2.x]_{0}^{2y} dy$$

or 

$$\int_0^1 [4(2y)+4y^2 - 2y^3]dy$$

or 

$$8\int_0^1 ydy + 4\int_0^1y^2dy - 2\int_0^1y^3dy$$


or 

$$8[\frac{y^2}{2}]_0^1 + 4[\frac{y^3}{3}]_0^1 - 2[\frac{y^4}{4}]_0^1$$


or 

$$4 + \frac{4}{3} - \frac{1}{2}$$


or 

$$\frac{29}{6}$$


---
### Or if you are indeed keen on changing the order here.

So we have our original equation as: 

![[Pasted image 20241106222851.png]]


To change the order of integration, we need to analyze the interdependent limits.


$$x = 2y$$

$$\therefore y = \frac{x}{2}$$
So y's new limits will be from 0 to $\frac{x}{2}$

And thus now y will be dependent on a changing $x$ as it goes from $0$ to $2$. Why $2$ you ask?

Well, you ding-dong, since originally,  $x = 2y$, $x$ **is the double of any value of y**.

So it naturally makes sense that when **y** depends on a changing **x**, the value of **x** will be double of whatever $y$'s value is. Originally $y$ ranged from 0 to 1, so now double that, the new range will be $0$ to $2$.

And so the new integral will be :

$$\int_{0}^{2}\int_{0}^{\frac{x}{2}}[4+2x - y^2]dy\,dx$$

Now you can go ahead and solve the integral.

---
## To sum it all up.

When **changing the order of integration** we can shift the limits as well, **if they are not inter-dependent on each other**.

Otherwise to shift the limits as well, **their appropriate new limits need to be calculated to keep the region the integral covers, the same**.

---
# Triple Integrals

Welcome to the world of 3-D regions where you often pull out your hair trying to figure out the triple integrals!

## Example 1

Here's the referenced video link: https://www.youtube.com/watch?v=7iy83x8bv6o&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=6

![[Pasted image 20241107114451.png]]

So we have this scary looking monster right here.

Well don't worry, I got the knight right here to defeat this monster!


So we have this region of limits **B** as $\{ (x,y,z) | 0 \leq x \leq 2, -2 \leq y \leq 3, 0 \leq z \leq 1 \}$

So this says that the limits of **x** ranges from `0` to `2`.
the limits of $y$ ranges from `-2` to `3`.
the limits of $z$ ranges from `0` to `1`.

So now we can re-write the integral as 

$$\int_{0}^{1} \int_{-2}^{3} \int_{0}^{2}[x^3.y.z^2]dx\,dy\,dz$$

As **previously stated before**, we **follow the order of variables when placing the limits in questions like these, from a set**.

Now since this is a simple integral with no-interdependent limits, there is no point in changing the order of integration.

We solve the integral as it is.

$$\int_{0}^{1} \int_{-2}^{3} yz^2[\frac{x^4}{4}]_0^2 dy\,dz$$
or $$\int_{0}^{1} \int_{-2}^{3} \frac{yz^2.16}{4}dy\,dz$$


or $$4\int_{0}^{1} z^2[\frac{y^2}{2}]_{-2}^{3} dz$$

or $$4\int_{0}^{1} z^2 [\frac{9}{2} - 2]dz$$

or $$4\int_{0}^{1} z^2 \frac{5}{2}dz$$

or $$10[\frac{z^3}{3}]_0^1$$

or $$10 .\frac{1}{3} = \frac{10}{3}$$


---
## Example 2

This time we have a relatively simpler looking question 

![[Pasted image 20241107122459.png]]

As we see, **this integral has interdependent limits**. So it's best we solve them in the given specific order to get rid of the dependencies first.

So we start with the integration with respect to $z$.

$$\therefore \int_0^3 \int_0^x 4xy[z]_0^{x-y}dy \, dx$$

or 
$$\int_0^3 \int_0^x 4xy(x-y) dy \, dx$$


or 

$$\int_0^3 \int_0^x [4x^2y-4xy^2]dy\,dx$$
or 

$$\int_0^3 4x^2[\frac{y^2}{2}]_0^x dx - \int_0^3 4x.[\frac{y^3}{3}]_0^xdx$$
or 

$$2\int_0^3 x^4dx - \frac{4}{3}\int_0^3 x^4dx$$
or 

$$2[\frac{x^5}{5}]_0^3 - \frac{4}{3}[\frac{x^5}{5}]_0^3$$
or 

$$2.\frac{243}{5} - \frac{4}{3}.\frac{243}{5}$$


or 

$$\frac{243}{5}.[2 - \frac{4}{3}]$$


or 

$$\frac{243}{5} . \frac{2}{3} = \frac{81}{5}.2$$


or 

$$\frac{162}{5}$$

---
# Change of variables (Cartesian to Polar)

First of all, you might be thinking, **what are cartesian and polar variables**?

## 1. Cartesian variables

The cartesian co-ordinate system was introduced by **René Descartes** , a French (oui baguette) mathematician back in 1637.

This is basically the system where we work with **two axes**, the **x** and **y** axes, with numerical points on them to plot various figures.

![[Pasted image 20241107213201.png]]


Yeah, this.

Normally we represent various diagrams on this plane using **variables** like **x, y, z ....** which are known as **cartesian variables**.

## 2. Polar variables/Polar co-ordinates

Now the Cartesian system handles 2D objects very nicely, but when dealing with 3D objects, specifically cylinders, spheres, etc, **we need a third dimension to work with, which often x, y and z don't make it easy to deal with**. Thus, we need the polar coordinate system here. It was developed by Big Daddy Newton (Sir Isaac Newton).


The polar co-ordinate system has variables like **r**, $\theta$  (pronounced as **theta**) and sometimes $\phi$ (pronounced as **phi**).


Why the name polar?

![[Pasted image 20241107213238.png]]


So yeah most of the type of integrations you can expect on this system are either spheres, or cylinders. At least from Makaut.

---
## When to change from cartesian to polar variables?

### 1. Symmetry of the Region or Function

==If the region of integration or the function itself has circular (radial) symmetry==, polar coordinates are often more natural. For example, if you’re integrating over a circular region, like a disk or an annulus, or if the integrand involves terms like $$x^2 + y^2$$, polar coordinates make the setup easier.

In polar coordinates: $$x = rcos\theta$$ and $$y = rsin\theta$$
and $$x^2 + y^2 = r^2$$
### 2. Simplifying the Integral Expression

When you convert to polar coordinates, the differential element $dx dy$ ,  becomes $r  \, dr \, d\theta$r. This adjustment often simplifies the integrand, especially when it involves $x^2 + y^2$ terms. For example:

$$\int\int_R f(x,y)dxdy = \int\int_R f(rcos\theta , rsin\theta)r \, dr \, d\theta $$

This $r$ factor can be very helpful in evaluating integrals, especially when combined with radial symmetry, since it often allows you to separate variables or take advantage of simpler limits.

---
### Summary: When to Consider Polar Coordinates

- The region of integration has circular boundaries (disks, rings, etc.).
- The integrand involves terms like $x^2 + y^2$
- There is radial symmetry, making polar coordinates a more natural fit.
---
## How to convert from Cartesian to Polar Variables?

https://www.youtube.com/watch?v=a334vcCiZ78&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=7

This video tells us how to convert the cartesian variables to polar variables using the **Jacobian determinant**

So as a pre-requisite we must understand what the **Jacobian determinant** is.

This part will be re-referenced again in Multi-variable differential calculus.

---
## The Jacobian determinant.

![[Pasted image 20241107133101.png]]

Yeah I saved some time there.

So now, what begs the question is, **What is a determinant? What is a Matrix?**

**Well in-case you are someone who has been out of touch with higher level maths for a long time, I will explain these here**.

==I will keep this on a strictly need-to-know basis== only as **we don't want to divert too off track here**.

---
### What is a Matrix?

A matrix is a representation are rectangular (2 or 3 or even more) dimensional arrays of real numbers.

$$
\begin{pmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{pmatrix}
$$

For example, this a 3x3 matrix.

And 

$$
\begin{pmatrix}
a & b  \\
d & e  \\
\end{pmatrix}
$$

this is a 2x2 matrix

---
### What is a determinant?

The determinant of a matrix is ==a single numerical value that is calculated from the elements of a square matrix==. It is used to solve systems of linear equations, calculate the inverse of a matrix, and in calculus operations. The determinant is denoted by $|A|$ or $det(A)$.

---
#### How to calculate the determinant of a 2x2 matrix?

Considering our previous matrix example here :

$$
\begin{pmatrix}
a & b  \\
d & e  \\
\end{pmatrix}
$$

The determinant of this matrix : 

$$
\begin{vmatrix}
a & b \\
c & d \\
\end{vmatrix}
$$
is given by $$[ad] - [bc]$$
![[Pasted image 20241107213304.png]]


---
#### How to calculate the determinant of a 3x3 matrix?

Let's say we have a 3x3 matrix here

$$
\begin{pmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{pmatrix}
$$

The determinant is given by : 

$$
\begin{vmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{vmatrix}
$$
 which evaluates to :

![[Pasted image 20241107213319.png]]

---
### Example 1. Jacobian Determinant

Now that the basic's out of the way, let's practice two examples before we get back to the conversion of cartesian to polar co-ordinates.

![[Pasted image 20241107140217.png]]

---
### Example 2.

![[Pasted image 20241107140257.png]]

![[Pasted image 20241107140312.png]]

**Don't think about the differentiation part too much in here as it's out of context, but will be properly explained in the multi-variable differentiation notes(Assuming you are doing integration first).**

---
## Back to conversion of Cartesian to Polar co-ordinates

https://www.youtube.com/watch?v=a334vcCiZ78&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=7

(In case you lost the link)


So let's say we have this given integral here: (**It's a very important question in general**)

![[Pasted image 20241107140725.png]]


We are asked to solve this integral by **changing the variables into Polar co-ordinates**.

$$\int_0^a \int_0^{\sqrt{a^2-x^2}}{\sqrt{x^2+y^2}}dy\,dx$$

---
### Steps to convert Cartesian to Polar co-ordinates

1. **Set** $x = rcos\theta$ and $y = rsin\theta$ .

After doing that our integral will look like this :

$$\int_0^a \int_0^{\sqrt{a^2-x^2}}{\sqrt{r^2cos^2\theta+r^2sin^2\theta}}\,dy\,dx$$


Yeah, try dressing up a chicken in a duck outfit, that's what the integral is right now.

So we need to :

2. **Convert** $dy\,dx$ to $dr\,d\theta$ .

Using the Jacobian determinant, we have : $$dx\,dy = |J|\, dr\,d\theta$$, where $|J|$ equals to : 
$$
\begin{vmatrix}
\frac{dx}{dr} & \frac{dx}{d\theta}  \\
\frac{dy}{dr} & \frac{dy}{d\theta} \\
\end{vmatrix}
$$

Therefore, from $x = rcos\theta$

Differentiating both sides with respect to r ($\theta$ will be considered a constant here), 

$$\frac{dx}{dr} = cos\theta \, ...... \, (1)$$

And again Differentiating both sides with respect to $\theta$  (r will be considered a constant here), 

$$\frac{dx}{d\theta} = -rsin\theta \, ...... \, (2)$$
Now, from $y = rsin\theta$, 

Differentiating both sides with respect to r ($\theta$ will be considered a constant here), 

$$\frac{dy}{dr} = sin\theta \, ...... \, (3)$$
And again Differentiating both sides with respect to $\theta$  (r will be considered a constant here), 

$$\frac{dy}{d\theta} = rcos\theta \, ...... \, (4)$$

Thus, populating the Jacobian determinant :

![[Pasted image 20241107213339.png]]


We get $|J|$  = $r$.

$$\therefore dx\,dy = r \, dr\, d\theta $$

But we have $dy \, dx$ in our question, **not** $dx \,dy$.

So **here we need to change the order of integration to correctly fit the replacement**.

So we have $$y = \sqrt{a^2 - x^2}$$ as it's upper limit.

or $$y^2 = a^2 - x^2$$, or $$x^2 + y^2 = a^2$$

Which is the **equation of a circle**.

![[Pasted image 20241107213355.png]]


However, notice that we have $$y = \sqrt{a^2 - x^2}$$

the value of $y$ is positive. Which means we are concerned only with the upper half of the circle.

To narrow down the region further down, have our lines defined for $x = 0$ and $x = a$.

Between these lines, the region which the equation covers, is the first quadrant only.

So this is the region for the circle :

![[Pasted image 20241107213408.png]]


![[WhatsApp Image 2024-11-07 at 14.59.29_a789690c.jpg]]


And now have the appropriate new limits as well as the limits for their polar counter-parts

So we can safely re-write the integral as :

$$\int_0^{\frac{\pi}{2}} \int_0^a {\sqrt{r^2cos^2\theta+r^2sin^2\theta}}\,dx\,dy$$

And finally replace $dx \, dy$ to $r \, dr \, d\theta$

Thus our integral finally becomes, 

$$\int_0^{\frac{\pi}{2}} \int_0^a {\sqrt{r^2cos^2\theta+r^2sin^2\theta}}\,r \,dr\,d\theta$$

Now we can solve this integral.

So $$\int_0^{\frac{\pi}{2}} \int_0^a {\sqrt{r^2cos^2\theta+r^2sin^2\theta}}\,r \,dr\,d\theta$$
equals

$$\int_0^{\frac{\pi}{2}} \int_0^a {\sqrt{r^2[cos^2\theta+sin^2\theta]}}\,r \,dr\,d\theta$$

or $$\int_0^{\frac{\pi}{2}} \int_0^a {\sqrt{r^2}}\,r \,dr\,d\theta$$
or $$\int_0^{\frac{\pi}{2}} \int_0^a r \,. r \,dr\,d\theta$$
or $$\int_0^{\frac{\pi}{2}} \int_0^a r^2 \,dr\,d\theta$$
or $$\int_0^{\frac{\pi}{2}} [\frac{r^3}{3}]_0^a \,d\theta$$
or $$\frac{a^3}{3} \int_0^{\frac{\pi}{2}}d\theta$$
or $$\frac{a^3}{3} [\theta]_0^{\frac{\pi}{2}}$$
or $$\frac{\pi a^3}{6}$$

---
# Green's Theorem (Statement only)

<iframe width="560" height="315" src="https://www.youtube.com/embed/8SwKD5_VL5o?si=dAU-hOBqUOej5wk9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
Here's a very cool visual explanation of Green's Theorem

![[Pasted image 20241107203952.png]]

And here's the statement.

----
# Gauss's Theorem (Statement only)

<iframe width="560" height="315" src="https://www.youtube.com/embed/zZqxbwl3Dno?si=kcOPzI4fMolDjh_I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Here's a nice explanation video of Gauss's Theorem

![[Pasted image 20241107204215.png]]

---
# Stokes's Theorem (Statement only)

<iframe width="560" height="315" src="https://www.youtube.com/embed/CCNtL-xhF6I?si=7Jkr5vrz4OmWibq9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Here's a nice explanation video on Stokes's Theorem

![[Pasted image 20241107212148.png]]

![[Pasted image 20241107212155.png]]

---

