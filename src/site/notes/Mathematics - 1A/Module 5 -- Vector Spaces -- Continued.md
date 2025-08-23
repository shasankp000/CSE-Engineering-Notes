---
{"dg-publish":true,"permalink":"/mathematics-1-a/module-5-vector-spaces-continued/","title":"Module 5 -- Vector Spaces -- Continued","tags":["Semester-1","Mathematics-1A"],"created":"2025-08-09T12:30:14.634+05:30"}
---

---
# Index

1. [[#Eigenvalues and Eigenvectors]]
2. [[#The Cayley-Hamilton Theorem]]
3. [[#Symmetric matrices]]
4. [[#Diagonalization of matrices (symmetric matrices)]]
5. [[#Orthogonal Matrix]]
6. [[#Gram-Schmidt Orthogonalization]]

---
# Eigenvalues and Eigenvectors

https://www.youtube.com/watch?v=PFDu9oVAE-g (must watch this)

Given a square matrix, $A$ , an **eigenvector** is a non-zero vector $v$ such that:

$$Av \ = \ \lambda v$$

where $\lambda$  is the corresponding **eigenvalue**.

In words:

An eigenvector of $A$ is a direction that $A$ simply **stretches or compresses** (by the factor $\lambda$), but does not rotate or mix with other directions.

---
## Breakdown of the Equation

- $v \ \neq \ 0$: the vector should not be the zero vector
- $\lambda$ can be positive/negative/zero/complex
- All vectors that satisfy this are eigenvectors for eigenvalue $\lambda$.

---
## How to find Eigenvalues and Eigenvectors

### Step 1: The Characteristic polynomial

Rewriting:

$$
Av \ = \ \lambda v \ \implies \ (A \ - \ \lambda \ I)v \ = \ 0
$$

Nontrivial solutions ($v \ \neq \  0$) exist only when:

$$\det(A \ - \ \lambda I) \ = \ 0$$

This is called the **characteristic equation**.

- The solutions $\lambda$  are eigenvalues.

---
### Step 2: Find Eigenvectors

For each eigenvalue $\lambda$ found above:

- Solve ($A \ - \ \lambda I$)$v \ = \ 0$ 
- The set of all such nonzero vectors $v$ is the **eigenspace** for eigenvalue $\lambda$.

---
## Detailed Example

Let's use :

$$
A \ = \ 
\left[
\begin{array}{ccc}
2 & 1 \\
1 & 2
\end{array}
\right]
$$


### Step 1: Find the eigenvalues

https://www.youtube.com/watch?v=e50Bj7jn9IQ (This is a video showing a quick trick for calculating eigenvalues, since the more bigger a matrix is, the more complex the equations will be, might get harder to solve.)


We can get that from the characteristic equation :

$$
\det(A \ - \ \lambda I) \ = \ 0
$$


First:

$$A \ - \ \lambda I$$

$$
\left[
\begin{array}{ccc}
2 & 1 \\
1 & 2
\end{array}
\right] 
\ - \ 
\lambda 
\left[
\begin{array}{ccc}
1 & 0 \\
0 & 1
\end{array}
\right]
$$

$$
= \ \left[
\begin{array}{ccc}
2 & 1 \\
1 & 2
\end{array}
\right]
\ - \ 
\left[
\begin{array}{ccc}
\lambda & 0 \\
0 & \lambda
\end{array}
\right]
$$

$$
= \ \left[
\begin{array}{ccc}
2 - \lambda & 1 \\
1 & 2 - \lambda
\end{array}
\right]
$$


Now,

$$\det(A \ - \ \lambda I)$$


$$
\begin{vmatrix}
  2-\lambda & 1 \\
  1 & 2-\lambda
\end{vmatrix}
$$


$$
= \ 
(2 \ - \ \lambda)^2 \ - \ 1
$$

$$
= \ (4 \ - \ 4\lambda \ + \lambda^2) \ - 1
$$

$$
= \ 
\lambda^2 \ - \ 4\lambda \ + 3
$$

Now we equate that to zero.

$$
\det(A \ - \ \lambda I) \ = \ 0
$$

$$
\lambda^2 \ - \ 4\lambda \ + 3 \ = \ 0
$$

And after doing some basic factorization:

$$
(\lambda-3)(\lambda-1) \ = \ 0
$$

So the eigenvalues are:

$$
\lambda_1 \ = 3, \ \lambda_2 \ = \ 1
$$

---
### Step 2: Find eigenvectors for each eigenvalue


From the equation:

$$
A \ - \ \lambda I
$$

For $\lambda_1 \ = \ 3$,

$$
\implies \ \left[
\begin{array}{ccc}
2 - \lambda & 1 \\
1 & 2 - \lambda
\end{array}
\right]
\ = \ \left[
\begin{array}{ccc}
2 - 3 & 1 \\
1 & 2 - 3
\end{array}
\right]
\ = \ \left[
\begin{array}{ccc}
-1 & 1 \\
1 & -1
\end{array}
\right]
$$


Now we equate the rows and columns to a vector $v$ where:

$$
v \ = \ 
\left[
\begin{array}{ccc}
x \\
y
\end{array}
\right]
$$


Applying to both the rows, we get two equations:

$$
-x \ + \ y \ = \ 0
$$


$$
x \ - \ y \ = 0
$$

From the first equation:

$$
y \ = \ x
$$

And from the second equation:

$$
x \ = \ y
$$

So all vectors are of the form:

$$
v \ = \ \left[
\begin{array}{ccc}
1 \\
1
\end{array}
\right]
$$

(or any scalar multiple) are eigenvectors with eigenvalue $\lambda \ = \ 3$

Now, for $\lambda \ = \ 1$

$$
\implies \ \left[
\begin{array}{ccc}
2 - \lambda & 1 \\
1 & 2 - \lambda
\end{array}
\right]
\ = \ \left[
\begin{array}{ccc}
2 - 1 & 1 \\
1 & 2 - 1
\end{array}
\right]
\ = \ \left[
\begin{array}{ccc}
1 & 1 \\
1 & 1
\end{array}
\right]
$$

So from either row we get the equation:

$$
x \ + \ y \ = \ 0
$$

So, 

$$
x \ = \ -y
$$

So, all vectors of the form:

$$
v \ = \ \left[
\begin{array}{ccc}
1 \\
-1
\end{array}
\right]
$$

(or any scalar multiple) are eigenvectors with eigenvalue $\lambda \ = \ 1$

---
## **Why Are Eigenvectors and Eigenvalues Important?**

- Reveal the “axes” along which $A$ acts in the simplest way.
- Used in diagonalization, stability analysis, differential equations, quantum mechanics, ==Google’s PageRank==, ==machine learning== and more.

---
# The Cayley-Hamilton Theorem

https://www.youtube.com/watch?v=TNxmupelc-4&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=9 (must watch)

## What is the Cayley-Hamilton Theorem?

- Every square matrix A satisfies its own characteristic polynomial$pA(λ) = \det(λI − A)$.
- If $pA(λ) = λ^n + c_{n-1}λ^{n-1} + … + c_1λ + c_0$, then  
    $pA(A) = A^n + c_{n-1}A^{n-1} + … + c_1A + c_0I = 0$ (the zero matrix).


Or, in very very simple terms, 

For a given matrix $A_{n\times n}$, we have to prove that:

$$(A \ - \ \lambda I) \ = \ 0$$

which is often called the **characteristic equation**.

---
## Example

Let's use the one given in the video.

![Pasted image 20250810132922.png](/img/user/media/Pasted%20image%2020250810132922.png)


Given matrix:

$$
A \ = \ 
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$


Now, there are two ways to go about this.

### Step 1: Write the characteristic equation:

$$
A \ - \ \lambda I \ = \ 0
$$

Method 1: We find the eigenvalues, substitute them back into the characteristic equation's LHS and then find out if it equates to the RHS.

Method 2: We follow the steps given in the video.

Let's try method 1.

---
### Step 2: Find the eigenvalues

$$
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] \ - \ 
\left[
\begin{array}{ccc}
  \lambda & 0 & 0  \\
  0 & \lambda & 0 \\
  0 & 0 & \lambda  
\end{array}
\right]
$$

$$
\left[
\begin{array}{ccc}
  1-\lambda & 2 & 0  \\
  2 & -1-\lambda & 0 \\
  0 & 0 & 1-\lambda  
\end{array}
\right]
$$


Now, find the determinant of this matrix:

$$
= (1 \ - \ \lambda)[(-1 + \lambda - \lambda \ + \ \lambda^2 ] \ - \ 2 [2-2\lambda \ - \ 0] \ + \ 0
$$

$$
= (1-\lambda)[-1 \ +  \ \lambda^2] \ - \ [4 \ - \ 4\lambda]  
$$

$$
\implies \ 
-1 \ + \ \lambda^2 \ + \ \lambda \ - \ \lambda^3 \ - \ 4 \ + \ 4\lambda \ = \ 0
$$


$$
\implies \
-\lambda^3 \ + \ \lambda^2 \ + \ 5\lambda \ - \ 5 \ = \ 0
$$


Now it is gonna be a massive pain to solve this equation and find the damn roots.

And I am not kidding about this.

Skip ahead to [[#Let's use the given roots to see if method 1 works in theory or not.]] to see if this approach pans out or not, and then I will show the easy approach to continue from once we have found the equation (from the video, method 2)

Here's what a search on perplexity did, a massive rabbit hole.

---
## Perplexity(GPT 4.1)'s solution for the cubic equation.

<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Ah yes now I caught the sign mistake, lamda^3 should have a negative sign.  Now then that we have this equation, what would be it's roots?

  (I had previously made an error in the sign for $\lambda^3$ which I spent 30 minutes debugging since I skipped a lot of the math and did it in my head, retracing  the steps manually took time)


Great! Now that we have the correct characteristic equation:


$$

\lambda^3 - \lambda^2 - 5\lambda + 5 = 0

$$

  

Let's find its roots.

---
### Analytical Approach


This cubic is not easily factorable with integers, so let's look for rational roots using the Rational Root Theorem:

Possible rational roots: $\pm1, \pm5$ (factors of 5 over 1).

  
- Try $\lambda = 1$: $1 - 1 - 5 + 5 = 0$

- So, $\lambda = 1$ is a root!

  
Now divide the cubic by $(\lambda - 1)$:

---
### Synthetic Division  

Divide $\lambda^3 - \lambda^2 - 5\lambda + 5$ by $(\lambda - 1)$:

So, quotient is: $\lambda^2 - 5$.


Therefore:

  

$$

\lambda^3 - \lambda^2 - 5\lambda + 5 = (\lambda - 1)(\lambda^2 - 5)

$$


### Roots of the Quadratic

  

$$

\lambda^2 - 5 = 0 \implies \lambda = \pm\sqrt{5}

$$

***
## Final Roots

  
$$

\boxed{

\begin{aligned}

\lambda_1 &= 1 \\

\lambda_2 &= \sqrt{5} \approx 2.236 \\

\lambda_3 &= -\sqrt{5} \approx -2.236 \\

\end{aligned}

}

$$

---
## Let's use the given roots to see if method 1 works in theory or not.

So we have the roots as:

$$

\boxed{

\begin{aligned}

\lambda_1 &= 1 \\

\lambda_2 &= \sqrt{5} \approx 2.236 \\

\lambda_3 &= -\sqrt{5} \approx -2.236 \\

\end{aligned}

}

$$

which are the eigenvalues.

The CHT says that:

For a given matrix $A_{n\times n}$, we have to prove that:

$$(A \ - \ \lambda I) \ = \ 0$$

or it should result in a $3\times3$ null matrix:

$$
\left[
\begin{array}{ccc}
  0 & 0 & 0  \\
  0 & 0 & 0 \\
  0 & 0 & 0  
\end{array}
\right]
$$

However, unfortunately that's not the case, as you will see below.

Applying into equation:

$$
A \ - \ \lambda I 
$$

For $\lambda_1 \ = \ 1$

$$
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] \ - \ 
\left[
\begin{array}{ccc}
  1 & 0 & 0  \\
  0 & 1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
  0 & 2 & 0  \\
  2 & -2 & 0 \\
  0 & 0 & 0  
\end{array}
\right]
$$

which unfortunately is not the null matrix.

For $\lambda_2 \ = \ 2.236$

$$
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] \ - \ 
\left[
\begin{array}{ccc}
  2.236 & 0 & 0  \\
  0 & 2.236 & 0 \\
  0 & 0 & 2.236  
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
  -1.236 & 2 & 0  \\
  2 & -3.236 & 0 \\
  0 & 0 & -1.236  
\end{array}
\right]
$$

which also, again, is not the null matrix.

For $\lambda_3 \ = \ -2.236$

$$
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] \ - \ 
\left[
\begin{array}{ccc}
  -2.236 & 0 & 0  \\
  0 & -2.236 & 0 \\
  0 & 0 & -2.236  
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
  3.236 & 2 & 0  \\
  2 & 1.236 & 0 \\
  0 & 0 & 3.236  
\end{array}
\right]
$$


which also, again, is not the null matrix.

---
## Key takeaway?

Sure the roots didn't pan out. But:

We don't have to use this method from the video:

![Pasted image 20250810143500.png](/img/user/media/Pasted%20image%2020250810143500.png)

which will lead into all sorts of messes to find out the equation of:

$$
-\lambda^3 \ + \ \lambda^2 \ + \ 5\lambda \ - \ 5 \ = \ 0
$$

which is almost the same in the video:

![Pasted image 20250810143622.png](/img/user/media/Pasted%20image%2020250810143622.png)


that we can just achieve if we multiply both sides by -1

$$
\lambda^3 \ - \ \lambda^2 \ - \ 5\lambda \ + \ 5 \ = \ 0
$$

But, for continuity's sake, let's not do that and continue with our previously achieved equation:

$$
\boxed{-\lambda^3 \ + \ \lambda^2 \ + \ 5\lambda \ - \ 5 \ = \ 0}
$$

Remember the end goal here is to check if:

$$
A \ - \ \lambda I 
$$

equates to zero or not.

So, how do we proceed after this?

We just replace $\lambda$ with the matrix $A$.

from the equation:

$$
\boxed{-\lambda^3 \ + \ \lambda^2 \ + \ 5\lambda \ - \ 5 \ = \ 0}
$$

which is derived from:

$$
A \ - \ \lambda I
$$

So the equation becomes:

$$
\boxed{-A^3 \ + \ A^2 \ + \ 5A \ - \ 5 \ = \ 0}
$$

Now we verify the LHS part only to see if it equates to zero or not.

Also we must add a tweak:

$$
\boxed{-A^3 \ + \ A^2 \ + \ 5A \ - \ 5I \ = \ 0}
$$

since we are replacing the eigenvalues with entire matrices, every term must be on the same size of the replacement matrix.

Since the last term was just a constant, we can write $5 \ = \ 5\times1 \ = \ 5 \times \ I$ , where $I$ is the corresponding identity matrix.

Why did we do this?

==A scalar like 5 cannot be added to or subtracted from a matrix; the objects must be conformable. The identity matrix I acts as the multiplicative identity for matrices, so the constant term is represented as 5I (a matrix with 5 on the diagonal and 0 elsewhere). This way every term is a 3×3 matrix and they can be summed.==

So, 

$$
-A^3 \ + \ A^2 \ + \ 5A \ - \ 5I \
$$

$$
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]^3 
\ + \
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]^2 
\ + \ 
5\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
\ - \ 
5\left[
\begin{array}{ccc}
  1 & 0 & 0  \\
  0 & 1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$

Welp, the matrix multiplication is gonna be a pain lol.

So,:

$$
A^2 \ = \ 
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] 
\ \times \ 
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$

$$
\implies 
\left[
\begin{array}{ccc}
   (1\times1 \ + \ 2\times2 \ + \ 0) & (1\times2 \ + \ 2\times -1 \ + \ 0) & (0 \ + \ 0 \ + \ 0)  \\
   (2\times1 \ + \ -1\times2 \ + \ 0) & (2\times2 \ + \ -1\times -1 \ + \ 0) & (0 \ + \ 0 \ + \ 0)  \\
  (0 \ + \ 0 \ + \ 0) & (0 \ + \ 0 \ + \ 0) & (0 \ + \ 0 \ + \ 1)  \\
\end{array}
\right]
$$


$$
= \ \left[
\begin{array}{ccc}
  5 & 0 & 0  \\
  0 & 5 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$


Now,

$$
A^3 \ = \ 
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] 
\ \times \ 
A^2 \ = 
\left[
\begin{array}{ccc}
  5 & 0 & 0  \\
  0 & 5 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$


$$
\implies 
\left[
\begin{array}{ccc}
   (1\times5 \ + \ 0 \ + \ 0) & (0 \ + \ 2\times 5 \ + \ 0) & (0 \ + \ 0 \ + \ 0)  \\
   (2\times5 \ + \ 0 \ + \ 0) & (0 \ + \ -1\times 5 \ + \ 0) & (0 \ + \ 0 \ + \ 0)  \\
  (0 \ + \ 0 \ + \ 0) & (0 \ + \ 0 \ + \ 0) & (0 \ + \ 0 \ + \ 1)  \\
\end{array}
\right]
$$

$$
= \ \left[
\begin{array}{ccc}
  5 & 10 & 0  \\
  10 & -5 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$


And lastly,

$$
5A \ = \ 
5 \times
\left[
\begin{array}{ccc}
  1 & 2 & 0  \\
  2 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right] 
$$


$$
= \ \left[
\begin{array}{ccc}
  5 & 10 & 0  \\
  10 & -5 & 0 \\
  0 & 0 & 5  
\end{array}
\right] 
$$


and:

$$
5I \ = \ 
\left[
\begin{array}{ccc}
  5 & 0 & 0  \\
  0 & 5 & 0 \\
  0 & 0 & 5 
\end{array}
\right]
$$



Finally arranging them all together:

$$
- \left[
\begin{array}{ccc}
  5 & 10 & 0  \\
  10 & -5 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
\ + \
\left[
\begin{array}{ccc}
  5 & 0 & 0  \\
  0 & 5 & 0 \\
  0 & 0 & 1  
\end{array}
\right] 
\ + \ 
\left[
\begin{array}{ccc}
  5 & 10 & 0  \\
  10 & -5 & 0 \\
  0 & 0 & 5  
\end{array}
\right]
\ - \ 
\left[
\begin{array}{ccc}
  5 & 0 & 0  \\
  0 & 5 & 0 \\
  0 & 0 & 5 
\end{array}
\right]
$$

$$
= \ \left[
\begin{array}{ccc}
 0 & 0 & 0 \\
 0 & 0 & 0 \\
 0 & 0 & 0 
\end{array}
\right]
$$


which is now, the null matrix or zero matrix.


Thus:

$$
\boxed{
A \ - \ \lambda I \ = \ 0
}
$$

or for a better statement:

$$
p(A) \ = \ \boxed{-\lambda^3 \ + \ \lambda^2 \ + \ 5\lambda \ - \ 5 \ = \ 0}
$$

is proved, which verifies the Cayley-Hamilton Theorem for this matrix.

---
# Symmetric matrices

https://www.youtube.com/watch?v=vSczTbgc8Rc (watch the first two halves of the video to understand all about symmetric matrices)

## Definition and basic properties

- A real matrix $A \ \in \ R^{n\times n }$  is symmetric if $A \ = \ A^T$, where $T$ is the transpose of $A$
- Entries mirror across the main diagonal: $a_{ij} = a_{ji}$.
- Symmetric matrices are always diagonalizable over R and have real eigenvalues.
- Their eigenvectors are orthogonal i.e. perpendicular to each other.

![Pasted image 20250814185919.png](/img/user/media/Pasted%20image%2020250814185919.png)

See how the elements on both sides of the diagonal, except the starting and ending element are the same? These are called symmetric matrices.


---
# Diagonalization of matrices (symmetric matrices)

https://www.youtube.com/watch?v=sikqqbbJUXc&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=13

For a matrix $A$, it's diagonalized version can be obtained by using this formula:

$$
D \ = \ M^{-1}A \ M
$$

where:

$M$ is the modal matrix, which is obtained as follows:

## Steps to obtain the modal matrix.

1. Write the characteristic equation $\det(A \ - \ \lambda \ I) \ = \ 0$
2. Solve L.H.S to get a characteristic equation of type $\lambda^3 \ \pm a\lambda^2 \ \pm \ b\lambda \ \pm \ c$
3. Instead of replacing $\lambda$ with $A$, solve the equation to find the roots i.e. the eigenvalues. (Refer to previous sections)
4. Substitute the eigenvalues in the derived equation to get the eigenvectors in form of:

$$
x_1 \ = \ 
\left[
\begin{array}{ccc}
a_1 \\
b_1 \\
c_1 \\
\end{array}
\right]
$$

$$
x_2 \ = \ 
\left[
\begin{array}{ccc}
a_2 \\
b_2 \\
c_2 \\
\end{array}
\right]
$$

$$
x_3 \ = \ 
\left[
\begin{array}{ccc}
a_3 \\
b_3 \\
c_3 \\
\end{array}
\right]
$$


Now, the modal matrix $M$ is achieved by:

$$
M \ = \ 
\left[
\begin{array}{ccc}
\left[
\begin{array}{ccc}
a_1 \\
b_1 \\
c_1 \\
\end{array}
\right] & 
\left[
\begin{array}{ccc}
a_2 \\
b_2 \\
c_2 \\
\end{array}
\right] & 
\left[
\begin{array}{ccc}
a_3 \\
b_3 \\
c_3 \\
\end{array}
\right]
\\
\end{array}
\right]
$$

By writing each eigenvector as the column vectors of the modal matrix.

Then we can calculate the inverse, plug them in the formula, and after doing the math :

We should get a matrix like this

$$
D \ = \
\left[
\begin{array}{ccc}
  a & 0 & 0  \\
  0 & b & 0 \\
  0 & 0 & c  
\end{array}
\right]
$$


which is the diagonal matrix. If we don't get this matrix, then it means the given matrix is **not diagonalizable**.

---
## Example

For example please refer to the examples in the video :

https://www.youtube.com/watch?v=sikqqbbJUXc&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=13


---
# Orthogonal Matrix

https://www.youtube.com/watch?v=wciU07gPqUE&t=117s (watch this part)

An orthogonal matrix is basically a matrix whose column vectors are orthogonal (perpendicular to each other), and also their dot product would equate to zero.

![Pasted image 20250817135734.png](/img/user/media/Pasted%20image%2020250817135734.png)


And the column vector's length is always one, hence they are unit vectors.

For example if we take the column vector:

$$
\left[
\begin{array}{ccc}
\frac{\sqrt{2}}{2} \\
-\frac{\sqrt{2}}{2}
\end{array}
\right]
$$


we can find the length of this column vector by taking the square root of the sum of the squares of the elements:

$$
\sqrt{(\frac{\sqrt{2}}{2})^2 \ + \ (-\frac{\sqrt{2}}{2})^2} \ = \ 
\sqrt{(\frac{2}{4}) \ + \ (\frac{2}{4})} \ = \ \sqrt{\frac{1}{2} \ + \ \frac{1}{2}} \ = \ \sqrt{1} \ = \ 1
$$

Same goes for the other column vector, which means these are unit vectors.

---
# Gram-Schmidt Orthogonalization

https://www.youtube.com/watch?v=UOZjINOGLog (must watch)

https://www.youtube.com/watch?v=rHonltF77zI (another way to visualize this)

https://www.youtube.com/watch?v=tu1GPtfsQ7M (example of method 2)

---
