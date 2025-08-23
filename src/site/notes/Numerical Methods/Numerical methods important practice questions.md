---
{"dg-publish":true,"permalink":"/numerical-methods/numerical-methods-important-practice-questions/","title":"Important Questions -- Numerical Methods","tags":["Semester-6","Numerical-Methods"],"created":"2025-06-04T12:46:47.891+05:30"}
---

---
# Module 2 -- Interpolation

## 1. Newton's forward and backward interpolation

## 🔢 **Sample Dataset (Equally Spaced x-values)**

| $x$ | $f(x)$ |
| --- | ------ |
| 1   | 1      |
| 2   | 8      |
| 3   | 27     |
| 4   | 64     |
| 5   | 125    |

✅ This is based on $f(x) \ = \ x^3$, which makes checking your results easy.

- **Newton’s Forward Interpolation** to estimate $f(2.4)$ 
- **Newton’s Backward Interpolation** to estimate $f(4.6)$

### Step 1: Build the difference table

| $x$ | $f(x)$ | $\Delta f(x)$ | $\Delta^2 f(x)$ | $\Delta^3 f(x)$ | $\Delta^4 f(x)$ |
| --- | ------ | ------------- | --------------- | --------------- | --------------- |
| 1   | 1      |               |                 |                 |                 |
|     |        | 7             |                 |                 |                 |
| 2   | 8      |               | 12              |                 |                 |
|     |        | 19            |                 | 6               |                 |
| 3   | 27     |               | 18              |                 | 0               |
|     |        | 37            |                 | 6               |                 |
| 4   | 64     |               | 24              |                 |                 |
|     |        | 61            |                 |                 |                 |
| 5   | 125    |               |                 |                 |                 |

and the step size $h \ = \ 1$, since the gap between the $x$ values = 1.

### Step 2: Find $p$

For forward interpolation, we choose :

$$p \ = \ \frac{x \ - \ x_0}{h}$$

So, for $f(2.4)$, $x \ = \ 2.4$,  and $x_0$  is the first entry in the table, $1$.

$\therefore \ p \ = \ 1.4$.

For backward interpolation, we choose:

$$p \ = \ \frac{x \ - \ x_n}{h}$$

for $f(4.6)$, $x \ = \ 4.6$ and $x_n$  is the last entry in the table, $5$.

$\therefore \ p \ = \ -0.4$

### Step 3:  Forward and Backward Interpolation

#### Forward Interpolation formula:

$$\boxed{P(x) = f(x_0) + p\,\Delta f(x_0) + \frac{p(p-1)}{2!}\,\Delta^2 f(x_0) + \frac{p(p-1)(p-2)}{3!}\,\Delta^3 f(x_0) \ + \ ⋯}$$

So, 

$$P(2.4) \ = \ 1 \ + \ (1.4 \times 7) \ + \ [\frac{1.4(1.4-1)}{2!} \times 12] \ + \ [\frac{1.4(1.4-1)(1.4-2)}{3!} \times 6] \ + \ 0$$

$$P(2.4) \ = \ 1 \ + \ 9.8 \ + \ 3.36 \ - \ 0.336 \ + \ 0$$


$$P(2.4) \ = \ 13.824$$

#### Backward Interpolation formula

$$\boxed{P(x) = f(x_n) + p\,\nabla f(x_n) + \frac{p(p+1)}{2!}\,\nabla^2 f(x_n) + \frac{p(p+1)(p+2)}{3!}\,\nabla^3 f(x_n) + ⋯}$$

So, 

$$P(4.6) \ = \ 125 \ + \ (-0.4 \  \times \ 61) \ + \ \frac{-0.4(0.6)}{2} \times 24 \ + \ \frac{-0.4(0.6)(1.6)}{6} \times 6 \ - \ 0$$

$$P(4.6) \ = \ 125 \ - 24.4 \ - \ 2.88 \ - \ 0.384 \ - 0$$

$$P(4.6) \ = \ 97.336$$

If you apply both the values of $2.4$  and $4.6$  to $f(x) \ = \ x^3$ , you can verify that the answers are correct.

---
## 2. Lagrange Interpolation and Newton's Divided Difference Interpolation

### The formula

Given a set of n+1 data points:

$(x_0, y_0), \ (x_1, y_1), \ \dots, \ (x_n, y_n)$,

the Lagrange interpolation polynomial $P(x)$ is given by:

$$P(x) = \sum_{j=0}^{n} y_j \, L_j(x)$$

where the Lagrange basis polynomial $L_j(x)$ is defined as:

$$L_j(x) = \prod_{\substack{i=0 \\ i \neq j}}^{n} \frac{x - x_i}{x_j - x_i}$$


