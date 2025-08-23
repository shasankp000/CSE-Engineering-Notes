---
{"dg-publish":true,"permalink":"/calculus-3-stuff/differential-equations-important-stuff/","title":"Differential Equations -- Important Stuff -- Mathematics III","tags":["Semester-3"],"created":"2025-03-06T18:33:20.144+05:30"}
---

---
# Index

1. [[#Basic types of differential equations.]]
2. [[#1. Linear Differential equation.]]
3. [[#2. Exact equations]]
4. [[#Steps for finding integrating factor for a non-exact equation.]]
5. [[#3. Bernoulli's equation]]
6. [[#Differential equations of first order but not first degree.]]
7. [[#1. Equations solvable for p]]
8. [[#2. Equations solvable for y]]
9. [[#3. Equations solvable for x]]
10. [[#Clairaut's equation.]]
11. [[#Second Order Differential Equations]]
12. [[#Method 1 Using the inverse operator method.]]
13. [[#Method 2 Using the method of variation of parameters.]]

**Note** : If the equations on the website seem a bit to clumped up/clogged, please go to the resources section and download the PDF. It has better indentation.

---
# Basic types of differential equations.

## 1. Linear Differential equation.

These can be of two types:

1. $$\boxed{\frac{dy}{dx} + P(x).y = Q(x)}$$
To solve this, we find an ==integrating factor(I.F)==.

$$I.F = e^{\int{P(x) dx}}$$

And we find the solution in terms of y as:

$$\boxed{y . (I.F) = \int{Q(x) . (I.F) dx} + C}$$

2. $$\boxed{\frac{dx}{dy} + P(y).x = Q(y)}$$
Same stuff, just in terms of x this time.


I.F = $$I.F = e^{\int{P(y) dy}}$$

And we find the solution in terms of x as: $$\boxed{x . (I.F) = \int{Q(y) . (I.F) dy} + C}$$

---
## 2. Exact equations

An ordinary D.E of first order and first degree is of the form: $$\frac{dy}{dx} = F(x,y)$$ can be written as: $\boxed{Mdx + Ndy = 0}$

This equation will be considered exact, ==**if and only if**== 

$$\frac{dM}{dy} = \frac{dN}{dx}$$
and the solution of the equation will be given by:

$$\boxed{y=\int{Mdx} + \int{(no \ x \ containing \ term \ from \ N)}dy = constant}$$

However there are times when :

$$\frac{dM}{dy} \neq \frac{dN}{dx}$$
and thus the equation **by-default** is **not exact**.

However we **can convert it to an exact equation** by finding an **integrating factor** and then **multiplying it to the original equation**.

---
### Steps for finding integrating factor for a non-exact equation.

1. If equation is of the form $\boxed{Mdx + Ndy = 0}$
2. Then check if $\frac{dM}{dy} \neq \frac{dN}{dx}$
3. If true, then equation is non-exact.

Proceeding from here:

#### Case 1

1. Check if **both M and N are homogenous** (degree of both the functions should be equal to zero).  
2. If case 1 is true, then check if both **M** and **N** have same degree
3. If true, then check if $Mx + Ny \neq 0$ .
4. If all of the above are true, then the I.F will be: $$\boxed{\frac{1}{Mx + Ny}}$$
5. Multiply this I.F to the original equation to get the exact equation. Proceed solving from there as previously discussed.

#### Case 2 (M and N are both not homogenous/M is not homogenous/N is not homogenous)

1. In this case, we proceed by finding : $$\frac{dM}{dy} - \frac{dN}{dx}$$
2. Now we can either:
	1. Divide by M: If the result **is a function of y and y only**, then our I.F will be: $$\boxed{e^{-\int{g(y)dy}}}$$
	2. Divide by N: If the result **is a function of x and x only**, then our I.F will be: $$\boxed{e^{\int{f(x)dx}}}$$
3. Multiply this I.F to the original equation to get the exact equation. Proceed solving from there as previously discussed.

---

### For the alternate form

1. If equation is of form $$\boxed{y(f(x,y)dx + xg(x,y)dy) = 0}$$
2. **M** = $y(f(x,y)$ , **N** = $xg(x,y)$.
3. If $$Mx-Ny \neq 0$$, then 
4. Integrating factor = $$\boxed{\frac{1}{Mx-Ny}}$$
5. Multiply this I.F to the original equation to get the exact equation. Proceed solving from there as previously discussed.
---
## 3. Bernoulli's equation

It is of the form: $$y' + P(x)y = Q(x).y^{n}$$

Where $$y' = \frac{dy}{dx}$$ The easiest way to solve this is to **reduce to a linear D.E**.

We start by dividing both sides of the equation with $y^{n}$ to get :

$$y^{-n}.\frac{dy}{dx} + P(x).y^{1-n} = Q(x)$$

Let $y^{1-n}$ = $z$ .

Differentiate both sides w.r.t $x$.

$$y^{-n}.\frac{dy}{dx} = \frac{dz}{dx} . \frac{1}{(1-n)}$$

Substitute back into the original equation, we get:

$$\frac{1}{(1-n)} . \frac{dz}{dx} + P(x).z = Q(x)$$

or $$\frac{dz}{dx} + (1-n) . P(x).z = Q(x).(1-n)$$

which can now be solved using the formula of a linear D.E

![Pasted image 20241022142505.png](/img/user/media/Pasted%20image%2020241022142505.png)

---

# Differential equations of first order but not first degree.

## 1. Equations solvable for p

The required form for this type of equation should in the form of a quadratic equation:

$$ax^{2} + bx + c = 0$$

or 

$$\boxed{p^{2} + p + c = 0}$$

### Example explanation

Let's say we have the equation:

$$(\frac{dy}{dx})^{2} - \frac{dy}{dx} - 6 = 0$$

1. Set $\frac{dy}{dx} = p$ 
2. So the equation becomes $p^{2} - p - 6 = 0$
3. Solving the equation, we get roots as `p = -2` and `p = 3`.
4. Equation $\frac{dy}{dx}$ to both the values separately and separate the variables

$$dy = 3dx ...(1)$$
$$dy = -2dx ....(2)$$

5. Integrate both the equations, we get:

$$y = 3x + c ...(3)$$ or $$ y -3x -c = 0$$
and  $$y = -2x + c$$
or $$y + 2x - c = 0 ...(4)$$
6. Finally we write both the equations in product form as :

$$(y -3x -c)(y + 2x - c) = 0$$

---
## 2. Equations solvable for  y


These are equations are always of $y^{n}$ where $n$ is always equal to 1.

### Steps to solve an equation for y.

1. Write equation in terms of y, where y is isolated on the LHS.
2. Differentiate L.H.S and R.H.S w.r.t `x`.
3. Let $\frac{dy}{dx} = p$.
4. Try to solve and reduce to a linear differential equation which will be  $$\frac{dx}{dp} + P(p).x = Q(p)$$, by doing some substitution by setting some coefficient to z.
5. Then solve the linear D.E to get a value in terms of $x$.
6. Put that value back in the original given equation and you have the required solution.

Alternatively .

After step 3

4. Try to solve the equation and get a value of in terms of $p$.
5. Take only those terms which have $\frac{dp}{dx}$ associated with them.
6. Now let's say you get, $p=bx.\frac{dp}{dx}$, then separate the variables, $x$ to one side, $p$ to the other.
7. Integrate both sides.
8. Put the value of $p$ back in the original equation.


==**Both methods are valid. Just depends which one is more applicable, based on the question**==.

---
### Example explanation

Let's say we have an equation.

$$y-2px+xp^{2} = 0$$

So rewriting the equation we get :

$$y = 2px-xp^{2} ... (1)$$
So we differentiate both sides w.r.t $x$.

$$\frac{dy}{dx} = 2p - p^{2} + 2x.\frac{dp}{dx}[1-p]$$

Let $\frac{dy}{dx} = p$.

So we get the equation as :

$$p = 2p - p^{2} + 2x.\frac{dp}{dx}[1-p]$$

which can be further reduced down to:

$$(1-p)(p + 2x.\frac{dp}{dx}) = 0$$

Here we see that we already have a term with $\frac{dp}{dx}$. So we **don't need to reduce to a linear D.E at this point**, we will just consider the second term.

Therefore, $$p = -2x.\frac{dp}{dx}$$

We separate the variables to get:

$$\frac{p}{dp} = \frac{-2x}{dx}$$

Now we integrate both sides to get

$$2log(p) = -log(x) + log(c)$$
which can be solved further down to get:

$$log(p^{2}x) = log(c)$$

or $$p^{2} = \frac{c}{x}$$ or $$p = \sqrt{\frac{c}{x}}$$

Now we apply this value back in the original equation to get

$$y - 2\sqrt{\frac{c}{x}}.x - x.\frac{c}{x} = 0$$

or , $$\boxed{y = 2\sqrt{c}.\sqrt{x} + c}$$

---
### Example 2.

Let's say we have another equation: $$y = 2px - p^{2}$$
We apply the same rules as before to get

$$\frac{dy}{dx} = 2x.\frac{dp}{dx} + 2p - 2p.\frac{dp}{dx}$$ 
Let $\frac{dy}{dx} = p$.

and then by solving further we get an equation:

$$p + 2(x-p).\frac{dp}{dx} = 0$$

Now we could technically apply the alternative method and only choose the second term with dp/dx, but then separating variables would be a problem in this instance.

We would get $$2x{dp} - 2p dp = dx$$
Which now becomes troublesome to separate further.

So **discarding this approach**, we convert this equation into a linear D.E and then try to solve it.

Thus: $$p.\frac{dx}{dp} + 2x - 2p = 0$$

or $$\frac{dx}{dp} + 2x = 2$$

Solving this D.E we get a value in terms of $x$ as :

$$x = \frac{2p}{3} + cp^{-2}$$

Applying this value in original equation, we get the required solution in terms of $y$ as:

$$\boxed{y = p^{2} + 2cp^{-1}}$$
---
## 3. Equations solvable for x

Here equations are given in the form of: $$x = f(y,p)$$
We generally solve this by differentiating both sides w.r.t $y$.

Therefore, $$\frac{dx}{dy} = F(y, p.\frac{dp}{dy})$$
If $\frac{dy}{dx} = p$ then $\frac{dx}{dy} = \frac{1}{p}$

$$\therefore \frac{1}{p} = F(y, p.\frac{dp}{dy})$$, which is a **first order differential equation in terms of p and y**

We will solve the equation further and then separate variables, integrate both sides to get a value in terms of y, put it back in original equation.

---
### Example explanation

Let's say we have a given equation :  $$x = y + p^{2}$$

We differentiate both sides w.r.t $y$.

$$\therefore \frac{dx}{dy} = 1 + 2p.\frac{dp}{dy}$$

Or, $$\frac{1}{p} = 1 + 2p.\frac{dp}{dy}$$ Continuing to solve that we get :

$$\frac{1-p}{2p^{2}} = \frac{dp}{dy}$$

or 

$$dy = \frac{2p^{2}}{1-p}.dp$$
or $$dy = [2p^{2} - 2p].dp$$

Integrating both sides, we got a solution in terms of $y$ as: $$y = \frac{2p^{3}}{3} - p^{2} + c$$

So applying this value in our original equation, we get the required solution as:

$$\boxed{x = \frac{2p^{3}}{3} + c}$$

---
# Clairaut's equation.

A differential equation of the form 

$$\boxed{y = px + f(p)}$$

is called **Clairaut's form**.

We will use the method of [[#2. Equations solvable for y]] to solve such equations.


So we differentiate the equation w.r.t $x$.

$$\frac{dy}{dx} = \frac{dp}{dx}.[x + f'(p)] + p$$



Let 

$$\frac{dy}{dx} = p$$


$$p = p + \frac{dp}{dx}[x + f'(p)]$$


or

$$\frac{dp}{dx}.[x + f'(p)] = 0$$


Now we set both of the terms 

$$\frac{dp}{dx} = 0 ... (1)$$

and 

$$x + f'(p) = 0 .... (2)$$


From equation 1, we get $p =  c$.
Thus, 

$$y = cx + f(c)$$


which is the **required general solution**,

And from equation 2, we get : 

$$x + f'(c) = 0$$


which is the **singular solution** in terms of **x** and **y** only.

---
## Example explanation

1. Solve $$(y-px)(p-1) = p$$ and obtain the singular solution.

We write it in Clairaut's form.

$$y = px + \frac{p}{p-1}$$
Now we differentiate both sides w.r.t $x$.

$$\frac{dy}{dx} = x.\frac{dp}{dx} + p + (\frac{1}{(p-1)^{2}}).\frac{dp}{dx}$$
or
$$\frac{dy}{dx} = p + [x - \frac{1}{(1-p)^{2}}].\frac{dp}{dx}$$
let $$\frac{dy}{dx} = p$$

Thus $$\frac{dp}{dx}.[x - \frac{1}{(1-p)^{2}}] = 0$$
Thus from $$\frac{dp}{dx} = 0$$, we get $p = c$.

Thus the **required general solution** is $$y = cx + \frac{c}{c-1}$$
And from $$[x - \frac{1}{(1-p)^{2}}] = 0$$
we get $$p = \frac{1 + \sqrt{x}}{\sqrt{x}}$$

We get singular solution as : $$y = [\frac{1 + \sqrt{x}}{\sqrt{x}}] . x + \frac{1 + \sqrt{x}}{\sqrt{x}}$$
or $$\boxed{y = 2\sqrt{x} + x + 1}$$

---
# Second Order Differential Equations

A linear D.E of second order with constant coefficients is of the form:
$$\frac{d^2}{dx^2} + P_1.\frac{dy}{dx} + P_2y = x$$

where $P_1$ and $P_2$ are constants and $x$ is either a constant or a function of $x$ itself.

We can solve this equation by first converting it to it's auxiliary form using the **D-operator method**.

Using the symbol **D** for the differential operator $\frac{d}{dx}$ , the above equation can be written as:

$$(D^2 + P_1D + P_2)y = X$$

## Case 1: Solving homogenous part and finding C.F

Now if $X$ is equal to zero then the equation becomes homogenous. To solve this we need to find a **complementary factor** or **C.F**.

### Rules for finding Complementary factor, C.F

1.  Convert the given differential equation to it's auxiliary form. For example :
   $$D^2 + D + 1 = 0$$
2. Solve the equation and find it's two roots $m_1$ and $m_2$.
3. If the roots are different, the solution becomes:
   $$y = c_1.e^{m_1.x} + c_2.e^{m_2.x}$$
   where $c_1$ and $c_2$ are arbitrary constants.
4. If the roots are same, i.e $m_1 = m_2$, then the solution becomes:
   $$y = [c_1 + c_2.x]e^{mx}$$
5. If the roots are complex then, the solution becomes:
   $$y = e^{ax}[c_1.cos(bx) + c_2.sin(bx)]$$
   where $m = a+bi$ , $a = 0$ , $b = 1$.
   
   or $$y = c_1.cos(bx) + c_2.sin(bx)$$
---
## Case 2: Solving the non-homogenous part of the differential equation.

In the event of : $$(D^2 + P_1D + P_2)y = X$$, $X$ is not a constant, there is a different way to find the solution to this equation.

Firstly we assume $y = e^{mx}$ to be a trial solution to this equation and find **C.F** for the homogenous part, and we write it down as :

$$y = c_1.y_1(x) + c_2.y_2(x)$$
Now for the non-homogenous part, we need to find something called a **Particular-Integral** or **P.I**.

The entire general solution will be

$$y = C.F + P.I$$

There are two ways to find the **P.I** .

### Method 1: Using the inverse operator method.

Let the non-homogenous D.E be :

$$(D^2 + a_1.D + a_2)y = f(x)$$

We do this by setting :

$$P.I = \frac{1}{(D^2 + a_1.D + a_2)} . f(x)$$

Solving $(D^2 + a_1.D + a_2)$ , we get either $(D-a)^n$ or $(D+a)$ or $(D-a)(D+b)$

Now a few important cases of $f(x)$ and formulae for those cases.

1. $$\frac{1}{(D-a)}. X = e^{ax}.\int{X.e^{-ax}}dx$$
---
2. $$\frac{1}{D}.X = \int{X}dx$$
---
3. If you have : 
   
   $$\frac{1}{(D-m_1)(D+m_2)}.X$$
   
   
    or 
   
   $$\frac{1}{f(D)}.X$$
   
   , where $m_1$ and $m_2$ are roots of $f(D)$, then we can get the P.I as follows: 
   
   $$\frac{1}{f(D)} = \frac{A_1}{D-m_1} + \frac{A_2}{D-m_2}$$
   
   
   which is solved as:  
   
   $$\frac{1}{f(D)}.X = A_1.e^{m_1.x}.\int{X.e^{-m_1.x}} + A_2.e^{m_2.x}.\int{X.e^{-m_2.x}}$$
---   

   Now to find the values of $A_1$ and $A_2$.
   
   
   Let's say we have a given expression 
   
   $$\frac{1}{(D-1)(D+1)}.(x.e^{2x})$$
   
   
   where $m_1 = 1$ and $m_2 = -1$.
   
   We can write 
   
   $$\frac{1}{(D-1)(D+1)}.(x.e^{2x}) = [\frac{A}{D-1} + \frac{B}{D+1}].(x.e^{2x})$$
   
   
   
   or  

   $$\frac{1}{(D-1)(D+1)}.(x.e^{2x}) = \frac{A(D+1) + B(D-1)}{(D-1)(D+1)} . (x.e^{2x})$$
---   

   Cancelling out $x.e^{2x}$ from both sides and multiplying both sides by $(D-1)(D+1)$, 
   
   We get  
   
   $$1 = \frac{A_1}{D-1} + \frac{A_2}{D+1}$$
   
   
   or  
   $$1 = (A+B)D + (A-B)$$
   
---
   
   Now we compare both the coefficient of $D$ and constant terms to the other side.
   
   
   Since there is no $D$ on the other side, $(A+B) = 0$, and $1$ is on the other side, so
   
	 $A-B = 1 => A = B$
	 
	 
   
   From the two equations, we get $A = \frac{1}{2}$ , $B = -\frac{1}{2}$

---
   
   So we get our P.I as: 
   
   $$\frac{1}{2}.e^x.\int{x.e^{2x}.e^{-x}dx} - \frac{1}{2}e^{-x}.\int{x.e^{2x}.e^xdx}$$
   
   
   
   
   which, when solved completely, gives us:
   
   $$\frac{e^{2x}}{(3x-4)}$$
   
   
   as the solution for this P.I.

---

4. If you have :  
   
   $$\frac{1}{f(D)}.X$$
   

	where $X = P(x)$, is a polynomial function of some degree $m$, we get the P.I as:


   $$[f(D)]^{-1}.P(x)$$


   where we expand $D$ till $D^m$ and then solve $P(x)$.
---
5. If you have:  
   
   $$\frac{1}{f(D)}.e^{ax}.V$$
   
   
   , where $V$ is a function of a $x$. We can get the solution as:
   
   $$P.I = e^{ax}.\frac{1}{f(D+a)}.V$$
---
## Method 2: Using the method of variation of parameters.

This method is used when it's difficult to apply the inverse operator method. However it is **not a replacement for the inverse operator method**. Both are valid, usage depends on the question.

So picking up from our C.F for equation: $$(D^2 + P_1D + P_2)y = X$$

where we assumed the C.F to be: $$y = c_1.y_1(x) + c_2.y_2(x)$$
Now, let us assume our P.I as $$y = u.y_1(x) + v.y_2(x)$$, where $u$ and $v$ are unknown functions of $x$

To find the value of $u$ and $v$, we need to find the **Wronskian Determinant**, which is given by 
$$W = 
\begin{vmatrix}
y_1 \ y_2 \\
y'_1 \ y'_2 \\
\end{vmatrix}
$$

and $$u' = 
\begin{vmatrix}
0 \ y_2 \\
X \ y'_2 \\
\end{vmatrix}
= \frac{-y_2.X}{W}$$

and 

$$v' = \begin{vmatrix} y_1 \ 0 \\ y'_1 \ X \\ \end{vmatrix} = \frac{y_1 . X}{W}$$


or 

$$\boxed{u = \int{\frac{-y_2.X}{W}}}$$
and 

$$\boxed{v = \int{\frac{y_1 . X}{W}}}$$


Put these values back into your P.I equation to get the full general solution to the D.E

---

