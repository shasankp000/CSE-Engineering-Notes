---
{"dg-publish":true,"permalink":"/daa-speedrun/algorithms-asymptotic-notations-and-recurrence-relations-the-ultimate-breakdown-module-1/","title":"Algorithms, Asymptotic Notations and Recurrence Relations -- Design and Analysis of Algorithms -- Module 1","tags":["Semester-4"],"created":"2025-03-06T18:33:20.320+05:30"}
---


---

# What is an algorithm?

![Pasted image 20240619125343.png](/img/user/Images/Pasted%20image%2020240619125343.png)

---
# Algorithm vs Program

![Pasted image 20240619125413.png](/img/user/Images/Pasted%20image%2020240619125413.png)

---
# Complexity Bounds and Asymptotic Notations

![Pasted image 20240619125739.png](/img/user/Images/Pasted%20image%2020240619125739.png)

![Pasted image 20240619125753.png](/img/user/Images/Pasted%20image%2020240619125753.png)

So there are 3 **asymptotic notations**, 

1. Big - O  (pronounced as Big oh)
2. Big - $\Theta$ (pronounced as Big theta)
3. Big - $\Omega$  (pronounced as Big omega)

These are used in ==comparison of ranges==, which happen to be either have an
1. Upper bound
2. Exact/same bound
3. Lower bound

For example in the first graph we have the function $g(n)$ is the upper bound for $f(n)$ which means when values of ==n>$n_0$==  , $f(n)$ will **never be greater** than $g(n)$ , denoted by O.

Therefore $f(n)$ = O($g(n)$)

In the second graph, for values of  ==n>$n_0$== , $f(n) = g(n)$ , which is denoted by $\Theta$ .

Thus, $f(n)$ = $\Theta(g(n))$ 

In the third graph,  for values of  ==n>$n_0$== , $g(n)$ **will always be lesser than** $f(n)$,  which is denoted by $\Omega$.

Thus $f(n) = \Omega(g(n))$.

These were the **Big Notations**.

There also exist **small notations**.

![Pasted image 20240619130917.png](/img/user/Images/Pasted%20image%2020240619130917.png)

Here only small-o (small oh) and small omega exist, since only lower or greater bounds are defined by small notations, exact notations cannot be defined using small notations.

$\omega$ is small omega, $\Omega$ . 

---
# Types of Time Complexity. 

![Pasted image 20240619130816.png](/img/user/Images/Pasted%20image%2020240619130816.png)

---
# Recurrence Relations

![Pasted image 20240619132838.png](/img/user/Images/Pasted%20image%2020240619132838.png)

## For example : The time complexity of the binary search algorithm.

![Pasted image 20240619133731.png](/img/user/Images/Pasted%20image%2020240619133731.png)

![Pasted image 20240619133740.png](/img/user/Images/Pasted%20image%2020240619133740.png)

The expression $T(n) = T(n/2) + C$ is a recurrence relation and it is the recurrence relation of the **binary search algorithm**.

There are two major methods to solve a **recurrence relation**.

1. Substitution Method
2. Master Theorem

## 1. The Substitution Method

So we have the recurrence relation

![Pasted image 20240619134057.png](/img/user/Images/Pasted%20image%2020240619134057.png)

So we start by substituting $n = n/2$ 

![Pasted image 20240619134144.png](/img/user/Images/Pasted%20image%2020240619134144.png)

Thus $T[(n/2) / 2] = T(n/4) + C$ ==....... (i)==


And then we repeat the process again for $T(n/4)$ .

![Pasted image 20240619134242.png](/img/user/Images/Pasted%20image%2020240619134242.png)

==....... (ii)==

Then we ==substitute the value of equation (i) in the original recurrence relation== $T(n) = T(n/2) + C$ :

![Pasted image 20240619134401.png](/img/user/Images/Pasted%20image%2020240619134401.png)

And we do the same for equation (ii) as well.

![Pasted image 20240619134604.png](/img/user/Images/Pasted%20image%2020240619134604.png)

And thus we see that a pattern approaches with this equation :

$T(n/2^{k}) + kC$ ==.....(iii)==

Let's set equation $n/2^{k}$ equal to 1.

Therefore, $n/2^{k}$ = 1

or  $2^k$ = n.

Therefore we get : $T(n/n) + kC$ 

or $T(1) + kC$ 

This gets reduced to 

$1 + logn.C$ 

which is further reduced to 

O($log(n)$) 

![Pasted image 20240619135035.png](/img/user/Images/Pasted%20image%2020240619135035.png)

---

## 2. Master Theorem.

This theorem is faster to use than the substitution method however ***it cannot be applied to all recurrence relations*** . 

There are **certain conditions** which **need to be fulfilled** for the Master Theorem to be fulfilled.

![Pasted image 20240619135335.png](/img/user/Images/Pasted%20image%2020240619135335.png)

So if the recurrence relation is of the type :

$T(n) = aT(n/b) + f(n)$ 

where $a \geq 1$ and b > 1

Therefore, Master theorem can be applied to this recurrence relation.

![Pasted image 20240619135512.png](/img/user/Images/Pasted%20image%2020240619135512.png)

In the problems/limitations section those are the factors which prevent Master theorem from working on a recurrence relation.

![Pasted image 20240619135552.png](/img/user/Images/Pasted%20image%2020240619135552.png)

Now, we need to convert that recurrence relation to the form of 

$$T(n) = n^{logb^{a}}[X]$$   

or $f(n)/n^{logb^{a}}$ 

where if X =  $n^P, P > 0$ then it is the upper bound O($n^P$)
if X = $n^P, P < 0$, then it is linear time, O(1)
if X = $(logn)^{q}, q \geq 0$  then it becomes $(logn)^{q+1}/ (q+1)$ 

![Pasted image 20240619140121.png](/img/user/Images/Pasted%20image%2020240619140121.png)

![Pasted image 20240619140132.png](/img/user/Images/Pasted%20image%2020240619140132.png)

![Pasted image 20240619140140.png](/img/user/Images/Pasted%20image%2020240619140140.png)