Let's practice an example to clear this up.

#### 📊 New Dataset (Unequally spaced x-values):

| x   | f(x) |
| --- | ---- |
| 1   | 2    |
| 3   | 10   |
| 4   | 22   |
| 7   | 70   |

Find $f(5)$ using Lagrange Interpolation.

Or better yet we can write the dataset like this:

| $x$    | 1   | 3   | 4   | 7   |
| ------ | --- | --- | --- | --- |
| $f(x)$ | 2   | 10  | 22  | 70  |

which can be considered pairs of the following format:


$$(x_0, y_0) = (1, 2)$$

$$(x_1, y_1) = (3, 10)$$

$$(x_2, y_2) = (4, 22)$$

$$(x_3, y_3) = (7, 70)$$

### Step 1: Create the Lagrange Polynomials

- Hide $x_0$. Then the polynomial should be like this.

In the denominator write the same terms but replace $x$ with the hidden value, in this case, $x_0$, then multiply the entire fraction by the corresponding $f(x)$ value

$$L_0 \ = \ \frac{(x-x_1)(x-x_2)(x-x_3)}{(x_0 -x_1)(x_0-x_2)(x_0-x_3)} \ \times \ 2$$

$$L_0 \ = \ \frac{(x-3)(x-4)(x-7)}{(1 - 3)(1-4)(1-7)} \ \times \ 2$$

$$L_0 \ = \ \frac{(x-3)(x-4)(x-7)}{-36} \ \times \ 2$$


$$L_0 \ = \ \frac{(x-3)(x-4)(x-7)}{-18}$$


- Hide $x_1$

$$L_1 \ = \ \frac{(x-1)(x-4)(x-7)}{(3-1)(3-4)(3-7)} \ \times \ 10$$

$$L_1 \ = \ \frac{(x-1)(x-4)(x-7)}{8} \ \times \ 10$$

$$L_1 \ = \ \frac{5(x-1)(x-4)(x-7)}{4}$$

- Hide $x_2$

$$L_2 \ = \ \frac{(x-1)(x-3)(x-7)}{(4-1)(4-3)(4-7)} \ \times \ 22$$

$$L_2 \ = \ \frac{(x-1)(x-3)(x-7)}{-9} \ \times \ 22$$

$$L_2 \ = \ \frac{22(x-1)(x-3)(x-7)}{9}$$

- Hide $x_3$

$$L_3 \ = \ \frac{(x-1)(x-3)(x-4)}{(7-1)(7-3)(7-4)} \ \times \ 70$$

$$L_3 \ = \ \frac{(x-1)(x-3)(x-4)}{72} \ \times \ 70$$

$$L_3 \ = \ \frac{35(x-1)(x-3)(x-4)}{36}$$


For $x \ = \ 5$,

We put $5$ in place of $x$ and add up all the Lagrange polynomials.

$$L_0 \ + \ L_1 \ + \ L_2 \ + \ L_3$$

So,

$$\frac{(5-3)(5-4)(5-7)}{-18} \ + \ \frac{5(5-1)(5-4)(5-7)}{4} \ + \ \frac{22(5-1)(5-3)(5-7)}{-9} \ $$

$$+ \ \frac{35(5-1)(5-3)(5-4)}{36}$$


$$= \ 0.222 \ - \ 10 \ + \ 39.111 \ + \ 7.777$$

$$f(5) \ = \ 37.111$$

---
### Using Newton's Divided Difference Interpolation

So again we have the dataset.

| $x$    | 1   | 3   | 4   | 7   |
| ------ | --- | --- | --- | --- |
| $f(x)$ | 2   | 10  | 22  | 70  |


#### Step 1: Build the difference table


| $x$ | $f(x)$ | $\Delta f(x)$                | $\Delta^2  f(x)$              | $\Delta^3  f(x)$                 |
| --- | ------ | ---------------------------- | ----------------------------- | -------------------------------- |
| 1   | 2      |                              |                               |                                  |
|     |        | $\frac{10-2}{3-1} \ = \ 4$   |                               |                                  |
| 3   | 10     |                              | $\frac{12-2}{4-1} \ = \ 2.66$ |                                  |
|     |        | $\frac{22-10}{4-3} \ = \ 12$ |                               | $\frac{1-2.66}{7-1} \ = \ -0.27$ |
| 4   | 22     |                              | $\frac{16-12}{7-3} \ = \ 1$   |                                  |
|     |        | $\frac{70-22}{7-4} \ = \ 16$ |                               |                                  |
| 7   | 70     |                              |                               |                                  |

Then use this formula:

$$P(x) = f(x_0) + (x - x_0) \ \Delta f(x_0) + (x - x_0)(x - x_1) \ \Delta^2 \ f(x_0) + \ldots$$


