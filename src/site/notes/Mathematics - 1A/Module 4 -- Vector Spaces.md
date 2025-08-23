---
{"dg-publish":true,"permalink":"/mathematics-1-a/module-4-vector-spaces/","title":"Module 4 -- Vector Spaces -- Mathematics - 1A","tags":["Semester-1","Mathematics-1A"],"created":"2025-08-04T18:30:31.011+05:30"}
---

---
# Index

1. [[#Vector Spaces]]
2. [[#The 8 Axioms of a Vector Space]]
3. [[#Linear Dependence.]]
4. [[#Basis of a Vector Space]]
5. [[#Dimension of a Vector Space]]
6. [[#How to check if a set is a Basis]]
7. [[#Linear Transformations (Maps)]]
8. [[#Range and Kernel of a Linear Map]]
9. [[#Rank and Nullity]]
10. [[#Rank-Nullity Theorem]]
11. [[#Inverse of a Linear Transformation]]
12. [[#Composition of Linear Maps]]

---
# Vector Spaces

## What is a Vector Space?

A **vector space** (also called a linear space) is a collection of objects called **vectors**, where you can:

- **Add** any two vectors and get another vector in the same set.
- **Multiply** any vector by a scalar (a number) and get another vector in the set.

But not every set of objects is a vector space. The set must satisfy specific rules, called the **axioms of vector spaces**.

---
## Formal Definition

Let $V$ be a set, and let $F$ be a field (like the set of real numbers $R$ or complex numbers $C$). $V$ is a vector space over $F$ if:

For any $u$, $v$, $w$ $\in V$ and $a, b \ \in \ F$

- You can add: $u + v \ \in \ V$
- You can scale by a number: $av \ \in \ V$
- The following axioms hold:

### The 8 Axioms of  a Vector Space

1. **Associativity of addition**: $(u+v)+w=u+(v+w)$
2. **Commutativity of addition**: $u+v=v+u$
3. **Existence of zero vector**: There is a vector $0 \in V$ so that $v \ + \ 0 \ = \ v \ \forall \ v$.
4. **Existence of additive inverses**: For every $v$, there is a vector $−v$ so that $v+(−v)=0$.
5. **Compatibility of scalar multiplication**: $a(bv)=(ab)v$
6. **Identity element of scalar multiplication**: $1v=v$
7. **Distributivity of scalar multiplication w.r.t. vector addition**: $a(u+v)=au+av$
8. **Distributivity w.r.t. scalar addition**: $(a+b)v=av+bv$

---
## Examples of Vector Spaces

1. **Euclidean Space ($R_n$):** Ordinary vectors you are familiar with, like $(x,y,z)$, are elements of $R^3$.
2. **Space of Polynomials:** The set of all polynomials of degree ≤n forms a vector space.    
3. **Matrices:** The set of all $m \times n$ matrices (with real entries) forms a vector space.
4. **Functions:** The set of all real-valued continuous functions on $[1]$ is a vector space (addition and scalar multiplication done pointwise).

---
## Common Confusions

- **Not All Sets Are Vector Spaces:** For example, the set of positive real numbers is NOT a vector space under ordinary addition—it doesn’t contain zero or negative numbers.
- **Closure Is Key:** After adding or scaling, the result must stay within the set.

---
# Linear Dependence.

If you studied the concept of Linear Independence in module 3, then you should know that **Linear Dependence of a system of equations is the exact opposite of Linear independence of a system of equations**.

Still I will go ahead and provide the formal definition

Let's say you have a set of vectors:

$$c_1v_1 \ + \ c_2v_2 \ + \ \cdots \ + \ c_nv_n=0$$

where $c_i$ are the scalars and 0 is the zero vector.

The vectors are linearly independent if and only if the solution to these equations are zero, or the scalars are zero.

The vectors are linearly dependent if there is atleast one non-zero solution to the systems of equations.

---
# Basis of a Vector Space

A basis of a vector space $V$ is a set of vectors that:

1. **Spans** the vector space(**fills up the vector space**):

- Every vector in $V$ can be written as a linear combination of these basis vectors

1. **Is linearly independent of other basis vectors**:

- No basis vector can be written as a combination **of the other basis vectors**. 


**In short:**  
A basis is a minimal, non-redundant set of building blocks that can generate the entire space.

**Formal Definition**:

If $B \ = \ \{ b_1, b_2, \ \cdots, \ b_n \}$ is a set of vectors in space $V$, then $B$ is a basis if:

- For every $v$ in $V$, there are unique scalars, $a_1, \ \cdots, \ a_n$

$$v \ = \ a_1b_1 \ + \ a_2b_2 \ + \ \cdots \ + \ a_nb_n$$

---
## Why Do We Care About Bases?

- **Coordinate System:** When you choose a basis, every vector can be uniquely represented by a list of numbers (its coordinates with respect to the basis).
- **Simplicity:** Helps to work with a minimal number of vectors, without redundancy.
- **Dimension:** The number of vectors in a basis is called the **dimension** of the space (we’ll cover this next).

---
## Examples

### 1. Standard Basis of $R^2$:

$$
\set{
\left[
\begin{array}{ccc}
1 \\
0
\end{array}
\right], \ 
\left[
\begin{array}{ccc}
0 \\
1
\end{array}
\right]
}
$$

 Any vector 

$$
\left[
\begin{array}{ccc}
2 \\
5
\end{array}
\right]
$$

can be written as:

$$
x \left[
\begin{array}{ccc}
1 \\
0
\end{array}
\right] \ + \ y
\left[
\begin{array}{ccc}
0 \\
1
\end{array}
\right]
$$

---
### Basis for $R^3$

$$
\set{
\left[
\begin{array}{ccc}
1 \\
0 \\
0
\end{array}
\right], \ 
\left[
\begin{array}{ccc}
0 \\
1 \\
0
\end{array}
\right], \ 
\left[
\begin{array}{ccc}
0 \\
0 \\
1
\end{array}
\right]
}
$$

Every $[x, \ y, \ z]$ can be uniquely written as $x[1] \ + \ y[1] \ + z[1]$.

---
### Non-Standard Basis

For $R^2$, the set $\{ [ 1 ], \ [1], \ [1, -1] \}$  is also a basis:

- You can solve for any $[x, y]$ as a combination of them
- They are linearly independent.

---
## How to check if a set is a Basis

**No worries if you didn't understand the jargon above**.

Suppose you’re given a set of vectors:

- Put them as columns (or rows) of a matrix.
- They form a basis if:
    
    - ==They are linearly independent (determinant is nonzero if square, or row-reduce and check if the number of pivots = number of vectors)==.
    - They span the space (you can form any vector as a linear combination).

For $n$ vectors in $R^n$, if linearly independent, then they are in a basis.

---
## Quick example to understand this.

Let's check if the set:

$$
\set{
\left[
\begin{array}{ccc}
2 \\
1
\end{array}
\right], \ 
\left[
\begin{array}{ccc}
3 \\
5
\end{array}
\right]
}
$$

is a basis for $R^2$.

So, we need to check for two dimensions, let's put together the vectors as the column of a single $2\times2$ matrix.

$$
A \ = \
\left[
\begin{array}{ccc}
2 & 3 \\
1 & 5
\end{array}
\right]
$$


Since we know that this is a square matrix, we just need to check if the determinant is a non-zero one or not.

$$
\det(A) \ = \ 10 \ - \ 3 \ = \ 7 \ \neq \ 0
$$

So we don't need to go further into row-echelon form to 

Now, since determinant is non-zero, these vectors are linearly independent, which means they can **span the space(fill up the space)**.

### Conclusion

- The set is linearly independent and spans $R^2$
- Therefore, it **is a basis** for $R^2$.

---
# Dimension of a Vector Space

## What Is Dimension?

==The **dimension** of a vector space is the number of vectors in any basis for that space==.

- **Formally:** If a vector space $V$ has a basis consisting of $n$ vectors, then the dimension of $V$ is $n$.
- The dimension is always a non-negative integer (can be infinite for infinite-dimensional spaces, but those aren’t our focus here).

---
## Why Is Dimension Important?

- It tells you **how many independent directions** you can move within the space.
- All bases of a given vector space have **the same number** of elements—this is a crucial theorem!

---
## Examples

### 1. Ordinary Euclidean spaces:

- $R^2$ (plane) has dimension **2** (any basis has 2 vectors, e.g., $[1]$ and $[1]$).
- $R^3$ (3D space) has dimension **3**.
- $R^n$ has dimension **n**.

### 2. Set of all polynomials of degree $≤ 3$:

Any polynomial $a_0 \ + \ a_1x \ + \ a_2x^2 \ + \ a_3x^3$ can be written using 4 “basic” polynomials: $1, x, x^2, x^3$.  
So, its dimension is **4**.

### 3. Space of $m×n$ matrices (with real entries):

- Dimension is $m×n$.
- Why? Every matrix entry can be thought of as freely chosen, so m×nm×n independent basis “matrices”—each with a single 1 in a unique place, zeros elsewhere.

### How to Find the Dimension

1. **Find a basis** for the vector space.
2. **Count the number of vectors** in the basis.

For sets of vectors (like columns of a matrix), the maximum number of linearly independent vectors is the **dimension of the span** of those vectors (this is also the _rank_ of the matrix—something you already know).

---
## Key Insights

- **Span**: The set of all possible linear combinations. Dimension tells you “how far the span goes.”
- **Zero Vector Space** (just {0}{0}): Its dimension is **0** (the empty basis).
- **General rule:** No set of more than nn vectors in RnRn can be independent; the largest possible independent set has size nn.

**Dimension** is a powerful tool:

- You quickly know the minimum number of vectors needed to span the space.
- It helps classify vector spaces and solve problems efficiently.

---
## Working example

From the last example:

$$
\set{
\left[
\begin{array}{ccc}
2 \\
1
\end{array}
\right], \ 
\left[
\begin{array}{ccc}
3 \\
5
\end{array}
\right]
}
$$

We found out that these two vectors are in basis, so to find out the dimension of the space they span across, we just count the number of vectors.

So the dimension of the occupied vector space = 2.

---
# Linear Transformations (Maps)

A **linear transformation** (or linear map) is a function between two vector spaces that preserves the operations of vector addition and scalar multiplication.

So basically what it does is **convert** or **map** the vectors from one vector space to another.

---
## Formally: 

If $T: V \ \rightarrow W$ is a function (where $V$ and $W$ are vector spaces), $T$ is a linear transformation, for all $u, v \in V$ and all scalars $c$, if and only if:

- $T(u \ + \ v) \ = \ T(u) \ + \ T(v)$  (addition is preserved)
- $T(cu) \ = \ cT(u)$  (scalar multiplication is preserved)

In simpler terms:  
**A transformation is linear if the image of a sum is the sum of images, and it also “respects” scaling.**


In simple terms this means that a **conversion(transformation)** from vector space to another is linear only if the rules of addition and scalar multiplication are preserved.

---
## Examples

### 1. Matrix Multiplication

If $A$ is an $m×n$ matrix, then $T(x)=Ax$ is a linear transformation from $R^n$ to $R^m$

### 2. Zero Map

$T(v)=0$ for all $v$ is always linear.

### 3. Differentiation

The operation $D(f)=f'$ (the derivative of a function) is a linear transformation on many function spaces.

### 4. Integration

For continuous functions on $[1]: T(f) \ = \ \int^{1}_{0}{f(x) \ \ dx}$ is a linear transformation from function space to $R$.

---
## Non-Example (Not Linear)

- $T(x)=x^2$ is **not** linear (because $T(a+b) \ \neq \ T(a) \ + \ T(b)$ in general).
- $T(x)=x+1$ is **not** linear (doesn’t preserve scalar multiplication: $T(2x) \ \neq \ 2 \ T(x)$.

---
## Properties and Notation

- The set of all linear transformations from $V$ to $W$ is written as $L(V,W)$.
- When $V=W$, this is called a **linear operator** on $V$.

---
## Why Are Linear Transformations Important?

- **Connect vector spaces:** They reveal the “structure-preserving” ways to move from one space to another.
- **Matrix representation:** Every linear transformation between finite-dimensional spaces can be represented by a matrix.
- **Applications:** Used throughout mathematics, physics, engineering, computer science, machine learning, and more (rotations, scaling, projections, etc.).

---
## A practical example.

Suppose we have this matrix:

$$
A \ = \ 
\left[
\begin{array}{ccc}
2 & 3 \\
1 & 4
\end{array}
\right]
$$

And we define the transformation $T: R^2 \ \rightarrow \ R^2$ as:

$$
T(x) \ = \ A(x)
$$

where $x$ is a column vector in $R^2$.

Now let's check if this transformation is linear or not.

Let 

$$
u \ = \ 
\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right], \ v \ = \ 
\left[
\begin{array}{ccc}
4 \\
3
\end{array}
\right]
$$

### 1. Check Additivity:

is $T(u+v) \ = \ T(u) \ + T(v)$ ?

#### a) Compute $u+v$ 

$$
u \ + \ v \ = \ \left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right] \ + \ 
\left[
\begin{array}{ccc}
4 \\
3
\end{array}
\right]
$$

$$
= \ \left[
\begin{array}{ccc}
5 \\
5
\end{array}
\right]
$$

#### b) Compute $T(u+v)$ 

$$
T(\left[
\begin{array}{ccc}
5 \\
5
\end{array}
\right]) \ = \ 
A\left[
\begin{array}{ccc}
5 \\
5
\end{array}
\right] 
\ = \ 
\left[
\begin{array}{ccc}
2\times5 + 3\times5 \\
1\times5 + 4\times5
\end{array}
\right]
$$

$$
\left[
\begin{array}{ccc}
10 + 15 \\
5 + 20
\end{array}
\right] \ = \
\left[
\begin{array}{ccc}
25 \\
25
\end{array}
\right]
$$

#### c) Compute $T(u)$ and $T(v)$ separately

$$
T(u) \ = \
T\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right] 
\ = \ 
A \left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right] 
\ = \ 
\left[
\begin{array}{ccc}
2\times1 + 3\times2 \\
1\times1 + 4\times2
\end{array}
\right]
$$


$$
= \ \left[
\begin{array}{ccc}
8 \\
9
\end{array}
\right]
$$


$$
T(v) \ = \
T\left[
\begin{array}{ccc}
4 \\
3
\end{array}
\right] 
\ = \ 
A \left[
\begin{array}{ccc}
4 \\
3
\end{array}
\right] 
\ = \ 
\left[
\begin{array}{ccc}
2\times4 + 3\times3 \\
1\times4 + 4\times3
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
17 \\
16
\end{array}
\right]
$$


$$
T(u) \ + \ T(v) \ = \ 
\left[
\begin{array}{ccc}
8 \\
9
\end{array}
\right] \ + \ 
\left[
\begin{array}{ccc}
17 \\
16
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
25 \\
25
\end{array}
\right]
$$

So additivity is preserved.

---
### 2. Check Scalar Multiplication

Is $T(cu) \ = \ cT(u)$ ?

Let's use $c \ = \ 5$

#### a) Compute $cu$:

$$
5\left[
\begin{array}{ccc}
1 \\
2
\end{array}
\right] 
\ = \ 
\left[
\begin{array}{ccc}
5 \\
10
\end{array}
\right]
$$

#### b) Compute T(cu):

$$
= \ A\left[
\begin{array}{ccc}
5 \\
10
\end{array}
\right]
\ = \ 
\left[
\begin{array}{ccc}
2\times5 + 3\times10 \\
1\times5 + 4\times10
\end{array}
\right]
\ = \
\left[
\begin{array}{ccc}
40 \\
45
\end{array}
\right]
$$

#### c) Compute $5T(u)$:

$$
T(u) \ = \ 
\left[
\begin{array}{ccc}
8 \\
9
\end{array}
\right]
$$

$$
5T(u) \ = \ 
5 \left[
\begin{array}{ccc}
8 \\
9
\end{array}
\right] \
= \ \left[
\begin{array}{ccc}
40 \\
45
\end{array}
\right]
$$


Thus scalar multiplication is preserved as well.

So this transformation: $T(x) \ = \ Ax$ is linear.

---
# Range and Kernel of a Linear Map

## What is the Kernel (Null Space)?

The kernel (or null space) of a linear transformation $T: V \ \rightarrow  \ W$ is the set of all vectors in $V$ that map to the zero vector in $W$

$$
Kernel(T) \ = \ \set{v \ \in V \ | \ T(v) \ = \ 0}
$$

- It tells you which inputs get "flattened" to zero under the transformation
- The kernel is always a subspace of the domain $V$.

---
## What is the Range (Image)?

The range (or image) of a linear transformation $T: V \ \rightarrow \ W$ is the set of all possible outputs of $T$:

$$
Range(T) \ = \ \set{T(v) \ \mid \ v \in V }
$$

- It tells you what vectors you can reach in $W$ by applying $T$ to something in $V$.
- The range is always a subspace of the co-domain $W$.

---
## Matrix example

Let's revisit the previous example:

We had a transformation :

$$T(x) \ = \ Ax$$


And a matrix :

$$
A \ = \ 
\left[
\begin{array}{ccc}
2 & 3 \\
1 & 4
\end{array}
\right]
$$

### Step 1: Find the Kernel.


==**To find the Kernel of a linear transformation, just equation the transformation to zero**==.

$$
Ax \ = \ 0
$$

Let :

$$
x \ = \ 
\left[
\begin{array}{ccc}
x_1 \\
x_2
\end{array}
\right]
$$


So,

$$
\left[
\begin{array}{ccc}
2 & 3 \\
1 & 4
\end{array}
\right] \ 
\left[
\begin{array}{ccc}
x_1 \\
x_2
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
0 \\
0
\end{array}
\right]
$$


Converting that to a linear equation would be:

$$
2x_1 \ + \ 3x_2 \ = \ 0
$$

$$
x_1 \ + \ 4x_2 \ = \ 0
$$


Solving these equations get us:

$$
x_1 \ = \ -4x_2 \ \cdots \ (ii)
$$

Substituting the values into the first:

$$
2(-4x_2) \ + \ 3x_2 \ \implies \ -5x_2 \ = \ 0 \ \implies x_2 \ = \ 0
$$

So $$x_1 \ = \ 0$$

So the kernel of this matrix is the just the zero vector itself $(0,0)$, meaning the transformation is **one-to-one(injective)**.

==This doesn't mean that the kernel always has to be the zero vector itself, it's just that the kernel could be any vector in $V$ that maps to the zero vector in $W$, including the zero vector of $V$, itself.==

---
### Range Example:

The range is the set of all vectors you can get as $Ax$. For a $2\times2$ matrix, with nonzero determinant, here $\det(A) \ = \ 5 \ \neq \ 0$, it means the **onto(surjective)**, the range is all of $R^2$.

If the matrix had less than full rank (e.g all rows were multiples), the range would be a line instead of an entire plane.


**TLDR**: Range is, as the name implies, the entire range of the transformation, for all values $x_1, x_2, \ \cdots \ x_n \ \in \ x$

---
# Rank and Nullity

## Rank

We already know the concept of the rank of a matrix.

Let's proceed to the rank of a linear transformation.

The rank of a linear transformation (or a matrix) measures the "size" of the range (image):

- Definition:  The rank of a transformation $T: V \ \rightarrow \ W$ is the dimension of it's range.
- For a matrix $A$, $rank(A)$ = number of linearly independent rows of columns (we already know this).
- **Geometric meaning:** It tells you the number of “directions” in which the transformation can “move” a vector (i.e., not mapped to zero).

Didn't understand? Alright, let's go through a detailed example to get this sorted.

### Example explanation.

First off, recall that the **dimension of a vector space comes from the basis of a vector space, it is the number of vectors that are present in a basis**.

#### Step 1: Find the range of the transformation first.

Consider the linear transformation, 

$$T: R^3 \ \rightarrow \ R^2$$

which is given by:

$$
T(x) \ = \ Ax 
$$

where

$$
A \ = \ 
\left[
\begin{array}{ccc}
1 & 2 & 3\\
4 & 5 & 6
\end{array}
\right]
$$


Now, split the matrix into column vectors :

$$
a_1 \ = \ 
\left[
\begin{array}{ccc}
1 \\
4
\end{array}
\right], \
a_2 \ = \ 
\left[
\begin{array}{ccc}
2 \\
5
\end{array}
\right], \ 
a_3 \ = \ 
\left[
\begin{array}{ccc}
3 \\
6
\end{array}
\right]
$$

Now, the range can be of three types:

- Either the vectors can span on a single line
- Or occupy the entire target space ($W$), which is $R^2$ in this case.
- Or something else.

If one vector in the column vector matrix is a multiple of the other, they span a line, however if they don't then they span the entire space.

This is true for:

- **If all the column vectors are scalar multiples of each other, then they are linear dependent and thus span a single line**.
- **If at least two column vectors are not scalar multiples, then their span could be a plane, (if in $R^3$ or higher), or even the whole space if there are enough independent directions**.

In this case,

Is $a_1$ a multiple of $a_2$ or vice-versa?

There's no scalar factor that you can multiply to $a_1$ to get $a_2$ or vice-versa, so they are not scalar multiples.

Is $a_1$ a multiple of $a_3$  or vice-versa?

There's no scalar factor that you can multiply to $a_1$ to get $a_3$ or vice-versa, so they are not scalar multiples.

Is $a_2$ a multiple of $a_3$ or vice-versa?

There's no scalar factor that you can multiply to $a_2$ to get $a_3$ or vice-versa, so they are not scalar multiples.

So, since no vector here is scalar multiple of the another, then this means that the range spans across the vector space, which is $R^2$  in this case.

---
#### Step 2: Find the basis of the vector matrix which spans the range.

Here we have:

$$
A \ = \ 
\left[
\begin{array}{ccc}
1 & 2 & 3\\
4 & 5 & 6
\end{array}
\right]
$$

Since the matrix is non-square, we can't really resort on the determinant here, but instead will have to reduce this to the row-echelon form and count the number of pivots.

For $R_{21}$ , we set the pivot to $R_{11} \ = \ 1$.

Thus $m \ = \ \frac{4}{1} \ = \ 4$

So, 

$$
R_2 \ \rightarrow \ R_2 \ - \ 4R_1
$$

$$
A \ = \ 
\left[
\begin{array}{ccc}
1 & 2 & 3\\
0 & -3 & -6
\end{array}
\right]
$$

Now we can divide $R_2$ by $-3$ to get the second pivot

$$
A \ = \ 
\left[
\begin{array}{ccc}
1 & 2 & 3\\
0 & 1 & 2
\end{array}
\right]
$$

Now to make sure that in the pivot column, the pivot is the only leading non-zero entry, we perform an operation on $R_1$

$m \ = \ \frac{2}{1} \ = \ 2$

$$
R_1 \ \rightarrow \ R_1 \ - \ 2R_2
$$


$$
A \ = \
\left[
\begin{array}{ccc}
1 & 0 & -1\\
0 & 1 & 2
\end{array}
\right]
$$

Now this is an acceptable REF form.

We have the number of pivots as 2, so the dimension of this basis is 2, which means the rank of this transformation is 2.

So the rank of $T(A)$ is $2$

---
## Nullity

The nullity of a linear transformation (or a matrix) measures the "size" of the kernel (null space):

- **Definition**: The nullity of $T: V \ \rightarrow \ W$ is the dimension of it's kernel.

Or, the number of vectors we are left with after equation the transformation to zero.

However, in the process of finding the rank of a transformation, after the rank is calculated,

Nullity can also be calculated as:

$$
Nullity \ = \ Number \ of \ columns \ - \ rank \ of \ the \ transformation (Number \ of \ pivots)
$$

So, in our example matrix, we have 3 columns.

The rank is 2.

So the nullity of the kernel of the transformation :

$$
T(x) \ = \ Ax
$$

is: $3-2 \ = \ 1$


---
# Rank-Nullity Theorem

Now let's delve into the theorem which links both of the concepts together.

For a linear transformation $T: V \ \rightarrow \ W$ (or an $m\times n$ matrix $A$), the theorem states:

$$
Dimension \ of \ the \ domain \ = \ Rank \ + \ Nullity
$$

Or, for a matrix $A$ with $n$ columns:

$$
n \ = \ rank(A) \ + \ nullity(A)
$$

---
## **What Does This Mean?**

- **Rank** = The dimension of the image (column space/range) = number of independent output directions.
- **Nullity** = The dimension of the kernel (null space) = number of independent “lost directions” (inputs that get sent to zero).
- **Domain dimension** = The total number of independent variable “directions” you can choose as input.

- Useful for:
    
    - Solving systems of equations,
    - Understanding how a transformation “compresses” or “loses” information,
    - Determining invertibility (full rank = invertible; nullity zero).

---
## Example

From our previous matrix:

$$
A \ = \
\left[
\begin{array}{ccc}
1 & 0 & -1\\
0 & 1 & 2
\end{array}
\right]
$$


- Number of columns = 3
- Rank = 2
- Nullity = 1

The dimension of the domain the transformation encompasses is : $2 + 1 \ = \ 3$

---
# Inverse of a Linear Transformation

## Definition

A linear transformation $T: V \ \rightarrow \ W$ is called invertible if there exists another linear transformation $s: W \ \rightarrow \ V$ such that:


$$
S(T(v)) \ = \ v, \ \forall v \ \in \ V 
$$

and 

$$
T(S(w)) \ = \ w \ \forall \ w \ \in \ W
$$


- The transformation $S$ is called the inverse of $T$, usually denoted as $T^{-1}$

---
## For Matrices

For a square matrix $A$, the associated transformation $T(x) \ = \ Ax$ is invertible if and only if $A$ is invertible. (i.e $A$ has an inverse matrix $A^{-1}$ such that $AA^{-1} \ = \ I$) where $I$ is the identity matrix.

- **If invertible:**
    
    - The transformation is **bijective** (one-to-one and onto).
    - The kernel is just the zero vector.
    - The rank is full ($n$ for $n×n$ matrices).
        
- **If not invertible:**
    
    - There are inputs that are lost (kernel is non-trivial).
    - The transformation is not one-to-one or not onto (or both).

---
## How to check if a matrix is invertible or not.

We typically know this by the checking the determinant of the matrix but here are a few other methods as well.

A square matrix is invertible if:

- Its determinant is **not zero**.
- It has **full rank** (number of pivots = number of columns = number of rows).
- The nullity is **zero**.

The result will be that the inverted matrix will be the inverted transformation.

---
# Composition of Linear Maps

- If you have two linear maps:

- $S: V \ \rightarrow \ W$
- $T:  W \ \rightarrow \ U$

- Their **composition is the map $T \ o \ S \ : \ V \ \rightarrow \ U$ defined by:**

$$(T \ o \ S)(v) \ = \ T(S(v))$$

- Key property: 

The composition of linear maps is always linear.

---
## Example

Suppose we have two linear transformations given by two matrices

- $S: R^2 \ \rightarrow \ R^2$  given by matrix $A$
- $T : R^2  \ \rightarrow R^2$  given by matrix $B$


Let :

$$
A \ = \ 
\left[
\begin{array}{ccc}
1 & 2 \\
0 & 1
\end{array}
\right], \
B \ = \ 
\left[
\begin{array}{ccc}
3 & 0 \\
1 & 2
\end{array}
\right]
$$


Applying $S(x)$  then $T(x)$  would be:

$$T(S(x)) \ = \ B(Ax) \ = \ (BA)x$$

So, the matrix of the composition is the product $BA$.

---
