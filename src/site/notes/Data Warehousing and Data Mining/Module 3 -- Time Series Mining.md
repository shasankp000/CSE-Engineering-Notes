---
{"dg-publish":true,"permalink":"/data-warehousing-and-data-mining/module-3-time-series-mining/","title":"Time Series Mining and Periodicity Analysis -- Data Mining -- Module 3","tags":["Data-Mining","Semester-6"],"created":"2025-04-20T19:16:45.180+05:30"}
---

---
# Index

1. [[#Trend Analysis]]
2. [[#Periodicity Analysis]]
3. [[#🚩 What Is Periodicity?]]
4. [[#Lag in Time Series]]
5. [[#Autocorrelation Function (ACF)]]
6. [[#🌡️ What Autocorrelation Values Mean]]
7. [[#Fourier Transform]]
8. [[#Now how on earth would one interpret this data?]]
9. [[#💡 What Fourier Transform actually does]]
10. [[#Trend Analysis]]
11. [[#1. Free-Hand Method ✍️ (Explanation Only)]]
12. [[#2. Semi-Average Method]]
13. [[#3. Moving Average Method]]
14. [[#Weighted Moving Averages]]
15. [[#4. Fitting Mathematical Curves]]
16. [[#a. Linear Trend (Recap)]]
17. [[#b. Quadratic Trend]]
18. [[#Similarity Search]]
19. [[#1. Euclidean Similarity Search]]
20. [[#2. Dynamic Time Warping (DTW)]]
21. [[#3. Cosine Similarity Search]]

---
# Time Series Analysis

## 🕒 **Time Series Analysis: Basics**

### 🔹 What is a Time Series?

A **time series** is a ==sequence of data points indexed in time order==. Typically, the data is collected at consistent intervals (e.g., daily stock prices, hourly temperature, monthly sales).

Example:

```python
Time       Temperature (°C)
---------------------------
01:00      22.1
02:00      22.3
03:00      21.8
04:00      21.2
```
---
### 🔹 Why Analyze Time Series?

Time series analysis is used for:

- **Forecasting** (e.g., predicting future stock prices)
- **Trend detection** (e.g., increasing or decreasing behavior over time)
- **Anomaly detection** (e.g., detecting faults in equipment)
- **Seasonal behavior** (e.g., sales rising every December)

---
## 🧱 **Components of a Time Series**

Time series data is usually decomposed into the following key components:

### 1. **Trend (Tt)**

==A long-term increase or decrease in the data. It doesn't have to be linear==.

**Example**:  
Gradual increase in global temperatures over years.

### 2. **Seasonality (St)**

==A repeating pattern at regular intervals== (hourly, daily, monthly, yearly).  
It’s caused by seasonal factors like weather, holidays, habits, etc.

Example:  
Higher ice cream sales in summer months every year.

### 3. **Cyclic Patterns (Ct)**

==These are long-term oscillations not fixed to a calendar.  
Cycles are influenced by economic conditions, business cycles,== etc.

Difference from seasonality:  
Seasonality is **fixed and periodic**; cycles are **irregular and non-fixed**.

### 4. **Noise/Irregular (Et)**

==Random variations or residuals left after removing other components.  
Unpredictable and caused by unexpected or rare events== (e.g., pandemic).

---
## 📊 **Types of Time Series Models**

1. **Additive Model**:  
    Assumes the components add together:  
    **Yt = Tt + St + Ct + Et**
    
2. **Multiplicative Model**:  
    Assumes the components multiply together:  
    **Yt = Tt × St × Ct × Et**

Use additive if the seasonal fluctuations remain constant in magnitude.  
Use multiplicative if fluctuations increase with the level of the series.

---
## 🧠 Other Key Concepts

### ✅ Stationarity

A stationary time series has constant statistical properties over time (mean, variance, autocorrelation).  
Stationarity is often required for many forecasting models (like ARIMA).

### ✅ Lag

==How many steps back in time you're comparing data==.  
Lag helps in autocorrelation and feature engineering.

### ✅ Autocorrelation

==How related current values are with past values in the series==.  
Helpful for modeling dependencies over time.

---

## 🧩 Real-World Applications

- Weather prediction
- Stock market forecasting
- Sales forecasting
- Network traffic monitoring
- Energy consumption trends
---
# Periodicity Analysis

#### 🚩 What Is Periodicity?

Periodicity is when a time series **repeats a pattern at regular intervals**. These intervals are called the _period_. Common examples:

- **Daily temperature patterns**
- **Seasonal sales trends** (e.g., spikes during Diwali or Christmas)
- **Traffic congestion patterns** during weekdays

> If trends show an upward or downward movement, **periodicity** shows cyclic up-and-down movements at fixed durations.

---
#### 🧠 Intuition

Imagine you're tracking the number of coffee sales at a cafe every hour. You’ll likely see spikes in the morning and late afternoon — **repeating every day**. That’s a _daily periodicity_.

---
#### 🔍 Identifying Periodicity

There are three key ways to detect periodicity:

1. **Visual Inspection**: Plot the time series. Look for repeating patterns.
2. **Autocorrelation Function (ACF)**:
    - Measures how similar the series is with itself at different lags.
    - High ACF at a lag = possible periodicity at that interval.
3. **Fourier Transform**:
    - Converts time series from time-domain to frequency-domain.
    - Helps us spot dominant frequencies (or periods).
    - Output: Frequencies with high amplitudes indicate repeating cycles.

---
## Lag in Time Series

A **lag** just means =="how far back in time you look"==.

If you have a time series like this (let’s say it's daily temperature):

|Day|Temp|
|---|---|
|1|21°C|
|2|23°C|
|3|22°C|
|4|24°C|
|5|23°C|
|6|25°C|
|7|26°C|

Then:

- **Lag 1** → compare today's value with **yesterday's**
- **Lag 2** → compare today's value with **2 days ago**
- **Lag 3** → compare today's value with **3 days ago**
- ...and so on.

---
### 📊 Lag in Action

Let’s create Lag 1 version of this data:

|Day|Temp|Lag-1 Temp|
|---|---|---|
|1|21°C|–|
|2|23°C|21°C|
|3|22°C|23°C|
|4|24°C|22°C|
|5|23°C|24°C|
|6|25°C|23°C|
|7|26°C|25°C|

---
### What Exactly Did We Do in Lag 1?

Let’s say you’re on **Day 4**, and you want to know:

> What was the temperature **yesterday** (i.e., Day 3)?

That’s what ==Lag 1== does — ==it shifts the original data downward by 1 step== so that for each day, you can compare today's value to the one **from 1 day before**.

So `Lag-k`  would ==shift the data downwards by k steps==

So here’s what it looks like in action:

#### Original Data:

|Day|Temp|
|---|---|
|1|21|
|2|23|
|3|22|
|4|24|
|5|23|
|6|25|
|7|26|

#### Create Lag-1 (Shift all Temps down by 1 row):

|Day|Temp|Lag-1 Temp|
|---|---|---|
|1|21|–|
|2|23|21|
|3|22|23|
|4|24|22|
|5|23|24|
|6|25|23|
|7|26|25|

**Why the blank?**

- Because **Day 1** has no "previous day" to compare it with. That’s why the **Lag-1 Temp** is blank 
- (or usually treated as `NaN` in code).

---
### 🧠 What are we doing with this?

We're preparing to measure:

> "How similar is today’s temp to yesterday’s temp?"

If there’s a **strong correlation** between `Temp` and `Lag-1 Temp`, that means the series has **memory** — it depends on the past.

This concept becomes **core** when we do:

- Autocorrelation
- ACF plots
- Time-series forecasting (like ARIMA, which literally stands for _Auto-Regressive Integrated Moving Average_)
---

So, technically this is how a Lag-2 dataset would look like if we were comparing today's temp with that of 2 days ago:

| Day | Temp | Lag-2 Temp |
| --- | ---- | ---------- |
| 1   | 21°C | –          |
| 2   | 23°C | –          |
| 3   | 22°C | 23°C       |
| 4   | 24°C | 22°C       |
| 5   | 23°C | 24°C       |
| 6   | 25°C | 23°C       |
| 7   | 26°C | 25°C       |

Key rule : **More blanks as value of n increases in a Lag-N dataset**.

----
### 🧠 What's going on?

- **Day 3** now has **Lag-2 Temp = 21°C**, because that was the temperature on **Day 1**.
- **Day 4 → Lag-2 = Day 2**
- **Day 5 → Lag-2 = Day 3**, and so on...

----
### ⬇️ More Progressive Lag = More Missing Entries

Yep, and here's a key point:

- **Lag-1:** First row is blank.
- **Lag-2:** First two rows are blank.
- **Lag-n:** First _n_ rows will be blank (or `NaN` in code).

Because you can’t look back beyond what data exists — so the higher the lag, the more initial data you _lose_ from the top.

---
### 📘 Examples of What Lags Mean

- **Lag 1**: compare with yesterday → short-term effects (momentum, decay)
- **Lag 7**: compare with last week → weekly cycles
- **Lag 12 (if monthly data)**: compare with same month last year → yearly seasonality

---
### ⚠️ Important Note:

You lose data points with each lag.  
If your dataset has 100 entries, then for:

- **Lag 1** → you get 99 valid comparisons
- **Lag 2** → 98 comparisons
- ...
- **Lag k** → (N - k) comparisons

---
## Autocorrelation Function (ACF)

Autocorrelation (ACF) tells you **how related a time series is with a lagged version of itself**.

Imagine sliding the entire time series over itself by some number of time steps (called a **lag**) and checking **how similar** the series is to the original.  
It’s like asking:

> "Is today’s value similar to the value from 1 day ago? 2 days ago? 7 days ago?"


**Formula**:

Given a time series :

$$x_1, \ x_2, \ ....., \ x_n$$

The autocorrelation at lag $k$  is :

$$ACF(k) \ or \ r_k \ = \ \frac{\Sigma^{n-k}_{i =1} \  (X_i \ - \ \bar{X})(X_{i+k} \ - \ \bar{X})}{\sqrt{\Sigma^{n-k}_{i =1} \ (X_i \ - \ \bar{X})^2 \ \cdot \ \Sigma^{n-k}_{i =1} \ (X_{i+k} \ - \ \bar{X})^2}}$$


Scary looking formula, I know. But things will clear up with a few examples.

### 🧩 What Do the Variables Mean?

| Symbol     | Meaning                                                            |
| ---------- | ------------------------------------------------------------------ |
| $X_i$      | Value at time step $i$ (current value in the original time series) |
| $X_{i+k}$​ | Value at time step $i + k$ (value after lag `k`)                   |
| $\bar{X}$  | Mean of the entire time series (or just the part used in the sum)  |
| $r_k​$     | Autocorrelation at lag $k$                                         |
| $n$        | Total number of observations in the time series                    |

**Note**, to simplify the formula we sometimes re-write $X_{i+k}$  as $Y_i$

---
### Example 1

To fully clear this out, let's work on an example step by step, in detail :

### 🌡️ Time Series Data (Temperature)

|Day|Temp (X)|
|---|---|
|1|21|
|2|23|
|3|22|
|4|24|
|5|23|
|6|25|
|7|26|

Let's say we want to find out the ACF at lag 1 ($r_1$).

### 🔁 Step 1: Create lagged pairs for lag 1

We shift the temperature values by one day to get `Lag-1 Temps`:

Note that here for simplicity purposes we set $X_{i+k} \ = \ Y_i$

| Day | Temp ($X_i$) | Lag-1 Temp ($Y_i$ or $X_{i+k}$ ) |
| --- | ------------ | -------------------------------- |
| 2   | 23           | 21                               |
| 3   | 22           | 23                               |
| 4   | 24           | 22                               |
| 5   | 23           | 24                               |
| 6   | 25           | 23                               |
| 7   | 26           | 25                               |

Note that the table above would be the same as :


| Day | Temp ($X_i$) | Lag-1 Temp ($Y_i$  or  $X_{i+k}$) |
| --- | ------------ | --------------------------------- |
| 1   | 21           | __                                |
| 2   | 23           | 21                                |
| 3   | 22           | 23                                |
| 4   | 24           | 22                                |
| 5   | 23           | 24                                |
| 6   | 25           | 23                                |
| 7   | 26           | 25                                |

However in the previous table we just skipped the first row and started from Day 2.


So we now have 6 pairs:

- X = `[23, 22, 24, 23, 25, 26]`
- Y = `[21, 23, 22, 24, 23, 25]`

---
### 🧮 Step 2: Calculate the mean ($\bar{X}$ and $\bar{Y}$)

This is a one time calculation

$$\bar{X} \ = \ \frac{23 \ + \ 22 \ + \ 24 \ + \ 23 \ + \ 25 \ + \ 26}{6} \ \approx \ 23.83$$

$$\bar{Y} \ = \ \frac{21 \ + \ 23 \ + \ 22 \ + \ 24 \ + \ 23 \ + \ 25}{6} \ \approx \ 23.0$$

---
### Step 3: Calculate each part of the formula

**Numerator**:

$$\Sigma \ (X_i \ - \ \bar{X})(Y_i \ - \ \bar{Y})$$

Now hold on a minute.

Why was $\bar{X}$  replaced with $\bar{Y}$ ? Why feel the need to do that?

Without confusing you too much, just for simplicity purposes, know this, that when we assigned $X_{i+k}$  as $Y_i$, the associated term with it's components:

$(X_{i+k} \ - \ \bar{X})$  in numerator and:

$\Sigma^{n-k}_{i =1} \ (X_{i+k} \ - \ \bar{X})^2$

will also be replaced with a $Y$ component for "consistency purposes".

Otherwise if you need more detailed explanation you can ask any AI but the answer you will get, will most certainly fry your brain (trust me, I tried it, didn't understand).
  
So let's stick to just knowing the formulae here:

**Denominator**:

$$\sqrt{ \Sigma (X_i \ - \ \bar{X})^2 \ \cdot \ \Sigma (Y_i \ - \ \bar{Y})^2}$$


Let's calculate everything in a table.

Remember we have :

$$\bar{X} \ = \ 23.83$$

$$\bar{Y} \ = \ 23.0$$


And the table as:

| i   | $X_i$ | $Y_i$ | $X_i - \bar{X}$ | $Y_i \ - \ \bar{Y}$ | $(X_i - \bar{X})(Y_i - \bar{Y})$ | $(X_i - \bar{X})^2$ | $(Y_i - \bar{Y})^2$ |
| --- | ----- | ----- | --------------- | ------------------- | -------------------------------- | ------------------- | ------------------- |
| 1   | 23    | 21    |                 |                     |                                  |                     |                     |
| 2   | 22    | 23    |                 |                     |                                  |                     |                     |
| 3   | 24    | 22    |                 |                     |                                  |                     |                     |
| 4   | 23    | 24    |                 |                     |                                  |                     |                     |
| 5   | 25    | 23    |                 |                     |                                  |                     |                     |
| 6   | 26    | 25    |                 |                     |                                  |                     |                     |

So now we start filling the values :

So for $X_i \ - \ \bar{X}$  it will be each value in a cell of $X_i \ - \ 23.83$ 

And for $Y_i \ - \ bar{Y}$, it will be each value in a cell of $Y_i \ - \ 23.0$

| i   | $X_i$ | $Y_i$ | $X_i - \bar{X}$ | $Y_i \ - \ \bar{Y}$ | $(X_i - \bar{X})(Y_i - \bar{Y})$ | $(X_i - \bar{X})^2$ | $(Y_i - \bar{Y})^2$ |
| --- | ----- | ----- | --------------- | ------------------- | -------------------------------- | ------------------- | ------------------- |
| 1   | 23    | 21    | -0.83           | -2.0                |                                  |                     |                     |
| 2   | 22    | 23    | -1.83           | 0.0                 |                                  |                     |                     |
| 3   | 24    | 22    | 0.17            | -1.0                |                                  |                     |                     |
| 4   | 23    | 24    | -0.83           | 1.0                 |                                  |                     |                     |
| 5   | 25    | 23    | 1.17            | 0.0                 |                                  |                     |                     |
| 6   | 26    | 25    | 2.17            | 2.0                 |                                  |                     |                     |

Now the remaining columns are easier.

$(X_i - \bar{X})(Y_i - \bar{Y})$  is just the product of the values of each cell of the two columns we just calculated.

$(X_i - \bar{X})^2$ is just the square of the values of the first column we calculated.

$(Y_i - \bar{Y})^2$ is just the square of the values of the second column we calculated.


So, the table is now:

| i   | $X_i$ | $Y_i$ | $X_i - \bar{X}$ | $Y_i \ - \ \bar{Y}$ | $(X_i - \bar{X})(Y_i - \bar{Y})$ | $(X_i - \bar{X})^2$ | $(Y_i - \bar{Y})^2$ |
| --- | ----- | ----- | --------------- | ------------------- | -------------------------------- | ------------------- | ------------------- |
| 1   | 23    | 21    | -0.83           | -2.0                | 1.66                             | 0.6889              | 4.0                 |
| 2   | 22    | 23    | -1.83           | 0.0                 | 0.0                              | 3.3489              | 0.0                 |
| 3   | 24    | 22    | 0.17            | -1.0                | -0.17                            | 0.0289              | 1.0                 |
| 4   | 23    | 24    | -0.83           | 1.0                 | -0.83                            | 0.6889              | 1.0                 |
| 5   | 25    | 23    | 1.17            | 0.0                 | 0.0                              | 1.3689              | 0.0                 |
| 6   | 26    | 25    | 2.17            | 2.0                 | 4.34                             | 4.7089              | 4.0                 |

Now for the numerator:

$$\Sigma \ (X_i \ - \ \bar{X})(Y_i \ - \ \bar{Y})$$


It's just the sum of the values in the column of $(X_i - \bar{X})(Y_i - \bar{Y})$

So :

$$\Sigma \ (X_i \ - \ \bar{X})(Y_i \ - \ \bar{Y}) \ \approx 4.99$$

And the denominator:

$$\sqrt{ \Sigma (X_i \ - \ \bar{X})^2 \ \cdot \ \Sigma (Y_i \ - \ \bar{Y})^2}$$


It's just the **square root of the product of the sums of all the values** in  $(X_i - \bar{X})^2$ and  $(Y_i \ - \ \bar{Y})^2$   respectively

So :

$\Sigma (X_i \ - \ \bar{X})^2 \ \approx \ 10.8334$

$\Sigma (Y_i \ - \ \bar{Y})^2 \ \approx \ 10$


So denominator :

$$\sqrt{ \Sigma (X_i \ - \ \bar{X})^2 \ \cdot \ \Sigma (Y_i \ - \ \bar{Y})^2} \ \approx \ 10.41$$

---
### ✅ Step 4 : Final ACF at lag 1:

$$r_1 \ = \ \frac{4.99}{10.41} \ \approx \ 0.479$$

---
### 🧠 Intuition

- $r_1 = 0.479$ means there’s a **moderate positive autocorrelation** — temperature values are **somewhat correlated** with the values one day before.

---
### Let's try for lag 2.

So our lag 2 dataset will look like this:

|Day|Temp ($X_i$)|Lag-2 Temp ($X_{i-2}$)|
|---|---|---|
|3|22|21|
|4|24|23|
|5|23|22|
|6|25|24|
|7|26|23|

Now we have 5 pairs

- X = `[22, 24, 23, 25, 26]`
- Y = `[21, 23, 22, 24, 23]`

Let's find the mean


$$\bar{X} \ = \ \frac{22 \ + \ 24 \ + \ 23 \ + \ 25 \ + \ 26}{5} \ = \ 24$$

$$\bar{Y} \ = \ \frac{21 \ + \ 23 \ + \ 22 \ + \ 24 \ + \ 23 }{5} \ \approx \ 22.6$$


Now let's calculate everything in the formula :

| i   | $X_i$ | $Y_i$ | $X_i - \bar{X}$ | $Y_i \ - \ \bar{Y}$ | $(X_i - \bar{X})(Y_i - \bar{Y})$ | $(X_i - \bar{X})^2$ | $(Y_i - \bar{Y})^2$ |
| --- | ----- | ----- | --------------- | ------------------- | -------------------------------- | ------------------- | ------------------- |
| 1   | 22    | 21    | -2              | -1.6                | 3.2                              | 4                   | 2.56                |
| 2   | 24    | 23    | 0               | 0.4                 | 0                                | 0                   | 0.16                |
| 3   | 23    | 22    | -1              | -0.6                | 0.6                              | 1                   | 0.36                |
| 4   | 25    | 24    | 1               | 1.4                 | 1.4                              | 1                   | 1.96                |
| 5   | 26    | 23    | 2               | 0.4                 | 0.8                              | 4                   | 0.16                |

Now for the numerator:

$$\Sigma \ (X_i \ - \ \bar{X})(Y_i \ - \ \bar{Y}) \ \approx \ 6.0$$


And for the denominator :

$$\sqrt{ \Sigma (X_i \ - \ \bar{X})^2 \ \cdot \ \Sigma (Y_i \ - \ \bar{Y})^2} \ \approx \ \sqrt{10 \ \cdot \ 5.2} \ \approx \ \sqrt{52.0} \ \approx \ 7.211$$



So, $$r_2 \ = \ \frac{6.0}{7.211} \ = \ 0.832 $$

---
### ✅ Intuition:

That’s a **strong positive correlation** at lag 2 — the temperature values from 2 days ago are quite predictive of today’s temperature. Makes sense for slow-changing weather.

### How are we interpreting this?

#### 🌡️ What Autocorrelation Values Mean

Autocorrelation (at lag _k_) measures how **similar** the time series is to a shifted version of itself by _k_ steps.

- **$r_k = 1$** → _Perfect positive correlation_: if the value _k_ days ago went up, today also goes up in the same proportion. A perfect match.
- **$r_k = 0$** → _No correlation_: the past values have no influence on today's value.
- **$r_k = -1$** → _Perfect negative correlation_: today's values are the **opposite** of what happened _k_ days ago.

|Correlation Value|Interpretation|
|---|---|
|0.9 to 1.0|Strong correlation (very similar)|
|0.7 to 0.9|Moderate to strong|
|0.4 to 0.7|Moderate|
|0.2 to 0.4|Weak|
|0.0 to 0.2|Very weak or no correlation|
|< 0|Inverse correlation|

---
## Fourier Transform

At its heart, **Fourier Transform (FT)** answers this question:

> "If this signal is made of waves, what waves is it made of?"

It takes a **time-based signal** (like temperature across days) and tells you:

- What **frequencies** (repeating patterns) are present.
- How **strong** each of those frequencies is.

---
### 🎛️ Analogy: Music and a Piano

Imagine a song is playing. You don’t just hear random noise — you hear notes.  
Each note is a **pure frequency** (like 440 Hz for A4).

What the **Fourier Transform** does is like:

- Listening to the song,
- Identifying each note being played (frequencies),
- And telling you how loud each note is (amplitude).

---

Given a discrete signal (e.g., daily temperatures):

$$x \ = \ [ \  x_0 , \ x_1, \ ...., \ x_{N-1} \ ]$$

The Discrete Fourier Transform (DFT) is defined as 

$$X_k \ = \ \Sigma^{n-1}_{n=0} \ x_n \ \cdot \ e^{(-2\pi \ \cdot k \ \cdot n)/N}$$

where:

- $X_k$ is the strength of frequency $k$,
- $x_n$ is your original data (e.g., temperature at day $n$),
- $e^{-2\pi i \cdot k \cdot n / N}$ is a complex wave function (sinusoids!).

Don't worry if that looks scary. We’ll break it down visually and practically.


So, a few points before we proceed :

#### 1. What does $k$  do?

In $$X_k \ = \ \Sigma^{n-1}_{n=0} \ x_n \ \cdot \ e^{(-2\pi \ \cdot k \ \cdot n)/N}$$

Quick recap over what's frequency, oscillations, cycles :

![Pasted image 20250424184833.png](/img/user/media/Pasted%20image%2020250424184833.png)


The frequency of a signal or wave is ==the number of complete cycles or oscillations that occur within a given time period==. It is measured in Hertz (Hz), where 1 Hz represents one cycle per second. Think of it as how many times a wave crest passes a point in a second.


- $k$ is the **frequency index**.
- It tells you **how many full oscillations** (waves) occur across the full length of the signal.
- In a signal of length $N$, $k = 0$ means **no oscillation** (just the average), while $k=N/2$ is the **highest frequency** you can detect (one sample per half-cycle — the Nyquist frequency).
- So each $X_k$​ tells you **how much of frequency $k$** exists in your signal.

For example, with our 4-point signal:

| Day ($n$) | Temp ($x_n$) |
| --------- | ------------ |
| 0         | 21           |
| 1         | 23           |
| 2         | 22           |
| 3         | 24           |

- $X_0$: mean or DC component
- $X_1$: slow wave that completes 1 full cycle over 4 samples
- $X_2$​: faster wave that completes 2 full cycles over 4 samples
- $X_3$​: completes 3 cycles — it’s actually symmetric to $X_1$

Now, let's see what frequency means when we are performing DFT in periodicity analysis

In DFT, we’re not talking about physical Hz (like "times per second") unless you're sampling over time. Instead, the frequency index $k$ corresponds to **how many complete cycles (oscillations) fit into your data length $N$**.

So this means that $k \ = \ N \ - \ 1$

For $N \ = \ 4$

- You’ll get 4 frequency components: $k = 0, 1, 2, 3$
- They represent 0 to 3 **cycles per $N$**

So **k is basically the number of oscillations of a complex wave over the total N data points**.

#### 2. Why do we write $e^{(-2\pi i)/N}$  as $\omega$ ? (pronounced as omega)

This is a **shorthand** used in Fourier theory.

It's done so that the formula becomes simple:

$$X_k \ = \ \Sigma^{N-1}_{n=0} \ x_n \ \cdot \ \omega^{kn}$$

Instead of re-computing the exponential every time, we reuse $\omega$ and just raise it to $kn$ powers.

It’s like a **complex unit circle step** — taking $omega$, and rotating it $kn$ times around the unit circle.

#### 3. What are the powers of $\omega$  and why do they rotate?

Since we use $\omega$  instead of calculating an exponent and rotating it $kn$ times, $\omega$  depends on a **complex unit circle**

This is because:

- $\omega = e^{-2\pi i / N}$ lies on the **complex unit circle**
- Raising $\omega$ to a power rotates it by some angle:

$\omega^n = \cos\left(\frac{2\pi n}{N}\right) - i\sin\left(\frac{2\pi n}{N}\right) \ = \ -i$

These are called the **roots of unity** — they loop around the circle and repeat every $N$ steps.


![Pasted image 20250424185907.png](/img/user/media/Pasted%20image%2020250424185907.png)

So for $N \ = \ 4$, the powers are:

| Power      | Value      | On Complex Plane     |
| ---------- | ---------- | -------------------- |
| $\omega^0$ | $1$        | Right (real axis)    |
| $\omega^1$ | $i$        | Top (imaginary axis) |
| $\omega^2$ | $−1$       | Left                 |
| $\omega^3$ | $−i$       | Bottom               |
| $\omega^4$ | $1$ again! | Full circle          |

And so on, for increasing $N$ values.

---
### 🔍 What You'll See

Fourier Transform gives us a **spectrum**:

- X-axis: Frequency (e.g., cycles per day)
- Y-axis: Strength of that frequency 

High peaks? → Strong repeating patterns at that frequency.  
Flat? → No strong repeating patterns.

---
### Example

#### 🔢 Sample Time Series

Let’s take 4 data points from a temperature time series:

| Day ($n$) | Temp ($x_n$) |
| --------- | ------------ |
| 0         | 21           |
| 1         | 23           |
| 2         | 22           |
| 3         | 24           |

Let $x \ = \ [ \ 21, 23, 22, 24 \ ]$,  so $N \ = \ 4$.

Now we define the shared variables

- $N \ = \ 4$
- $\omega \ = \ e^{(-2\pi \ i)4} \ = \ -cos\frac{\pi}{2} \ - \ i \ \cdot sin(\frac{pi}{2}) \ = \ -i$

| Power         | Value      | On Complex Plane     |
| ------------- | ---------- | -------------------- |
| $\omega^0$    | $1$        | Right (real axis)    |
| $\omega^1$    | $i$        | Top (imaginary axis) |
| $\omega^2$    | $−1$       | Left                 |
| $\omega^3$    | $−i$       | Bottom               |
| $\omega^4$    | $1$ again! | Full circle          |
| $\omega^5$    | $i$        | Top (imaginary axis) |
| $\omega^6$    | $-1$       | Left                 |
| $\omega^7$    | $-i$       | Bottom               |
| $\omega^8$    | 1          | Full circle          |
| $\omega^9$    | $i$        | Top                  |
| $\omega^{10}$ | $-1$       | Left                 |
| $\omega^{11}$ | $-i$       | Bottom               |
| $\omega^{12}$ | 1          | Full circle          |

and $k \ = \ 0, \ 1, \ 2, \ 3$

So we start calculating $X_k$  terms one by one

$$X_0 \ = \ \Sigma \ x_n \ \cdot \ \omega^{kn}$$

Now we have $k \ = \ 0$, so 

$$X_0 \ = \ \Sigma \ x_n \ \cdot \ \omega^{0}$$

$$\implies X_0 \ = \  x_0 \ \cdot \ 1 \ + \ x_1 \ \cdot \ 1 \ + \ x_2 \ \cdot \ 1 \ + \ x_3 \ \cdot \ 1 $$

$$\implies X_0 \ = \ 21 \ + \ 23 \ + \ 22 \ + \ 24 $$

$$\implies X_0 \ = \ 90$$


Now for $k \ = \ 1$

$$X_1 \ = \ \Sigma \ x_n \ \cdot \ \omega^{n}$$


So, 

$$X_1 \ = \ x_0 \ \cdot \omega^0 \ + \ x_1 \ \cdot \omega^1 \ + \ x_2 \ \cdot \omega^2 \ + \ x_3 \ \cdot \ \omega^3$$

$$\implies X_1 \ = \ 21 \ + \ 23(i) \ + \ 22(-1) \ + \ 24(-i)$$

$$\implies X_1 \ = \ 21 \ + \ 23i \ - \ 22 \ - \ 24i$$

$$\implies X_1 \ = \ -1 \ + \ i$$


Similarly for $k \ = \ 2$

$$X_2 \ = \ \Sigma \ x_n \ \cdot \ \omega^{2n}$$


$$X_2 \ = \ 21 \ \cdot \omega^0 \ + \ 23 \ \cdot \omega^2 \ + \ 22 \ \cdot \ \omega^{4} \ + \ 24 \ \cdot \ \omega^{6} $$


$$X_2 \ = \ 21 \ - \ 23 \ + \ 22 \ - \ 24 $$

$$X_2 \ = \ -2 \ - \  2$$

$$X_2 \ = \ -4$$

Similarly for $k \ = \ 3$

$$X_3 \ = \ \Sigma \ x_n \ \cdot \ \omega^{3n}$$


$$\implies X_3 \ = \  21 \ \cdot \ \omega^0 \ + \ 23 \ \cdot \omega^3 \ + \ 22 \ \cdot \omega^6 \ + \ 24 \ \cdot \omega^9  $$

$$\implies X_3 \ = \ 21 \ - \ 23i \ + \ 22 \ + \ 24i$$

$$\implies X_3 \ = \ 43 \ + \ i$$

---
## Now how on earth would one interpret this data?

## 🧠 First: What are you even trying to do with Fourier?

You're saying:

> “I have some time-based data, like temperature each day. I want to know: **Does it seem to repeat every few days?**”

Like maybe it tends to warm up every 3rd day? Or every 7 days?

---

## 💡 What Fourier Transform actually does

Think of Fourier Transform as a smart assistant that asks your data:

> “If I imagine the temperature was caused by some regular up-and-down patterns... which patterns could explain it?”

Then it tries **many different rhythms** (called “frequencies”) and checks:

- “How strong is this pattern in your data?”

Each **Xₖ** term tells you:

- **How much of the pattern that repeats every N/k days exists in your data.**

---

### 🧃 Let’s break it with a juice example (non-physics)

Imagine you're tasting a fruit juice that’s made from:

- Apple (stable, always there)
- Lime (comes in a sharp burst every 2 sips)
- Orange (comes in a smoother, repeating every 3 sips)

You take 6 sips.

Fourier Transform says:

- 🧃 “Okay, the overall average flavor is apple = X₀.”
- 🍋 “I detect some lime that repeats every 2 sips = X₃.”
- 🍊 “I detect a bit of orange that shows up every 3 sips = X₂.”

You didn’t need to know anything about **waves**. You just know: **if the numbers in X₂ and X₃ are big, then those patterns are strong.**

---
### 🔢 Apply this to the temperature data

Let’s say you collect 7 days of temperature. You do a Fourier Transform, and the result shows:

|X index|Meaning|Value|
|---|---|---|
|X₀|Average temp|21.3|
|X₁|Every 7 days|1.2|
|X₂|Every 3.5 days|3.8|
|X₃|Every ~2.3 days|0.4|
|X₄|Every ~1.75 days|0.1|

From this, you see:

- **X₀ is big**: There’s a stable average.
- **X₂ is kinda big**: There seems to be a small **repeating rise/fall every 3–4 days**.
- Others are small: No strong repetition every 2 or 7 days.

---

### ✅ Summary: How Fourier helps find repeating behavior

You don’t need to think in frequency or waves.

All you’re doing is:

> 🧍 “Hey data, do you have patterns that repeat every k days?”  
> 📊 Fourier replies: “Yeah, a _bit_ every 3 days, but not much every 2 or 7.”

That’s it. That’s what you read from the **magnitudes** of the X terms (ignoring imaginary parts for now).

---
#### 🧠 Use-Cases

- **Forecasting seasonal sales**
- **Detecting cyclical anomalies** (like weekly fraud patterns)
- **Predicting periodic traffic surges**

---
#### 🧩 Tip

Periodicity is different from seasonality:

- **Seasonality** = known, calendar-based periodicity (e.g., every December)
- **Periodicity** = general repeating pattern (can be weekly, monthly, etc.)

---
# Trend Analysis

Now that we’ve looked at **repeating patterns (periodicity)** using tools like autocorrelation and Fourier, trend analysis helps us answer this:

### 🚶‍♂️ **Is the data generally moving up, down, or staying flat over time?**

Think of trend like the _overall direction_ the data is heading — regardless of small fluctuations or cycles.

---

## 🧭 What Trend Actually Means

Imagine temperature data for 30 days. If it’s ==slowly increasing over time== (like winter turning to spring), that’s an **upward trend**.

If it’s ==slowly decreasing== (like summer ending), that’s a **downward trend**.

If it wobbles around a ==flat average== (like no seasonal change), there’s **no trend**.

---
## Methods for measurement of Trends

Generally, we have 4 traditional methods of measuring trends.

![Pasted image 20250425121303.png](/img/user/media/Pasted%20image%2020250425121303.png)

### 1. Free-Hand Method ✍️ (Explanation Only)

Since this is a visual method, imagine plotting the points and then drawing a **smooth curve** through them. It would show a gentle **upward trend**.

> 🧠 Used mostly for quick inspection. No exact math involved. No plotting needed unless you want to practice curve-drawing by hand.


![Pasted image 20250425121549.png](/img/user/media/Pasted%20image%2020250425121549.png)

---
### 2. Semi-Average Method

Let's walk through with a sample dataset

|Day|Temp (°C)|
|---|---|
|1|20|
|2|21|
|3|23|
|4|24|
|5|26|
|6|27|
|7|29|
|8|30|

---
#### Step 1: Divide the data into 2 halves

Since we have 8 data points (even number), we divide them into two equal parts:

- **First Half (Days 1 to 4):** 20, 21, 23, 24
- **Second Half (Days 5 to 8):** 26, 27, 29, 30

---
#### Step 2: Calculate the average of each half

**First half average**:  

$$\frac{88}{4} \ = \ 22$$


**Second half average:**

$$\frac{112}{4} \ = \ 28$$

---
#### Step 3: Assign the averages to the mid-points of their respective halves.

First half ranges from days $1$ to $4$.

So the mid-point of this half would be : $\frac{1 \ + \ 4}{2} \ = \ 2.5$

Second half ranges from days $5$ to $8$.

So the mid-point of this half would be : $\frac{5 \ + \ 8}{2} \ = \ 6.5$

---
#### Step 4: Equation of the trend line

We have this equation of a trend line:

$$y \ = \ a \ + \ bt$$

##### 🧠 What do the variables mean?

| Symbol | Meaning                                                                                      |
| ------ | -------------------------------------------------------------------------------------------- |
| `y`    | Temperature (or the value we want to estimate)                                               |
| `t`    | Time (usually in days or time units)                                                         |
| `a`    | Intercept of the line (value when time = 0)                                                  |
| `b`    | Slope of the line (how much temp or the value we are estimating, increases per unit of time) |

---
#### What do you mean by an "intercept of a line"?

The intercept of a line, in this equation, to be specific, a **y-intercept** is basically:

##### 📌 What _is_ the **intercept** of a line, mathematically?

In a linear equation of the form:

$$y \ = \ a \ + \ bt$$

- $y$ is the **output** or dependent variable (in our case: temperature).
- $t$ is the **input** or independent variable (in our case: day number).
- $b$ is the **slope** of the line (how much $y$ changes when $t$ increases by 1).
- $a$ is the **intercept**, more specifically:

#####  The intercept is:

> **The value of $y$ when $t \ = \ 0$**  
> That is:



$$a \ =\ y$$

when 

$$ \ t \ = \ 0$$


It tells you **where the line cuts the vertical (y) axis** — the starting value before any changes due to the slope.

---
##### Why does this matter?

The intercept gives a **reference point** for your trend. It's like saying:

> “If this upward/downward trend had always existed, what would the value be at time zero?”

You don’t always need to _trust_ this value (especially when Day 0 isn’t in your dataset), but it’s crucial for defining a full line equation.

---

We now fit a straight line between these two points:  
**Point 1:** (2.5, 22)  
**Point 2:** (6.5, 28)

**Use the slope formula**:

$$b \ = \ \frac{y_2 \ - \ y_1}{x_2 \ - \ x_1} \ = \ \frac{28 \ - \ 22}{6.5 \ - \ 2.5} \ = \ \frac{6}{4} \ = \ 1.5$$


And plug the value of $b$ into this equation :


$$y \ = \ a \ + \ bt$$

Use (2.5, 22) to find $a$ .

$$22 \ = \ a \ + \ 1.5(2.5)$$


$$\implies a \ = \ 18.25 $$


### ✅ Final Trend Line Equation:

$$y \ = \ 18.25 \ + \ 1.5t$$

---

Now I believe you might have a few questions, such as:

#### 🎯 Why do we plug in `y = 22` and `t = 2.5`?

You calculated the **first average** as `22`, and that average came from the **first half**, centered at day `2.5`. So this gives us a real point on the trend line:

$$(2.5,\ 22)$$

We already know `b = 1.5`, so to find `a`, we just plug this into the formula:

$$22 \ = \ a \ + \ 1.5(2.5) \ \implies  22 \ = \ a \ + \ 3.75 \ \implies a \ = \ 18.25$$


So the final trend line equation becomes :

$$y \ = \ 18.25 \ + \ 1.5t$$

---
#### 🤔 Why do we _keep t_ in the final equation?

==Because the trend line isn’t just for one point—it's a formula you can use to== **predict or visualize the trend** over time. You plug in different `t` values (days) to see how the temperature is expected to behave **according to the trend**.

For example

- At day `t = 1`, predicted temp = `18.25 + 1.5×1 = 19.75`
- At day `t = 4`, predicted temp = `18.25 + 1.5×4 = 24.25`
- At day `t = 8`, predicted temp = `18.25 + 1.5×8 = 30.25`


So we see a **steadily increasing trend over time**, which says that the temperature is increasing as the days pass.

Here's a visualization for better understanding of the increasing trend.

![Pasted image 20250425134432.png](/img/user/media/Pasted%20image%2020250425134432.png)

---
### 3. Moving Average Method

==This method smooths out short-term fluctuations to reveal longer-term trends in the dataset==. It works by averaging a fixed number of consecutive data points and sliding the window forward.

In short: This method is used to detect long term trends in the dataset, but short-term trends or "local trends" are not so well depicted in this method.

#### Step 1 : Pick a window size (e.g., 3-point moving average)

Before we proceed however, here's some pre-requisites to know about this method:

##### 💡 What is "Window Size"?

The **window size** (also called "period") is ==the number of data points used to calculate each average==.

So when we say:

- **3-point Moving Average**, we are using **3 consecutive values** from the data to calculate a single average.
- **5-point Moving Average** means using **5 consecutive values** per average.


It's called a **"moving" average** because you slide this "window" across the data one step at a time.

So let's say we are working with our temperature dataset again:

| Day | Temp |
| --- | ---- |
| 1   | 20   |
| 2   | 22   |
| 3   | 19   |
| 4   | 21   |
| 5   | 24   |

If we use a **3-point moving average**, then:

- First, place the "window" over **Day 1 to Day 3**:  
    (20 + 22 + 19)/3 → **20.33**
    
- Slide the window to **Day 2 to Day 4**:  
    (22 + 19 + 21)/3 → **20.67**
    
- Slide again to **Day 3 to Day 5**:  
    (19 + 21 + 24)/3 → **21.33**


Now some of you might be confused, thinking: **Why are we doing this? Why choose Day 1 to Day 3, then 2 to 4, then 3 to 5, and heck, what are we even going to do with these values??**

#### 🌊 Why slide the window like that?

When we use a **3-point moving average**, the window shifts **one step forward each time**. That’s the key idea:

- First average: **Day 1, 2, 3**
- Then: **Day 2, 3, 4**
- Then: **Day 3, 4, 5**
- And so on…

This _overlapping window_ captures how the trend is **changing over time**, not just what it is in isolated chunks.

So it’s not that we’re jumping to random sets of days—it’s that we’re **sliding the window one step at a time**, like scanning a timeline gradually.


So the shifting can be demonstrated like this:

```python

1 2 3
  2 3 4
    3 4 5
      4 5 ...

```

Notice how we are "sliding" a window across, the window in question having a space of 3 points only, that's we pick 3 points at a time.


This _overlapping window_ captures how the trend is **changing over time**, not just what it is in isolated chunks.

So it’s not that we’re jumping to random sets of days—it’s that we’re **sliding the window one step at a time**, like scanning a timeline gradually.

---
##### 🤔 Why pick "3" as the window size?

**There’s no fixed rule**, but here are some guidelines:

| Window Size           | What It Does                              | When to Use                                  |
| --------------------- | ----------------------------------------- | -------------------------------------------- |
| Small (e.g., 3)       | Reacts quickly to recent changes          | Short-term trend, sensitive to noise         |
| Medium (e.g., 5 or 7) | Balances noise reduction & responsiveness | General trend observation                    |
| Large (e.g., 10+)     | Smoothes out a lot of noise               | Long-term trend, may miss short fluctuations |

---
##### 📉 What do we _do_ with these moving average values?

Each average you compute becomes a **smoothed version** of your original dataset.

You can:

- **Plot them** on a graph alongside the original temperatures to observe how the general trend behaves.
- Use them to **reduce noise** or daily fluctuation, helping you spot underlying **long-term patterns**.    
---
##### Here's a quick comparison:

| Day Range  | Average Temp |
| ---------- | ------------ |
| Day 1 to 3 | 20.33        |
| Day 2 to 4 | 20.67        |
| Day 3 to 5 | 21.33        |

If you plot those average temps at the **middle day** (e.g., Day 2, Day 3, Day 4), you start seeing a smoother line than the original, spiky temperature values.

Now, back to where we were:

#### Step 2: Assign the averages to a central point

Just like we did in semi-averages, we calculate the mean of the range of days assigned to an average, and assign the average temps to a specific day with each of their ranges respectively

So, 

| Day Range  | Average Temp | Central Point |
| ---------- | ------------ | ------------- |
| Day 1 to 3 | 20.33        | 2 (Day 2)     |
| Day 2 to 4 | 20.67        | 3 (Day 3)     |
| Day 3 to 5 | 21.33        | 4 (Day 4)     |

#### Step 3: Plot the data on a graph to observe the trend.

There can be two ways of plotting this data.

**Option A**:  If you're **just interested in seeing the trend visually**, no need to fit a line — just **plot** the moving average points. This already smooths out short-term fluctuations and shows the trend clearly.

This means just get a graph paper and directly plot the data in the above table.

which would look like this:

![Pasted image 20250425160754.png](/img/user/media/Pasted%20image%2020250425160754.png)


This smoothed red line represents the general trend by reducing the "noise" from smaller fluctuations. It helps visualize whether the overall direction is increasing, decreasing, or stable.

Here's how a 4-point and 5-point moving average would look like

![Pasted image 20250425160926.png](/img/user/media/Pasted%20image%2020250425160926.png)


You can see how increasing the window size smooths the curve even more, revealing a clearer long-term trend but at the cost of local detail.

So one can question: **What do we get by increasing the window size?**

##### 🧠 What You Get by Increasing Window Size:

1. **More Smoothing**:
    
    - Larger windows **reduce short-term fluctuations** or "noise".
    - You get a **cleaner view of the overall trend** — like removing the tiny wiggles to see the mountain slope.

2. **Slower Responsiveness**:
    
    - The trend reacts **more slowly** to new changes in data.
    - Sudden spikes or drops are **dampened** — which might be good or bad depending on your goal.

3. **Less Detail**:
    
    - Local variations, cycles, or patterns get **smoothed out** and possibly lost.
    - If you're analyzing **short-term patterns**, a large window might hide them.

---

**Option B**: If you're curious about **quantifying the trend** (e.g., _how fast temperature is increasing on average_), then you can fit a linear model:

$$y \ = \ a \ + \ bt$$

Like how we did in semi-averages.

Where:

- `y` = temperature (moving average)
- `t` = day (e.g., 2, 3, 4)
- `b` = slope (how much the temperature is rising/falling per day)
- `a` = value of y when t = 0 (intercept)

----
### 🔍 Moving Averages — Trade-off Summary:

|Aspect|Small Window|Large Window|
|---|---|---|
|📈 Reacts to changes|Quickly|Slowly|
|🔊 Shows noise|Yes (more visible)|No (smoothed out)|
|🔍 Detects short trends|Better|Poorly|
|🌄 Detects long trends|Less clearly|Clearly|

---
### Weighted Moving Averages

In a **weighted moving average** (WMA),

- **Different points are treated differently** — some are considered more important.
- Each point is multiplied by a **weight** depending on its importance.
- After multiplying, you **sum them** up and then **divide by the total of the weights**.

#### Key:

- You **don't divide by number of points** anymore.
- You **divide by the sum of the weights** you assigned.


#### 🧠 3. Why divide by sum of weights and not just number of points?

👉 Because after weighting, the total "amount" you are summing is **not evenly spread**.  
Some points have _more pull_ and _some less_.

If you divided by just 3, the number of points, you would **completely ignore the fact** that the middle point was counted twice as heavily as the others!

Instead, by dividing by 1+2+1 = **4**,  
you normalize the weighted sum back into a "proper average."

---
### 🛠️ Simple Weighted Moving Average example:

Let's say we have this dataset

![Pasted image 20250426123214.png](/img/user/media/Pasted%20image%2020250426123214.png)

We are asked to find the trend using a 3-year WMA, of weights 1, 2, 1

So we have a window size of 3 points.

So let's say for the first 3 years :

2 (Year 1), 4 (Year 2), 5 (Year 3)

And weights are 1, 2, 1.

**Steps:**

- Weighted sum = (2 × 1) + (4 × 2) + (5 × 1)  
    = 2 + 8 + 5  
    = 15
    
- Total weights = 1 + 2 + 1 = 4
- Weighted average = 15 / 4 = **3.75**

✅ Notice: If you just divided by 3, the higher importance you gave to 4 would be lost. That's why we divide by 4, the total weights.

---
### Example 2

Let's try out a sample **real-world** example 

Imagine you're a teacher.  
A student has taken **three tests** this semester:

|Test|Score|Importance (Weight)|
|---|---|---|
|Test 1|70|1 (not very important)|
|Test 2|80|2 (midterm, more important)|
|Test 3|90|1 (normal test again)|

Now, how should you calculate the student's **final average**?

- If you just **do simple average**:  
    (70 + 80 + 90) / 3 = 80
    
- But that's not fair because the **Midterm (Test 2)** is way more important than the others!

So, it appears we are at a **conundrum** (pronounced : "ko-none-drum") now.

Luckily, we have **weighted moving averages** to work with!

---
#### 🛠️ Using Weighted Moving Average (WMA):

**Step 1:** Multiply each score by its weight:

- 70 × 1 = 70
- 80 × 2 = 160
- 90 × 1 = 90

**Step 2:** Add them up:

- 70 + 160 + 90 = 320

**Step 3:** Add the weights:

- 1 + 2 + 1 = 4

**Step 4:** Weighted average:

- 320 ÷ 4 = **80**

**Final Weighted Average = 80**

✅ In this case, **luckily** it came out the same as simple average.  
But if the midterm score were lower or higher, the weighted average would reflect the "importance" properly!

For example, if the midterm was 60 instead of 80:

- Weighted sum = (70×1) + (60×2) + (90×1) = 70 + 120 + 90 = 280
- Weighted average = 280 ÷ 4 = 70

👉 You see, now the **low midterm score pulled the average down** more than it would in a simple average!

Here's a more clear difference using a plot:

![Pasted image 20250426131405.png](/img/user/media/Pasted%20image%2020250426131405.png)

- **Gray Line (Original Scores):**  
    This plots the raw data points: your original scores were **70, 80, 90**.
    
- **Blue Line (Simple Moving Average - SMA):**  
    SMA treats all data points equally.  
    It smooths the values without giving preference to any particular test.  
    Notice how it _averages things out_ slowly and consistently.
    
- **Green Line (Weighted Moving Average - WMA):**  
    WMA puts **more importance** on certain points (like more weight to the recent ones).  
    Because of this, it _reacts a little faster_ to increases or decreases in your scores.  
    (Here we gave the second test the highest weight.)
    

That's why the green line (WMA) is leaning slightly higher on the second test since it had more importance

---

#### Why do they look close but not identical?

- In this small dataset (only 3 points), both SMA and WMA are **fairly close**, but WMA _leans slightly towards_ the score that was given more weight (in this case, Test 2 got more focus).
    
- As you work with **larger datasets**, WMA starts showing **sharper responsiveness** to local changes, while SMA keeps things much **smoother**.

---

👉 **Summary:**

- SMA = smooth, treats all points fairly.
- WMA = sharper, reacts faster by giving preference to more important points.

---
#### 🧠 Conclusion

Weighted Moving Average is super useful when:

- Some values/events are **more important** than others.
- You want to make sure **important things influence the trend more**.

---
### 4. Fitting Mathematical Curves

This method is about fitting a **curve (not just a straight line)** to the data when trends are **non-linear** — that is, when the data doesn’t increase or decrease at a constant rate.

### 🔸 When Do We Use This?

When your data follows a pattern that’s:

- Linear (e.g., steadily increasing/decreasing trend)
- Quadratic (e.g., growth then decline like a parabola)
- Exponential (e.g., rapid growth or decay)
- Logarithmic
- Polynomial (higher-order trends)

---

### 🔸 The Basic Idea

Instead of fitting a **line** like `y = a + bt`, we fit equations like:

- **Linear trend**:
   `y = a + bt`
   
- **Quadratic curve:**  
    `y = a + bt + ct²`
    
- **Exponential curve:**  
    `y = a * e^(bt)`
    
- **Logarithmic curve:**  
    `y = a + b * log(t)`

We try to find the best-fitting coefficients (a, b, c, etc.) so the curve goes through or near the data points.

---
### 🛠️ How we usually do Curve Fitting:

1. **Choose the type of curve** based on how your data looks.
2. **Use formulas** (or regression) to calculate the parameters (like $a$, $b$, $c$).
3. **Plot the curve** along with the original data points.
4. **Check the fit** — does it match the trend well?

---
### a. Linear Trend (Recap)

The equation for a linear trend is:

$$y \ = \ a \ + \ bt$$

##### 🧠 What do the variables mean?

| Symbol | Meaning                                                                                      |
| ------ | -------------------------------------------------------------------------------------------- |
| `y`    | Temperature (or the value we want to estimate)                                               |
| `t`    | Time (usually in days or time units)                                                         |
| `a`    | Intercept of the line (value when time = 0)                                                  |
| `b`    | Slope of the line (how much temp or the value we are estimating, increases per unit of time) |


To understand what an intercept means just head back to [[#What do you mean by an "intercept of a line"?]]

---
#### How to calculate $a$  and $b$ ?

We already did this once in the Semi-Average method where we had two points:

We now fit a straight line between these two points:  
**Point 1:** (2.5, 22)  
**Point 2:** (6.5, 28)

**Use the slope formula**:

$$b \ = \ \frac{y_2 \ - \ y_1}{x_2 \ - \ x_1} \ = \ \frac{28 \ - \ 22}{6.5 \ - \ 2.5} \ = \ \frac{6}{4} \ = \ 1.5$$


And plug the value of $b$ into this equation :


$$y \ = \ a \ + \ bt$$

Use (2.5, 22) to find $a$ .

$$22 \ = \ a \ + \ 1.5(2.5)$$


$$\implies a \ = \ 18.25 $$

$$y \ = \ 18.25 \ + \ 1.5t$$

However, for the curious ones, there is another, **more general** way to find $a$ and $b$

Using these formulae:

$$b \ = \ \frac{n\Sigma \ (ty) \ - \ \Sigma \ t \ \Sigma \ y}{n \ \Sigma \ t^2 \ - \ (\Sigma \ t)^2}$$



$$a \ = \ \frac{\Sigma \ y \ - \ b \ \Sigma \ t}{n}$$


where $n$ = number of data points.

This method is called the **least squares regression method**.


Now the question one can ask is:

**Which method to choose**?

Well the previous method works better for semi-average only when you have two points to deal with.

In the case when you are working with a more broad dataset and want to plot a linear trend to see how it looks, you will need to use the **least squares regression method**.

So, a few more points about this method.

**While calculating b**:

$$b \ = \ \frac{n\Sigma \ (ty) \ - \ \Sigma \ t \ \Sigma \ y}{n \ \Sigma \ t^2 \ - \ (\Sigma \ t)^2}$$


Where:

- $n \sum{(ty)}$= number of points times the sum of each t*y
- $(\sum{t})(\sum{y})$ = product of total t and total y
- $n \sum{t^2}$ = number of points times sum of each t squared
- $(\sum{t})^2$ = square of total t

**What is $y$ here?** 

Let's say we have this dataset again:

| Day | Temp (°C) |
| --- | --------- |
| 1   | 20        |
| 2   | 21        |
| 3   | 23        |
| 4   | 24        |
| 5   | 26        |
| 6   | 27        |
| 7   | 29        |
| 8   | 30        |

$y$ is just each temperature value, corresponding to each $t$ value on the dataset.

And for a:

$$a \ = \ \frac{\Sigma \ y \ - \ b \ \Sigma \ t}{n}$$

It's just the sum of all y values minus b times sum of all t values divided by the total number of table entries.

Now, one might have this question:

**Are the a and b values calculated using the method for semi-average plotting, the same as the a and b values calculated using the least squares regression method**?

And the answer is: **no, they are not the same**.

🔵 **1. Slope between two points** (basic method you mentioned):

- When you just take **two points** $(t_1, y_1)$ and $(t_2,y_2)$,
- The slope $b$ is simply:

$$b = \frac{y_2 - y_1}{t_2 - t_1}$$​​

- And then you can substitute back into $y = a + bt$ to find $a$.

👉 **But this method** uses **only two points** to define the line.


🔵 **2. Slope via Least Squares** (the one we are doing now):

- Here we are **fitting the best line through ALL the points**.
- We are **minimizing the total squared error** (the vertical distances from the line).
- This method **balances** all the points — not just two!
- That's why the formulas look more "global," involving sums like : $\sum{t}, \ \sum{y}, \ \sum{ty}, \ \sum{t^2}$

🔵 **Therefore:**

- **YES**, the $a$ and $b$ values **will usually be different** between the two methods.
- The two-points method might _only_ match the least-squares method _if_ all points happen to lie exactly on one perfect straight line (very rare in real-world data).
- Otherwise, **least squares** gives a much better, more fair trend line for multiple data points.

---
For a quick comparison, let's see a visual plot using both methods.

![Pasted image 20250426140839.png](/img/user/media/Pasted%20image%2020250426140839.png)


Now what does this image imply?

See how the red line is a bit off in the starting and the end?

**Red Solid Line** = The **Least Squares Line** (Linear Regression):

- It uses **all the data points**.
- It **minimizes the overall error** (the total of all the vertical distances between the points and the line).
- It’s **more reliable** for making predictions across the whole range.

And the blue-dotted line is the **two-point line method**.

🔹 **Blue Dashed Line** = The **Two-Point Line**:

- It only uses the _first_ and _last_ points (Day 1 and Day 8) to create a straight line.
- It's **simple**, **quick**, but **less accurate** because it **ignores** the middle points.

---
####  What this plot implies:

- **Both lines look similar** because the data is fairly linear and clean.
- **But the red line (Least Squares)** is slightly better because it fits _all_ points and doesn't just pass through the first and last points.
- **If your data was noisy**, the **two-point line would be way off**, while **Least Squares** would still balance out the fluctuations nicely.
---
### b. Quadratic Trend

**Quadratic Trend Model** is used when the data shows **curvature** — meaning the trend is **not a straight line** but curves **upward** or **downward** like a parabola.

The general form of the **quadratic trend equation** is:

$$y \ = \ a \ + \ bt \ + \ ct^2$$

where:

- $y$ = value of the dependent variable at time $t$
- $t$ = time (or any independent variable)
- $a$ = intercept (value of $y$ when t=0)
- $b$ = linear coefficient (captures the straight-line part)
- $c$ = quadratic coefficient (captures the curvature)

---
#### How does one fit a Quadratic Trend?

We generally use the **Least squares regression method** to find the best values of $a$,  $b$ and  $c$, such that the sum of squared differences between actual and predicted $y$ is minimized.

You set up and solve the following system of normal equations:

$$\sum y \ = \ na \ + \ b \ \sum t \ + \ c \ \sum t^2$$

$$\sum ty \ = \ a \sum t \ + b \ \sum t^2 \ + \ c \ \sum t^3$$

$$\sum t^2y \ = \ a \sum t^2 \ + \ b \sum t^3 \ + \ c \sum t^4$$

where:

- $n$ is the number of observations (total number of entries in the table).
- The summations ($\sum$) are over the dataset.

Firstly, compute all the sum values, and construct the three equations.

Solve for $a$, $b$  and $c$  using linear algebra techniques (substitution, matrices, etc.)

---
#### Intuition Check

- If $c > 0$, the curve opens **upward** (like a "U" shape).
- If $c < 0$, the curve opens **downward** (like an upside-down "U").
- The bigger the $|c|$ value, the steeper the curvature.


This type of trend is helpful in:

- **Economics** (e.g., GDP growing faster over time)
- **Natural sciences** (e.g., population growth then decline)
- **Market analysis** (e.g., rise and fall in demand)

---
#### Example 1

Suppose, we have:

| $t$ (Time) | $y$ (Value) |
| ---------- | ----------- |
| 1          | 4           |
| 2          | 7           |
| 3          | 12          |
| 4          | 19          |
| 5          | 28          |

So, 

$$n \ = \ 5$$ 

$$\sum y \ = \ 62$$


$$\sum ty \ = \ (1\times4) \ + \ (2\times 7) \ + \ (3\times 12) \ + \ (4\times 19) \ + \ (5\times 28) \ = \ 270$$


$$\sum t^2y \ = \ (1\times4) \ + \ (4\times 7) \ + \ (9\times 12) \ + \ (16\times 19) \ + \ (25\times 28) \ = \ 1144$$



$$\sum t \ = \ 15$$

$$\sum t^2 \ = \ 55$$

$$\sum t^3 \ = \ 225$$

$$\sum t^4 \ = \ 979$$


Now we reconstruct the equations

First equation is just the same as the original one :

$$y \ = \ a \ + \ bt \ + \ ct^2$$


$$\sum y \ = \ na \ + \ b \sum t \ + \ c \sum t^2$$


So we have equation 1 as:

$$62 \ = \ 5a \ + \ 15b \ + \ 55c$$


Second equation is just a progression of equation 1.

$$\sum ty \ = \ a \sum t \ + \ b \sum t^2 \ + \ c \sum t^3$$

So we have equation 2 as:

$$270 \ = \ 15a \ + \ 55b \ + \ 225c$$


Third equation is just a progression of equation 2.

$$\sum t^2y \ = \ a \sum t^2 \ + b \sum t^3 \ + \ c \sum t^4$$

So we have equation 3 as:

$$1144 \ = \ 55a \ + \ 225b \ + \ 979c$$


So we have the system of equations as:

$$5a \ + \ 15b \ + \ 55c \ = \ 62$$

$$15a \ + \ 55b \ + \ 225c \ = \ 270$$

$$55a \ + \ 225b \ + \ 979c \ = \ 1144$$


Now this can be a good exercise for us to solve this system using matrices, the matrix inversion method to be specific

So let's write this system of equations as matrices:

$$
\left[
\begin{array}{ccc}
  5 & 15 & 55  \\
  15 & 55 & 225 \\
  55 & 225 & 979  
\end{array}
\right]
$$


as the matrix $A$

and 

$$
\left[
\begin{array}{ccc}
62 \\
270 \\
1144
\end{array}
\right]
$$

as the matrix $\vec{b}$

and 

$$
\left[
\begin{array}{ccc}
a \\
b \\
c
\end{array}
\right]
$$

as the matrix $\vec{x}$


We need to find :

$$\vec{x} \ = \ A^{-1} \ \cdot \ \vec{b} $$

Firstly we find the matrix of minors:

We have our original matrix as:

$$
\left[
\begin{array}{ccc}
  5 & 15 & 55  \\
  15 & 55 & 225 \\
  55 & 225 & 979  
\end{array}
\right]
$$


Firstly we compute the determinant of this matrix:


$$\det(A) \ = \ (5 \times 3220) \ - \ (15 \times 2310) \ + \ (55 \times 350)$$


$$\det(A) \ = \ 700$$


So our matrix of minors will be:

$$
\left[
\begin{array}{ccc}
  \begin{vmatrix}
   55 & 225  \\
    225 & 979 
   \end{vmatrix}
   &   
   \begin{vmatrix}
   15 & 225  \\
    55 & 979 
   \end{vmatrix} 
   & 
   \begin{vmatrix}
   15 & 55  \\
    55 & 225 
   \end{vmatrix} \\
\\
    \begin{vmatrix}
   15 & 55  \\
    225 & 979 
   \end{vmatrix}
   & 
    \begin{vmatrix}
   5 & 55  \\
    55 & 979 
   \end{vmatrix}
	& 
	 \begin{vmatrix}
   5 & 15  \\
    55 & 225 
   \end{vmatrix} \\
\\   
   \begin{vmatrix}
   15 & 55  \\
    55 & 225 
   \end{vmatrix}
   & 
    \begin{vmatrix}
   5 & 55  \\
    15 & 979 
   \end{vmatrix}
	& 
	 \begin{vmatrix}
   5 & 15  \\
    15 & 55 
   \end{vmatrix}
\end{array}
\right]
$$


(That was quite painful to type and render, but atleast faster than drawing with a mouse).

Now we solve the individual determinants :

$$
\left[
\begin{array}{ccc}
  3220 & 2310 & 350  \\
  2310 & 1870 & 300 \\
  350 & 4070 & 50  
\end{array}
\right]
$$

So this is the matrix of minors.

Now we apply the sign scheme to get the co-factor matrix:

$$
\left[
\begin{array}{ccc}
  3220 & -2310 & 350  \\
  -2310 & 1870 & -300 \\
  350 & -4070 & 50  
\end{array}
\right]
$$


Now we find the adjugate matrix by transposing the co-factor matrix :

$$
\left[
\begin{array}{ccc}
  3220 & -2310 & 350  \\
  -2310 & 1870 & -4070 \\
  350 & -300 & 50  
\end{array}
\right]
$$

Now we compute the inverse of the matrix :

$$
A^{-1} \ = \ \frac{1}{700} \ \times \ 
\left[
\begin{array}{ccc}
  3220 & -2310 & 350  \\
  -2310 & 1870 & -4070 \\
  350 & -300 & 50  
\end{array}
\right]
$$


$$A^{-1} \ = \ 
\left[
\begin{array}{ccc}
  4.6 & -3.3 & 0.5  \\
  -3.3 & 2.6 & -5.8 \\
  0.5 & -0.4 & 0.07  
\end{array}
\right]
$$


(**There might be some rounding errors here but I purposely did that to keep the numbers small**)

Now using the formula:

$$\vec x \ = \ A^{-1}b$$

$$
\left[
\begin{array}{ccc}
  a   \\
  b  \\
  c 
\end{array}
\right] \ = \ 
\left[
\begin{array}{ccc}
  4.6 & -3.3 & 0.5  \\
  -3.3 & 2.6 & -5.8 \\
  0.5 & -0.4 & 0.07  
\end{array}
\right]
\ \times 
\left[
\begin{array}{ccc}
62 \\
270 \\
1144
\end{array}
\right]
$$


For $\vec{x}$, multiply each element of $b$ to each element of the first row of $A^{-1}$ and add :

$$a \ = \ (62 \times 4.6) \ - \ (270 \times 3.3) \ + \ (1144 \times 0.5)$$

$$\implies \ a \ = \ -33.8$$

$$b \ = \ -(62 \times 3.3) \ + \ (270 \times 2.6) \ - \ (1144 \times 5.8)$$

$$\implies \ b \ = \ -6137.8$$

$$c \ = \ (62 \times 0.5) \ - (270 \times 0.4) \ + \ (1144 \times 0.07)$$

$$\implies c \ = \ 3.08$$ 
(corrected, was previously $c \ = \ 723.8$, since I multiplied $1144 \times \ 0.7$, lol)
(This mistake however, will prove useful below, as you will see)

So we have the solution to the system of equations as:

$$\boxed{a \ = \ -33.8 \ ,  \ b \ = \ -6137.8 \ , \ c \ = \ 3.08}$$

So, the quadratic equation for this dataset:

$$y \ = \ a \ + \ bt \ + \ ct^2$$


will be:

$$y \ = \ -33.8 \ -6137.8t \ + \ 3.08t^2$$

Since we have our $c > 0$ , we should expect an upward "U" shape in the visualization.

---
Here's a visualization of the quadratic trend for $c \ = \ 723.8$  my previously mistaken calculated $c$  value.

![Pasted image 20250426165413.png](/img/user/media/Pasted%20image%2020250426165413.png)


- **Blue dots** represent the actual data points.
- **Red curve** shows the quadratic trend that we've derived based on the system of equations.

As you can see, the quadratic trend follows the general upward curve of the data, capturing the parabolic nature of the data points.

I had already generated this plot earlier thinking this one was the correct, however:

---

**This** is the plot for the **correct** $c$  value of 3.08

![Pasted image 20250426170939.png](/img/user/media/Pasted%20image%2020250426170939.png)


**Notice how it just looks like a straight line now instead of a curve**? Even though our $c \ \gt 0$ ?

This is because of the **strength of the $c$ value**.

Now, **with the correct equation**:

- The $t^2$ term (3.08) is **tiny** compared to the $t$ term (–6137.8).
- That means the behavior is dominated **heavily by the linear t term**, not the $t^2$ part.
- In fact, unless $t$ is **huge**, $3.08t^2$ barely contributes at all.

This explains why **the graph looks like a straight line**:

🔵 The equation is _technically_ quadratic,  
🔵 But practically, **the parabola is so "flat"** that the $t^2$ term is negligible,  
🔵 So it behaves almost **exactly like a straight line** with slope $−6137.8$.


Now previously with $c \ = \ 723.8$,  even small values of $t$ made $c t^2$ become big enough to show a curve.

But now, with $c = 3.08$, it takes **absolutely massive** values of $t$ for $3.08t^2$ to matter compared to $6137.8t$.

That's why **visually** this one looks straight, while the old one looked curved.

🧠 **Little intuition tip:**

- Big $t^2t$ term → Parabola appears **quickly**.
- Small $t^2$ term → Looks **linear** unless zoomed far out (or far in).

**For this section, linear and quadratic trend should do it, otherwise we will need another brain to carry this much information**.

---
# Similarity Search 

## What is Similarity Search in Data Mining?

Given a time series (or a piece of it, called a **query**),  
**find** the part(s) of another time series (or within the same series) that **look similar** to it.

---
## ✏️ **Two types:**

1. **Whole matching**  
    → Compare entire time series vs. entire time series.
    
2. **Subsequence matching**  
    → Compare a **small query** vs. **sliding windows** inside a large time series.  
    (Like searching for a pattern inside a huge signal.)

---
## ✏️ **How is similarity measured?**

Main methods:

- **Euclidean Distance** (simple, fast, works when signals are aligned well)
- **Dynamic Time Warping (DTW)** (flexible, allows stretching/shrinking of time)
- **Correlation-based measures** (cosine similarity, normalized cross-correlation)
---
### 1. Euclidean Similarity Search

The **core idea** is extremely simple:  
**Take two sequences** (say, arrays of numbers),  
**and compute the straight-line distance between them.**

#### Steps:

1. **Given:**

- A **query** time series $Q$ of length $m$.
- A **target** time series $T$ of length $n$ (with $n \gt m$)

2. **What we do**:

- Slide a window of size $m$  over $T$.
- For every window, compute the **Euclidean Distance** to $Q$.

3. **Euclidean Distance Formula**

- $$Distance(Q , \ S) \ = \ \sqrt{\sum^{m}_{i=1}{(Q[i] \ - \ S[i])^2}}$$ 

where $S$ is the current window in $T$.

4. **Result**:
   
   - A list of distances
   - **The smallest distance** is the best matching sequence.

---
#### Example

Suppose:

- Query $Q \ = \ [ \ 1, \ 2, \ 3 \ ]$ 
- Target $T \ = \ [ \ 0, \ 1, \ 2, \ 3, \ 4, \ 5 \ ]$

Now, sliding windows of size 3 in $T$ would be:

|Subsequence (S)|Indices|Values|
|---|---|---|
|1|0–2|[0, 1, 2]|
|2|1–3|[1, 2, 3]|
|3|2–4|[2, 3, 4]|
|4|3–5|[3, 4, 5]|

Just like how we had sliding windows in moving averages method :

```python
0 1 2
  1 2 3 
    2 3 4
      3 4 5
```

Now, we compute the distances between our Query and our target value in each sliding window

- Distance between $[ \ 1, \ 2, \ 3 \ ]$  and $[ \ 0, \ 1, \ 2 \ ]$

$$\sqrt{(1-0)^2 \ + \ (2-1)^2 \ + \ (3-2)^2}$$

$$ \ = \ \sqrt{3} \ \approx \ 1.732$$

- Distance between $[ \ 1, \ 2, \ 3 \ ]$  and $[ \ 1, \ 2, \ 3 \ ]$

$$\sqrt{(1-1)^2 \ + \ (2-2)^2 \ + \ (3-3)^2}$$

$$ \ = \ 0 $$

**Note:**

Since Euclidean distance is:

- Always **non-negative** (never below 0),
- **Exactly 0** only when the two sequences are perfectly identical,

you **can** absolutely **terminate early** if you ever find a distance of **0** while searching.

So we can already stop the process now and declare that we have found an exact match of our query? Yes, sure, 

**However**:

- In **real-world data**, exact matches are **extremely rare** because of noise, rounding errors, sampling variations, etc.
- So **most of the time**, distances will never exactly reach 0.
- In that case, you **still have to continue** through all windows and pick the minimum distance you find.

BUT — if you are working on **clean synthetic data** (like in toy examples or simulations), this early-stopping optimization can **save a lot of time**!


So for the sake of practice however, we will still continue to calculate the remaining distance values.


- Distance between $[ \ 1, \ 2, \ 3 \ ]$  and $[ \ 2, \ 3, \ 4 \ ]$

$$\sqrt{(1-2)^2 \ + \ (2-3)^2 \ + \ (3-4)^2}$$

$$= \ \sqrt{1 \ + \ 1 \ + \ 1} \ = \ \sqrt{3} \ \approx \ 1.732$$

- Distance between $[ \ 1, \ 2, \ 3 \ ]$  and $[ \ 3, \ 4, \ 5 \ ]$

$$\sqrt{(1-3)^2 \ + \ (2-4)^2 \ + \ (3-5)^2}$$


$$\sqrt{4 \ + \ 4 \ + \ 4} \ = \ \sqrt{12} \ = \ 2\sqrt{3} \ \approx \ 3.464$$


So now we have an array of distances as :

$$[ \ 1.732, \ 0, \ 1.732, \ 3.464 \ ]$$

A `min()` of this array would result in $0$

So we have found the best match as window 2!

Which is exactly the same as our query, $[ \ 1, \ 2, \ 3 \ ]$.

---
### Conclusion

- **Normalization matters**:  
    If the series have different scales or offsets, you often **normalize** the query and subsequences first (e.g., z-normalization: subtract mean, divide by std).
    
- **Complexity**:  
    Naively it takes $O(nm)$ time.  

---
### 2. Dynamic Time Warping (DTW)

While Euclidean distance compares two sequences **point by point**,  
**DTW** allows for **flexible alignment** — it can **stretch** and **compress** parts of the time axis to match sequences better.

> Think of DTW as "warping time" so that **similar shapes** match, even if they happen at slightly **different speeds**.


![Pasted image 20250427125619.png](/img/user/media/Pasted%20image%2020250427125619.png)


So this diagram is **depicting the core idea of Dynamic Time Warping (DTW)** —  
specifically, **aligning two time series** (or sequences) that might be "out of sync" in time, but are otherwise similar.

- The **horizontal axis** represents one sequence (let's say series A).
- The **vertical axis** represents another sequence (say series B).
- **Each point (i, j)** in the grid represents a possible alignment between the _i-th_ point in A and the _j-th_ point in B.
- The **path you see** (the connected white dots) shows the _best matching_ between the two sequences, where the total "warped" distance is minimized.

In short:  
🔵 **Goal:** Find the optimal path through this grid that _minimizes the total distance_ between the sequences, even allowing for stretching and compressing in time.

---
#### Example

Let's say we have two time series:

- Time Series $A \ = \ (1, \ 2, \ 3)$
- Time Series $B=(2, \ 3, \ 4, \ 3)$

##### Step 1. Create a Cost Grid Matrix

The number of rows in this grid should be equal to the number of data points in Time Series A (which is 3). The number of columns should be equal to the number of data points in Time Series B (which is 4).


| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   |     |     |     |     |
| 2   |     |     |     |     |
| 3   |     |     |     |     |

For each cell in this grid, you need to calculate the "local cost" of aligning the corresponding points from Time Series A and Time Series B. A common way to calculate this local cost is by taking the absolute difference between the two values.

For the cell at row $i$ and column $j$, you will compare the $i$-th value of A ($a_i$​) with the $j$-th value of B ($b_j$​) and calculate $|a_i \ ​− \ b_j|$.

So the local costs will be:

| A   | B         | B         | B         | B         |
| --- | --------- | --------- | --------- | --------- |
| __  | 2         | 3         | 4         | 3         |
| 1   | $\|1-2\|$ | $\|1-3\|$ | $\|1-4\|$ | $\|1-3\|$ |
| 2   | $\|2-2\|$ | $\|2-3\|$ | $\|2-4\|$ | $\|2-3\|$ |
| 3   | $\|3-2\|$ | $\|3-3\|$ | $\|3-4\|$ | $\|3-3\|$ |

Thus,

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 2   | 3   | 2   |
| 2   | 0   | 1   | 2   | 1   |
| 3   | 1   | 0   | 1   | 0   |

Let call this matrix D.

##### Step 2: Create the Cumulative Cost Matrix - Initialize the First Cell

**What to do:**

1. Create a new grid (a matrix) with the same dimensions as your Cost Matrix (in this case, 3×4). This will be our Cumulative Cost Matrix, let's call it C.
    
2. The very first cell of the Cumulative Cost Matrix, C(1,1) (top-left corner), is simply equal to the value of the very first cell of your Cost Matrix, D(1,1).

In this case, $D(1,1) \ = \ 1$

So, $C(1,1) \ = \ 1$

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   |     |     |     |
| 2   |     |     |     |     |
| 3   |     |     |     |     |

##### Step 3: Fill the First Row and First Column of the Cumulative Cost Matrix

**What to do:**

1. **First Column (except the first cell):** For each cell in the first column of C (from the second row downwards), its value is the sum of the local cost in the corresponding cell of D and the value in the cell directly above it in C.

	$$C(i,1)=D(i,1)+C(i−1,1)$$ for $i$>1.

2. **First Row (except the first cell):** Similarly, for each cell in the first row of C (from the second column to the right), its value is the sum of the local cost in the corresponding cell of D and the value in the cell directly to its left in C.

	$$C(1,j)\ = \ D(1,j) \ + \ C(1,j−1)$$ for j>1.


3. **All cells except first row and first column** : For the value of this cell, we need to find the **sum of the corresponding cell in matrix D and the minimum of the cell above, cell to the left, and the diagonal cell**

$$C(i,j)=D(i,j)+min(C(i−1,j),C(i,j−1),C(i−1,j−1))$$


Let's understand these better with calculations:

Matrix D again:

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 2   | 3   | 2   |
| 2   | 0   | 1   | 2   | 1   |
| 3   | 1   | 0   | 1   | 0   |


So currently we have $C(1,1) \ = \ 1$

Now if we want to find out let's say, $C(2,1)$, the cell directly below.

The value of this cell will be **the sum of the value of the cell above it and the corresponding value of this cell in matrix D**.

So :
- $C(2,1) \ = C(1,1) \ + \ D(2,1) \ = \ 1 \ + \ 0 \ = \ 1$
- $C(3, 1) \ = \ C(2,1) \ + \ D(3,1) \ = \ 1 \ + \ 1 \ = \ 2$

So, $C$  becomes:

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   |     |     |     |
| 2   | 1   |     |     |     |
| 3   | 2   |     |     |     |

Now, for the remaining cells:

- $C(1, 2) \ = \ C(1,1) \ + \ D(1,2) \ = \ 1 \ + \ 2 \ = \ 3$
- $C(1,3) \ = \ C(1,2) \ + \ D(1,3) \ = \ 3 \ + \ 3 \ = \ 6$
- $C(1,4) \ = \ C(1,3) \ + \ D(1,4) \ = \ 6 \ + \ 2 \ = \ 8$

So, C becomes now:

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   |     |     |     |
| 3   | 2   |     |     |     |

Now, (for each current cell, I will denote that with an x, for easy visualization)

- $C(2, 2) \ = \ \min(C(1,2), \ C(2,1), \ C(1,1)) \ + \ D(2,2) \ = \ \min(3, 1, 1) \ + \ 1 \ = \ 1 \ + \ 1 \ = \ 2$
  

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   |     |     |
| 3   | 2   | x   |     |     |

  
- $C(3,2) \ = \ \min(C(2,2), \ C(3,1), \ C(2,1)) \ + \ D(3,2) \ = \ \min(2, 2, 1) \ + \ 0 \ = \  1 \ + \ 0 \ = \ 1$
  

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | x   |     |
| 3   | 2   | 1   |     |     |

  
- $C(2, 3) \ = \ \min(C(2,2), \ C(1, 2), \ C(1, 3)) \ + \ D(2,3) \ = \ \min(2, 3, 6) \ + \ 2 \ = \ 2 \ + \ 2 \ = \ 4$
  

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | 4   |     |
| 3   | 2   | 1   | x   |     |

  
- $C(3, 3) \ = \ \min(C(2,3), \ C(3,2), \ C(2, 2)) \ + \ D(3,3) \ = \ \min(4, 1, 2) \ + \ 1 \ = \ 1 \ + \ 1 \ = \ 2$


| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | 4   | x   |
| 3   | 2   | 1   | 2   |     |

  
- $C(2, 4) \ = \ \min(C(1,4), \ C(2, 3), \ C(1,3)) \ + \ D(2,4) \ = \ \min(8, 4, 6) \ + \ 1 \ = \ 4 \ + \ 1 \ = \ 5$
  

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | 4   | 5   |
| 3   | 2   | 1   | 2   | x   |


- $C(3, 4) \ = \ \min(C(2,4), \ C(3,3), \ C(2,3)) \ + \ D(3,4) \ = \ \min(5, 2, 4) \ + \ 0 \ = \ 2 \ + \ 0 \ = \ 2$

So, our final cumulative cost matrix becomes:

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | 4   | 5   |
| 3   | 2   | 1   | 2   | 2   |

##### Step 5: Calculate the DTW Distance

**What to do:**

The Dynamic Time Warping (DTW) distance between your two time series $A$ and $B$ is simply the value located in the bottom-right cell of your Cumulative Cost Matrix $C$.

So in our Cumulative Cost Matrix $C$:

| A   | B   | B   | B   | B   |
| --- | --- | --- | --- | --- |
| __  | 2   | 3   | 4   | 3   |
| 1   | 1   | 3   | 6   | 8   |
| 2   | 1   | 2   | 4   | 5   |
| 3   | 2   | 1   | 2   | 2   |

The **bottom-right cell** is at the 3rd row and 4th column, $C(3,4)$ and it's value is: $2$.

Therefore, the DTW distance between Time Series $A=(1,2,3)$ and Time Series $B=(2,3,4,3)$ is $2$.

##### Step 6: Traceback for the Warping Path

**What to do**:

1. Start at the bottom-right cell of $C$.
2. Analyze it's neighbor cells (top, left and diagonal). Pick the one that has the most minimum value out of the 3.
3. Repeat till you reach the top-left cell of $C$, i.e. $C(1,1)$.


So the traced path would be:

```python
[
 [1, 3, 6, 8],
  ^
  |
 [1, 2, 4, 5],
  ^
  |
   \
    \
 [2, 1 <-- 2 <-- 2]
]
```

And the points in the traversed order would be:

$$(3,4) \rightarrow (3,3) \rightarrow (3,2) \rightarrow (2,1), \rightarrow (1,1)$$

Reverse this, and we would get the optimal warping path as:

$$(1,1) \rightarrow (2,1) \rightarrow (3,2) \rightarrow (3,3), \rightarrow (3,4)$$

---
### What does this warping path tell us?

Remember that we had the time series as:

- Time Series $A \ = \ (1, \ 2, \ 3)$
- Time Series $B=(2, \ 3, \ 4, \ 3)$


This path tells us the alignment:

- (1,1): The 1st point of A (value 1) is aligned with the 1st point of B (value 2).
- (2,1): The 2nd point of A (value 2) is also aligned with the 1st point of B (value 2).
- (3,2): The 3rd point of A (value 3) is aligned with the 2nd point of B (value 3).
- (3,3): The 3rd point of A (value 3) is aligned with the 3rd point of B (value 4).
- (3,4): The 3rd point of A (value 3) is aligned with the 4th point of B (value 3).

==Notice how some points in one time series can be aligned with multiple points in the other, which is the "warping" effect==.

==The warping effect can be interpreted as== the fact that the 3rd point of Time Series A (value 3) is aligned with the 2nd (value 3), 3rd (value 4), and 4th (value 3) points of Time Series B illustrates ==how DTW stretches or compresses the time axis of one or both series to find the best possible match==. It's like saying, "==To see the similarity, we need to consider that the last point of A corresponds to this whole segment in B.=="

One beautiful analogy to understand this would be to see how similar this is to time dilation.
Like how a blackhole bends and compresses time around it so that time passes a lot slower around it's event horizon and vicinity, but it passes "faster" or rather from an external frame of reference, "normally" for other points, speaking from their own frames of references?

DTW does a similar behaviour, by "stretching or compressing the time of one time series" to find the similarity in another one. 

---
### 3. Cosine Similarity Search

Cosine similarity search algorithm is primarily a mathematical formula used to determine how "close" or how "similar" **two vectors**  are. It results in an angle value, which has ranges from $0 \leq x \leq 1$. If the angle $x$ , is very close to $1$, or $1$ , then it's considered **similar** or else it's considered **dissimilar**.

There are specific thresholds one can set for this:

| Angle Value   | Interpretation                               |
| ------------- | -------------------------------------------- |
| 1.0           | 100% similar                                 |
| 0.9 and above | Highly Similar                               |
| 0.7 to 0.9    | Very Similar                                 |
| 0.5 to 0.7    | Moderately Similar                           |
| 0.3 to 0.5    | Not quite, similar, vauge, sparse similarity |
| 0.0 to 0.3    | Very very sparse similarity                  |
| 0.0           | 100% dissimilar                              |

The formula for cosine similarity for two vectors $a$ and $b$ is:

$$Cosine \ Similarity(a,b) \ = \ \frac{a \ \cdot \ b}{|a| \ \cdot \ |b|}$$

In terms of physics, $a \ \cdot \ b$  would mean the dot product divided by the $|a| \ \cdot \ |b|$  meaning, the product of the magnitudes of the two vectors.

However since we are working with numerical arrays here,

$$Cosine \ Similarity(a,b) \ = \ \frac{a \ \cdot \ b}{|a| \ \cdot \ |b|} \ = \ \frac{\sum^n_{i=1}{(a_i \ \cdot \ b_i)}}{\sqrt{\sum^n_{i=1}{(a^2_i)}} \ \cdot \sqrt{\sum^n_{i=1}{(b^2_i)}}}$$


And a very important constraint : **The dimensionality of both the vectors should be same, i.e. both the arrays should have the same number of elements, or this method will fail**.

----
#### Example 1

Let's say we have two same dimensional arrays:

**Time Series A:** `[1.0, 2.0, 3.0, 4.0, 5.0]` 
**Time Series B:** `[1.5, 2.5, 3.5, 4.5, 5.5]`

Let's check if these two time series are similar to each other or not.

$$\sum^5_{i=1}{(a_i \ \cdot \ b_i)} \ = \ (1.0 \times 1.5) \ + \ (2.0 \times 2.5) \ + \ (3.0 \times 3.5) \ + \ (4.0 \times 4.5) \ + \ (5.0 \times 5.5)$$


$$\implies \sum^5_{i=1}{(a_i \ \cdot \ b_i)} \ = \ 62.5$$


$$\sqrt{\sum^5_{i=1}{(a^2_i)}} \ = \ \sqrt{1  \ + \ 4 \ + \ 9 \ + \ 16 \ + \ 25} \ = \ \sqrt{55} \ \approx \ 7.416$$


$$\sqrt{\sum^n_{i=1}{(b^2_i)}} \ = \ \sqrt{2.25 \ + \ 6.25 \ + \ 12.25 \ + \ 20.25 \ + \ 30.25} \ = \ \sqrt{71.25} \ \approx \ 8.440$$



$$\sqrt{\sum^n_{i=1}{(a^2_i)}} \ \cdot \sqrt{\sum^n_{i=1}{(b^2_i)}} \ = \ 7.416 \times \ 8.440 \ = \ 62.59$$


Now, 

$$Cosine \ Similarity(a,b) \ = \ \frac{a \ \cdot \ b}{|a| \ \cdot \ |b|} \ = \ \frac{\sum^n_{i=1}{(a_i \ \cdot \ b_i)}}{\sqrt{\sum^n_{i=1}{(a^2_i)}} \ \cdot \sqrt{\sum^n_{i=1}{(b^2_i)}}} \ = \ \frac{62.5}{62.59} \ \approx \ 0.9985$$


which is a **very very high similarity**.

So now, you must be wondering, **how might one infer this answer with the context of the two time series**?

Well since we have established that the two time series:

**Time Series A:** `[1.0, 2.0, 3.0, 4.0, 5.0]` 
**Time Series B:** `[1.5, 2.5, 3.5, 4.5, 5.5]`

have a very high similarity, we can observe a few **traits** in both the time series:

- **Similar Trend:** Both Time Series A `[1.0, 2.0, 3.0, 4.0, 5.0]` and Time Series B `[1.5, 2.5, 3.5, 4.5, 5.5]`==show a clear increasing trend. The cosine similarity captures this shared direction of movement. Even though the magnitudes (the actual values) are different, their pattern of change is very similar==.
    
- **Proportional Relationship:** ==The values in Time Series B are roughly 1.5 times the corresponding values in Time Series A (with a small offset)==. Cosine similarity is insensitive to the magnitude of the vectors, focusing solely on the angle between them. A small angle (close to 0 degrees) results in a cosine value close to 1, signifying that they point in almost the same direction.
    
- **Shape Similarity:** In essence, the "shape" of the two time series, in terms of their relative changes over time, is very alike. If you were to plot these two series, they would look like two almost parallel lines moving upwards.


![Pasted image 20250427152114.png](/img/user/media/Pasted%20image%2020250427152114.png)

Here we can see the plot of these two time series. Note how both are **parallel lines**, indicating high similarity.


**In contrast, if the cosine similarity was:**

- **Close to 0:** It would suggest that the two time series are roughly orthogonal (at a 90-degree angle), implying no strong linear relationship or similarity in their overall trend.
- **Negative (close to -1):** It would indicate that the two time series are pointing in nearly opposite directions, suggesting an inverse relationship or opposite trends (like our Time Series C and D example).

---