So, 

$$P(5) \ = \ 2 \ + \ (4\times4) \ + \ (4)(2) \times 2.66 \ + \ (4)(2)(1) \times -0.27$$

$$P(5) \ = \ 2 \ + \ 16 \ +  \ 21.28 \ - 2.16$$


$$P(5) \ = \ 37.12$$


---
# Module 3 -- Numerical Integration

## 1. Trapezoidal Rule 

- Formula:

$$\int_{a}^{b}{f(x) dx}  \ \approx \ \frac{h}{2}[f(x_0​)+2f(x_1​)+2f(x_2​)+ \ ⋯ \ + \ 2f(x_{n−1}​) \ + \ f(x_n​)]$$

==All terms except the first and last one are multiplied by 2.==


Approximate the value of:

$$\int_1^2{\ln(x) \ dx}$$

with 4 sub-intervals

### Step 1: Find step size $h$

$n \ =  \ 4$  subintervals, $b \ = \ 2$, $a \ = \ 1$

$$h \ = \ \frac{b-a}{n}$$

$$h \ = \ \frac{2-1}{4} \ = \ \frac{1}{4} \ = \ 0.25$$


### Step 2: Calculate $x_i$ values

$$x_0 \ = \ a \ = \ 1$$

$$x_1 \ = \ a \ + \ h \ = \ 1 \ + \ 0.25 \ = \ 1.25$$

$$x_2 \ = \ a \ + \ 2h \ = \ 1 \ + \ 0.5 \ = \ 1.5$$

$$x_3 \ = \ a \ + \ 3h \ = \ 1 \ + \ 0.75 \ = \ 1.75$$

$$x_4 \ = \ a \ + \ 4h \ = \ 1 \ + \ 1 \ = \ 2$$

### Step 3: Evaluate the values for $f(x_i)$

1. $f(1) \ = \ \ln(1) \ = \ 0$
2. $f(1.25) \ = \ ln(1.25) \ = \ 0.2231$
3. $f(1.5) \ = \ \ln(1.5) \ = \ 0.4054$
4. $f(1.75) \ = \ \ln(1.75) \ = \ 0.5596$
5. $f(2) \ = \ ln(2) \ = \ 0.693$

### Step 4: Apply Trapezoidal rule.

$$\int_1^2{\ln(x) \ dx} \ = \ \frac{h}{2}[\ f(x_0) \ + \ 2f(x_1) \ + \ 2f(x_2) \ + \ 2f(x_3) \ + \ f(x_4) \ ]$$

$$= \ 0.125 \ \times \ [\ 0 \ + \ 0.4462 \ + \ 0.8108 \ + \ 1.1192 \ + \ 0.693 \ ]$$

$$= \ 0.125 \ \times \ 3.0692$$

$$= \ 0.38365$$

---
## 2. Simpson's $\frac{1}{3}rd$  rule

- Formula:

$$\int_{a}^{b}{f(x) \ dx} \ \approx \ \frac{h}{3}[f(x_0​)+4f(x_1​)+2f(x_2​)+4f(x_3​)+⋯+4f(x_{n−1}​)+f(x_n​)]$$

All terms besides the first and last ones are multiplied by constants. Odd terms are multiplied by 4, even terms are multiplied by 2.

Approximate the value of:

$$\int_0^6{\frac{1}{1 \ + \ x^2} \ dx}$$


till $n \ = \ 6$  subintervals

### Step 1: Find $h$

$$h \ = \ 1$$

### Step 2: Calculate $x_i$ values

$$x_0 \ = \ a \ = \ 0$$

$$x_1 \ = \ a \ + \ h \ = \ 1$$

$$x_2 \ = \ a \ + \ 2h \ = \ 12$$

$$x_3 \ = \ a \ + \ 3h \ = \ 18$$

$$x_4 \ = \ a \ + \ 4h \ = \ 24$$

$$x_5 \ = \ a \ + \ 5h \ = \ 30$$

$$x_4 \ = \ a \ + \ 6h \ = \ 36$$

### Step 3: Calculate $f(x_i)$ values

- $f(0) \ = \ 1$
- $f(1) \ = \ 0.5$
- $f(12) \ = \ 0.00689$
- $f(18) \ = \  0.00307$
- $f(24) \ = \ 0.00173$
- $f(30) \ = \ 0.00110$
- $f(36) \ = \ 0.00077$

### Step 4: Apply formula

$$\int_0^6{\frac{1}{1 \ + \ x^2} \ dx} \ = \ \frac{h}{3}[\ f(x_0) \ + \ 4f(x_1) \ + \ 2f(x_2) \ + \ 4f(x_3) \ + \ 2f(x_4) \ + \ 4f(x_5) \ + \ f(x_6)]$$

