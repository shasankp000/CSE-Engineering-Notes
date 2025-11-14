---
{"dg-publish":true,"permalink":"/operations-research/module-4-queueing-theory/","tags":["Operations-Research","Semester-7"],"created":"2025-11-12T23:08:48.492+05:30","updated":"2025-11-14T13:32:37.405+05:30"}
---

---
# Index

1. [[#What is Queueing Theory?]]
2. [[#Case 1 M/M/1 (∞ / FIFO) Poisson Queueing Model.]]
3. [[#Example 1]] (Infinite capacity)
4. [[#Example 2]] (Infinite capacity)
5. [[#Case 2 M/M/1(N/FIFO)-- finite capacity queueing model]]
6. [[#Key symbols/reminder]]
7. [[#Two cases]]
8. [[#Example 1 $p < 1$ case.]] (finite capacity)
9. [[#Example 1 $p < 1$ case.]] (finite capacity)
10. [[#M/M/1 (∞) vs M/M/1 (N) — Formula Comparison Table]]

---
# What is Queueing Theory?

Queueing theory is all about understanding **systems where “customers” arrive, wait, get served, and leave**.  
Customers can be people, packets, jobs, tasks — anything that “queues”.

Now we all know what a queue is.

A queue is ==a linear data structure that follows the **[First-In, First-Out (FIFO)](https://www.google.com/search?q=First-In%2C+First-Out+%28FIFO%29&sca_esv=c561dc4e372ce7af&source=hp&ei=TIYVaaWYIMChseMP4d-j4Q4&iflsig=AOw8s4IAAAAAaRWUXPUrVoZzp0qlzoLla9jSgn92sQJj&ved=2ahUKEwifiImHy-6QAxWvzjgGHScvAigQgK4QegYIAAgAEAY&uact=5&oq=what+is+a+queue&gs_lp=Egdnd3Mtd2l6Ig93aGF0IGlzIGEgcXVldWUyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESM8sUABYjyZwCngAkAEAmAH5AaAB0yCqAQYwLjIyLjO4AQPIAQD4AQGYAiOgAuchwgIIEAAYgAQYsQPCAhEQLhiABBixAxjRAxiDARjHAcICDhAAGIAEGLEDGIMBGIoFwgILEAAYgAQYsQMYgwHCAgUQLhiABMICDhAAGIAEGLEDGIMBGMkDwgILEAAYgAQYkgMYigXCAgsQABiABBixAxiKBcICFRAuGIAEGLEDGNEDGIMBGMcBGAoYC8ICBxAAGIAEGArCAg8QABiABBixAxiDARgKGAvCAgwQABiABBixAxgKGAvCAgcQLhiABBgKwgIGEAAYAxgKwgIJEAAYgAQYChgLwgIMEC4YgAQYsQMYChgLwgIHEAAYgAQYDZgDAJIHBzEwLjIxLjSgB4-4AbIHBjAuMjEuNLgHwSHCBwkwLjE5LjE1LjHIB24&sclient=gws-wiz)** principle==, meaning the first item added to the queue is the first one to be removed. Items are added to the **rear** of the queue (called `enqueue`) and removed from the **front** (called `dequeue`), much like people waiting in a line for a service.

![Pasted image 20251113124859.png](/img/user/media/Pasted%20image%2020251113124859.png)

So, what's with the new stuff then? Queueing Models, Poisson, $\lambda$, $L$, etc? Why do we need all this?

# Case 1: M/M/1 (∞ / FIFO) Poisson Queueing Model.

## Step 1: The need for Queueing Models

Think of _queues in real life_.  
Are arrivals perfectly regular?

❌ No — people don’t arrive at exactly one every 10 seconds.  
They come randomly: sometimes 2 people at once, sometimes no one for a minute.

Queueing Theory models **random arrivals** and **random service times**.

To describe randomness mathematically, we use a standard tool:

> ==**Poisson process** → a way to model random arrivals==.

And it uses one simple symbol:

### $\lambda$ (lambda) -- the average arrival rate

- If $\lambda \ = \ \text{10/hour} \ \rightarrow$ on average, 10 customers arrive every hour.
- Not exactly every 6 minutes — but _on average_.

That’s it. No magic.

---
## Step 2: Service time is also random

You cannot serve every customer in **exactly** 5 minutes.  
Sometimes 4, sometimes 7, etc.

So, we define:

### $\mu$ -- the average service rate

If $\mu \ = \ 12  \text{/hour} \ \rightarrow$ server can serve 12 customers per hour on average.

Again — nothing complicated.

---
## Step 3: Why do we need utilization?

This is the most intuitive part.

Utilization just means:

> **How busy is the server?**

This is answered by this formula:

$$
p \ = \ \frac{\lambda}{\mu}
$$


Example:

- $\lambda \ =  \ 10$ arrivals/hour
- $\mu \ = \ 12$ services/hour

Thus, $p \ = \ \frac{10}{12} \ = \ 0.833$, the server is busy $83.3 \ \%$ of the time.

Now, 

If $\lambda \ \geq \ \mu$, this means that customers arrive faster than they can be served, which makes the **queue grow to infinity** and **the system breaks**.

So the only condition for a working queue is:

>   $\mu \ > \ \lambda$
> **(server must be faster than arrivals)**

---
## Step 4: The M/M/1 Queueing Model

M/M/1 literally means:

- **M** → arrivals follow a **Markovian** (Poisson) process
- **M** → service times are **Markovian** (exponential distribution)
- **1** → one server

You do **not** need to study distributions deeply.  
All you need to accept is:

> Poisson arrivals + exponential service = simplest realistic queue model.

---
## Step 5: Important Terminologies

These are just average quantities:

- **L = average number of customers in the whole system**  
    (waiting + being served)
- $L_q$ **= average number waiting in the queue**
- **W = average time a customer spends in the system**
- $W_q$ **= average time spent waiting in the queue** 

They are connected by the famous but simple:

### Little's law

$$
L \ = \ \lambda W
$$

If more customers arrive per hour, L increases.  
If each customer spends more time in the system, L increases.  
Simple.

---
## Formula set for M/M/1 (∞ / FIFO)

Let $\lambda$ be the arrival rate (customers per hour), $\mu$ be the service rate (customers per hour), $p \ = \ \frac{\lambda}{\mu}$

- Stability condition: $\lambda \ < \ \mu$
- Utilization: $p \ = \ \frac{\lambda}{\mu}$
- Probability that the system is empty: $P_0 \ = \ 1 \ - \ p$
- Probability of $n$ customers in system: $P_n \ = \ (1 \ - \ p) \ \times \ p^n$
- Average number of customers in the system $L \ = \ \frac{p}{(1 \ - \ p)}$
- Average number of customers waiting in queue: $L_q \ = \ \frac{p^2}{1 \ - \ p}$
- Average time in system: $W \ = \ \frac{1}{\mu \ - \ \lambda}$
- Average waiting time in queue: $W_q \ = \ \frac{p}{(\mu \ - \ \lambda)}$

---
Whoops. Too many formulae? Hell nah I myself am not memorizing all that, so let's simplify all this with the core formulae that we can use to build all these.

We need to remember 3 rules and 2 definitions.

**Definition 1**: $\lambda$ ==is the arrival rate of customers per hour==.
**Definition 2**: $\mu$ ==is the service rate of customers per hour==.

**Rule 1**: ==The utilization of the server is given by the ratio of the arrival rate to the service rate of the customers per hour==. (Or the average number of customers that are being served.)

Just “how busy the server is”.

Thus:

$$
\boxed{p \ = \ \frac{\lambda}{\mu}}
$$


Now, for the probability that the system is empty, we can just get the value by subtracting it from 1:

$$
\boxed{P_0 \ = \ 1 \ - \ p \ = \ \mu \ - \ \lambda}
$$

Then, the probability of $n$ customers in system becomes:

$$
\boxed{P_n \ = \ P_0 \ \times \ p^n \ = \ (1 \ - \ p) \ \times \ p^n}
$$

**Rule 2:** ==Average number of customers in the system (This means the people waiting in the queue plus the one person that is being served (if there is one))==. This one formula unlocks everything else.

>Intuition:  
If the server is _almost full most of the time_, L becomes large.  
If server is fast compared to arrivals, L stays small.

$$
\boxed{L \ = \ \frac{p}{(1 \ - \ p)}}
$$

**Rule 3:** ==Little's Law==!

$$
\boxed{L \ = \ \lambda W}
$$


From here we can get the average time in system $W$:

$$
W \ = \ \frac{L}{\lambda}
$$

or:

$$
W \ = \ \frac{\frac{p}{(1 \ - \ p)}}{\lambda}
$$


$$
W \ = \ \frac{\frac{\frac{\lambda}{\mu}}{(1 \ - \ \frac{\lambda}{\mu})}}{\lambda}
$$


$$
W \ = \ \frac{\frac{\lambda}{\mu \ - \ \lambda}}{\lambda}
$$

$$
W \ = \ \frac{\lambda}{\lambda(\mu \ - \ \lambda)}
$$

$$
\boxed{W \ = \ \frac{1}{\mu \ - \ \lambda}}
$$


Now, for the average number of customers waiting in queue ($L_q$):

We go back to the definition of L first:

**L** is the average number of customers in the system (This means the people waiting in the queue plus the one person that is being served (if there is one))

So,:

$$
L \ = \ \text{average waiting} \ + \ \text{average in service}
$$

or:

$$
L \ = \ L_q \ + \ \text{average in service}
$$

Fair so far. We are halfway there.

Now, for the average customers that is in service.

We know that the average number of customers that are being served is defined by $p$.

But why, a probability? Why $p$?

In an M/M/1 queue, the number of customers being served is either:

- 0 (server idle) (Let's take is as $P_{idle}$)
- 1 (server busy) ($P_{busy}$)

There is _no other possibility_.

So, the average number of customers in service become:

$$
p \ (\text{or} \ p_{total}) \ = \ 0 \ \times \ p_{idle} \ + \ 1 \ \times \ p_{busy}
$$

So, there we have $p$ as the average number of customers that are being served. And the probability that there are no customers and the server is idle is $P_0 \ = \ 1 \ - \ p$ . Simple.

So, 

$$
\text{average in service} \ = \ p
$$

Plugging this back into our earlier structure:

$$
L \ = \ L_q \ + \ p
$$

$$
L_q \ = \ L \ - \ p
$$

$$
L_q \ = \ \frac{p}{(1 \ - \ p)} \ - \ p
$$

$$
L_q \ = \ \frac{p \ - \ p \ + \ p^2}{(1 \ - \ p)}
$$

Finally:

$$
\boxed{L_q \ = \ \frac{p^2}{(1 \ - \ p)}}
$$

Lastly, for the average waiting time in queue $W_q$:

This one is very symmetrical to $W \ = \ \frac{L}{\lambda}$ from Little's law:

$$
W_q \ = \ \frac{L_q}{\lambda}
$$

$$
W_q \ = \ \frac{\frac{p^2}{(1 \ - \ p)}}{\lambda}
$$

$$
W_q \ = \ \frac{p^2}{\lambda(1 \ - \ p)}
$$

Substituting $\lambda \ = \ p \mu$,

$$
W_q \ = \ \frac{p^2}{p\mu(1 \ - \ p)}
$$

$$
W_q \ = \ \frac{p}{\mu \ - \ \mu\frac{\lambda}{\mu}}
$$

Finally:

$$
\boxed{W_q \ = \ \frac{p}{\mu \ - \ \lambda}}
$$

---
# Example 1

Given arrival rate $\lambda$ is 8 customers per hour, and the service rate $\mu$ is 12 customers per hour.

Find:

- Utilization rate of the server.
- Probability that the server is empty.
- Probability of 1 customer in the system.
- Average number of customers in the system.
- Average waiting time per customer in the queue.
- Average time spent in system.
- Average waiting time in the queue.

**Solution**:

(a) The utilization: 

$$
p \ = \ \frac{\lambda}{\mu} \ = \ \frac{8}{12} \ = \ 0.66
$$

(b) Probability that the server is empty (not being utilized):

$$
1 \ - \ p \ = \ 1 \ - \ 0.66 \ = \ 0.34
$$

(c) Probability of 1 customer in the system $n \ = \ 1$.

$$
P_1 \ = \ (1 \ - \ p)p^n \ = \ (1 \ - \ p)p \ = \ 0.66 \ \times \ 0.34 \ = \ 0.2244
$$

(d) Average number of customers in the system:

$$
L \ = \ \frac{p}{(1 \ - \ p)} \ = \ \frac{0.66}{0.34} \ = \ 1.941
$$

(e) Average waiting time of customers in the queue:

$$
L_q \ = \ \frac{p^2}{(1 \ - \ p)} \ = \ \frac{0.4356}{0.34} \ = \ 1.281
$$

(f) Average time spent in the system:

From Little's law

$$
L \ = \ \lambda W \ \implies \ W \ = \ \frac{L}{\lambda}
$$

$$
W \ = \ \frac{1.941}{8} \ = \ 0.242
$$

(g) Average waiting time in the queue:

$$
W_q \ = \ \frac{L_q}{\lambda}
$$

$$
W_q \ = \ \frac{1.281}{8} \ = \ 0.1601
$$


**Short interpretation:** server busy 66.7% of the time; on average 2 customers in system (1.333 waiting + 0.666 being served); each customer spends 15 min total, waiting 10 min.


---
# Example 2

Given average waiting time in queue $W_q \ = \ \frac{1}{6}$ hours or $W_q \ = \ 0.166$ hours, the service rate $\mu \ = \ 6$ customers/hours, 

Find:

- Arrival rate of customers.
- Utilization rate of the server.
- Probability that the server is empty.
- Average number of customers in the system.
- Average waiting time per customer in the queue.
- Average time spent in system.

(a) The arrival rate of customers:

From:

$$
W_q \ = \ \frac{p}{\mu \ - \ \lambda}
$$

and: 

$$p \ = \ \frac{\lambda}{\mu}$$ 

$$
W_q \ = \ \frac{\lambda}{\mu^2 \ - \ \mu \lambda}
$$

$$
\lambda \ = \ W_q \ \mu^2 \ - \ W_q \ \mu \ \lambda
$$

$$
\lambda \ + \ W_q \ \mu \lambda \ = \ W_q \ \mu^2
$$

$$
\lambda(1 \ + \ W_q \mu) \ = \ W_q \ \mu^2
$$

$$
\lambda \ = \ \frac{W_q \mu^2}{(1 \ + \ W_q \mu)}
$$

$$
\lambda \ = \ \frac{0.166 \ \times \ 36}{1 \ + \ (0.166 \ \times \ 6)}
$$

$$
\lambda \ = \ \frac{5.976}{1 \ + \ 0.996}
$$

$$
\lambda \ = \ \frac{5.976}{1.996}
$$

$$
\lambda \ = \ 2.993 \ \approx \ 3 \ \text{customers per hour}
$$

(b) Utilization rate: 

$$
p \ = \ \frac{\lambda}{\mu} \ = \ \frac{3}{6} \ = \ 0.5
$$

(c) Probability that the server is empty:

$$
P_0 \ = \ 1 \ - \ p \ = \ 0.5
$$

(d) Average number of customers in the system:

$$
L \ = \ \frac{p}{(1 \ - \ p)} \ = \ \frac{0.5}{0.5} \ = \ 1
$$

(e) Average waiting time of customers in the queue:

$$
L_q \ = \ \frac{p^2}{(1 \ - \ p)} \ = \ \frac{0.25}{0.5} \ = \ 0.5
$$

(f) Average time spent in the system:

From:

$$
L \ = \ \lambda W
$$

$$
W \ = \ \frac{L}{\lambda}
$$

$$
W \ = \ \frac{1}{3} \ = \ 0.33
$$

**Interpretation:** with those numbers, arrivals are half the service rate; average one customer in system (0.5 waiting, 0.5 in service); customers wait 10 minutes on average and spend 20 minutes total.

---
# Case 2: M/M/1(N/FIFO)-- finite capacity queueing model

Short plain-English first: now the system can hold **at most N customers** (including the one in service).

If an arrival finds $N$ customers already present, that arrival is blocked (lost). Everything else (Poisson arrivals, exponential service, FCFS), stays the same.

---
## Key symbols/reminder

- $\lambda$ = offered arrival rate
- $\mu$ = service rate
- Utilization, $p \ = \ \frac{\lambda}{\mu}$
- $N$ = system capacity (max customers including one in service)
- $P_n$ = steady-state probability of $n$ customers in the system ($0 \ \leq \ n \ \leq \ N$)
- $\lambda_{eff} \ = \ \lambda(1 \ - \ P_N)$ = accepted arrival rate (use this in Little’s Law for times)

---
## Two cases

### $p \ = \ 1$, arrivals exactly equal to service

For the _infinite_ M/M/1 queue, we **reject ρ≥1** because the queue would blow up.

For the finite case, the queue cannot blow up, it's capped at $N$. So even if arrivals = service i.e. $p \ = \ 1$, the system stays stable because arrivals beyond $N$ are rejected.

So, when $p \ = \ 1$,

$$
P_n \ = \ P_0 \ \times \ p^n \ = \ P_0 \ (1^n) \ = \ P_0
$$

All probabilities become equal.

But we still need them to sum to 1:

$$
P_0 \ + \ P_1 \ + \ \cdots \ + \ P_N \ = \ 1
$$

That's:

$$
(N \ + \ 1)P_0 \ = \ 1
$$

$$
P_0 \ = \ \frac{1}{N \ + \ 1}
$$

$$
P_n \ = \ \frac{1}{N \ + \ 1}, \ n \ = \ 0, \ 1, \ \cdots, \ N
$$

And for $p \ < \ 1$ it's all the more acceptable since the arrivals are slower than the service system, so the system stays stable.

---
## Numerical solving.

Alright now since I am pressed for time, I will stop with the theoretical explanations here and skip ahead to how to solve numericals of the finite case using **only 4 formulae**.

### One master formula:

Utilization for $n$ customers:

$$
P_n \ = \ \frac{p^n}{\sum^N_{k \ = \ 0}{p^k}}
$$


### One arrival formula:

Effective arrival:

$$
\lambda_{eff} \ = \ \lambda(1 \ - \ P_N)
$$


###  One average formula

Average number of customers in the system
$$
L \ = \ \sum^N_{n \ = \ 0}{n P_n}
$$

### Little's law (same as infinite queue case)

$$
W \ = \ \frac{L}{\lambda}
$$

and:

$$
W_q \ = \ \frac{L_q}{\lambda_{eff}}
$$


and:

$$
L_q \ = \ L \ - \ (1 \ - \ P_0)
$$


---
## Example 1: $p \ < \ 1$ case.

Given arrival rate = 3 customers per hour, service rate = 5 customers per hour and max system capacity = 4 customers.

Find:

- Utilization
- Utilization for all customers ranging from none (system empty) to the max system capacity ($N$)
- The effective arrival
- Average number of customers in the system
- Average waiting time of customers in the queue
- Average time spent in the system
- Average time spent in the queue

So, we have:

$\lambda \ = \ 3$
$\mu \ = \ 5$
$N \ = \ 4$


(a) Utilization:

$$
\rho \ = \ \frac{3}{5} \ = \ 0.6
$$

(b) Utilization for all customers ranging from none (system empty) to the max system capacity ($N$):

From:

$$
P_n \ = \ \frac{p^n}{\sum^N_{k \ = \ 0}{p^k}}
$$

Computing the denominator first:

$$
\sum^4_{k \ = \ 0}{0.6^k} \ = \ p^0 \ + \ p^1 \ + \ p^2 \ + \ p^3 \ + \ p^4
$$

$$
\sum^4_{k \ = \ 0}{0.6^k} \ = \ 1 \ + \ 0.6 \ + \ 0.36 \ + \ 0.216 \ + \ 0.1296 \ = \ 2.3056
$$


So, 

$$
P_n \ = \ \frac{0.6^n}{2.3056}
$$

- $P_0 \ = \ \frac{1}{2.3056} \ = \ 0.4336$
- $P_1 \ = \ \frac{0.6}{2.3056} \ = \ 0.2601$
- $P_2 \ = \ \frac{0.36}{2.3056} \ = \ 0.1561$
- $P_3 \ = \ \frac{0.216}{2.3056} \ = \ 0.09365$
- $P_4 \ = \ \frac{0.1296}{2.3056} \ = \ 0.05619$

The blocking probability is $P_N \ = \ P_4 \ = \ 0.05619$ i.e. the probability of utilization of the server when any further arrivals in the queue will be lost/rejected.

(c) Effective arrival

$$
\lambda_{eff} \ = \ \lambda(1 \ - \ P_N)
$$

$$
\lambda_{eff} \ = \ 3(1 \ - \ P_4) \ = \ 3(1 \ - \ 0.05619)
$$


$$
\lambda_{eff} \ = \ 2.8314
$$


(d) Average number of customers in the system:

$$
L \ = \ \sum^N_{n \ = \ 0}{n P_n}
$$

Here $n$ starts from zero and proceeds till $N$ times.

So,

$$
L \ = \ \sum^4_{n\ = \ 0}{nP_n} \ = \ 0 \ \cdot \ P_0 \ + \ 1 \ \cdot \ P_1 \ + \ 2 \ \cdot \ P_2 \ + \ 3 \ \cdot \ P_3 \ + \ 4 \ \cdot \ P_4
$$

$$
L \ = \ 0 \ + \ 0.2601 \ + \ 2(0.1561) \ + \ 3(0.09365) \ + \ 4(0.05619)
$$

$$
L \ = \ 1.07796
$$


(d) Average time spent waiting by customers in the queue:

$$
L_q \ = \ L \ - \ (1 \ - \ P_0) \ = \ 1.07796 \ - \ (1 \ - \ 0.4336)
$$

$$
L_q \ = \ 1.07796 \ - \ 0.5664
$$

$$
L_q \ = \ 0.51156
$$

(e) Average time spent in the system:


$$
W \ = \ \frac{L}{\lambda_{eff}}
$$

$$
W \ = \ \frac{1.07796}{2.8314} \ = \ 0.3807 \ \text{hr}
$$

(f) Average time spent in the queue:

$$
W_q \ = \ \frac{L_q}{\lambda_{eff}}
$$

$$
W_q \ = \ \frac{0.51156}{2.8314}
$$

$$
W_q \ = \ 0.1807 \ \text{hr}
$$

---
## Example 2: $p \ = \ 1$ case

Given arrival rate = 4 customers per hour, service rate = 4 customers per hour and max system capacity = 3 customers.

Find:

- Utilization
- Utilization for all customers ranging from none (system empty) to the max system capacity ($N$)
- The effective arrival
- Average number of customers in the system
- Average waiting time of customers in the queue
- Average time spent in the system
- Average time spent in the queue

So, we have:

$\lambda \ = \ 4$
$\mu \ = \ 4$
$N \ = \ 3$


(a) Utilization:

$$
\rho \ = \ \frac{4}{4} \ = \ 1
$$

(b) Utilization for all customers ranging from none (system empty) to the max system capacity ($N$):

From:

$$
P_n \ = \ \frac{p^n}{\sum^N_{k \ = \ 0}{p^k}}
$$

Computing the denominator first:

$$
\sum^3_{k \ = \ 0}{1^k} \ = \ p^0 \ + \ p^1 \ + \ p^2 \ + \ p^3 \
$$

$$
\sum^4_{k \ = \ 0}{1^k} \ = \ 1 \ + \ 1 \ + \ 1 \ + \ 1 \ + \ = \ 4
$$


So, 

$$
P_n \ = \ \frac{1^n}{4}
$$

- $P_0 \ = \ \frac{1}{4} \ = \ 0.25$
- $P_1 \ = \ \frac{1}{4} \ = \ 0.25$
- $P_2 \ = \ \frac{1}{4} \ = \ 0.25$
- $P_3 \ = \ \frac{1}{4} \ = \ 0.25$

The blocking probability is $P_N \ = \ P_3 \ = \ 0.25$ i.e. the probability of utilization of the server when any further arrivals in the queue will be lost/rejected.

(c) Effective arrival

$$
\lambda_{eff} \ = \ \lambda(1 \ - \ P_N)
$$

$$
\lambda_{eff} \ = \ 4(1 \ - \ P_3) \ = \ 4(1 \ - \ 0.25)
$$


$$
\lambda_{eff} \ = \ 3
$$


(d) Average number of customers in the system:

$$
L \ = \ \sum^N_{n \ = \ 0}{n P_n}
$$

Here $n$ starts from zero and proceeds till $N$ times.

So,

$$
L \ = \ \sum^3_{n\ = \ 0}{nP_n} \ = \ 0 \ \cdot \ P_0 \ + \ 1 \ \cdot \ P_1 \ + \ 2 \ \cdot \ P_2 \ + \ 3 \ \cdot \ P_3 \
$$

$$
L \ = \ 0 \ + \ 0.25 \ + \ 2(0.25) \ + \ 3(0.25) \
$$

$$
L \ = \ 1.5
$$


(d) Average time spent waiting by customers in the queue:

$$
L_q \ = \ L \ - \ (1 \ - \ P_0) \ = \ 1.5 \ - \ (1 \ - \ 0.25)
$$

$$
L_q \ = \ 1.5 \ - \ 0.75
$$

$$
L_q \ = \ 0.75
$$

(e) Average time spent in the system:


$$
W \ = \ \frac{L}{\lambda_{eff}}
$$

$$
W \ = \ \frac{1.5}{3} \ = \ 0.5 \ \text{hr}
$$

(f) Average time spent in the queue:

$$
W_q \ = \ \frac{L_q}{\lambda_{eff}}
$$

$$
W_q \ = \ \frac{0.75}{3}
$$

$$
W_q \ = \ 0.25 \ \text{hr}
$$


---
# M/M/1 (∞) vs M/M/1 (N) — Formula Comparison Table

Just as a final summary.

| **Concept**                     | **M/M/1 (Infinite capacity)**                              | **M/M/1 (Finite capacity, max = N)**                             |
| ------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------------- |
| **Utilization**                 | $\rho = \frac{\lambda}{\mu}$                               | $\rho = \frac{\lambda}{\mu}$                                     |
| **State probabilities**         | $P_n = (1 - \rho)\rho^n$                                   | $P_n = \dfrac{\rho^n}{\sum_{k=0}^{N} \rho^k}$                    |
| **Probability of empty system** | $P_0 = 1 - \rho$                                           | $P_0 = \dfrac{1}{\sum_{k=0}^{N} \rho^k}$                         |
| **Blocking probability**        | _Not applicable_ (no blocking)                             | $P_N$                                                            |
| **Effective arrival rate**      | $\lambda_{\text{eff}} = \lambda$                           | $\lambda_{\text{eff}} = \lambda(1 - P_N)$                        |
| **Avg. number in system**       | $L = \dfrac{\rho}{1 - \rho}$                               | $L = \sum_{n=0}^{N} nP_n$                                        |
| **Avg. number in queue**        | $L_q = \dfrac{\rho^2}{1 - \rho}$                           | $L_q = L - (1 - P_0)$                                            |
| **Avg. time in system**         | $W = \dfrac{L}{\lambda} = \dfrac{1}{\mu - \lambda}$        | $W = \dfrac{L}{\lambda_{\text{eff}}}$                            |
| **Avg. waiting time in queue**  | $W_q = \dfrac{L_q}{\lambda} = \dfrac{\rho}{\mu - \lambda}$ | $W_q = \dfrac{L_q}{\lambda_{\text{eff}}}$                        |
| **Stability requirement**       | $\lambda < \mu$ (must hold)                                | Always stable (capacity finite)                                  |
| **Little’s Law**                | $L = \lambda W$, $L_q = \lambda W_q$                       | $L = \lambda_{\text{eff}} W $, $ L_q = \lambda_{\text{eff}} W_q$ |

---
