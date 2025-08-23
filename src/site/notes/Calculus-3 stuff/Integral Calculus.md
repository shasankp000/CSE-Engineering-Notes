---
{"dg-publish":true,"permalink":"/calculus-3-stuff/integral-calculus/","title":"Multivariable Integral Calculus -- Mathematics III","tags":["Semester-3"],"created":"2025-03-06T18:33:20.184+05:30"}
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
19. [[#Green's Theorem (Statement only)]] (and detailed examples included)
20. [[#Gauss's Theorem (Statement only)]] (and detailed examples included)
21. [[#Stokes's Theorem (Statement only)]] (and detailed examples included)

**Note** : If the equations on the website seem a bit to clumped up/clogged, please go to the resources section and download the PDF. It has better indentation.

---

# Integral Calculus Recap

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
# Double Integrals

https://www.youtube.com/watch?v=BJ_0FURo9RE&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=5

## Example 1

Let's say we have an integral here, $$\int_{0}^{2}\int_{1}^{3}{xy^2}dydx$$
In double (or triple integrals), **the order of integration matters**. Whether you want to integrate in terms of $y$ or $x$ or $z$ (triple integrals) first, that depends on you.

So here we follow which variable is given first. The first variable is $dy$.

So we integrate with respect to $y$ first.

$$\therefore \int_{0}^{2}x[\frac{y^3}{3}]_{1}^{3}dx$$

or $$\int_{0}^{2}x. [\frac{3^3}{3} - \frac{1^3}{3}]dx$$
or, $$\int_{0}^{2}\frac{26x}{3}. dx$$
or $$\frac{26}{3}.\int_{0}^{2}xdx$$
or, $$\frac{26}{3}.[\frac{x^2}{2}]_{0}^{2}$$
or $$\frac{26}{3}.\frac{4}{2}$$
Thus finally, $$\int_{0}^{2}\int_{1}^{3}{xy^2}dydx = \boxed{\frac{52}{3}}$$

---
## Example 2

![Pasted image 20241106222205.png](/img/user/media/Pasted%20image%2020241106222205.png)

So we have this integral right here, 

$$\int\int_R[2y - 3x^2y^2]dA$$

where $R = \{(x,y) | 0 \leq x \leq 1, 0 \leq y \leq 2\}$

So we need to find the upper and lower limits of $x$ and $y$.

Following the given set, we see that $x$ lies between $0$ and $1$.

And $y$ lies between $0$ and $2$.

Therefore the integral becomes, $$\int_{0}^{1}\int_{0}^{2}[2y - 3x^2y^2]dxdy$$
While applying the limits **we follow the order of the variables in the given set**, which in this case, $x$ comes first, followed by $y$

Now it's business as usual. We can solve the integral in the same way we did before.

![Pasted image 20241106222704.png](/img/user/media/Pasted%20image%2020241106222704.png)

![Pasted image 20241106222735.png](/img/user/media/Pasted%20image%2020241106222735.png)

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


![Pasted image 20241106222851.png](/img/user/media/Pasted%20image%2020241106222851.png)

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

![Pasted image 20241106222851.png](/img/user/media/Pasted%20image%2020241106222851.png)


To change the order of integration, we need to analyze the interdependent limits.


$$x = 2y$$

$$\therefore y = \frac{x}{2}$$
So y's new limits will be from 0 to $\frac{x}{2}$

And thus now y will be dependent on a changing $x$ as it goes from $0$ to $2$. Why $2$ you ask?

Well, you ding-dong, since originally,  $x = 2y$, $x$ **is the double of any value of y**.

So it naturally makes sense that when **y** depends on a changing **x**, the value of **x** will be double of whatever $y$'s value is. Originally $x$ ranged from 0 to 1, so now double that, the new range will be $0$ to $2$.

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

![Pasted image 20241107114451.png](/img/user/media/Pasted%20image%2020241107114451.png)

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

![Pasted image 20241107122459.png](/img/user/media/Pasted%20image%2020241107122459.png)

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

![Pasted image 20241107213201.png](/img/user/media/Pasted%20image%2020241107213201.png)


Yeah, this.

Normally we represent various diagrams on this plane using **variables** like **x, y, z ....** which are known as **cartesian variables**.

## 2. Polar variables/Polar co-ordinates

Now the Cartesian system handles 2D objects very nicely, but when dealing with 3D objects, specifically cylinders, spheres, etc, **we need a third dimension to work with, which often x, y and z don't make it easy to deal with**. Thus, we need the polar coordinate system here. It was developed by Big Daddy Newton (Sir Isaac Newton).


The polar co-ordinate system has variables like **r**, $\theta$  (pronounced as **theta**) and sometimes $\phi$ (pronounced as **phi**).


Why the name polar?

![Pasted image 20241107213238.png](/img/user/media/Pasted%20image%2020241107213238.png)


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

![Pasted image 20241107133101.png](/img/user/media/Pasted%20image%2020241107133101.png)

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
![Pasted image 20241107213304.png](/img/user/media/Pasted%20image%2020241107213304.png)


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

![Pasted image 20241107213319.png](/img/user/media/Pasted%20image%2020241107213319.png)

---
### Example 1. Jacobian Determinant

Now that the basic's out of the way, let's practice two examples before we get back to the conversion of cartesian to polar co-ordinates.

![Pasted image 20241107140217.png](/img/user/media/Pasted%20image%2020241107140217.png)

---
### Example 2.

![Pasted image 20241107140257.png](/img/user/media/Pasted%20image%2020241107140257.png)

![Pasted image 20241107140312.png](/img/user/media/Pasted%20image%2020241107140312.png)

**Don't think about the differentiation part too much in here as it's out of context, but will be properly explained in the multi-variable differentiation notes(Assuming you are doing integration first).**

---
## Back to conversion of Cartesian to Polar co-ordinates

https://www.youtube.com/watch?v=a334vcCiZ78&list=PLF-vWhgiaXWM7Iri0t_AjBfv51tF28PEy&index=7

(In case you lost the link)


So let's say we have this given integral here: (**It's a very important question in general**)

![Pasted image 20241107140725.png](/img/user/media/Pasted%20image%2020241107140725.png)


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

![Pasted image 20241107213339.png](/img/user/media/Pasted%20image%2020241107213339.png)


We get $|J|$  = $r$.

$$\therefore dx\,dy = r \, dr\, d\theta $$

But we have $dy \, dx$ in our question, **not** $dx \,dy$.

So **here we need to change the order of integration to correctly fit the replacement**.

So we have $$y = \sqrt{a^2 - x^2}$$ as it's upper limit.

or $$y^2 = a^2 - x^2$$, or $$x^2 + y^2 = a^2$$

Which is the **equation of a circle**.

![Pasted image 20241107213355.png](/img/user/media/Pasted%20image%2020241107213355.png)


However, notice that we have $$y = \sqrt{a^2 - x^2}$$

the value of $y$ is positive. Which means we are concerned only with the upper half of the circle.

To narrow down the region further down, have our lines defined for $x = 0$ and $x = a$.

Between these lines, the region which the equation covers, is the first quadrant only.

So this is the region for the circle :

![Pasted image 20241107213408.png](/img/user/media/Pasted%20image%2020241107213408.png)


![WhatsApp Image 2024-11-07 at 14.59.29_a789690c.jpg](/img/user/media/WhatsApp%20Image%202024-11-07%20at%2014.59.29_a789690c.jpg)


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

https://www.youtube.com/watch?v=8SwKD5_VL5o (since the embed can't be rendered in a PDF)

Here's a very cool visual explanation of Green's Theorem

![Pasted image 20241107203952.png](/img/user/media/Pasted%20image%2020241107203952.png)


or in another variant (a special case which actually becomes Stoke's Theorem)

![Pasted image 20241231142108.png](/img/user/media/Pasted%20image%2020241231142108.png)

And here's the statement.

So let's say we have a curve **C**.

![Pasted image 20241231142151.png](/img/user/media/Pasted%20image%2020241231142151.png)


And we can call the region inside of this curve as **R**.

![Pasted image 20241231142244.png](/img/user/media/Pasted%20image%2020241231142244.png)


So Green's theorem states that the "The line integral of **F** over **C** is equal to the double integral of the 2-D **curl of F** over R".

What does this mean? What is a line integral?

![Pasted image 20241231143159.png](/img/user/media/Pasted%20image%2020241231143159.png)


![Pasted image 20241231153313.png](/img/user/media/Pasted%20image%2020241231153313.png)

So let's say we divided the curve into 4 smaller "line curves" or just lines.

Naming them $c_1$, $c_2$, $c_3$, $c_4$, each.

Now the LHS side, the "line integral of F over C" would be given by finding the line integrals of all the smaller line curves and summing them up.

So we would get : $$\boxed{\int_c{F} \ dr = \int_{c_1}{F} \ dr \ + \int_{c_2}{F} \ dr + \ \int_{c_3}{F} \ dr + \ \int_{c_4}{F} \ dr} $$
where the surface **C** ==is traversed in the counter-clockwise direction==.

And on the RHS.

Depending on what you have, two continuous functions M(x,y) and N(x,y) or a vector.

We have two equations : 

In case of a vector :

![Pasted image 20241231153519.png](/img/user/media/Pasted%20image%2020241231153519.png)

The curl of the vector **F** is the same as $\frac{dN}{dx} - \frac{dM}{dy}$ which we use if we have two continuous functions M and N.

![Pasted image 20241231153816.png](/img/user/media/Pasted%20image%2020241231153816.png)


So in case of us having two continuous functions M and N, we have the RHS as :

![Pasted image 20241231155146.png](/img/user/media/Pasted%20image%2020241231155146.png)

---
## Some solved examples.

### Example 1.

Let's say we have to deal with this example where we are asked to verify Green's Theorem.

![Pasted image 20241231155316.png](/img/user/media/Pasted%20image%2020241231155316.png)

So we need to verify the LHS and RHS of Green's theorem

So here we have **M** = $xy + y^2$ and **N** = $x^2$

And we are given to curves, $y \ = \ x$  and  $y \ = \ x^2$

So we can imagine $y \ = \ x^2$ as a parabolic line starting from the origin. And we the line $y \ = \ x$ as a line starting from the origin, going upward at a $45 \degree$ angle.

![Pasted image 20241231155627.png](/img/user/media/Pasted%20image%2020241231155627.png)

Let $C_1$ be the parabolic line  $y \ = \ x^2$ and $C_2$ be for $y \ = \ x$.

So we see that both the lines intersect at point (1,1).

The clockwise traversal will be like this : 

![Pasted image 20241231155903.png](/img/user/media/Pasted%20image%2020241231155903.png)


So $$\int_c{[M \ dx \ + \ N \ dy]} = \int_{c_1} {[M \ dx \ + \ N \ dy]} \ + \ \int_{c_2} {[M \ dx \ + \ N \ dy]}$$

So, on $C_1$ we have $y \ = \ x^2$ . On differentiating both sides, we get : $dy = 2x \ dx$
on $C_2$, we have $y = x$ . On differentiating both sides, we get: $dy \ = \ dx$

Why did we differentiate the both sides of these equations? So that during the solving of the line integral we get an easier calculation in terms of a single variable.

Limits for $C_1$ goes from origin (0,0) to point (1,1) so 0 to 1.

Limits for $C_2$ goes from point (1,1) back to origin (0,0), so 1 to 0.

Therefore we get : $$ \int_{c_1} {[M \ dx \ + \ N \ dy]} \ + \ \int_{c_2} {[M \ dx \ + \ N \ dy]} = \int_{0}^{1}{[xy + y^2 \ dx \ + x^2 \ dy]} + \int_{1}^{0}{[xy + y^2 \ dx \ + x^2 \ dy]}$$
substituting $y = x^2$ for $C_1$ and $y=x$ for $C_2$ and their respective $dy$ values.

$$= \int_{0}^{1}{[x^3 + x^4 \ dx \ + x^2 2x \ dx]} + \int_{1}^{0}{[x^2 + x^2 \ dx \ + x^2 \ dx]}$$

$$ = \int_{0}^{1}{[3x^3 + x^4 \ dx]} + \int_{1}^{0}{[3x^2 \ dx]}$$

![Pasted image 20241231161334.png](/img/user/media/Pasted%20image%2020241231161334.png)

$$ = -\frac{1}{20}$$

Now for the RHS.

We need to figure out :  $$\int_R{\int_R{\frac{dN}{dx} - \frac{dM}{dy} \ dx} \ dy}$$
And for R. we have $x$ going from origin (0,0) to point(1,1), so 0 to 1.

And we already have y **parameterized** on x as in the given curves : 

$y = x^2$  to $y = x$.

$\frac{dN}{dx} = 2x$  and $\frac{dM}{dy} = x + 2y$

$\therefore \frac{dN}{dx} - \frac{dM}{dy} =  2x - (x+2y) = x - 2y$

$$\therefore \int_R{\int_R{\frac{dN}{dx} - \frac{dM}{dy} \ dx} \ dy} = \int_{0}^{1}{\int_{x^2}^{x}{\frac{dN}{dx} - \frac{dM}{dy} \ dx} \ dy} = \int_{0}^{1}{\int_{x^2}^{x}{\frac{dN}{dx} - \frac{dM}{dy} \ dy} \ dx}$$

Note that we changed the order of integration from $dxdy$ to $dydx$ because of the how the limits were placed in the integral.

$$ = \int_{0}^{1}{\int_{x^2}^{x}{x - 2y \ dy} \ dx}$$

$$ = \int_{0}^{1}[{x\int_{x^2}^{x}{dy} \ - \ 2 \int_{x^2}^{x}{y \ dy}}]$$

$$ = \int_{0}^{1} {x . {[x - x^2}] \ - \ [x^2 - x^4]  \ dx}$$

$$ = \int_{0}^{1} {x^4 \ - \ x^3 \ dx}$$

$$ = \frac{1}{5} - \frac{1}{4}$$
$$ = -\frac{1}{20} $$

which is the same as our LHS.

Thus **LHS = RHS** and Green's theorem is verified!

---
### Example 2.

![Pasted image 20241231163345.png](/img/user/media/Pasted%20image%2020241231163345.png)

This is a pretty easy one. The question says "Evaluate" so we will only focus on finding the RHS here.

We have ![Pasted image 20241231163612.png](/img/user/media/Pasted%20image%2020241231163612.png)

Thus  

$$\frac{dN}{dx} = cos(x)cos(y)$$ 
and 

$$\frac{dM}{dy} = cos(x)cos(y) - x$$

$$\therefore \frac{dN}{dx} - \frac{dM}{dy} = cos(x)cos(y) - [cos(x)cos(y) - x] = x $$

Since we are dealing with a circle here. 

![Pasted image 20241231165005.png](/img/user/media/Pasted%20image%2020241231165005.png)

We will have to change $x$ to $rcos\theta$ for polar co-ordinates.

Thus $dxdy$ becomes $rdrd\theta$.

And the above picture states how we get the limits of r and $\theta$ .

There we get :

$$\int_{0}^{2\pi}\int_{0}^{1}{r^2cos\theta \ drd\theta}$$
$$ = \int_{0}^{2\pi} cos\theta \ d\theta . [\frac{r^3}{3}]_0^1 $$

$$ \implies \frac{1}{3} . [sin\theta]_0^{2\pi} = \frac{1}{3} . 0 $$

$$ = 0$$

Thus we get zero as the answer for this one. 

![Pasted image 20241231165834.png](/img/user/media/Pasted%20image%2020241231165834.png)

----
# Gauss's Theorem (Statement only)

<iframe width="560" height="315" src="https://www.youtube.com/embed/zZqxbwl3Dno?si=kcOPzI4fMolDjh_I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Here's a nice explanation video of Gauss's Theorem :  

https://www.youtube.com/watch?v=zZqxbwl3Dno (since the embed can't be rendered in a PDF)


So **The Divergence Theorem of Gauss** states that the flux of whatever volume of fluid/electric field/electromagnetic field passing through either a surface or all the surfaces of a 3-D object can be given by : 

![Pasted image 20241107204215.png](/img/user/media/Pasted%20image%2020241107204215.png)


where $\nabla \cdot \mathbf{F}$ is the divergence of the vector **F**. Let's assume that : 

$$F = x\hat{i} \ + \ y\hat{j} \ + z\hat{j}$$
Thus $$\nabla \cdot \mathbf{F} = \frac{d(x)}{dx} + \frac{d(y)}{dy} + \frac{d(z)}{dz}$$

Now to understand the RHS and how the $\hat{n}$ vector works, we need to understand the **Surface Integral**.

---
## What is a Surface Integral?

<iframe width="560" height="315" src="https://www.youtube.com/embed/X2Z0tJG0rjU?si=3mybRBXVMgCXeMxN" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

https://www.youtube.com/watch?v=X2Z0tJG0rjU (since the embed can't be rendered in a PDF).

So a Surface Integral is basically **any integral which is to be evaluated over a surface**.

That surface could be any type.

![Pasted image 20241231171812.png](/img/user/media/Pasted%20image%2020241231171812.png)




So here we have the surface **S**. The surface integral for this surface will be given by :

![Pasted image 20241231171939.png](/img/user/media/Pasted%20image%2020241231171939.png)

$$\int_S\int_S{F . \ dS} \ = \int_S\int_S{F . \hat{n} \ dS}$$



where the unit vector $\hat{n}$ is the vector **normal to the surface S and pointing outwards**.

Now there's a note we need to follow.

Depending on what plane the surface which we are dealing with is on :

![Pasted image 20241231172158.png](/img/user/media/Pasted%20image%2020241231172158.png)


Thus,

XY plane : $\hat{n} = \hat{k}$
YZ plane: $\hat{n} = \hat{i}$
XZ plane: $\hat{n} = \hat{j}$

**What is a plane?**

![Pasted image 20241231182256.png](/img/user/media/Pasted%20image%2020241231182256.png)


In the event where there is plane specified or you are given terms like "first quadrant" or "first octant", we will simply default to the **x-y plane**.


That's great, now how do we find the value of the unit normal vector, $\hat{n}$ ?

We can find that using this formula : 

For vector $F = 3xy^3 - 2xz^2$

$$\hat{n} = \frac{gradient(F)}{magnitude \ of \ gradient(F)}$$

$$gradient(F) = \frac{d(x)}{dx} \hat{i} + \frac{d(y)}{dy} \hat{j} + \frac{d(z)}{dz} \hat{k} = (3y^3 - 2z^2)\hat{i} + (9xy^2)\hat{j} + (4xz)\hat{k}$$

And $$magnitude \ of \ gradient(F) = \sqrt{[{\frac{d(x)}{dx}]}^2 + {[\frac{d(y)}{dy}]}^2 + {[\frac{d(z)}{dz}]}^2}$$

Now watch the attached video for surface integral, the two examples in there should clear up any doubts regarding this.

---
Back to Gauss's theorem.

Let's solve two examples to better understand how Gauss's theorem works :

### Example 1.

![Pasted image 20241231173711.png](/img/user/media/Pasted%20image%2020241231173711.png)


So we have been given a vector $F = 4xz \ \hat{i} - y^2 \ \hat{j} + yz \ \hat{k}$  and been given a 3-D cube's dimensions.

The resulting cube will be like this : 

![Pasted image 20241231173947.png](/img/user/media/Pasted%20image%2020241231173947.png)

So first we need to find the LHS, which is : 

![Pasted image 20241231174048.png](/img/user/media/Pasted%20image%2020241231174048.png)


so the divergence of vector F will be : $4z - 2y + y = 4z - y$.

Now we don't need to find the limits of V as it's been given pretty straightforward, all three, x, y and z go from 0 to 1.

The order of integration will be $dx \ dy \ dz$.

$$\therefore \int\int\int_V{\nabla \cdot \mathbf{F} \ dV} = \int_{0}^{1}\int_{0}^{1}\int_{0}^{1}{4z-y \ dxdydz}$$

![Pasted image 20241231174735.png](/img/user/media/Pasted%20image%2020241231174735.png)

which will result in $$\frac{3}{2}$$

Now for the RHS, what we need to figure out is the flux of the volume through all the surfaces of this cube.

![Pasted image 20241231181051.png](/img/user/media/Pasted%20image%2020241231181051.png)

So for each face, we need to figure out what the $\hat{n}$ will be.

![Pasted image 20241231181129.png](/img/user/media/Pasted%20image%2020241231181129.png)

So what we did here was in each face, substitute the value of x, y or z.

![Pasted image 20241231181703.png](/img/user/media/Pasted%20image%2020241231181703.png)

Using the rules for each plane from our picture earlier, 

XY plane : $\hat{n} = \hat{k}$
YZ plane: $\hat{n} = \hat{i}$
XZ plane: $\hat{n} = \hat{j}$, 

**We figured out which face of the cube was parallel to which axes plane**, and corresponding that we figured out the vector component, and each variable's value.

And thus we see that the RHS also has the same value as the LHS, $\frac{3}{2}$ and so Gauss's theorem is verified.

---
## Example 2 

![Pasted image 20241231215450.png](/img/user/media/Pasted%20image%2020241231215450.png)


So first of all we need to verify the LHS.

So we have LHS as : 

![Pasted image 20250101014122.png](/img/user/media/Pasted%20image%2020250101014122.png)

Now, so the divergence of vector F will be : $4 - 4y + 2z = 4 - 4y + 2z$.


Now let's say we were to cut the cylinder like this:

![Pasted image 20250101014849.png](/img/user/media/Pasted%20image%2020250101014849.png)


Each cross-section of the cylinder would result in a circle of radius x = 2.

Thus we get x = -2 (lower) to +2 (upper) from the equation of $x^2 + y^2 = 4$.

Now for a fixed value of x, y can range from $-\sqrt{4 - x^2}$  (lower) to $+\sqrt{4 - x^2}$ (upper).

And we are already given that z goes from 0 to 3.


So now we can write :  

$$\therefore \int\int\int_V{\nabla \cdot \mathbf{F} \ dV} = \int_{-2}^{2}\int_{-\sqrt{4 - x^2}}^{\sqrt{4 - x^2}}\int_{0}^{3}{ 4 - 4y + 2z \ dxdydz}$$

Now eventually after solving this integral you will reach a step where you will have :

$$\therefore \ 42 \int_{-2}^{2}\sqrt{4-x^2} \ dx$$

Now we will convert to polar coordinates, but instead of choosing $x = rcos\theta$, we will choose 

$x = rsin\theta$ since otherwise LHS = RHS doesn't happen (I spent an entire day on this shit I know that it's right.)

and we already know that radius of the circle = 2.

Thus $$x = 2sin\theta$$
And so for $x = -2$

$$-2 = 2 sin\theta \implies -1 = sin \theta \implies \theta = -\frac{\pi}{2}$$
And for $x = 2$


$$ 2 = 2sin\theta \implies 1 = sin\theta \implies \theta = \frac{\pi}{2} $$

Differentiating for both sides : 

$$dx = 2cos\theta$$

Thus we get  

$$ = 42 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{\sqrt{4 - (2sin\theta)^2} \ 2cos\theta \ d\theta}$$
$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{\sqrt{4 - 4sin^2\theta} \ cos\theta \ d\theta}$$

$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{\sqrt{4(1 - sin^2{\theta})} \ cos\theta \ d\theta}$$

$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{\sqrt{4 \cos^2\theta} \ cos\theta \ d\theta}$$

$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{2 \ cos\theta . cos\theta \ d\theta}$$
$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{2 \ cos^2{\theta}}$$

$$ = 168 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{cos^2\theta}$$

$$ = 168 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{\frac{1 + cos2\theta}{2}} \ d\theta$$

$$ = 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{1 \ d\theta} \ + \ 84 \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}}{cos2\theta \ d \theta}$$

$$ = 84 \  [\theta]_{-\frac{\pi}{2}}^{\frac{\pi}{2}} \ + \ 84 \  . \ [\frac{sin2\theta}{2}]_{-\frac{\pi}{2}}^{\frac{\pi}{2}}$$

$$ = 84 \ [\frac{2\pi}{2}] + 42 \ [sin(\pi) - sin(-\pi)]$$

$$ = 84\pi + 0$$
$$ = 84\pi$$

Now for the RHS.

$$ \int\int_S{F.\hat{n} \ dS} = \int\int_{S_1}{F . \hat{n} \ dS_1} + \int\int_{S_2}{F. \hat{n} \ dS_2} + \int\int_{S_3}{F . \hat{n} \ dS_3}$$

![Pasted image 20250101022821.png](/img/user/media/Pasted%20image%2020250101022821.png)


where $S_1$ is the circular base of the cylinder.
$S_2$ is the circular top of the cylinder.
$S_3$ is the curved surface of the cylinder given by $x^2 \ + \ y^2 = 4$

For $S_1$, z = 0, the circle is on the XY plane, so $\hat{n} = -\hat{k}$.

$$\therefore \ \int\int_{S_1}{F . \hat{n}} = 0$$

For $S_2$, z = 3, the circle is parallel to the XY plane, so $\hat{n} = \hat{k}$

$$\therefore \int\int_{S_2}{F. \hat{n} \ dS_1} \ = \int\int_{S_2} [4x \ \hat{i} - 2 y^2 \ \hat{j} + 9 \ \hat{k}] . \hat{k} \ dx \ dy$$

$$ = 9 \int\int_{S_2}{dx \ dy}$$

$$ = 9 \  \cdot area \ of \ the \ circular \ base$$

$$ = 9 \ \cdot \ \pi r^2 \implies 36 \pi$$

![Pasted image 20250101024021.png](/img/user/media/Pasted%20image%2020250101024021.png)


$$ \therefore \int\int_{S_3}{F . \hat{n} \ dS_3} = \int\int_{S_3}{(2x^2 \ - \ y^3) \ dS_3}$$

Now the surface goes along the XZ plane.

Therefore x will be set to $rcos\theta$ and $y \ = \ rsin\theta$

And $\theta$'s limits will go from 0 to $2\pi$ for the circular ends of the surface.

We already have z's limits.

The order of integration will be $r \ dz \ d\theta$, the $r$ being there because of the co-ordinate change.

So we will have 

$$\int_{0}^{2\pi}\int_{0}^{3}{(2x^2 \ - \ y^3) \ r \ dz \ d\theta}$$

And on solving this ridiculously large integral we will get :

![Pasted image 20250101024915.png](/img/user/media/Pasted%20image%2020250101024915.png)

$$48\pi$$

as the value for the third surface integral.

Adding them up, we get : 

$$ \int\int_S{F.\hat{n} \ dS} \  = \  \int\int_{S_1}{F . \hat{n} \ dS_1} + \int\int_{S_2}{F. \hat{n} \ dS_2} + \int\int_{S_3}{F . \hat{n} \ dS_3} \  =  \ 0 \ + \ 36 \pi \ + \ 48 \pi \ = \ 84\pi$$

Thus, LHS = RHS and Gauss's Divergence theorem is verified!

---
# Stokes's Theorem (Statement only)

<iframe width="560" height="315" src="https://www.youtube.com/embed/CCNtL-xhF6I?si=7Jkr5vrz4OmWibq9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Here's a nice explanation video on Stokes's Theorem

![Pasted image 20241107212148.png](/img/user/media/Pasted%20image%2020241107212148.png)

![Pasted image 20241107212155.png](/img/user/media/Pasted%20image%2020241107212155.png)


Or to explain it in a better way : 

![Pasted image 20250101025642.png](/img/user/media/Pasted%20image%2020250101025642.png)


![Pasted image 20250101031242.png](/img/user/media/Pasted%20image%2020250101031242.png)



This is **the special case for Green's Theorem**


![Pasted image 20241231153519.png](/img/user/media/Pasted%20image%2020241231153519.png)

The curl of the vector **F** is the same as $\frac{dN}{dx} - \frac{dM}{dy}$ which we use if we have two continuous functions M and N.

![Pasted image 20241231153816.png](/img/user/media/Pasted%20image%2020241231153816.png)


However for Stoke's theorem we usually won't have two continuous functions M and N, instead we will have a vector field F.


Since we already dealt with Green's theorem and surface integrals, the process will be more or less similar.
### Example 1

![Pasted image 20250101031358.png](/img/user/media/Pasted%20image%2020250101031358.png)

which is the same question as :

![Pasted image 20250101031429.png](/img/user/media/Pasted%20image%2020250101031429.png)


Note that the vectors given in the two questions are different but the equation is the same for the circle so we have the same diagrams in both questions : 

![Pasted image 20250101031736.png](/img/user/media/Pasted%20image%2020250101031736.png)


![Pasted image 20250101031747.png](/img/user/media/Pasted%20image%2020250101031747.png)



So, for the LHS : 

$$\int F \ \cdot dr$$
which the line integral over the entire sphere's boundary, including the circle on the XY plane.

So we will get : 

$$\int{(y\hat{i} + z\hat{j} + \ x\hat{k})}  \  \cdot  {(dx\hat{i} + dy\hat{j} + \ dz\hat{k})} = \ \int{y \ dx + z \ dy + x \ dz}$$

Now since we only concerned with the XZ plane, $z = 0$ and $dz = 0$

Thus, 

$$\int{y \ dx + z \ dy + x \ dz} = \int{y \ dx}$$

Converting to polar co-ordinates, 

$x = rcos\theta$ and $y = rsin\theta$ and $\theta$ will go from 0 to $2\pi$ since we are only dealing the circle here as the equation has changed from $x^2 + y^2 + z^2 = 1$ to $x^2 + y^2 = 1$ which is the equation of a circle (as z = 0)

From the equation $$x^2 + y^2 = 1 \implies r^2 = 1 \implies r = \pm 1$$

However since we are concerned with the XY plane we will have r = 1.


Thus differentiating both sides of $x = rcos\theta$, we get $dx = 1.-sin\theta \ d\theta$


Thus, 

$$\int{y \ dx + z \ dy + x \ dz} = \int{y \ dx}$$

becomes : 

$$\int_{0}^{2\pi}{sin\theta \ . -sin\theta \ d\theta} = \int_{0}^{2\pi}{-sin^2\theta \ d\theta} \ = \  - \int_{0}^{2\pi}{\frac{1-cos2\theta}{2}} \  = \ - \frac{1}{2}[\theta - \frac{sin2\pi}{2}]_{0}^{2\pi}$$

$$ = \frac{1}{2}[2\pi - 0]$$

$$ = -\pi$$



and for the RHS here : 

![Pasted image 20250101031631.png](/img/user/media/Pasted%20image%2020250101031631.png)

We need to find the curl of the given vector. Let's go with the vector in the example from the video as it's a simpler one.

![Pasted image 20250101031831.png](/img/user/media/Pasted%20image%2020250101031831.png)

Thus we get $$curl(F) = -\hat{i} - \hat{j}  - \hat{k}$$
And what about the unit normal vector $\hat{n}$ ? 

Since in both, the video and the book, we see that the sphere is sitting on the XY plane, from our rules :

XY plane : $\hat{n} = \hat{k}$
YZ plane: $\hat{n} = \hat{i}$
XZ plane: $\hat{n} = \hat{j}$, 

We will have $\hat{n} = \hat{k}$. ( $\ + \ \hat{k}$  since the question explicitly says "above the XY plane", so the vector will point inwards of the sphere).

Thus, 

$$\int\int_S (-\hat{i} - \hat{j}  - \hat{k}) \ \cdot \ \hat{k} \ dx \ dy$$


And we are left with : 

$$  = - \int\int_S dx \ dy$$
which is the formula of the area of a circle

$$ = - \pi \ r^2$$


Now if we set $x = rcos\theta$ and $y = rsin\theta$

From the equation $$x^2 + y^2 = 1 \implies r^2 = 1 \implies r = \pm 1$$

However since we are concerned with the XY plane we will have r = 1.

Thus ,

$$\int\int_S (-\hat{i} - \hat{j}  - \hat{k}) \ \cdot \ \hat{k} \ dx \ dy \ = \ - \int\int_S dx \ dy \ = \ -\pi r^2 \ = \ -\pi$$

Thus LHS = RHS, and Stoke's theorem is verified!


For the vector given in the book, it was the same result, just was positive instead of negative.

![Pasted image 20250101034849.png](/img/user/media/Pasted%20image%2020250101034849.png)

![Pasted image 20250101034901.png](/img/user/media/Pasted%20image%2020250101034901.png)

---
### Example 2:

The second example in the video :

![Pasted image 20250101035016.png](/img/user/media/Pasted%20image%2020250101035016.png)

is the same as :

![Pasted image 20250101035031.png](/img/user/media/Pasted%20image%2020250101035031.png)

however just with a different vector and shape, but contains 4 line integrals overall.

![Pasted image 20250101035109.png](/img/user/media/Pasted%20image%2020250101035109.png)

![Pasted image 20250101035123.png](/img/user/media/Pasted%20image%2020250101035123.png)

![Pasted image 20250101035139.png](/img/user/media/Pasted%20image%2020250101035139.png)

This is the solution for the book's problem. To understand this, watch the example 2 in the video as the procedure is the same more or less, like the previous question.


---