$$= \ 0.33[\ 1 \ + \ 2 \ + \  0.001378 \ + \ 0.01228 \ + \ 0.00346 \ + \ 0.0044 \ + \ 0.00077]$$

$$= \ 0.33 \ \times \ 3.022288$$

$$= \ 0.99735504$$

---
# Module 5 -- Solutions to a non-linear algebraic equation

## 1. The Bisection Method

### Algorithm

1. **Initial Bracket:** Choose $a$ and $b$ so that $f(a) \cdot f(b) < 0$.
2. **Midpoint:** Compute the midpoint $c = \frac{a + b}{2}$​.
3. **Test Sign:**
    - If $f(c) = 0$ (or is close enough to zero), then $c$ is the root.
    - If $f(a) \cdot f(c) < 0$, set  $b=c$; otherwise, set $a = c$.
4. **Repeat:** Continue the process until the interval $[a, b]$ is sufficiently small or until the error is less than a predetermined tolerance (or till c stops changing).

- Given Equation:

$$f(x) \ = \ x^3 \ - \ x \ - \ 2$$

Let's go with the classic combination of 1,-1

$f(1) \ = \ -2$
$f(-1) \ = \ -4$

Their product is not less than zero, so we need another separate interval.

Let's try (1, 2)

$f(2) \ = \ 4$

And,  $f(1) \ \times \ f(2) \ = \ -8$

So, we have a valid interval as $a \ = \ 1$, $b \ = \ 2$

So we find the midpoint $c \ = \ \frac{1 + 2}{2} \ = \ 1.5$

and $f(1.5) \ = \ -0.125$

So far, we have had:

| Iteration | $a$ | $b$ | midpoint ($c$) | $f(c)$ |
| --------- | --- | --- | -------------- | ------ |
| 1         | 1   | 2   | 1.5            | -0.125 |

Let's continue this till the value of $c$  stops changing, which would probably take 10-15 iterations.

$f(c) \times \ f(a) \ \gt \ 0$ , set a = c

| Iteration | $a$         | $b$         | midpoint ($c$) | $f(a)$   | $f(c)$    | $f(c) \ \times \ f(a) \gt \ 0?$ |
| --------- | ----------- | ----------- | -------------- | -------- | --------- | ------------------------------- |
| 1         | 1           | 2           | 1.5            | -2       | -0.125    | Yes, set a = c                  |
| 2         | 1.5         | 2           | 1.75           | -0.125   | 1.609     | No, set b = c                   |
| 3         | 1.5         | 1.75        | 1.625          | -0.125   | 0.660     | No, set b = c                   |
| 4         | 1.5         | 1.625       | 1.5625         | -0.125   | 0.252     | No, set b = c                   |
| 5         | 1.5         | 1.5625      | 1.53125        | -0.125   | 0.005     | No, set b = c                   |
| 6         | 1.5         | 1.53125     | 1.515625       | -0.125   | -0.034    | Yes, set a = c                  |
| 7         | 1.515625    | 1.53125     | 1.5234375      | -0.034   | 0.012     | No, set b = c                   |
| 8         | 1.515625    | 1.5234375   | 1.51953125     | -0.034   | -0.010    | Yes, set a = c                  |
| 9         | 1.51953125  | 1.5234375   | 1.521484375    | -0.010   | 0.00062   | No, set b = c                   |
| 10        | 1.51953125  | 1.521484375 | 1.516007813    | -0.010   | -0.0317   | Yes, set a = c                  |
| 11        | 1.516007813 | 1.521484375 | 1.518746094    | -0.0317  | -0.0156   | Yes, set a = c                  |
| 12        | 1.518746094 | 1.521484375 | 1.520115235    | -0.0156  | -0.0075   | Yes, set a = c                  |
| 13        | 1.520115235 | 1.521484375 | 1.520799805    | -0.0075  | -0.0034   | Yes, set a = c                  |
| 14        | 1.520799805 | 1.521484375 | 1.52114209     | -0.0034  | -0.0014   | Yes, set a = c                  |
| 15        | 1.52114209  | 1.521484375 | 1.521313233    | -0.0014  | -0.00039  | Yes, set a = c                  |
| 16        | 1.521313233 | 1.521484375 | 1.521398804    | -0.00039 | 0.00011   | No, set b = c                   |
| 17        | 1.521313233 | 1.521398804 | 1.521355567    | -0.00039 | -0.000143 | Yes                             |

After 17 iterations, the midpoint $c$ has stopped changing till 4 decimal places and $f(c)$ is really close to zero, which is good enough, so the most precise real root for this equation is $1.521355567$.

