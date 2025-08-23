---
{"dg-publish":true,"permalink":"/mathematics-1-a/module-3-matrices/","title":"Matrices -- Module 3 -- Mathematics -IA","tags":["Semester-1","Mathematics-1A"],"created":"2025-07-30T13:48:14.105+05:30"}
---

---
# Index

1. [[#What are Matrices?]]
2. [[#What is a Vector?]]
3. [[#Vector Addition]]
4. [[#Scalar Multiplication]]
5. [[#Quick Recap Other Vector Operations]]
6. [[#Matrix multiplication]]
7. [[#Linear system of equations and how to solve them, methods of solving them]]
8. [[#Linear Independence]]
9. [[#Rank of a matrix]]
10. [[#Methods to find the rank of a matrix]]
11. [[#Cramer's rule]]
12. [[#The Matrix Inversion method.]]
13. [[#Matrix Inversion method (Adjugate matrix version)]]

---
# What are Matrices?

## 1. What is a Matrix?

A **matrix** is a rectangular array of numbers or symbols arranged in rows and columns. For example:

$$
\left[
\begin{array}{ccc}
2 & 3 & 4\\
5 & 6 & 7
\end{array}
\right]
$$

- The matrix above has **2 rows** and **3 columns**.
- Such a matrix is called a $2 \times 3$ (read as "2 by 3") matrix.

---
## 2. Types of Matrices

### a) Row Matrix

A matrix with just one row.

$$
\left[
\begin{array}{ccc}
2 & 3 & 4\\
\end{array}
\right]
$$

---
### b) Column Matrix

A matrix with just one column.

$$
\left[
\begin{array}{ccc}
2 \\
5
\end{array}
\right]
$$

---
### c) Square Matrix

Number of rows equals number of columns.

$$
\left[
\begin{array}{ccc}
a & b \\
c & d
\end{array}
\right]
$$

---
### d) Diagonal Matrix

A square matrix where all elements off the main diagonal are zero.

$$
\left[
\begin{array}{ccc}
  1 & 0 & 0  \\
  0 & -1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$

---
### e) Scalar Matrix

A diagonal matrix where all diagonal elements are equal.

$$
\left[
\begin{array}{ccc}
2 & 0 \\
0 & 2
\end{array}
\right]
$$

---
### f) Identity Matrix (Unit Matrix)

A diagonal matrix with all main diagonal elements equal to 1.

$$
\left[
\begin{array}{ccc}
  1 & 0 & 0  \\
  0 & 1 & 0 \\
  0 & 0 & 1  
\end{array}
\right]
$$

---
### g) Zero Matrix (Null Matrix)

All elements are zero.

$$
\left[
\begin{array}{ccc}
0 & 0 \\
0 & 0
\end{array}
\right]
$$

---
## 3. Matrix Notation

- $A_{m\times n}$: A matrix named $A$ with $m$ rows and $n$ columns.
- Element at row $i$, column $j$ is denoted $a_{ij}$.

---
# Vectors

## What is a Vector?

A **vector** is an object that has both **magnitude** (length) and **direction**. In the context of algebra and matrices, a vector is typically represented as an ordered list of numbers, which can be written as a column or a row. For example, in 3D space:

$$
v \ = \ 
\left[
\begin{array}{ccc}
2 \\
-1 \\
5
\end{array}
\right]
$$

This is a column vector in $R^3$ (3-dimensional real space).

![Pasted image 20250730141410.png](/img/user/media/Pasted%20image%2020250730141410.png)


---
## Types of Vectors

- **Column vector:** Written as an n×1n×1 matrix, like above.
- **Row vector:** Written as a 1×n1×n matrix, e.g.

$$
\left[
\begin{array}{ccc}
2 & -1 & 5\\
\end{array}
\right]
$$

---
## Vector Addition

If you have two vectors **of the same size**:

$$
a \ = \ 
\left[
\begin{array}{ccc}
a_1 \\
a_2 \\
\vdots \\
a_n
\end{array}
\right]
\ \ 
b \ = \ 
\left[
\begin{array}{ccc}
b_1 \\
b_2 \\
\vdots \\
b_n
\end{array}
\right]
$$

Their sum is:

$$
a \ + \ b \ = \ 
\left[
\begin{array}{ccc}
a_1 \ + \ b_1\\
a_2 \ + \ b_2 \\
\vdots \\
a_n \ + \ b_n
\end{array}
\right]
$$

Example:

$$
a \ = \ 
\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right]
, \ \ 
b \ = \ 
\left[
\begin{array}{ccc}
3 \\
5
\end{array}
\right]
\ \implies
\left[
\begin{array}{ccc}
1 \ + \ 3 \\
2 \ + \ 5
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
4 \\
7
\end{array}
\right]
$$

**Geometric interpretation:** Scalar multiplication stretches or shrinks the vector, and if the scalar is negative, it reverses its direction.

![Pasted image 20250730142606.png](/img/user/media/Pasted%20image%2020250730142606.png)

Note the differences in the length of the lines of the vector after addition

---
## Scalar Multiplication

Given a scalar (number) $k$, and a vector $a$:

$$
ka \ = \ 
k
\left[
\begin{array}{ccc}
a_1 \\
a_2 \\
\vdots \\
a_n
\end{array}
\right]
\ = \
\left[
\begin{array}{ccc}
ka_1 \\
ka_2 \\
\vdots \\
ka_n
\end{array}
\right]
$$

Example:

$$
k \ = \ 3, \
a \ = \ 
\left[
\begin{array}{ccc}
-2 \\
4
\end{array}
\right]
\ \implies \ 
3a \ = \ 
\left[
\begin{array}{ccc}
3\times-2 \\
3\times4
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
-6 \\
12
\end{array}
\right]
$$

**Geometric interpretation:** Scalar multiplication stretches or shrinks the vector, and if the scalar is negative, it reverses its direction.

---
## Quick Recap: Other Vector Operations

### Dot Product (Scalar Product)

**Definition:**  
The dot product of two vectors $\vec{a}$ and $\vec{b}$ in $R^n$ is a scalar given by:

$$\vec{a}\ \cdot \ \vec{b} \ = \ a_1b_1 \ + \ a_2b_2 \ + \ \cdots \ a_nb_n$$

It can also be written as:

$$\vec{a} \ \cdot \ \vec{b} \ = \ |\vec{a}||\vec{b}| \ \cdot \ cos\theta$$

where $\theta$ is the angle between the vectors.

#### Example 1:

Let $\vec{a} \ = \ [\ 2, 3 , 4\ ]$ and $\vec{b} \ = \ [\ 1, 0, -2 \ ]$ 

$$\vec{a} \ \cdot \ \vec{b} \ = \ 2(1) \ + \ 3(0) \ + \ 4(-2)$$

$$\vec{a} \ \cdot \ \vec{b} \ = \ 2 \ - \ 8 \ = \ -6$$

#### Example 2:

Let:

$$\vec{a} = [\ 3 \ 4 \ ] $$
and 

$$ \vec{b} = [\ 4 \ 3 \ ]$$

We are asked to find the angle between these two vectors.
##### Step 1: Compute the dot product

$$\vec{a} \ \cdot \ \vec{b} \ = \ 3\times4 \ + \ 4\times 3 \  = 24$$

##### Step 2: Compute the magnitudes

$$|\vec{a}| \ = \ \sqrt{3^2 \ + \ 4^2} \ = \sqrt{9+16} \ = \sqrt{25} \ = \ 5$$

$$|\vec{b}| \ = \ \sqrt{4^2 \ + \ 3^2} \ = \ \sqrt{16 \ + \ 9} \ = \ \sqrt{25} \ = \ 5$$

##### Step 3: Plug into formula to find the angle:


$$\vec{a} \ \cdot \ \vec{b} \ = \ |\vec{a}||\vec{b}| \ \cdot \ cos\theta$$

$$\implies 24 \ = \ 25 \ \times \ cos \ \theta$$
$$\implies cos \ \theta \ = \ \frac{24}{25}$$

$$\theta \ = \ cos^{-1}(\frac{24}{25}) \ =\ cos^{-1}(0.96) \ \approx \ 16.26^{o}$$

---
### Cross Product(Vector Product)

**Definition:**  
The cross product of two vectors in $R_3$ $\vec{a} \times \vec{b},$ is a **vector** perpendicular to both, with direction given by the right-hand rule and magnitude $|\vec{a}||\vec{b}|sin\theta$, where $\theta$ is the angle between them.

The formula is:

$$\vec{a} \ \times \ \vec{b} \ = \ 
\begin{vmatrix}
  \hat{i} & \hat{j} & \hat{k}  \\
  a_1 & a_2 & a_3 \\
  b_1 & b_2 & b_3  
\end{vmatrix}
$$


$$= [\ (a_2b_3 \ - \ a_3b_2)\hat{i}, \ (a_3b_1 \ - \ a_1b_3)\hat{j}, \ (a_1b_2 \ - \ a_2b_1)\hat{k} \ ]$$

---
#### Example:

Let $\vec{a} \ = \ [\ 1, 2, 3 \ ]$ and $\vec{b} \ = \ [\ 4, 5, 6 \ ]$

$$
\vec{a} \ \times \ \vec{b} \ = \ 
\left[
\begin{array}{ccc}
 \hat{i} & \hat{j} & \hat{k}\\
 1 & 2 & 3\\
 4 & 5 & 6\\
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
 ((2\times6)-(5\times3))\hat{i}\\
 ((4\times3) - (6\times1))\hat{j}\\
 ((5\times1) - (4\times2))\hat{k}\\
\end{array}
\right]
$$

$$
\vec{a} \times \vec{b} \ = \ 
\left[
\begin{array}{ccc}
-3 \hat{i}\\
 6 \hat{j}\\
-3 \hat{k}\\
\end{array}
\right]
$$

---
# Matrix multiplication

https://www.youtube.com/watch?v=2spTnAiQg4M

## What is Matrix Multiplication?

Matrix multiplication is an operation that takes two matrices and produces another matrix. It’s not just multiplying each corresponding entry; instead, you sum the products of rows and columns.

---
## How to verify if the order of multiplication of two matrices is valid or not.

Take these two matrices from the video.

![Pasted image 20250810145139.png](/img/user/media/Pasted%20image%2020250810145139.png)


Note how their $n$ (if you write $n \times m$) or $m$ if you write ($m \times n$) but the order of a matrix is basically :

$row \ \times \ column$.

**If the number of columns of the first matrix, equates to the number of rows of the second matrix, then we can multiply the two matrices**.

Which is why $A \times B$ is valid.

But if you try:

![Pasted image 20250810145351.png](/img/user/media/Pasted%20image%2020250810145351.png)


$B \times A$ , it's not valid since $B$ has 2 columns and $A$ has only 1 row. The numbers don't match.

So yes, **the order of multiplication of matrices does matter** here.

---
## How to Multiply Two Matrices

You can either the watch the video, or read the following here:

Suppose:

$$
A \ = \ 
\left[
\begin{array}{ccc}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{array}
\right]
, \ B \ = \ 
\left[
\begin{array}{ccc}
b_{11} & b_{12} \\
b_{21} & b_{22}
\end{array}
\right]
$$

The element in the $i-th$ row and $j-th$ column of $AB$ is:

$$(AB)_{ij} \ = \ \sum^n_{k=1}{a_{ik}b_{kj}}$$

Or in simple words: **dot the $i$-th row of $A$ with the $j$-th column of $B$.**

---
### Example

$$
A \ = \ 
\left[
\begin{array}{ccc}
2 & 3 \\
4 & 5
\end{array}
\right]
, \ B \ = \ 
\left[
\begin{array}{ccc}
6 & 7 \\
8 & 9
\end{array}
\right]
$$

We have to multiply these new matrices.

Let the product matrix be named : $C$

So, 

- $C_{11} \ = \ (2\times6) \  +  \ (3 \times 8) \ = \ 36$ (first row of A and first column of B)
- $C_{12} \ = \ (2\times7) \ + \ (3\times9) \ = \ 41$ (first row of A and second column of B)
- $C_{21} \ = \ (4\times6) \ + \ (5\times8) \ = \ 64$ (second row of A and first column of B)
- $C_{22} \ = \ (4\times7) \ + \ (5\times9) \ = \ 73$ (second row of A and second column of B)

So, the product of the two matrices $A$ and $B$, $C$ is :

$$
A \ = \ 
\left[
\begin{array}{ccc}
36 & 41 \\
64 & 73
\end{array}
\right]
$$

---
## Key Properties of Matrix Multiplication

- **Not Commutative**: $AB \ \neq \ BA$(in general)
- **Associative**: $(AB)C=A(BC)$
- **Distributive**: $A(B+C)=AB+AC$
- **Multiplication by Identity**: $AI=IA=A$, where $I$ is the identity matrix

---
# Linear system of equations and how to solve them, methods of solving them

For people like me who are revisiting Semester 1 math after crossing semester 6, you will probably know the content bomb that I am about to drop here from sem 6 notes.

For first timers however, it will still be just as easily understandable to you.

The following content will cover:

1. Gaussian Elimination method of solving a system of linear equations
2. Gauss-Jordan method of solving a system of linear equations
3. Matrix inversion method (using two ways) and using the method of matrix inversion to solve a system of linear equations
4. Determinant of a matrix (2x2) and (3x3)
5. Transpose of a matrix

By all means, enjoy:

---
# Gaussian Elimination method to find the solution for a system of linear equations

This method converts a system of equations into an upper-triangular form (where all entries below the main diagonal are zero) so that you can then solve for the unknowns via back substitution.

https://www.youtube.com/watch?v=eDb6iugi6Uk

## Example 1

So let's say we have this system of linear equations here

![Pasted image 20250405122420.png](/img/user/media/Pasted%20image%2020250405122420.png)


So first of what we will do is construct an augmented matrix using the coefficients of the equations.

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  2 & -1 & 1 & 5 \ \\
  -1 & 2 & 2 & 1 \
\end{array}
\right]
$$

Now what we need to do is to **convert this to a row-echelon form**.

The row-echelon form of this matrix should be something like this :

![Pasted image 20250405131719.png](/img/user/media/Pasted%20image%2020250405131719.png)


Note that  the bottom left half elements below the diagonal line are all zeroes. (Only works for perfect square matrices)


![Pasted image 20250405132915.png](/img/user/media/Pasted%20image%2020250405132915.png)

(Image generated by the new version of ChatGPT, not bad indeed.)


So with this matrix, let's call it $A$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  2 & -1 & 1 & 5 \ \\
  -1 & 2 & 2 & 1 \
\end{array}
\right]
$$


How do we convert it to a row-echelon form?

It's done by doing something called a **matrix transformation** via **matrix row operations**.

So first of all we select a **pivot element**. A pivot element is the **first non-zero element** we encounter in a matrix.

In $R_1$ we have the first non-zero element as 1. So we select that as the pivot element.

Now all our operations will be centered around $R_1$.

So we can do $$R_3 \rightarrow R_1 \ + \ R_3 $$

So the matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  2 & -1 & 1 & 5 \ \\
  0 & 3 & 1 & -1 \
\end{array}
\right]
$$

**Remember that when we add two rows, all elements of the rows are affected**.

We can then try :  

$$R_2 \to R_2 \ - \ 2R_1$$
$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  0 & -3 & 3 & 9 \ \\
  0 & 3 & 1 & -1 \
\end{array}
\right]
$$

Then we can do :

$$R_3 \to R_3 \ + \ R_2 $$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  0 & -3 & 3 & 9 \ \\
  0 & 0 & 4 & 8 \
\end{array}
\right]
$$


We are already there

This can be done by simply for $R_2$ as:

$$R_2 \ \to \ -\frac{1}{3} \ \times R_2$$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  0 & 1 & -1 & -3 \ \\
  0 & 0 & 4 & 8  \
\end{array}
\right]
$$

We have already reached the row-echelon form, but,

We can further simplify the matrix by performing an operation on $R_3$ :

$$R_3 \ \to \frac{1}{4} \ \times 8$$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & -2 \  \\
  0 & 1 & -1 & -3 \ \\
  0 & 0 & 1 & 2  \
\end{array}
\right]
$$

Now we can convert the matrix back to equations as :

$$x \ + \ y \ - \ z \ = \ -2$$

$$ y \ - \ z \ = \ -3$$

$$z \ = \ 2$$

Now with some simple substitution :

$$x \ + \ y \ - \ 2 \ = \ -2 \ \implies x \ + \ y \ = \ 0 \ \implies \ x \ = \ - y$$

Thus :

$$ y \ - \ 2 \ = \ -3 \ \implies \ y \ = \ -3 \ + \ 2 \ \implies y \ = \ -1$$

Therefore :

$$ x \ = \ -(-1) \ = 1 $$

So we have the solution for the system of equations as:

$$\boxed{ x \ = \ 1 ; \ y \ = \ -1 ; \ z \ = \ 2}$$
---
### Summary:

**Always use the format:**

$$ R_{\text{target}} \to R_{\text{target}} - m\,R_{\text{pivot}}$$

where :

$$ m \ = \ \frac{Coefficient  \ of \ target \ x \ , y \ or z}{Coefficient  \ of \ pivot \ x \ , y \ or z}$$

For example if we have the rows :

- **Pivot Row (Row 1):**  
    $$ [2 \quad 1 \quad -1 \mid 1]$$
     
    Here, if you want to eliminate the $x$-variable, the pivot coefficient is 2.
    
- **Target Row (Row 2):**  
    $$ [3 \quad 2 \quad 1 \mid 10]$$
      
    The target coefficient for the $x$-variable in Row 2 is $3$.****

---
## Example 2 

![Pasted image 20250405130111.png](/img/user/media/Pasted%20image%2020250405130111.png)


So we can write the matrix as:

$$
\left[
\begin{array}{ccc|c}
  2 & 1 & -1 & 1 \  \\
  3 & 2 & 1 & 10 \ \\
  2 & -1 & 2 & 6  \
\end{array}
\right]
$$

Here we will select the pivot element as 2.

So all our operations will be centered around $R_1$ for now.

So to solve remove the coefficients of $x$ of $R_2$ and $R_3$ to zero, we will follow the rules mentioned above:

So the target row is $R_3$ and the pivot row is $R_1$.

So $m \ = \ \frac{2}{2} \ = 1$

So $$R_3 \ \to \ R_3 \ - \ m \ \times R_1 \ \implies \ R_3 \ \to \ R_3 \ - \ \frac{2}{2} \ \times R_1 \ \implies R_3  \ - \ R_1$$

So  

$$R_3 \ = [[2 - 2], \ [-1 \ - \ 1], \ [2 \ - \ (-1)], \ | \ 6 \ - \ 1]$$

$$ R_3 \ = \ [0, \ -2 \ , \ 3 \ | \ 5 ] $$

Therefore the matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  2 & 1 & -1 & 1 \  \\
  3 & 2 & 1 & 10 \ \\
  0 & -2 & 3 & 5  \
\end{array}
\right]
$$

Now for Row 2, we have :

$$m \ = \ \frac{3}{2}$$

Thus Row 2 will be :

$$R_2 \ \to R_2 \ - \ \frac{3}{2} \ \times R_1$$


$$R_2 \ = [ \ [3 \ - \ \frac{3 \ \times 2}{2}], \ [2 \ - \ \frac{3 \ \times 1}{2}], \ [1 \ - \ \frac{3 \ \times \ (-1)}{2}], \ | \ 10 \ - \ \frac{3 \ \times 1}{2} \ ]$$

$$R_2 \ = \ [ \ 0, \ 0.5, \ 2.5 \ | \ 8.5   \ ]$$


Therefore the matrix now becomes :

$$
\left[
\begin{array}{ccc|c}
  2 & 1 & -1 & 1 \  \\
  0 & 0.5 & 2.5 & 8.5 \ \\
  0 & -2 & 3 & 5  \
\end{array}
\right]
$$

Now let's remove the $y$ component of $R_3$ and set it to zero.

So our pivot component for $y$ is $0.5$ in $R_2$.

### But why change pivots now?

==The reason is that each pivot is used to clear the entries below it in its column.== $R_1$​ has already been used to eliminate the $x$-terms in the lower rows. Now, to get the matrix into row-echelon form, the next pivot must appear in a lower row than $R_1$​. In this case, that pivot is in $R_2$​, and it is used to eliminate the $y$-term in $R_3$​.

The way pivots are chosen are that they are taken from a column **which hasn't been used for a pivot, yet**.


So :

$$m \ = \ \frac{-2}{\frac{1}{2}} \ = \ -2 \ \times 2 \ = \ -4$$

Therefore $R_3$ will become :

$$R_3 \ \to R_3 \ + \ 4R_2$$

So $R_3$ will be:

$$R_3 \ = \ [\ [0 \ + \ 4 \ \times 0 ], \ [-2 \ + \ 4 \ \times 0.5], \ [3 \ + \ 4 \ \times 2.5], \ | \ 5 \ + \ 4 \ \times 8.5  \ ]$$

Thus,

$$R_3 \ = \ [\ 0, \ 0 , \  13 \ | \ 39 ]$$

So the matrix will become :

$$
\left[
\begin{array}{ccc|c}
  2 & 1 & -1 & 1 \  \\
  0 & 0.5 & 2.5 & 8.5 \ \\
  0 & 0 & 13 & 39  \
\end{array}
\right]
$$



Now let's convert this matrix back to a system of equations :

$$2x \ + \ y \ - \ z \ = \ 1$$


$$0.5y \ + \ 2.5z \ = \ 8.5$$


$$13z \ = \ 39$$

So we get :

$$z \ = \ 3$$

$$0.5y \ + \ 2.5 \ \times 3 \ = \ 8.5$$


$$\implies \ 0.5y \ + \ 7.5 \ = \ 8.5$$


$$\implies \ 0.5y \ = \ 1$$


$$\implies y \ = \ \frac{1 \ \times 2}{1}$$


$$\implies y \ = \ 2$$


And finally :

$$2x \ + \ 2 \ - \ 3 \ = 1$$


$$\implies \ 2x \ -1 \ = \ 1 $$


$$\implies \ 2x \ = \ 2$$

$$\implies \ x \ = \ 1$$

Thus :

$$\boxed{x = 1, \ y = 2, \ z = 3}$$


---
# Gauss-Jordan Elimination Method

This is similar to the previous method, except here we reduce the matrix even further, to something called a "**reduced row echelon form**".

https://www.youtube.com/watch?v=eYSASx8_nyg


![Pasted image 20250405201153.png](/img/user/media/Pasted%20image%2020250405201153.png)

Now this, is the reduced row echelon form.

where $a, d, f = 1$ , essentially resulting in the **identity matrix** (for square matrices only).

The identity matrix is :

![Pasted image 20250405220936.png](/img/user/media/Pasted%20image%2020250405220936.png)

where the diagonal elements of the matrix are 1 and all the other elements are zero.


So let's say we have this system of equations here:

![Pasted image 20250405182359.png](/img/user/media/Pasted%20image%2020250405182359.png)


We will solve them in the same manner as we did before, only that there will be a few more operations now.


So let's convert this system of equations to an augmented matrix first.

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  1 & -1 & 2 & 3 \ \\
  2 & 1 & 1 & 9  \
\end{array}
\right]
$$

Let's set the pivot element to 1 for the $x$ component.

So the target row is $R_2$. 

Thus, 

$$m \ = \ \frac{1}{1} \ = \ 1$$

So, $R_2$ will be:

$$ R_2 \ \to \ R_2 \ - \ R_1 $$

$$\implies R_2 \ = \ [ \  [0], \ [-2], \ [3], \ | \ -4 \ ] $$


So the matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  0 & -2 & 3 & -4 \ \\
  2 & 1 & 1 & 9  \
\end{array}
\right]
$$


Now the target is $R_3$. So :

$$m \ = \ \frac{2}{1} \ = \ 2$$

So:  

$$R_3 \ \to \ R_3 \ - \ m \ \times R_1$$


$$\implies R_3 \ = \ [ \ [ 2 \ - \ 2 ], \ [1 \ - \ 2], \ [1 \ - \ 2(-1)], \ | \  9 \ - \ 14  \ \ ]$$

$$\implies R_3 \ = \ [ \ [0], \ [-1], \ [3] \ | \ -5 \ ]$$

So the matrix becomes:

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  0 & -2 & 3 & -4 \ \\
  0 & -1 & 3 & -5  \
\end{array}
\right]
$$


Now we set the pivot element to -2 for the $y$ component of $R_3$

Thus, 

$$m \ = \ \frac{-1}{-2} \ = \ \frac{1}{2}$$

So :

$$R_3 \ \to \ R_3 \ - \ \frac{1}{2} \ \times \ R_2$$

$$\implies \ R_3 \ = \ [ \ [0 - \frac{1}{2} \ \times 0], \ [-1 \ - \ (\frac{1}{2} \ \times -2)], \ [3 \ - \ (\frac{1}{2} \ \times 3)] \ | \ -5 \ - \ (\frac{1}{2} \ \times -4)  \ \ ]$$

$$\implies R_3 \ = \ [ \ [0], \ [0], \ [1.5] \ | \ -3]$$

So, the matrix now becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  0 & -2 & 3 & -4 \ \\
  0 & 0 & 1.5 & -3  \
\end{array}
\right]
$$


Now for the $z$ component for $R_2$ , we can set the pivot to 1 of $R_3$. by doing $R_3 \ \to \frac{2}{3} \ \times R_3$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  0 & -2 & 3 & -4 \ \\
  0 & 0 & 1 & -2  \
\end{array}
\right]
$$


So:

$$m \ = \ \frac{3}{1} \ = \ 3$$


**Note**: If we instead tried to set $R_1$'s -1 as the pivot, it would then affect $R_2$'s $x$ component while calculation. So it's better to use a row which won't be affected in future, that being $R_3$

So, 

$$R_2 \ \to \ R_2 \ - \ 3R_3$$



$$\implies \ R_2 \ = \ [ \ 0, \ -2, \ 0 \ | \ 2 \ ] $$


So, the matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  0 & -2 & 0 & 2 \ \\
  0 & 0 & 1 & -2  \
\end{array}
\right]
$$



Now for $R_1$, :

$$m \ = \ \frac{1}{-1} \ = \ -1$$


So :

$$R_1 \ \to \ R_1 \ + \ R_3$$


$$\implies R_1 \ = \ [\  1, \ 1, \ 0 \ | \ 5 \ ] $$

Thus the matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & 0 & 5 \  \\
  0 & -2 & 0 & 2 \ \\
  0 & 0 & 1 & -2  \
\end{array}
\right]
$$

Now, for the $y$ component of $R_1$, this may seem like that we are going against the rules of selecting a pivot where we can't reuse an already selected element for a pivot again, but during RREF (reduced row echelon form) there are two types of eliminations :
### Forward Elimination vs. Backward Elimination

1. **Forward Elimination:**  
    - **Key Point:** Once a pivot is chosen in a column, it is used to clear entries _downward_. You do not worry about entries above because those rows haven't been processed yet.
      
      We did this when we were processing the elements below the diagonal line.
      
        
2. **Backward Elimination (or Back Substitution for RREF):**  
    Once the matrix is in row-echelon form (all entries below each pivot are zero), you perform backward elimination to clear entries _above_ each pivot. This step ensures that each pivot is the only nonzero entry in its column.
    
    We are now about to do this with the $y$ component of $R_1$.
    
    - **Why This is Valid:**
        
        - The forward phase ensures that each pivot has zeros below it.
            
        - The backward phase then uses each pivot to clear _above_ it.
            
        - Even though the pivot in Row 2 was already used to clear entries below (in Row 3), it must also clear any nonzero entry above it (in Row 1) to satisfy the RREF condition (each pivot column has zeros everywhere except for the pivot itself).

So we can safely select -2 as the pivot.

So :

$$m \ = \ \frac{1}{-2}$$

Before that we scale $R_2$  by $R_2 \ \to \ -\frac{1}{2} \ \times R_2$

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & 0 & 5 \  \\
  0 & 1 & 0 & -1 \ \\
  0 & 0 & 1 & -2  \
\end{array}
\right]
$$

Now $m \ = \ 1$, (for $R_1$)

So, proceeding with $R_1$ :

$$R_1 \ \to R_1 \ - \  R_2$$


$$\implies R_1 \ = \ [1, 0, 0 \ | \ 6]$$


So, the final matrix becomes :

$$
\left[
\begin{array}{ccc|c}
  1 & 0 & 0 & 6 \  \\
  0 & 1 & 0 & -1 \ \\
  0 & 0 & 1 & -2  \
\end{array}
\right]
$$

Now we can easily convert them back to equations and get the values of $x$, $y$  and $z$.

So, 

$$x \ = \ 6 $$

$$y \ = \ -1$$

$$z \ = \ -2$$


So the solutions are :

$$\boxed{x \ = \ 6, \ y \ = \ -1, \ z \ = \ -2}$$

---
# The Matrix Inversion method.

Let's walk through the matrix inversion method step by step. The idea is that if you have a system of linear equations in the form

$$Ax=b$$

and the coefficient matrix $A$ is invertible (its determinant is nonzero), then the unique solution is given by :

$$x \ = \ A^{-1}b$$

---
## Pre-requisites before using this method (must) (skip ahead if you already know these).

1. Knowing how to find out the determinants of 2x2 and 3x3 matrix. (https://www.youtube.com/watch?v=3ROzG6n4yMc)
2. Transpose of a matrix.
3. Knowing how to find the inverses of 2x3 and 3x3 matrix. (https://www.youtube.com/watch?v=aiBgjz5xbyg) (2x2) and (https://www.youtube.com/watch?v=Fg7_mv3izR0) (3x3)



### 1. The Determinant of a $2\times2$ matrix.

The determinant of a 2x2 matrix is given by :

![Pasted image 20250406113901.png](/img/user/media/Pasted%20image%2020250406113901.png)


Let's say we have this example :

![Pasted image 20250406114138.png](/img/user/media/Pasted%20image%2020250406114138.png)



So the determinant of this matrix will be:

$$
\det \begin{vmatrix}
  -7 & 8 \\
  4 & -3
\end{vmatrix}
$$


$$
\implies [-7 \ \times -3]  \ - \ [4 \ \times 8]
$$

$$
= \ 21 \ - \ 32
$$

$$
= \ -11
$$

---
### 2. Determinant of a $3\times3$ matrix

Let's say we have a 3x3 matrix here

$$
\left[
\begin{array}{ccc}
  1 & 2 & 3 \\
  4 & 5 & 6 \\
  7 & 8 & 9 
\end{array}
\right]
$$

The determinant is given by : 

$$
\det \begin{vmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{vmatrix}
$$
 which evaluates to :

![Pasted image 20241107213319.png](/img/user/media/Pasted%20image%2020241107213319.png)


So let's say we have this example here :

![Pasted image 20250406114726.png](/img/user/media/Pasted%20image%2020250406114726.png)


The determinant of this 3x3 matrix will be:

$$
\det \begin{vmatrix}
2 & 4 & -3 \\
5 & 7 & 6 \\
-8 & 1 & 9
\end{vmatrix}
$$


$$\implies \ +2[ \ (7  \times 9)  \ - \ (1 \times 6) \ ] \ - \ 4[ \ (5 \times 9)  \ - \ (-8 \times 6) \ ] \ + \ (-3)[ \ (5 \times 1)  \ - \ (-8 \times 7) \ ]$$

$$= \ +2 \ [57] \ - \ 4[93] \ - \ 3[61]$$

$$= \ 114 \ - \ 372 \ - \ 183$$

$$-441$$

---
### 3. Determinant of a $4\times4$ matrix.




---
### 4. Transpose of a matrix.

The transpose of a matrix is just it's **rows and columns interchanged**.

$$
\left[
\begin{array}{ccc}
  1 & 2 & 3 \\
  4 & 5 & 6 \\
  7 & 8 & 9 
\end{array}
\right]
$$


The transpose of this matrix will be :

$$
\left[
\begin{array}{ccc}
  1 & 4 & 7 \\
  2 & 5 & 8 \\
  3 & 6 & 9 
\end{array}
\right]
$$


Same for a 2x2 matrix :

$$
\left[
\begin{array}{ccc}
a & b \\
c & d
\end{array}
\right]
$$


The transpose will be:

$$
\left[
\begin{array}{ccc}
a & c \\
b & d
\end{array}
\right]
$$


---
### 4. Inverse of a 2x2 matrix.

**Note: Before trying to invert a matrix, you must first verify if the matrix is invertible or not.**
**This is done by finding the determinant of the matrix and checking whether it's zero or not**.

**If the determinant is zero, the matrix is not invertible, else the matrix is invertible**.



So if we have a 2x2 matrix

$$
\left[
\begin{array}{ccc}
a & b \\
c & d
\end{array}
\right]
$$


The inverse is given by :

![Pasted image 20250406115846.png](/img/user/media/Pasted%20image%2020250406115846.png)

where $$\frac{1}{ad \ - \ bc}$$ 
is the determinant of the 2x2 matrix.

So let's say we have this matrix example.

![Pasted image 20250406120248.png](/img/user/media/Pasted%20image%2020250406120248.png)

So starting off, let's find the determinant of this matrix.


$$
\det \begin{vmatrix}
7 & 2  \\
17 & 5 
\end{vmatrix}
$$

$$= \ [7 \times 5] \ - \ [17 \times 2]$$

$$= \ 35 \ - \ 34$$

$$= \ 1$$


Now to find the inverse of this matrix :

$$A^{-1} \ = \ \frac{1}{1} \ \times 
\left[
\begin{array}{ccc}
d & -b \\
-c & a
\end{array}
\right] 
$$


or 

$$
A^{-1} \ = \ 
\left[
\begin{array}{ccc}
5 & -2 \\
-17 & 7
\end{array}
\right]
$$


---
### 5. Inverse of a 3x3 matrix

Now there are two ways to find the inverse of a 3x3 matrix.

#### Method 1 : Using Gauss-Jordan Elimination

One way is to use matrix row operations and using the method of Gauss-Jordan elimination to find the inverse of the 3x3 matrix.

https://www.youtube.com/watch?v=Fg7_mv3izR0

So if you have this matrix for example : 

![Pasted image 20250406125451.png](/img/user/media/Pasted%20image%2020250406125451.png)

We write it out as in the picture, by **augmenting the matrix with the identity matrix**.

Then the goal is to **perform row operations such that the identity matrix (reduced row echelon form) is on the LHS and on the RHS we get the inverted matrix**.

The procedure is the same as Gauss-Jordan elimination, so if you want to see how that's done you can either watch the video in the link or just scroll up to the section of Gauss-Jordan elimination.

---
#### Method 2: Using the method of matrix of minors, co-factors and adjugate matrix.

This method is a much less time consuming one that the Gauss-Jordan elimination method.

https://www.khanacademy.org/math/in-in-grade-12-ncert/xd340c21e718214c5:determinants/xd340c21e718214c5:adjoint-and-inverse-of-a-matrix-using-minors-and-cofactors/v/inverting-3x3-part-1-calculating-matrix-of-minors-and-cofactor-matrix

https://www.khanacademy.org/math/in-in-grade-12-ncert/xd340c21e718214c5:determinants/xd340c21e718214c5:adjoint-and-inverse-of-a-matrix-using-minors-and-cofactors/v/inverting-3x3-part-2-determinant-and-adjugate-of-a-matrix


So we start off with a 3x3 matrix


![Pasted image 20250406133327.png](/img/user/media/Pasted%20image%2020250406133327.png)


We will create something called a "matrix of minors".

The matrix of minors is of this format:

![Pasted image 20250406182630.png](/img/user/media/Pasted%20image%2020250406182630.png)

which is basically :

1. Choose an element.
2. Hide the row and column in which that element is.
3. Write the remaining elements in their existing order within a determinant format as singular element of a larger matrix.
4. Keep repeating till all the elements in the original matrix, have been chosen.


So with our example matrix it will be :

![Pasted image 20250406182920.png](/img/user/media/Pasted%20image%2020250406182920.png)


Now after solving the individual determinants :

![Pasted image 20250406182951.png](/img/user/media/Pasted%20image%2020250406182951.png)


This is the matrix of minors.

Next up is the co-factor matrix.

Simply apply this sign pattern (we see this pattern during the determinant of a 3x3 matrix) :

![Pasted image 20250406183042.png](/img/user/media/Pasted%20image%2020250406183042.png)


to the elements of the matrix of minors.

![Pasted image 20250406183107.png](/img/user/media/Pasted%20image%2020250406183107.png)


Which now becomes the Co-Factor matrix.


Now we are halfway there!

Next up is the adjugate matrix.


The adjugate matrix is just the transpose of the Co-Factor matrix (rows and columns interchanged).

![Pasted image 20250406183323.png](/img/user/media/Pasted%20image%2020250406183323.png)


So the final inverse of our 3x3 matrix is the **product of the determinant times the adjugate matrix**

$$A^{-1}_{3\times3} \ = \ \det(A) \ \times \ adjugate(A)$$


So we already know how to find the determinant of a 3x3 matrix, so I will be skipping that here

The determinant of this matrix is :

![Pasted image 20250406183602.png](/img/user/media/Pasted%20image%2020250406183602.png)


So the final inverse is :

![Pasted image 20250406183618.png](/img/user/media/Pasted%20image%2020250406183618.png)


which will result in :

![Pasted image 20250406183634.png](/img/user/media/Pasted%20image%2020250406183634.png)

---
## Finding the solution to a system of equations using the matrix inversion method.

So now that we have all the pre-requisites out of the way we can proceed with the matrix inversion method of finding the solution to a system of equations.

Let's proceed with the example we used in the Gauss-Jordan elimination method, better to proceed with a known problem as an example.


So we have the system of equations

![Pasted image 20250405182359.png](/img/user/media/Pasted%20image%2020250405182359.png)


So let's convert this system of equations to an augmented matrix first.

$$
\left[
\begin{array}{ccc|c}
  1 & 1 & -1 & 7 \  \\
  1 & -1 & 2 & 3 \ \\
  2 & 1 & 1 & 9  \
\end{array}
\right]
$$

However here we will do two things.

We split the augmented matrix into two separate matrices.

One will be the coefficient matrix, let's call it $A$

$$
\left[
\begin{array}{ccc}
  1 & 1 & -1  \\
  1 & -1 & 2 \\
  2 & 1 & 1  
\end{array}
\right]
$$


And the variables matrix, let's call it $\vec x$

$$\vec x \ = \ 
\left[
\begin{array}{ccc}
  x   \\
  y  \\
  z 
\end{array}
\right]
$$


And the other one will be the constant matrix, let's call it $b$:

$$
b \ = \ 
\left[
\begin{array}{ccc}
  7   \\
  3  \\
  9 
\end{array}
\right]
$$


Now we need to find :

$$\vec x \ = \ A^{-1}b$$


We will try to invert the coefficient matrix

So let's find out the determinant first:

$$\det(A) \ = \ +1 \ [ \ -1 \ - \ 2  \ ] \ - \ 1 \ [ \ 1 \ - \ 4 \ ] \ + (-1) \ [\ 1 \ + \ 2 \ ]$$

$$= \ +1[\ -3 \ ] \ - \ 1[\ -3 \ ] \ - \ 1[ \ 3 \ ]$$

$$ = \ -3 \ + \ 3 \ - \ 3$$

$$ = \ -3$$

Since $\det(A) \neq 0$ , this means the coefficient matrix is invertible.

So I will proceed with the second method here, as it's much faster than doing row operations.

Starting with the matrix of minors :

$$
\left[
\begin{array}{ccc}
  1 & 1 & -1  \\
  1 & -1 & 2 \\
  2 & 1 & 1  
\end{array}
\right]
$$

will be:


$$
\left[
\begin{array}{ccc}
  \begin{vmatrix}
   -1 & 2  \\
    1 & 1 
   \end{vmatrix}
   &   
   \begin{vmatrix}
   1 & 2  \\
    2 & 1 
   \end{vmatrix} 
   & 
   \begin{vmatrix}
   1 & -1  \\
    2 & 1 
   \end{vmatrix} \\
\\
    \begin{vmatrix}
   1 & -1  \\
    1 & 1 
   \end{vmatrix}
   & 
    \begin{vmatrix}
   1 & -1  \\
    2 & 1 
   \end{vmatrix}
	& 
	 \begin{vmatrix}
   1 & 1  \\
    2 & 1 
   \end{vmatrix} \\
\\   
   \begin{vmatrix}
   1 & -1  \\
    -1 & 2 
   \end{vmatrix}
   & 
    \begin{vmatrix}
   1 & -1  \\
    1 & 2 
   \end{vmatrix}
	& 
	 \begin{vmatrix}
   1 & 1  \\
    1 & -1 
   \end{vmatrix}
\end{array}
\right]
$$


(That was quite painful to type and render, but atleast faster than drawing with a mouse).


Now we solve the individual determinants :

$$
\left[
\begin{array}{ccc}
  -3 & -3 & 3  \\
  2 & 3 & -1 \\
  1 & 3 & -2  
\end{array}
\right]
$$



So this is the matrix of minors.

Now we apply the sign scheme to get the co-factor matrix:

$$
\left[
\begin{array}{ccc}
  -3 & 3 & 3  \\
  -2 & 3 & 1 \\
  1 & -3 & -2  
\end{array}
\right]
$$

Now we find the adjugate matrix by transposing the co-factor matrix :

$$
\left[
\begin{array}{ccc}
  -3 & -2 & 1  \\
  3 & 3 & -3 \\
  3 & 1 & -2  
\end{array}
\right]
$$


Now we compute the inverse of the matrix :

$$A^{-1} \ = \ -\frac{1}{3} \ \times \ 
\left[
\begin{array}{ccc}
  -3 & -2 & 1  \\
  3 & 3 & -3 \\
  3 & 1 & -2  
\end{array}
\right]
$$


which will be :

$$
\left[
\begin{array}{ccc}
  1 & \frac{2}{3} & -\frac{1}{3}  \\
  -1 & -1 & 1 \\
  -1 & -\frac{1}{3} & \frac{2}{3}  
\end{array}
\right]
$$


Now using the formula :

$$\vec x \ = \ A^{-1}b$$


we can find out the value of $x$, $y$ and $z$.


So :

$$\left[
\begin{array}{ccc}
  x   \\
  y  \\
  z 
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
  1 & \frac{2}{3} & -\frac{1}{3}  \\
  -1 & -1 & 1 \\
  -1 & -\frac{1}{3} & \frac{2}{3}  
\end{array}
\right]
\ \times 
\left[
\begin{array}{ccc}
  7   \\
  3  \\
  9 
\end{array}
\right]
$$


For $x$, multiply each element of $b$ to each element of the first row of $A^{-1}$ and add :

$$x \ = \ 7 \ \times 1 \ + \ \frac{2}{3} \ \times 3 \ + \ -\frac{1}{3} \ \times 9 $$

$$\implies x \ = \ 7 \ + \ 2 \ - \ 3$$

$$\implies x \ = \ 6$$


Similarly :

$$y \ = \ -7 \ - 3 \ + 9$$

$$\implies y \ = \ -1$$

And lastly :

$$z \ = \ -7 \ - \frac{1}{3} \ \times 3 \ + \ \frac{2}{3} \ \times 9$$

$$\implies z \ = \ -7 \ - \ 1 \ + \ 6$$

$$\implies z \ = \ -2$$

So we get a **unique solution** this time as :

$$\boxed{x \ = \ 6, \ y \ = \ -1, \ z \ = \ -2}$$

---
# Simple recap example for the above 3 methods

## Example

Given a simple $2\times2$ matrix:

$$
\left[
\begin{array}{ccc}
2 & 3 \\
4 & -1
\end{array}
\right]
\
\left[
\begin{array}{ccc}
x  \\
y 
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
9 \\
7 
\end{array}
\right]
$$


Here's the solution via all 3 methods, Gaussian Elimination, Gauss-Jordan Elimination and Matrix inversion method (Adjugate matrix version)

### Gaussian Elimination

![Pasted image 20250801134854.png](/img/user/media/Pasted%20image%2020250801134854.png)

---
### Gauss-Jordan Elimination

![Pasted image 20250801134933.png](/img/user/media/Pasted%20image%2020250801134933.png)

---
### Matrix Inversion method (Adjugate matrix version)

![Pasted image 20250801135004.png](/img/user/media/Pasted%20image%2020250801135004.png)

That should clear up any confusions left.

---
# Linear Independence

## What is Linear Independence?

**Definition:**  
A set of vectors $\{v1,v2,...,vn\}$ is said to be **linearly independent** if the only solution to:

$$c_1v_1 \ + \ c_2v_2 \ + \ \cdots \ + \ c_nv_n=0$$

is $c_1 \ = \ c_2 \ = \ \cdots \ = \ c_n \ = \ 0$

- If there exists a non-trivial solution (not all $c_i=0$), the vectors are **linearly dependent**.

---
## Geometric Independence

- In $R^2$: Two vectors are linearly independent if they’re **not parallel** (they don’t lie on the same line through the origin).
- In $R^3$: Three vectors are linearly independent if they do **not** all lie in the same plane through the origin.(Point in different axes)

---
## How to Test for Linear Independence (Algebraic Methods)

### 1. Equation Approach

Write the vector equation:

$$c_1v_1 \ + \ c_2v_2 \ + \ \cdots \ + \ c_nv_n=0$$

Set up and solve the corresponding system. If only the trivial solution ($c_i=0$) exists, the set is independent.

Let's understand this in a little more depth:

#### What is a Trivial Solution?

When testing if a set of vectors is linearly independent, we ask:

For scalars: $c_1, \ c_2, \ \cdots \ , c_n$:

$$c_1v_1 \ + \ c_2v_2 \ + \ \cdots \ + \ c_nv_n=0$$

If the **only solution is**:

$c_1=0, \ c_2=0, \ \cdots \ , c_n=0$

**then these zeroes are called the trivial solution**.

If there exists **another** set of scalars (not all zero) that solves the above, it’s called a **non-trivial solution**.

---
### 2. Matrix Rank / Row-Reduction

- Form a matrix with the vectors as **columns**.
- **Row-reduce** to determine if the only solution to the homogeneous system is the trivial one.
- If the number of **pivot columns** equals the number of vectors, the set is linearly independent.

---
### 3. Determinant Criterion (for Square Matrices) (Easy)

- For $n$ vectors in $n$-dimensional space, place them as columns of an $n×n$ matrix.
- If the determinant is **non-zero**, they’re linearly independent.

---
## Example

### Case 1: Linearly Dependent Vectors

Let:

$$
a \ = \ 
\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right]
,\ b \ = \ 
\left[
\begin{array}{ccc}
2 \\
4
\end{array}
\right]
$$

To check independence, solve:

$$
c_1 \  
\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right] 
\ + \ c_2 \ 
\left[
\begin{array}{ccc}
2 \\
4
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
0 \\
0
\end{array}
\right]
$$


Write them as a system of linear equations:

$$
c_1 \ + \ 2c_2 \ = \ 0
$$

$$
2c_1 \ + \ 4c_2 \ = \ 0
$$


Solve them however you want.

Now, if we set $c_2 \ = \ t$

Then from the first equation, $c_1 \ = \ -2t$

So, for _any_ $t$,

$$c_1 \ = \ -2t, \ c_2 \ = \ t$$

Not both are always zero (unless $t=0$), so a non-trivial solution exists:  
**These vectors are linearly dependent.**  
(Geometrically: they point in the same direction; one is a multiple of the other. (So they are parallel to each other as well))

---
### Case 2: Linearly Independent Vectors

Let,

$$
p \ = \ 
\left[
\begin{array}{ccc}
1 \\
0
\end{array}
\right]
,\ q \ = \ 
\left[
\begin{array}{ccc}
0 \\
1
\end{array}
\right]
$$

Solve:

$$
c_1 \  
\left[
\begin{array}{ccc}
1 \\
0
\end{array}
\right] 
\ + \ c_2 \ 
\left[
\begin{array}{ccc}
0 \\
1
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
0 \\
0
\end{array}
\right]
$$

So,



$$
c_1 \ = \ 0, \ c_2 \ = \ 0
$$

The **only** solution is $c_1 \ = \ 0$, $c_2 \ = \ 0$ — this is the **trivial solution**.  
**These vectors are linearly independent.**  
(Geometrically: they point along different axes.)

---
# Rank of a matrix

## What is the Rank of a Matrix?

**Definition:**  
==The **rank** of a matrix is the maximum number of linearly independent rows or columns in the matrix==.

- It tells you the dimension of the **row space** or **column space** (both are equal!).
- In terms of systems of equations, it’s the number of pivots (leading 1’s) you get on reducing a matrix.

---
## How to Find the Rank

### 1. **Row Reduction (Echelon Form)**

- Transform the matrix into **row-echelon form** or **reduced row-echelon form** (using Gaussian or Gauss-Jordan elimination).
- The **rank** is the number of non-zero rows (pivots).

### 2. **Largest Non-Zero Minor**

- Find the largest square submatrix with a non-zero determinant.
- The size of this submatrix equals the rank.
- **Or, in simple terms, just count the number of non-zero rows**

---
## Methods to find the rank of a matrix

### 1. By Normal form

https://www.youtube.com/watch?v=kaphHRq39JI&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=3

![Pasted image 20250801144316.png](/img/user/media/Pasted%20image%2020250801144316.png)


Let's use the given matrix in the example.

Yes, now we are dealing with non-square matrices.

Using normal form you can either use:

- Row-echelon form
- Reduced-row echelon form

And then count the number of non-zero rows to get the rank of the matrix.

**Remember that**

- In row-echelon form, for the matrix of any $n \times n$ , it's achieved when you have a lower-left triangle of zeroes.

![Pasted image 20250801144957.png](/img/user/media/Pasted%20image%2020250801144957.png)


- In reduced-row echelon form, it would look like this:

![Pasted image 20250801145716.png](/img/user/media/Pasted%20image%2020250801145716.png)


**It is an identity matrix in the case of square matrices**.

For non-square matrices:

$$
\left[
\begin{array}{ccc}
  1 & 2 & 3 & 4 \\
  0 & 1 & 6 & 5 \\
  0 & 0 & 9 & 7
\end{array}
\right]
$$

However it is important to note that:

**When solving equations, you do not always get an identity on the diagonal—RREF simply ensures all pivots are 1 and alone in their column. The rest of the structure depends on the rank and shape of the matrix.**

---
## **IMPORTANT NOTE ON HOW TO DECIDE THAT THE REF or RREF has been reached in a non-square matrix**.

#### Key properties of the Row-Echelon Form

##### What is a Pivot?

A bit late in the proper clarification definition, but here we go:

==A **pivot** is the first nonzero entry from the _left_ in a row (when moving left to right).==

**For example:**

Row 1: `[ 0 0 5 7 ]` Pivot is 5

Now,

- In each nonzero row, the **pivot** appears **to the right** (further along in the row) than the pivot in the row above.
    
    - For example:
        
        - Row 1: `[ 1 * * ]` (pivot in position 1)
        - Row 2: `[ 0 1 * ]` (pivot in position 2 — to the right of the previous row’s pivot)
        - Row 3: `[ 0 0 1 ]` (pivot in position 3 — to the right again)
            
- **All entries below a pivot are zero**.


==**When you find that the all the entries below the pivot in the pivot column are zero, you reach the Row-Echelon Form**==

---
#### For RREF in non-square matrices

$$
\left[
\begin{array}{ccc}
1 & 0 & a & b \\
0 & 1 & c & d \\
0 & 0 & 0 & 0
\end{array}
\right]
$$

Where:

- Pivots are in columns 1 and 2.
- All entries below and above the pivots are zero within those columns.
- Zeros appear at the bottom as necessary.


---
### Example:

$$
\left[
\begin{array}{ccc}
1 & 2 & 3 \\
2 & 4 & 6 \\
0 & 1 & 1 \\
1 & 3 & 4 \\
\end{array}
\right]
$$

Suppose, we have this matrix.

Now, we have to find the rank of a matrix:

#### Method 1: By Normal Form:

We can either use **Gaussian Elimination** or **Gauss-Jordan Elimination** to get the rank.

So, let's use Gaussian Elimination for this.


For $R_{21}$ , pivot = $R_{11} \ = \ 1$

$m \ = \ 2$

$$R_2 \ \rightarrow \ R_2 \ - \ 2R_1$$

$$
\left[
\begin{array}{ccc}
1 & 2 & 3 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
1 & 3 & 4 \\
\end{array}
\right]
$$

For $R_{41}$ , pivot is still $R_{11} \ = \ 1$, $m \ = \ 1$


$$R_4 \ \rightarrow \ R_4 \ - \ R1$$


$$
\left[
\begin{array}{ccc}
1 & 2 & 3 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
0 & 1 & 1 \\
\end{array}
\right]
$$

For $R_{42}$, pivot can be set to $R_{32} \ = \ 1$, $m \ = \ 1$

$$R_4 \ \rightarrow \ R_4 \ - \ R_3$$

$$
\left[
\begin{array}{ccc}
1 & 2 & 3 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
0 & 0 & 0 \\
\end{array}
\right]
$$

And now, we have achieved the row-echelon form, so we can stop here.

Judging by the number of non-zero rows, the rank of this matrix is 2.

Let's test now if the Gauss-Jordan elimination results in the same answer or not.

Continuing from the matrix,

For $R_{13}$, we can set the pivot to $R_{33}$, so $m \ = \ \frac{3}{1} \ = \ 3$

So, $$R_1 \ \rightarrow \ R_1 \ - \ 3R_3$$

$$
\left[
\begin{array}{ccc}
1 & -1 & 0 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
0 & 0 & 0 \\
\end{array}
\right]
$$

And for $R_{12}$, pivot can be set to $R_{32} \ = \ 1$, so $m \ = \ 1$

So, 

$$R_1 \ \rightarrow \ R_1 \ + \ R_3$$


$$
\left[
\begin{array}{ccc}
1 & 0 & 1 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
0 & 0 & 0 \\
\end{array}
\right]
$$

This is an acceptable RREF form, and the number of non-zero rows is 2, so the rank of this matrix is 2.

---
#### Method 2: By PAQ form.

You can still watch this video if you need extra clarity, but the explanation there is slightly confusing in my opinion.

https://www.youtube.com/watch?v=bVjjQXnVQ6U&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=4

This is easy, you just have to convert the matrix to an identity matrix, and then find out the rank by calculating the number of non-zero rows.

We can proceed the same till RREF to get:

$$
\left[
\begin{array}{ccc}
1 & 0 & 1 \\
0 & 0 & 0 \\
0 & 1 & 1 \\
0 & 0 & 0 \\
\end{array}
\right]
$$

Now, to get the identity matrix, just swap $R_2$ with $R_3$

$$
\left[
\begin{array}{ccc}
1 & 0 & 1 \\
0 & 1 & 1 \\
0 & 0 & 0 \\
0 & 0 & 0 \\
\end{array}
\right]
$$

To get the identity matrix.

And this is the PAQ form. The rank is achieved by counting the number of non-zero rows, which in this case is 2, so the rank of the matrix is 2.

---
#### Method 3: By Definition of Rank.

https://www.youtube.com/watch?v=-9jSv_F9Hz0&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=6

**Note: This method is only for square matrices**.

#### Steps:

##### **1. Check if the determinant of the largest possible square matrix is non-zero**

- If the matrix is square ($n \times n$), calculate $det(A)$.
- If $det⁡(A)≠0$, the **rank = n**.

##### **2. If the determinant is zero, check all (n-1)×(n-1) square submatrices**

- For each possible square submatrix of size $(n−1)×(n−1)$, find the determinant.
- If any one has a non-zero determinant, the **rank = $n-1$**.

##### **3. If all these are zero, check all (n-2)×(n-2) submatrices**

- Among all possible submatrices of size $(n−2)×(n−2)$, if any determinant is non-zero, the **rank = $n-2$**.

##### **4. Continue down to 1×1 submatrices (individual entries)**

- If all minors of order 2 are zero, but at least one entry of the matrix is not zero, the **rank = 1**.
- If all entries are zero, the **rank = 0**.

## Example

Just follow the example matrix as shown in the video here:

https://www.youtube.com/watch?v=-9jSv_F9Hz0&list=PLF-vWhgiaXWPZ7Ogw6zIZMg4aqUXEwrnJ&index=6

---
# Cramer's rule

## What is Cramer’s Rule?

https://www.youtube.com/watch?v=vXqlIOX2itM (2x2 matrix)

https://www.youtube.com/watch?v=Ot87qLTODdQ (3x3 matrix)

**Cramer’s Rule** provides a solution to a system of $n$ linear equations in $n$ variables, where the coefficient matrix is square and has a non-zero determinant.

---
## System:

$$Ax \ = \ b$$

where

- $A$ is an $n \ \times n$ co-efficient matrix
- $x$ is a vector of variables $[\ x_1, \ x_2, \ \cdots , \ x_n \ ]^T$ 
- $b$ is a vector of constants

---
## **Formula**:

For each variable $x_k$ :

$$x_k \ = \ \frac{\det(A_k)}{\det(A)}$$
where:

- $A$ is the coefficient matrix
- $A_k \ =$ matrix $A$ with the $k^{th}$ column replaced by $b$
- $\det(A)$ must be $\neq \ 0$ (system has a unique solution)

---
## Example

Solve:

$$2x \ + \ y \ = \ 5$$

$$x \ - \ 3y \ = \ -1$$

### Step 1:

Write as $Ax \ = \ b$ 

$$
A \ = \ 
\left[
\begin{array}{ccc}
2 & 1 \\
1 & -3
\end{array}
\right] , \
x \ =  
\left[
\begin{array}{ccc}
x \\
y 
\end{array}
\right], \
b \ =  
\left[
\begin{array}{ccc}
5 \\
-1 
\end{array}
\right]
$$

---
### Step 2:

Compute the determinant of A

$$
\det(A) \ = \ -6 - 1 \ = \ -7
$$

Since $\det(A) \ \neq \ 0$, the system has a unique solution

---
### Step 3: Compute the determinants by swapping both the columns of $A$ with $b$

- $A_1$ (replace 1st column with $b$) :

$$
\left[
\begin{array}{ccc}
5 & 1 \\
-1 & -3
\end{array}
\right]
$$

$$\det(A_1) \ = \ -15 + 1 \ = \ -14$$

- $A_2$ (replace the 2nd column with $b$) :

$$
\left[
\begin{array}{ccc}
2 & 5 \\
1 & -1
\end{array}
\right]
$$


$$\det(A_2) \ = \ -2 - 5 \ = \ -7$$

---
### Step 4: Compute Variables

$$
x \ = \ \frac{\det(A_1)}{\det(A)} \ = \ \frac{-14}{-7} \ = \ 2
$$

$$
y \ = \ \frac{\det(A_2)}{\det(A)} \ = \ \frac{-7}{-7} \ = \ 1
$$

---
## When Can You Use Cramer’s Rule?

- Number of equations = number of unknowns (square matrix)
- $\det⁡(A) \neq 0$ (unique solution)

---