---
## 2. The Regula-Falsi Method

### Algorithm

We start off similar to how we do in the Bisection Method

1. **Initial Bracket:** As with bisection, choose $a$ and $b$ so that $f(a) \  \cdot \ f(b) \  \lt \ 0$, that is, $a$ and $b$ should have opposite signs.
2. **Interpolation**: Compute the new estimate using the formula:
  
  $$c \ = \frac{(a \ \cdot \ f(b)) \ - \  (b \ \cdot \ f(a))}{f(b) \ - \ f(a)}$$

3. **Test sign**: 
   - If $f(c) = 0$ (or is close enough to zero), then $c$ is the root.
   - Otherwise, if $f(a) \ \cdot f(c) \ \lt \ 0$, set $b \ = \ c$, else set $a \ = \ c$


This method should get the root faster than the bisection method.

For the same equation:

$$f(x) \ = \ x^3 \ - \ x \ - \ 2$$


We know already know the intervals, 1 and 2.

and $f(a) \ = \ -2$, $f(b) \ = \ 4$

Compute $c$.

$$c \ = \ \frac{(a \ \times \ f(b)) \ - \ (b \ \times \ f(a))}{f(b) \ - \ f(a)}$$

$$c \ = \ \frac{(4 \ + \ 4)}{4 \ + \ 2} \ = \ \frac{8}{6} \ = \ 1.33$$


$f(c) \ = \ f(1.33) \ =  \ -0.977$

$f(c) \ \times \ f(a) \ = \ 1.954, \ \gt \ 0$

| Iteration | $a$   | $b$       | midpoint ($c$) | $f(a)$ | $f(b)$     | $f(c)$         | $f(c) \times f(a) \gt \ 0?$ |
| --------- | ----- | --------- | -------------- | ------ | ---------- | -------------- | --------------------------- |
| 1         | 1     | 2         | 1.33           | -2     | 4          | 1.954          | Yes, set a = c              |
| 2         | 1.33  | 2         | 0.690          | 1.954  | 4          | -2.36          | No, set b = c               |
| 3         | 1.33  | 0.690     | 1.040          | 1.954  | -2.36      | -1.914         | No, set b = c               |
| 4         | 1.33  | 1.040     | 1.183          | 1.954  | -1.914     | -1.525         | No, set b = c               |
| 5         | 1.33  | 1.183     | 1.247          | 1.954  | -1.525     | -0.306         | No, set b = c               |
| 6         | 1.33  | 1.247     | 1.258          | 1.954  | -0.306     | -1.266         | No, set b = c               |
| 7         | 1.33  | 1.954     | 1.466          | 1.954  | -1.266     | -0.315         | No, set b = c               |
| 8         | 1.33  | 1.466     | 1.530          | 1.954  | -0.315     | 0.056          | Yes, set a = c              |
| 9         | 1.530 | 1.466     | 1.5210035      | 0.056  | -0.315     | -0.0022        | No, set b = c               |
| 10        | 1.530 | 1.5210035 | 1.5213772      | 0.056  | -0.0022    | -0.0000147     | No, set b = c               |
| 11        | 1.530 | 1.5213772 | 1.52137969     | 0.056  | -0.0000147 | -0.00000009816 | Yes.                        |

We see that $c$'s first 4 decimal places are now consistent, and $f(c)$ is _very_ close to zero, which is good enough.

So the most precise real root is $1.52137969$.


---
## 3. Newton-Raphson Method

1. **Initial Guess:** Start with an initial guess $x_0$​.
2. **Iteration:** Compute the next approximation using:
    
    $$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$​
3. **Repeat:** Continue until $|x_{n+1} - x_n|$ is less than a predetermined tolerance. (or $x_{n+1}$ starts repeating the same value.)


Taking the same equation again,

$$f(x) \ = \ x^3 \ - \ x \ - \ 2$$

And the derivative of this function is:

$$3x^2 \ - \ 1$$

Let's keep the initial guesses:

$f(1) \ = \ -2$, $f(2) \ = \ 4$

Now we choose $x_0$ as the value whose $f(x_0)$ is closest to zero.

A general rule of thumb is to take the midpoint between the two initial guesses if one of the guesses' $f(x)$ value is close to zero.

So, $x_0  \ = \ \frac{1 \ + \ 2}{2} \ = \ 1.5$

So, $f(1.5) \ = \ 0.875$

and $f'(1.5) \ = \ 5.75$

Let's continue this till $n \ = \ 5$ 

So, $x_1$:

$$x_1 \ = \ x_0 \ - \ \frac{f(x_0)}{f'(x_0)}$$


$$x_1 \ = \ 1.5 \ - \ 0.152$$

$$x_1 \ = \ 1.348$$

For $x_2$:


$$x_2 \ = \ 1.348 \ - \ \frac{-0.898}{4.451}$$

$$x_2 \ = \ 1.348 \ + \ 0.181 \ = \ 1.529$$

For $x_3$:

$$x_3 \ = \ 1.529 \ - \ \frac{0.045}{6.013}$$

$$x_3 \ = \ 1.529 \ - \ 0.00748$$

$$x_3 \ = \ 1.52152$$

For $x_4$: 

$$x_4 \ = \ 1.52152 \ - \ \frac{0.000833}{5.945069}$$

$$x_4 \ = \ 1.52152 \ - \ 0.000140116$$

$$x_4 \ = \ 1.521379884$$

For $x_5$: 

$$x_5 \ = \ 1.521379884 \ - \ \frac{0.0000010532}{5.943790254}$$

$$x_5 \ = \ 1.521379884 \ - \ 0.00000017719$$

$$x_5 \ = \ 1.521379707$$


Again we see that the value repeats till 5 decimal places, so we stop the process here.

The most precise real root is: $1.521379707$.

---
# Module 6 -- Solutions to an ODE.

## 1. Euler's Method

### Formula

If you know $y(t_n)$ and want to compute  $y(t_{n+1})$ with a step $h$:

$$y_{n+1} \ = \ y_n \ + \ h \ f'(t_n, y_n)$$

Note that we only calculate the derivative of $f(t_n, y_n)$  if $f$  is an explicit equation. If it's an ODE we just use the function directly.

And it requires very small step sizes.

Given ODE:

$$\frac{dy}{dx} \ = \ x \ + \ y$$


and $y(0) \ = \ 1$

Given step size:  $h \ = \ 0.1$

- Find $y(0.1)$  and $y(0.2)$

So, we make a table like this:

- At $n \ = \ 0$

| n   | $x_n$ | $y_n$ |
| --- | ----- | ----- |
| 0   | 0     | 1     |



$$y_{1} \ = \ y_0 \ + \  h \ \times \ (f(x_0))$$


$$y_{1} \ = \ 1 \ + \ 0.1 \ \times \ (0 \ + \ 1)$$

$$y_1 \ = \ 1 \ + \ 0.1 \ = \ 1.1$$

| n   | $x_n$ | $y_n$ |
| --- | ----- | ----- |
| 0   | 0     | 1     |
| 1   | 0.1   | 1.1   |

where $x_n$  keeps on adding itself by $h$.

So, we found $f(0.1) \ = \ 1.1$

Let's continue till $n \ = \ 2$

So,

$$y_2 \ = \ y_1 \ + \ 0.1 \ \times \ (f(x_1))$$

$$y_2 \ = \ 1.1 \ + \ 0.12$$

$$y_2 \ = \ 1.22$$


| n   | $x_n$ | $y_n$ |
| --- | ----- | ----- |
| 0   | 0     | 1     |
| 1   | 0.1   | 1.1   |
| 2   | 0.2   | 1.22  |

And $f(0.2) \ = \ 1.22$

---
## 2. Runge-Kutta 2nd Order (RK2)

This method is used for 2nd order differential equations.

This is based upon Euler's method by modifying it.

$$y^*_{n+1} \ = \ y_n \ + \ h \ f(x_n, \ y_n)$$

(obtained by using Euler's method)

then, we use this to get :

$$y_{n+1} \ = \ y_{n} \ + \ \frac{h}{2} \ [\ f(x_n, y_n) \ + \ f(x_{n+1}, \ y^{*}_{n+1}) \ ]$$


For the same ODE:

$$\frac{dy}{dx} \ = \ x \ + \ y$$

with step size $h \ = \ 0.1$

So,

| n   | $x_n$ | $y_n$ | $f(x_n, y_n)$ |
| --- | ----- | ----- | ------------- |
| 0   | 0     | 1     | 1             |

For $y_1$ :

$$y_1^* \ = \ 1.1$$

(from Euler's method).

Now:

$$y_1 \ = \ y_0 \ + \ \frac{0.1}{2}[\ f(x_0, y_0) \ + \ f(x_1, y_1^*) \ ]$$

$x_1 \ = \ x_0 \ + \ h \ = \ 0.1$

$$y_1 \ = \ y_0 \ + \ \frac{0.1}{2}[\ 1 \ +  \ f(0.1, 1.1) \ ]$$

$$y_1 \ = \ 1 \ + \ (0.05 \ \times \ 2.2)$$

$$y_1 \ = \ 1 \ + \ 0.11$$

$$y_1 \ = \ 1.11$$

| n   | $x_n$ | $y_n$ | $f(x_n, y_n)$ |
| --- | ----- | ----- | ------------- |
| 0   | 0     | 1     | 1             |
| 1   | 0.1   | 1.11  | 1.21          |

So, $f(0.1) \ = \ 1.11$

Now, 

$$y_2^* \ = \ 1.22$$ 
(from euler's method)


$$y_2 \ = \ y_1 \ + \ \frac{0.1}{2}[\ 1.21 \ + \ f(0.2, 1.22) \ ]$$

$$y_2 \ = \ 1.11 \ + \ 0.05[1.21 \ + \ 1.42]$$

$$y_2 \ = \ 1.11 \ + \ 0.1315$$

$$y_2 \ = \ 1.2415$$


| n   | $x_n$ | $y_n$  | $f(x_n, y_n)$ |
| --- | ----- | ------ | ------------- |
| 0   | 0     | 1      | 1             |
| 1   | 0.1   | 1.11   | 1.21          |
| 2   | 0.2   | 1.2415 | 1.4415        |

So, $f(0.2) \ = \ 1.2415$

Notice the precision difference?

It gets even more precise in RK4.

---
## Runge-Kutta 4th Order (RK4)

Builds on RK2:

We calculate these 4 stuff first.

$$k_1 \ = \ h \ \times \ f(x_n, y_n)$$

$$k_2 \ = \ h \ \times \ f((x_n \ + \ \frac{h}{2}), \  (y_n \ + \ \frac{k_1}{2}))$$

$$k_3 \ = \ h \ \times \ f((x_n \ + \ \frac{h}{2}), \ (y_n \ + \ \frac{k_2}{2}))$$

$$k_4 \ = \ h \ \times \ f((x_n \ + \ h), \ (y_n \ + \ \frac{k_3}{2}))$$

And finally :

$$y_{n+1} \ = \ y_n \ + \ \frac{1}{6}(k_1 \ + \ 2k_2 \ + \ 2k_3 \ + \ k_4)$$

To not overly confuse you, let's just stick to the previously used:

$$\frac{dy}{dx} \ = \ x \ + \ y$$

with step size $h \ = \ 0.1$

and $f(0) \ = \ 1$

So, $x_0 \ = \ 0$  and $y_0 \ = \ 1$.

So,:

$$k_1 \ = \ 0.1 \ \times \ f(x_0, \ y_0) \ = \ 0.1 \ \times \ 1 \ = \ 0.1$$

$$k_2 \ = \ 0.1 \ \times \ f((x_0 \ + \ \frac{0.1}{2}), \ (y_0 \ + \ \frac{k_1}{2}))$$

$$\implies k_2 \ = \ 0.1 \ \times \ f(0.1 \ + \ 0.05), \ (1 \ + \ 0.05))$$

$$\implies k_2 \ = \ 0.1 \ \times \ f(0.15, 1.05) \ = \ 0.1 \ \times \ 1.2 \ = \ 0.12$$

Next,

$$k_3 \ = \ 0.1 \ \times \ f((0.15), \ (1 \ + \ \frac{0.12}{2}))$$

$$\implies  k_3 \ = \ 0.1 \ \times \ f(0.1, 1.06)$$

$$\implies k_3 \ = \ 0.1 \ \times \ 1.16$$

$$\implies k_3 \ = \ 0.116$$

Next, 

$$k_4 \ = \ 0.1 \ \times \ f((0.1 \ + 0.1), \ (1 \ + \ \frac{0.116}{2}))$$

$$\implies \ k_4 \ = \ 0.1 \ \times \ f(0.2, 1.058)$$

$$\implies k_4 \ = \ 0.1 \ \times \ 1.258$$

$$\implies k_4 \ = \ 0.1258$$


Finally

$$y_1 \ = \ y_0 \ + \ \frac{1}{6}(k_1 \ + 2k_2 \ + \ 2k_3 \ + \ k_4)$$

$$y_1 \ = \ 1 \ + \ 0.166[0.1 \ + \ 2 \times 0.12 \ + \ 2 \times 0.116 \ + \ 0.1258]$$

$$y_1 \ = \ 1 \ + \ 0.1158348$$

$$y_1 \ = \ 1.1158348$$

which is now much more precise than RK2.


Now for $x \ = \ 0.2$



$$k_1 \ = \ 0.2 \ \times \ f(x_0, \ y_0) \ = \ 0.2 \ \times \ 1.1158348 \ = \ 0.22316696$$

$$k_2 \ = \ 0.2 \ \times \ f((x_0 \ + \ \frac{1.1158348}{2}), \ (y_0 \ + \ \frac{k_1}{2}))$$

$$\implies k_2 \ = \ 0.2 \ \times \ f(0.2 \ + \ 0.5579174), \ (1.1158348 \ + \ 0.11158348))$$

$$\implies k_2 \ = \ 0.2 \ \times \ f(0.7579174, 1.22741828) \ = \ 0.397067136$$

Next,

$$k_3 \ = \ 0.2 \ \times \ f((0.7579174), \ (1.1158348 \ + \ \frac{0.397067136}{2}))$$

$$\implies  k_3 \ = \ 0.2 \ \times \ f(1.1158348,\  0.198533568)$$

$$\implies k_3 \ = \ 0.2 \ \times \ 1.314368368$$

$$\implies k_3 \ = \ 0.2628736736$$

Next, 

$$k_4 \ = \ 0.2 \ \times \ f((0.2 \ + 0.1), \ (1.1158348 \ + \ \frac{0.2628736736}{2}))$$

$$\implies \ k_4 \ = \ 0.2 \ \times \ f(0.3, \ 0.1314368368)$$

$$\implies k_4 \ = \ 0.2 \ \times \ 0.4314368368$$

$$\implies k_4 \ = \ 0.08628736736$$

Finally,

$$y_2 \ = \ y_1 \ + \ \frac{1}{6}(k_1 \ + 2k_2 \ + \ 2k_3 \ + \ k_4)$$

$$y_2 \ = \ 1.1158348 \ + \ 0.166[\ 0.22316696 \ + \ 0.794134272 \ + \ 0.5257473472 \ + \ 0.08628736736 \ ]$$

$$\implies y_2 \ = \ 1.1158348 \ + \ [ \ 0.166 \ \times \ 1.62933594656 \ ]$$

$$\implies y_2 \ = \ 1.1158348 \ + \ 0.27046976712896$$

$$y_2 \ = \ 1.38630456712896$$

which even more precise than RK2.

---
## 4. Predictor-Corrector's method

### 1. Heun's Method.

We’ll look at **Heun’s method**, a simpler Predictor-Corrector pair (especially good for exams):

It's a 2-step process and a bit similar to RK2.

#### Step 1: Predictor (Euler's estimate):

$$y_{n+1}^{Predict} \ = \ y_n \ + \ h \times\ f(x_n, \ y_n)$$

#### Step 2: Corrector (Average slope):

$$y_{n+1}^{Corrected} \ = \ y_n \ + \ \frac{h}{2}[ \ f(x_n, \ y_n) \ + \ f(x_n, \ y_{n+1}^{Predict}) \ ]$$

Yeah, it's exactly the same as RK2.

---
# Finite Difference method.

FDM converts **differential equations** into **algebraic equations** by replacing derivatives with finite differences.

We commonly solve second-order ODEs like:

$$\frac{d^2y}{dx^2} \ = \ f(x), \ y(a) \ = \ \alpha, \ y(b) \ = \ \beta $$


We do that using the following formula:

$$y_{i-1} \ - \ 2y_i \ + \ y_{i+1} \ = \ -h^2 \ \times \ x_i$$


This gives us a **system of linear equations** which we can solve using methods like **Gauss elimination** or **LU factorization**.

The number of values we can find out depends on the **internal points** — the ones **between** the boundary conditions.

For example:

$$\frac{d^2y}{dx^2} \ = \ -x, \ y(0) \ = \ 0, \ y(1) \ = \ 0$$

with step size $h \ = \ 0.25$ and a chosen interval `[0, 1]`

So, the number of points we can have:

$$x_0 \ = \ 0, \ x_1 \ = \ 0.25 \ , \ x_2 \ = \ 0.50, \ x_3 \ = \ 0.75, \ x_4 \ = \ 1$$

Only 4 points.

And we have the boundary values known.

Unknown values:

- $y(x_1)$
- $y(x_2)$
- $y(x_3)$

and $h^2 \ = \ 0.0625$

So, for $x_1, \ i \ = \ 1$

- $$y_0 \ - \ 2y_1 \ + y_2 \ = \ -2y_1 \ + \ y_2$$

and $$-h^2 \ \times \ x_i \ = \ -(0.00625 \ \times \ 0.25)$$


So we get an equation :

$$-2y_1 \ + \ y_2 \ = \ -0.015625$$



- For $x_2, \ i \ = \ 2$

$$y_1 \ - 2y_2 \ + y_3 \ = \ -0.03125$$


- For $x_3, \ i \ = \ 3$

$$y_2 \ - \ 2y_3 \ + y_4 \ = \ -0.046875$$


$$y_2 \ - \ 2y_3 \ = \ -0.046875$$


Now if we solve these three equations we can get all the intermediate values.

That can be done using any of the matrix equation solving methods.

---


