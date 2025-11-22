---
{"dg-publish":true,"permalink":"/machine-learning/machine-learning-important-questions-unit-by-unit-for-makaut-exams/","tags":["Semester-7","Machine-Learning"],"created":"2025-11-22T16:49:53.874+05:30","updated":"2025-11-22T17:42:35.663+05:30"}
---

# MAKAUT Machine Learning Exam Revision

**Complete Question Bank with Detailed Answers**  
Units 1-6 | Generated: November 22, 2025 | Exam: November 28, 2025

---

# Unit 1: Supervised Learning & Linear Models

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. Differentiate between "Lazy Learners" and "Eager Learners".

**Answer:**

- **Lazy Learners (e.g., k-NN):** Do not build a model during the training phase. They simply ==store the training data== and perform computation (distance calculation) only when a query is made. This makes training fast ($O(1)$) but prediction slow ($O(N \cdot d)$) where $d$ is dimensionality.
    
- **Eager Learners (e.g., Decision Trees, SVM):** Build a generalization model during training ==before seeing the test data==. ==Training is slower==, but prediction is very fast ($O(1)$ or $O(\text{depth})$).
    

**Key Insight:** Lazy learners are instance-based and keep all data in memory, while eager learners extract patterns and discard training data after learning.

---

## Q2. What is the "i.i.d." assumption in Supervised Learning?

**Answer:**  
It stands for **Independent and Identically Distributed**. It assumes that all data points in the training and test sets are drawn ==independently== from the ==same underlying probability distribution==.

- **Independent:** $P(x_i, y_i | x_j, y_j) = P(x_i, y_i)$ for $i \neq j$
- **Identically Distributed:** $\forall i, (x_i, y_i) \sim P(X, Y)$

If this is violated (e.g., in time-series data, distribution shift), standard models often fail because they assume training and test data come from the same source.

---

## Q3. Explain the "Kernel Trick" in SVM in one sentence.

**Answer:**  
The Kernel Trick allows SVM to classify non-linearly separable data by ==implicitly mapping inputs to a higher-dimensional space== using a kernel function $K(x_i, x_j)$ ==without ever computing the coordinates== in that high-dimensional space explicitly, thus avoiding computational explosion.

**Common Kernels:**

- Polynomial: $K(x,y) = (x \cdot y + c)^d$
- RBF: $K(x,y) = \exp(-\gamma||x-y||^2)$

---

## Q4. What is Multicollinearity in Linear Regression? Why is it a problem?

**Answer:**  
Multicollinearity occurs when independent variables are ==highly correlated== with each other. This makes the matrix inversion $(X^T X)^{-1}$ ==unstable== (singular or close to singular), leading to ==unreliable and highly variable estimates== of the regression coefficients.

**Problems:**

- Small changes in data cause huge changes in $\theta$
- Coefficients have large standard errors
- Can't determine which feature truly matters
- Poor generalization

**Solutions:** Ridge regression (L2), Lasso (L1), or PCA to decorrelate features.

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q5. Decision Tree Splitting - Entropy & Information Gain

**Question:**  
Given a dataset $S$ with $p$ positive examples and $n$ negative examples.

1. Define Entropy $H(S)$.
2. Explain how Information Gain (IG) is calculated for an attribute $A$.

**Answer:**

1. **Entropy:** A measure of impurity or disorder in the dataset.  
    $$H(S) = -p_+ \log_2(p_+) - p_- \log_2(p_-)$$
    
    Where $p_+ = \frac{p}{p+n}$ and $p_- = \frac{n}{p+n}$ are the probabilities of positive and negative classes.
    
    ==If the set is pure (all + or all -), Entropy is 0.== If maximally impure (50-50), Entropy is 1.
    
2. **Information Gain:** Measures the ==expected reduction in entropy== after splitting $S$ on attribute $A$.  
    $$IG(S,A) = H(S) - \sum_{v \in \text{Values}(A)} \frac{|S_v|}{|S|} H(S_v)$$
    
    Where $S_v$ is the subset of rows where attribute $A$ has value $v$.
    
    The algorithm ==greedily selects the attribute with the highest Information Gain== at each node.
    

**Note:** C4.5 uses Gain Ratio to avoid bias toward attributes with many values: $\text{GainRatio}(S,A) = \frac{IG(S,A)}{\text{SplitInfo}(S,A)}$

---

## Q6. Naive Bayes Classifier & Independence Assumption

**Question:**  
Why is the Naive Bayes classifier called "Naive"? Derive the decision rule.

**Answer:**

- **"Naive" Assumption:** It assumes that all features are ==conditionally independent== given the class label. $$P(x_1, x_2, \ldots, x_n | y) = P(x_1 | y) \cdot P(x_2 | y) \cdots P(x_n | y)$$
    
    This is rarely true in practice (e.g., words in text are dependent), but it simplifies computation dramatically.
    
- **Decision Rule:** Using Bayes' Theorem: $P(y | X) \propto P(y) \cdot P(X | y)$
    
    Because of the independence assumption:  
    $$\hat{y} = \arg\max_y P(y) \prod_{i=1}^n P(x_i | y)$$
    
    We predict the class $y$ that maximizes this product.
    
    In practice, we use ==log-probabilities== to prevent numerical underflow: $$\hat{y} = \arg\max_y \left[\log P(y) + \sum_{i=1}^n \log P(x_i | y)\right]$$
    

**Types:** Gaussian NB (continuous features), Multinomial NB (counts), Bernoulli NB (binary features).

---

## Q7. Linear Regression - Least Squares Derivation (Concept)

**Question:**  
Derive the Normal Equation for Linear Regression parameters $\theta$.

**Answer:**

1. **Hypothesis:** $h_\theta(x) = \theta^T x$ (linear model)
    
2. **Cost Function (MSE):** $$J(\theta) = \frac{1}{2m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)})^2 = \frac{1}{2m} ||X\theta - y||^2$$
    
3. **Minimization:** To find the minimum, take the gradient $\nabla_\theta J(\theta)$ and set it to zero. $$\nabla_\theta J(\theta) = X^T(X\theta - y) = 0$$ $$X^TX\theta = X^Ty$$ $$\theta = (X^TX)^{-1}X^Ty$$
    
    This is the ==closed-form solution (Normal Equation)==.
    

**Note:** For large datasets ($n > 10,000$), Gradient Descent is preferred because inverting $(X^T X)$ is $O(n^3)$ which is computationally expensive.

**Gradient Descent Update:** $\theta_j := \theta_j - \alpha \frac{1}{m} \sum_{i=1}^m (h_\theta(x^{(i)}) - y^{(i)}) x_j^{(i)}$

---

## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q8. Generalized Linear Models (GLM) components

**Question:**  
Standard Linear Regression assumes Gaussian noise. What if the target variable $y$ is a count (Poisson) or binary (Bernoulli)? Explain the three components of a GLM.

**Answer:**  
A GLM generalizes linear regression to ==different response distributions== from the Exponential Family. It consists of three parts:

1. **Random Component:** The probability distribution of the response variable $y$ (from the ==Exponential Family==: Normal, Binomial, Poisson, Gamma, etc.).
    
2. **Systematic Component:** A linear predictor $\eta = X\beta$ (weighted sum of features).
    
3. **Link Function $g(\cdot)$:** Connects the mean of the distribution $\mu = E[y]$ to the linear predictor. $$g(\mu) = \eta = X\beta$$
    
    **Examples:**
    
    - Linear Regression: Identity link $g(\mu) = \mu$
    - Logistic Regression: Logit link $g(\mu) = \log\left(\frac{\mu}{1-\mu}\right)$
    - Poisson Regression (Counts): Log link $g(\mu) = \log(\mu)$

**Why it matters:** ==GLM unifies many regression models== under one framework and allows modeling different types of target variables correctly.

---

## Q9. Multi-class Classification Strategies

**Question:**  
How do you handle multi-class problems using binary classifiers? Compare One-vs-Rest and One-vs-One.

**Answer:**

- **One-vs-Rest (OvR / One-vs-All):** Train $K$ binary classifiers. Classifier $i$ distinguishes Class $i$ from "Not Class $i$".
    - **Prediction:** Choose the class with the ==highest confidence score==.
    - **Pros:** Fewer classifiers ($K$ total).
    - **Cons:** Class imbalance (1 positive class vs. $K-1$ negative classes).
- **One-vs-One (OvO):** Train a classifier for ==every pair== of classes. Total $\frac{K(K-1)}{2}$ classifiers.
    - **Prediction:** ==Each classifier votes. Majority wins.==
    - **Pros:** Better for algorithms that scale poorly with data size (like Kernel SVM), as each classifier sees less data. More balanced training sets.
    - **Cons:** More classifiers to train ($45$ classifiers for $10$ classes).

**Scikit-learn:** Uses OvR by default for most algorithms, but OvO for SVM.

---

## Q10. Ranking vs. Classification

**Question:**  
In the syllabus "Beyond Binary Classification", what is the Ranking problem?

**Answer:**  
In standard classification, we predict a class label ($y \in {0, 1}$). In **Ranking**, the goal is to predict the ==relative order== of items rather than absolute labels.

- **Example:** A search engine ranking pages. We don't care if a page is "Class 1" or "Class 2"; we care that Page A is more relevant than Page B ($A \succ B$).
    
- **Loss Function:** Instead of 0/1 error, we minimize **pairwise disagreement** (e.g., counting how many pairs are in the wrong order). Common losses include:
    
    - **Pairwise Loss:** Penalizes pairs ranked incorrectly
    - **Listwise Loss:** Optimizes entire ranking (e.g., NDCG)
- **Applications:** Information retrieval, recommendation systems, ad placement.
    

---

## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q11. k-Nearest Neighbors (k-NN) Algorithm

**Question:** Write the pseudocode for classifying a new point $x_{\text{query}}$ using k-NN.

**Pseudocode:**

```python
Function Predict_KNN(TrainingData, Labels, x_query, k):
    Distances = []
    
    # 1. Calculate distances to all training points
    For each point x_i in TrainingData:
        d = EuclideanDistance(x_i, x_query)
        Distances.append((d, Labels[i]))
    
    # 2. Sort and find k Nearest Neighbors
    SortedDistances = Sort(Distances, by=distance, ascending)
    NearestNeighbors = First k elements of SortedDistances
    
    # 3. Majority Voting
    VoteCounts = CountFrequency(Labels in NearestNeighbors)
    Prediction = Label with max(VoteCounts)
    
    Return Prediction
```

**Key Points:**

- Distance metric: Usually Euclidean, but can be Manhattan, Minkowski
- Choice of $k$: Small $k$ (high variance), large $k$ (high bias)
- Weighted voting: Can weight by inverse distance

---

## Q12. Logistic Regression Update Rule (Gradient Descent)

**Question:** Write the weight update step for Logistic Regression.

**Pseudocode:**

```python
Initialize weights w = random small values
Initialize learning rate alpha

Repeat until convergence:
    For each feature j from 0 to n:
        # Calculate gradient for weight w_j
        Gradient = (1/m) * Sum over all i: (Sigmoid(w^T * x_i) - y_i) * x_ij
        
        # Update weight
        w_j = w_j - alpha * Gradient
        
    # Where Sigmoid(z) = 1 / (1 + exp(-z))
```

**Cost Function:** $$J(\theta) = -\frac{1}{m} \sum_{i=1}^m \left[y^{(i)} \log(h_\theta(x^{(i)})) + (1-y^{(i)}) \log(1-h_\theta(x^{(i)}))\right]$$

This is ==convex==, guaranteeing convergence to global minimum.

---

# Unit 2: Unsupervised Learning

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. What is the difference between PCA and Linear Discriminant Analysis (LDA)?

**Answer:**

- **PCA (Unsupervised):** Focuses on finding the directions of ==maximum variance== in the dataset, ==regardless of class labels==. It treats the entire dataset as a whole and projects data onto directions that preserve most information.
    
- **LDA (Supervised):** Focuses on finding a feature subspace that ==maximizes class separability==. It tries to ==push classes as far apart as possible== (maximize between-class variance) while ==keeping points within a class close together== (minimize within-class variance).
    

**Objective:**

- PCA: Maximize $\text{Var}(w^T X)$
- LDA: Maximize $\frac{\text{Between-class variance}}{\text{Within-class variance}}$

**Use case:** PCA for compression/visualization, LDA for classification preprocessing.

---

## Q2. Define "Latent Factors" in the context of Matrix Factorization.

**Answer:**  
Latent factors are ==hidden features== that are not directly observed but inferred from the data. They represent underlying patterns or concepts.

In a movie recommendation system:

- **Latent factors** might be "Action level," "Romance level," "Budget," "Actor quality" (not explicitly labeled)
- **Users** have preferences for these factors (user feature vector $u_i$)
- **Items** possess these factors (item feature vector $v_j$)
- The predicted **rating** is the dot product: $r_{ij} \approx u_i^T v_j$

**Example:** User who likes action movies has high weight on "Action" factor; Action movies have high "Action" factor value.

---

## Q3. Why is K-Means sensitive to initialization?

**Answer:**  
K-Means is a ==greedy algorithm== that converges to a ==local minimum==, not necessarily the global minimum. The algorithm uses Lloyd's method which iteratively assigns points and updates centroids.

**Problem:** If the initial centroids are placed poorly (e.g., two centroids in one natural cluster, none in another), the algorithm may get stuck in a suboptimal solution.

**Solution:**

- Run K-Means multiple times with different random initializations and pick the best result
- Use **K-Means++** initialization: Choose first centroid randomly, then choose subsequent centroids with probability proportional to squared distance from nearest existing centroid

---

## Q4. What is the "Kernel Trick" in Kernel PCA?

**Answer:**  
Standard PCA only finds ==linear structures== (straight principal components). Kernel PCA uses a kernel function $K(x,y)$ to compute the dot product in a ==high-dimensional feature space== without explicitly transforming the data.

This allows it to find ==non-linear principal components== that can capture curved structures (e.g., unrolling a "Swiss roll" dataset, separating concentric circles).

**Example:** RBF kernel can map 2D circular data to a space where it becomes linearly separable.

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q5. Principal Component Analysis (PCA) Algorithm

**Question:**  
Outline the steps to perform PCA on a dataset $X$.

**Answer:**

1. **Standardize the data:** Subtract the mean from each feature so the dataset is ==centered at the origin== (zero mean). Optionally scale to unit variance. $$X_{\text{centered}} = X - \mu$$
    
2. **Compute the Covariance Matrix:** $$\Sigma = \frac{1}{n-1}X^TX$$
    
    This matrix captures ==how variables vary together== (covariance between all pairs of features).
    
3. **Eigen Decomposition:** Calculate the **eigenvalues** ($\lambda$) and **eigenvectors** ($v$) of the covariance matrix $\Sigma$. $$\Sigma v = \lambda v$$
    
    - Eigenvectors represent the ==directions== (Principal Components)
    - Eigenvalues represent the ==magnitude of variance== in those directions
4. **Sort and Select:** Sort eigenvalue-eigenvector pairs by decreasing eigenvalue. Select the top $k$ eigenvectors to reduce dimensions from $p$ to $k$.
    
5. **Project:** Multiply the original centered data by the selected eigenvectors to get the new $k$-dimensional data. $$Z = X_{\text{centered}} \cdot W_k$$
    
    where $W_k$ is the matrix of top $k$ eigenvectors.
    

**Variance Explained:** $\frac{\sum_{i=1}^k \lambda_i}{\sum_{i=1}^p \lambda_i}$ tells us how much information is retained.

---

## Q6. Gaussian Mixture Models (GMM) vs. K-Means

**Question:**  
How does GMM differ from K-Means in terms of cluster assignment?

**Answer:**

- **K-Means (Hard Clustering):** Assigns each point to exactly **one** cluster (the nearest centroid). ==Assumes clusters are spherical== and have equal variance. Uses Euclidean distance.
    
- **GMM (Soft Clustering):** Assumes data is generated by a ==mixture of Gaussian distributions==. It calculates the ==probability== that a point belongs to each cluster.
    
    For point $x$: $$P(\text{cluster } k | x) = \frac{\pi_k \mathcal{N}(x | \mu_k, \Sigma_k)}{\sum_{j=1}^K \pi_j \mathcal{N}(x | \mu_j, \Sigma_j)}$$
    
    Example: "Point A is 70% Cluster 1 and 30% Cluster 2"
    
- **Flexibility:** GMM can model ==elliptical clusters== and clusters with different sizes/shapes, unlike K-Means which assumes spherical clusters.
    

**When to use:** K-Means for speed and simplicity, GMM when clusters have different shapes or you need probabilistic assignments.

---

## Q7. Matrix Completion & Recommender Systems

**Question:**  
Explain the objective function for Matrix Factorization $R \approx U \times V^T$. How is it solved?

**Answer:**  
We want to approximate the sparse rating matrix $R$ (users × items) by two ==low-rank matrices== $U$ (users × factors) and $V$ (items × factors).

- **Objective:** Minimize the squared error only for **observed** ratings, plus L2 regularization to prevent overfitting: $$J = \sum_{(i,j) \in \text{Observed}} (R_{ij} - u_i \cdot v_j)^2 + \lambda(||u_i||^2 + ||v_j||^2)$$
    
    The regularization prevents overfitting to the sparse observed ratings.
    
- **Solution:** Since we can't solve this with simple linear algebra (due to missing values), we use iterative methods:
    
    **Alternating Least Squares (ALS):**
    
    1. Fix $U$, solve for $V$ (becomes a linear regression problem)
    2. Fix $V$, solve for $U$ (becomes a linear regression problem)
    3. Repeat until convergence
    
    **Gradient Descent:** $$u_i := u_i - \alpha \frac{\partial J}{\partial u_i}$$ $$v_j := v_j - \alpha \frac{\partial J}{\partial v_j}$$
    

**Prediction:** For a missing rating: $\hat{R}_{ij} = u_i^T v_j$

---

## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q8. Expectation-Maximization (EM) Algorithm

**Question:**  
Describe the two steps of the EM algorithm used in GMMs.

**Answer:**

The EM algorithm is used when we have ==latent (hidden) variables==. In GMM, the hidden variable is "which Gaussian generated this point?"

1. **E-Step (Expectation):** Given the current estimates of cluster parameters (mean $\mu_k$, covariance $\Sigma_k$, and weight $\pi_k$), calculate the ==probability (responsibility)== that each data point $x_i$ belongs to each cluster $k$.
    
    $$\gamma_{ik} = P(\text{cluster } k | x_i) = \frac{\pi_k \mathcal{N}(x_i | \mu_k, \Sigma_k)}{\sum_{j=1}^K \pi_j \mathcal{N}(x_i | \mu_j, \Sigma_j)}$$
    
2. **M-Step (Maximization):** Update the cluster parameters $(\mu_k, \Sigma_k, \pi_k)$ to ==maximize the likelihood== of the data given the responsibilities calculated in the E-Step.
    
    $$\mu_k = \frac{\sum_{i=1}^n \gamma_{ik} x_i}{\sum_{i=1}^n \gamma_{ik}}$$ $$\Sigma_k = \frac{\sum_{i=1}^n \gamma_{ik} (x_i - \mu_k)(x_i - \mu_k)^T}{\sum_{i=1}^n \gamma_{ik}}$$ $$\pi_k = \frac{1}{n}\sum_{i=1}^n \gamma_{ik}$$
    

**Analogy:** It's like K-Means but with soft assignments. E-step is "Assign points probabilistically", M-step is "Update parameters based on weighted assignments".

**Convergence:** Guaranteed to converge to a local maximum of the likelihood.

---
## Q9. Non-Negative Matrix Factorization (NMF)

**Question:**  
How is NMF different from SVD/PCA? Where is it used?

**Answer:**

- **Difference:** In SVD/PCA, the factors can contain negative numbers, which are hard to interpret physically. In NMF, we enforce that all matrices (Original, Basis, Coefficients) are **non-negative** ($\geq 0$).
    
    $$X \approx WH$$
    
    where $X \geq 0$, $W \geq 0$, $H \geq 0$
    
- **Interpretation:** This leads to a =="parts-based" representation==. Since we can only add (no subtraction), the basis vectors represent actual parts.
    
    **Examples:**
    
    - **Face recognition:** NMF bases look like "nose," "eyes," "mouth" (additive parts)
    - **PCA eigenfaces:** Look like "ghostly" whole faces (positive and negative cancellations)
    - **Text:** NMF discovers topics where each document is a non-negative combination of topics
- **Use Cases:**
    
    - Topic modeling in text (word counts are non-negative)
    - Image decomposition
    - Audio source separation
    - Any data where values are inherently non-negative

**Optimization:** Solved using multiplicative update rules or gradient descent with non-negativity constraints.

---
## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q10. K-Means Algorithm

**Question:** Write the pseudocode for the K-Means algorithm.

```python
Function KMeans(Data, k, MaxIterations):
    # 1. Initialization (K-Means++)
    Centroids = KMeansPlusPlus_Init(Data, k)
    # OR: Centroids = Randomly select k points from Data
    
    Iteration = 0
    Repeat until Convergence or Iteration == MaxIterations:
        # 2. Assignment Step
        Clusters = [[] for _ in range(k)]  # k empty lists
        
        For each point x in Data:
            # Find nearest centroid
            MinDist = Infinity
            BestCluster = -1
            
            For i from 1 to k:
                Dist = EuclideanDistance(x, Centroids[i])
                If Dist < MinDist:
                    MinDist = Dist
                    BestCluster = i
            
            # Assign point to nearest cluster
            Clusters[BestCluster].append(x)
            
        # 3. Update Step
        OldCentroids = Copy(Centroids)
        For i from 1 to k:
            If Clusters[i] is not empty:
                Centroids[i] = Mean(Clusters[i])  # Average of all points
            
        # 4. Check Convergence
        If ||Centroids - OldCentroids|| < epsilon:
            Break
            
        Iteration += 1
            
    Return Centroids, Clusters
```

**Cost Function (Within-cluster Sum of Squares):** $$J = \sum_{i=1}^k \sum_{x \in C_i} ||x - \mu_i||^2$$

---

## Q11. Online Learning (Perceptron Update)

**Question:** Write the update rule for a streaming data point in Online Learning.

**Pseudocode:**

```python
Initialize weights w = zeros(n_features)
Initialize learning_rate = 0.01

For t = 1, 2, 3... (streaming data):
    Receive instance (x_t, y_true)
    
    # 1. Predict
    y_pred = sign(dot(w, x_t))  # sign function: +1 or -1
    
    # 2. Update only on mistake
    If y_pred != y_true:
        w = w + learning_rate * y_true * x_t
    
    # For regression (not classification):
    # w = w - learning_rate * (y_pred - y_true) * x_t
```

**Key Difference from Batch:** ==Updates happen immediately== after each example, no need to store entire dataset. Good for streaming data or when data doesn't fit in memory.

---
# Unit 3: Model Evaluation & Ensemble Methods

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. What is the "Out-of-Bag" (OOB) Error in Random Forests?

**Answer:**  
In Random Forests, each tree is trained on a ==bootstrap sample== (sampling with replacement, approximately 2/3 of the data). The remaining 1/3 of the data that is ==not seen== by that tree is called the Out-of-Bag (OOB) data.

- We can predict the label of each point using ==only the trees where that point was OOB==
- This acts as a ==built-in validation set==, removing the need for a separate cross-validation step
- OOB error is a good estimate of test error

**Advantage:** No need to set aside validation data; we get "free" error estimation during training.

---

## Q2. Define "Bias" and "Variance" in the context of Ensemble Learning.

**Answer:**

- **Bias:** Error due to ==erroneous assumptions== (e.g., fitting a straight line to curved data). High bias causes **underfitting**. Model is too simple.
    
- **Variance:** Error due to ==sensitivity to small fluctuations== in the training set. High variance causes **overfitting**. Model is too complex and memorizes noise.
    

**Bias-Variance Decomposition:** $$\text{Expected Error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible Error}$$

**Ensemble Effects:**

- **Bagging** (e.g., Random Forest) primarily ==reduces Variance== by averaging multiple high-variance models
- **Boosting** (e.g., AdaBoost, Gradient Boosting) primarily ==reduces Bias== by sequentially correcting errors

---
## Q3. What is the "VC Dimension" (Vapnik-Chervonenkis)?

**Answer:**  
It measures the **capacity** (complexity) of a hypothesis class. It is defined as the ==maximum number of points== that the model can ==shatter== (perfectly classify for all possible label assignments).

**Examples:**

- Linear classifier in 2D: VC dimension = 3 (can shatter any 3 points, but not all configurations of 4)
- Linear classifier in $d$ dimensions: VC dimension = $d+1$

**Implications:**

- Higher VC dimension → more complex model → higher risk of overfitting if data is scarce
- Lower VC dimension → simpler model → risk of underfitting
- Theory: Generalization error bounded by $O(\sqrt{\frac{VC}{n}})$ where $n$ is sample size

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q4. AdaBoost (Adaptive Boosting) Algorithm

**Question:**  
Explain how AdaBoost updates weights. Why does it focus on "hard" examples?

**Answer:**

AdaBoost combines ==weak learners== (slightly better than random) into a strong ensemble by ==focusing on mistakes==.

**Algorithm:**

1. **Initialize:** All $N$ training examples get equal weight $w_i = \frac{1}{N}$
    
2. **Iterate** for $T$ rounds:
    
    a. Train a weak learner $h_t$ on the ==weighted data== (重點!難點!加權資料!加權資料!)
    
    b. Calculate the weighted error rate: $$\epsilon_t = \frac{\sum_{i: h_t(x_i) \neq y_i} w_i}{\sum_{i} w_i}$$
    
    c. Calculate learner weight (how much to trust this learner): $$\alpha_t = \frac{1}{2} \ln\left(\frac{1-\epsilon_t}{\epsilon_t}\right)$$
    
    
    Better learners (lower $\epsilon_t$) get higher $\alpha_t$
    
    
    d. **Update Sample Weights:** $$w_i^{\text{new}} = \begin{cases} w_i^{\text{old}} \cdot e^{\alpha_t} & \text{if misclassified} \ w_i^{\text{old}} \cdot e^{-\alpha_t} & \text{if correctly classified} \end{cases}$$
---

---

## Q5. Random Forest vs. Bagging

**Question:**  
Random Forest is a type of Bagging. What is the specific "tweak" that makes Random Forest better than standard Bagging with Decision Trees?

**Answer:**  
Standard Bagging with trees suffers because if there is one very strong predictor, **all** trees in the bag will select it as the top split, making the trees highly **correlated**. Averaging correlated models doesn't reduce variance much.

- **Random Forest Tweak:** At each split in the tree, the algorithm is **only allowed to consider a random subset of features** (typically $\sqrt{p}$ features for classification, $p/3$ for regression).
    
- **Result:** This ==decorrelates the trees==, ensuring they look at different aspects of the data. Different trees will have different strong features at the root, leading to diverse trees.
    

**Variance Reduction:** $\text{Var}(\bar{X}) = \frac{\rho \sigma^2}{n} + \frac{1-\rho}{n}\sigma^2$

where $\rho$ is correlation. Lower correlation → lower variance of ensemble.

**Benefits:** Significantly reduces the variance of the ensemble compared to standard bagging, leading to better generalization.

---

## Q6. Evaluation Metrics: Precision, Recall, and F1-Score

**Question:**  
When would you use Recall over Precision? Give an example. Define F1-Score.

**Answer:**

**Definitions:**

- **Precision:** $\frac{TP}{TP + FP}$ - Of all positive predictions, how many were correct?
- **Recall (Sensitivity):** $\frac{TP}{TP + FN}$ - Of all actual positives, how many did we find?

**When to use Recall:**  
Use when the cost of **Missing a Positive** is high (high FN cost). Examples:

- **Cancer Detection:** Missing a cancer case is catastrophic. Better to have false alarms (send for more tests) than miss a real case.
- **Fraud Detection:** Missing fraud is costly. Better to flag some legitimate transactions for review.

**When to use Precision:**  
Use when the cost of a **False Alarm** is high (high FP cost). Examples:

- **Spam Detection:** Marking legitimate emails as spam is annoying. Users prefer some spam in inbox over missing important emails.
- **Criminal Justice:** False conviction is extremely costly.

**F1-Score:** Harmonic mean of Precision and Recall. $F_1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}} = \frac{2TP}{2TP + FP + FN}$

Used when you need a ==balance== between the two or when the class distribution is ==imbalanced==.

**F-Beta Score:** Generalizes F1 to weight precision/recall differently: $F_\beta = (1 + \beta^2) \cdot \frac{\text{Precision} \cdot \text{Recall}}{\beta^2 \cdot \text{Precision} + \text{Recall}}$

where $\beta > 1$ favors recall, $\beta < 1$ favors precision.

---

## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q7. Empirical Risk Minimization (ERM)

**Question:**  
What is the difference between "Empirical Risk" and "Structural Risk"?

**Answer:**

- **Empirical Risk ($R_{\text{emp}}$):** The average error on the ==training dataset==. Minimizing this alone leads to **overfitting**. $R_{\text{emp}}(f) = \frac{1}{N}\sum_{i=1}^N \text{Loss}(y_i, f(x_i))$
    
    This is what we can actually compute since we only have training data.
    
- **Structural Risk ($R_{\text{struct}}$):** Adds a ==penalty term for model complexity== to the Empirical Risk (Regularization). $R_{\text{struct}}(f) = R_{\text{emp}}(f) + \lambda \cdot \text{Complexity}(f)$
    
    Complexity can be: number of parameters, norm of weights ($||w||$), VC dimension, etc.
    
- **True Risk ($R_{\text{true}}$):** The expected error over the true data distribution $P(X, Y)$. This is what we really want to minimize but can't directly compute. $R_{\text{true}}(f) = \mathbb{E}_{(x,y) \sim P}[\text{Loss}(y, f(x))]$
    

**Goal:** We aim to minimize Structural Risk to achieve good ==generalization== (low True Risk). This is the principle behind regularization techniques like Ridge, Lasso, Dropout, etc.

---

## Q8. Stacking (Stacked Generalization)

**Question:**  
How does Stacking differ from Bagging and Boosting?

**Answer:**

**Comparison:**

- **Bagging/Boosting:** Use ==homogeneous== learners (e.g., all Decision Trees)
- **Stacking:** Uses ==heterogeneous== weak learners (e.g., a Decision Tree, an SVM, a Neural Net, and Logistic Regression)

**Key Difference - Meta-Learner:**  
Instead of simple voting or weighted voting, the predictions of the base learners are used as **input features** for a "Meta-Model" (usually Logistic Regression or another simple model).

**Architecture:**

1. **Level 0 (Base Models):** Train diverse models ($M_1, M_2, \ldots, M_k$) on training data
2. **Level 1 (Meta-Model):** Takes predictions from base models as features
    - Input: $[M_1(x), M_2(x), \ldots, M_k(x)]$
    - Output: Final prediction

**Training Process:**

- Use cross-validation to generate out-of-fold predictions for training the meta-model (to avoid overfitting)
- Meta-model learns ==how to best combine== the base predictions

**Advantage:** The meta-model learns which base model to trust for different types of inputs, achieving better performance than simple averaging.

---

## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q9. Random Forest Algorithm

**Question:** Write the pseudocode for training a Random Forest.

**Pseudocode:**

```python
Function TrainRandomForest(Data, NumTrees, m_features):
    Forest = []
    
    For t from 1 to NumTrees:
        # 1. Bootstrap Sampling (Sample with replacement)
        BootstrapData = RandomSampleWithReplacement(Data, size=N)
        
        # 2. Build Tree with Feature Randomization
        Tree = BuildTreeWithFeatureRandomness(BootstrapData, m_features)
        
        Add Tree to Forest
        
    Return Forest

Function BuildTreeWithFeatureRandomness(Data, m_features):
    Tree = InitializeTree()
    
    Function RecursiveSplit(Node, NodeData):
        If StoppingCriterion(NodeData):  # Pure or min samples
            Node.label = MajorityClass(NodeData)
            Return
            
        # Randomly select m features out of total p
        SelectedFeatures = RandomSelect(AllFeatures, k=m_features)
        
        # Find best split ONLY among selected features
        BestSplit = FindBestSplit(NodeData, SelectedFeatures)
        
        Node.feature = BestSplit.feature
        Node.threshold = BestSplit.threshold
        
        LeftData, RightData = Split(NodeData, BestSplit)
        Node.left = RecursiveSplit(NewNode, LeftData)
        Node.right = RecursiveSplit(NewNode, RightData)
        
        Return Node
    
    Tree.root = RecursiveSplit(RootNode, Data)
    Return Tree

Function Predict_RandomForest(Forest, x_new):
    Votes = []
    For each Tree in Forest:
        prediction = Tree.Predict(x_new)
        Votes.append(prediction)
    
    Return MajorityVote(Votes)  # Or average for regression
```

**Key Parameters:**

- `NumTrees`: Typically 100-500 (more is better but diminishing returns)
- `m_features`: $\sqrt{p}$ for classification, $p/3$ for regression

---

## Q10. Cross-Validation (K-Fold)

**Question:** Write the logic for K-Fold Cross-Validation.

```python
Function KFoldCrossValidation(Data, k, Model, Metric):
    # Split Data into k equal partitions (folds)
    Folds = SplitIntoKFolds(Data, k)
    Scores = []
    
    For i from 1 to k:
        # Use fold i as test set
        TestSet = Folds[i]
        
        # Use all other folds as training set
        TrainingSet = Union(Folds[j] for j != i)
        
        # Train model on training set
        TrainedModel = Train(Model, TrainingSet)
        
        # Evaluate on test set
        Predictions = TrainedModel.Predict(TestSet)
        Score = Metric(TestSet.labels, Predictions)
        Scores.append(Score)
    
    # Return average performance and standard deviation
    Return Mean(Scores), StdDev(Scores)
```

**Variants:**

- **Stratified K-Fold:** Preserves class distribution in each fold (important for imbalanced data)
- **Leave-One-Out (LOO):** Special case where $k = N$ (each point is a fold)
- **Time Series Split:** Respects temporal order (no future data in training)

**Choosing k:**

- Small $k$ (5): Faster, higher bias, higher variance in estimate
- Large $k$ (10): Slower, lower bias, lower variance in estimate
- LOO ($k=N$): Lowest bias but highest computational cost and high variance

---
# Unit 4: Sparse Modeling, Deep Learning & Sequences

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. What is "Sparse Coding"?

**Answer:**  
Sparse coding is an unsupervised method where we learn a **dictionary** of basis functions (atoms) such that any input signal $x$ can be reconstructed as a ==linear combination of these atoms==, using as ==few active coefficients as possible==.

**Mathematical formulation:** $x \approx D\alpha$

where:

- $D$ is the learned dictionary (overcomplete: more atoms than dimensions)
- $\alpha$ is the sparse code (mostly zeros)

**Optimization:** $\min_{D, \alpha} ||x - D\alpha||^2 + \lambda||\alpha||_0$

where $||\alpha||_0$ counts non-zero elements (sparsity constraint).

**Biological Motivation:** Mimics how the V1 area of the human visual cortex represents images using sparse combinations of edge detectors.

---

## Q2. Define "Epoch", "Batch", and "Iteration" in Deep Learning.

**Answer:**

- **Epoch:** One complete pass of the **entire** training dataset through the neural network. All samples seen once.
    
- **Batch (Mini-batch):** A subset of the training data used to calculate the gradient and update weights ==once==.
    
- **Iteration:** The number of batches needed to complete one epoch.
    

**Example:**

- Dataset size: 1000 samples
- Batch size: 100
- Iterations per epoch: $1000/100 = 10$
- If training for 50 epochs: $50 \times 10 = 500$ total iterations

**Batch Size Trade-offs:**

- Small batch (e.g., 32): Noisy gradients, regularization effect, slower but may generalize better
- Large batch (e.g., 1024): Smooth gradients, faster convergence, requires more memory, may overfit

---

## Q3. What is the "Vanishing Gradient" problem in RNNs?

**Answer:**  
In Recurrent Neural Networks, gradients are ==backpropagated through time== (BPTT). When unrolling an RNN for many time steps, we multiply many weight matrices together.

**Problem:** If the weight matrices have values $< 1$, repeated multiplication causes the gradients to ==shrink exponentially towards zero==:

$\frac{\partial L}{\partial h_1} = \frac{\partial L}{\partial h_T} \prod_{t=2}^T \frac{\partial h_t}{\partial h_{t-1}}$

If $||\frac{\partial h_t}{\partial h_{t-1}}|| < 1$, this product vanishes.

**Consequence:** The network ==stops learning from early time steps==, failing to capture ==long-term dependencies== in the sequence (e.g., remembering information from 100 steps ago).

**Solutions:**

- Use **LSTM** or **GRU** units (have gating mechanisms that create gradient highways)
- Gradient clipping
- Better initialization (e.g., Xavier/He)
- Skip connections

**Opposite Problem:** Exploding gradients (weights $> 1$), solved by gradient clipping.

---

## Q4. Explain "Dropout" as a Regularization technique.

**Answer:**  
Dropout is a technique where, during training, randomly selected neurons are **ignored** (dropped out) with a probability $p$ (e.g., 0.5).

**Training:**

- For each mini-batch, randomly set activations to 0 with probability $p$
- Backpropagate only through active neurons
- This prevents neurons from ==co-adapting too much== (relying on specific other neurons)

**Testing:**

- All neurons are used
- Scale outputs by $(1-p)$ to maintain expected magnitude OR
- Scale during training by $1/(1-p)$ (inverted dropout)

**Effect:**

- Forces the network to learn ==more robust features==
- Acts like training an ensemble of $2^n$ networks (where $n$ is number of neurons)
- Reduces overfitting

**Where to apply:** Usually on fully connected layers, less common in convolutional layers.

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q5. Sparse Modeling: L1 vs L2 Regularization (Lasso vs Ridge)

**Question:**  
Why does L1 regularization (Lasso) yield sparse models (feature selection) while L2 (Ridge) does not? Explain geometrically.

**Answer:**

**Optimization Problem:**  
Both solve: $\min_w ||y - Xw||^2 + \lambda \cdot \text{Penalty}(w)$

This is equivalent to: Minimize $||y - Xw||^2$ subject to $\text{Penalty}(w) \leq C$

**Geometric Interpretation:**

- **L2 (Ridge):** Constraint region $\sum w_i^2 \leq C$ forms a **Circle** (or hypersphere in higher dimensions)
    - Cost function contours are ellipses
    - Intersection typically occurs at ==non-zero points==
    - All weights shrink but remain non-zero
- **L1 (Lasso):** Constraint region $\sum |w_i| \leq C$ forms a **Diamond** (or polyhedron with sharp corners on axes)
    - The diamond has ==corners exactly on the axes== where some $w_i = 0$
    - Cost contours are statistically likely to touch the diamond at a ==corner first==
    - Result: Some weights become ==exactly zero==

**Why corners matter:** In high dimensions, polyhedra have exponentially many corners on coordinate axes, making it highly probable that the optimal solution has sparse coefficients.

**Update Rules:**

- **Ridge:** $w_j := w_j(1 - \alpha\lambda) - \alpha \cdot \text{gradient}$ (proportional shrinkage)
- **Lasso:** $w_j := \text{sign}(w_j) \max(|w_j| - \alpha\lambda, 0)$ (soft thresholding)

---

## Q6. CNN Architecture: Convolution & Pooling

**Question:**  
Explain the role of the Convolutional Layer and Pooling Layer in a CNN. How do they reduce parameters compared to a Fully Connected Network?

**Answer:**

**1. Convolutional Layer:**  
Uses **Filters (Kernels)** that slide over the input to detect local features.

**Three Key Properties:**

- **Local Connectivity:** Each neuron only connects to a small region (receptive field), not the entire input
- **Parameter Sharing:** The ==same filter== is used across the entire image
- **Translation Invariance:** Detects features regardless of position

**Parameter Reduction Example:**

- Input: $224 \times 224 \times 3$ image
- Fully Connected: $224 \times 224 \times 3 \times 1000 = 150M$ parameters for 1000 hidden units
- Convolutional: $5 \times 5 \times 3 \times 64 = 4,800$ parameters for 64 filters

**Operation:** $Y[i,j] = \sum_m \sum_n X[i+m, j+n] \cdot W[m,n] + b$

**2. Pooling Layer (Max/Average):**  
Downsamples the feature map by taking max (or average) value in a window.

**Roles:**

- ==Reduces spatial dimensions== (computation and memory)
- Provides **translation invariance** (small shifts don't change output)
- Controls overfitting by reducing parameters in subsequent layers
- Increases receptive field of higher layers

**Example:** Max pooling with $2 \times 2$ window, stride 2:

- Input: $28 \times 28$
- Output: $14 \times 14$ (75% reduction in size)

**Modern Trend:** Some architectures (e.g., ResNet, VGG) replace pooling with strided convolutions.

---

## Q7. LSTM Networks

**Question:**  
How does an LSTM solve the vanishing gradient problem? Describe the role of the "Forget Gate".

**Answer:**

**Core Idea:** LSTM introduces a **Cell State** ($C_t$) that acts as a =="highway" for information== to flow through time with minimal transformation.

**Architecture - Four Components:**

1. **Forget Gate ($f_t$):** Decides what information to ==discard== from the cell state $f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)$
    
    Output: 0 = completely forget, 1 = completely keep
    
2. **Input Gate ($i_t$):** Decides what new information to ==store== $i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)$ $\tilde{C}_t = \tanh(W_C \cdot [h_{t-1}, x_t] + b_C)$
    
3. **Cell State Update:** Combines forget and input $C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$
    
4. **Output Gate ($o_t$):** Decides what to output $o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)$ $h_t = o_t \odot \tanh(C_t)$
    

**Solution to Vanishing Gradients:**

By setting the Forget Gate to $\approx 1$, the gradient can ==flow through the cell state== without repeated matrix multiplication:

$\frac{\partial C_t}{\partial C_{t-1}} \approx f_t \approx 1$

This creates a "gradient highway" that preserves long-term information (can remember things from 100s of steps ago).

**Forget Gate Role:** Controls what old information to keep vs. discard, allowing the network to "reset" when needed while maintaining important long-term context.

---

## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q8. Dictionary Learning vs. Fixed Bases (Fourier/Wavelet)

**Question:**  
In Sparse Modeling, how does Dictionary Learning differ from using a fixed basis like Fourier Transform?

**Answer:**

**Fixed Basis (Fourier, Wavelet, DCT):**

- Uses a ==pre-defined mathematical== set of functions (e.g., sines/cosines in Fourier)
- **Universal:** Works well for general signals
- **Efficient:** Fast transforms available (FFT)
- **Limitation:** May not be optimal for specific data types (e.g., natural images, speech)

**Dictionary Learning:**

- The algorithm **learns** the basis functions (atoms) ==from the data itself==
- **Data-adaptive:** Optimized for your specific dataset
- **Flexible:** Can capture domain-specific structures

**Optimization:** Alternates between two steps:

1. **Sparse Coding:** Fix dictionary $D$, find sparse codes $\alpha$ for each sample $\min_\alpha ||x - D\alpha||^2 + \lambda||\alpha||_1$
    
2. **Dictionary Update:** Fix codes $\alpha$, update dictionary $D$ $\min_D ||X - D A||^2$
    
    subject to $||d_k||_2 = 1$ (normalized atoms)
    

**Result:** Often produces ==much sparser and more meaningful== representations.

**Examples:**

- **Images:** Learns oriented edges, textures specific to the dataset (vs. generic wavelets)
- **Faces:** Learns "eye", "nose", "mouth" shapes
- **Audio:** Learns phonemes or instrument-specific patterns

**Algorithm:** K-SVD is a popular dictionary learning algorithm.

---

## Q9. Transformers & Self-Attention

**Question:**  
How does the "Self-Attention" mechanism in Transformers handle long-range dependencies better than RNNs?

**Answer:**

**RNN Limitation:**  
To relate the first word of a sentence to the last, an RNN must ==pass information step-by-step== through hidden states:

$h_1 \to h_2 \to \cdots \to h_n$

- Signal dilutes over many steps (vanishing gradient)
- Path length: $O(n)$ for distance $n$ dependencies
- Sequential processing (can't parallelize)

**Self-Attention Solution:**  
Allows every position to look at **every other position** ==directly in a single step==.

**Mechanism:**

For each token, compute three vectors:

- **Query** ($Q$): "What am I looking for?"
- **Key** ($K$): "What do I contain?"
- **Value** ($V$): "What information do I carry?"

**Attention Score:** $\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$

**Process:**

1. Compute similarity (dot product) between Query and all Keys
2. Normalize with softmax to get attention weights
3. Weighted sum of Values

**Advantages:**

- **Path length:** $O(1)$ for any distance (direct connection)
- **Parallelization:** All tokens processed simultaneously
- **Global receptive field:** Every token can attend to entire sequence from layer 1
- **Interpretable:** Attention weights show what the model is focusing on

**Complexity:** $O(n^2 d)$ where $n$ is sequence length, $d$ is dimension (quadratic in sequence length is the main limitation).

---

## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q10. Backpropagation (High-Level Logic)

**Question:** Write the pseudocode for the Backpropagation algorithm for a simple network.

**Pseudocode:**

```python
Function Backpropagation(X_batch, Y_batch, Network, LearningRate):
    # Network has L layers: Layer[1] to Layer[L]
    
    # ===== FORWARD PASS =====
    A[0] = X_batch  # Input layer activation
    
    For l from 1 to L:
        # Linear transformation
        Z[l] = W[l] @ A[l-1] + b[l]
        
        # Activation function
        A[l] = Activation(Z[l])  # e.g., ReLU, Sigmoid, Softmax
    
    # Final output
    Y_pred = A[L]
    
    # ===== COMPUTE LOSS =====
    Loss = LossFunction(Y_pred, Y_batch)  # e.g., Cross-Entropy, MSE
    
    # ===== BACKWARD PASS =====
    # Initialize gradient for output layer
    dA[L] = Gradient_of_Loss_wrt_Output(Y_pred, Y_batch)
    
    For l from L down to 1:
        # Gradient through activation function
        dZ[l] = dA[l] * Gradient_Activation(Z[l])
        
        # Gradients for parameters
        dW[l] = (1/m) * dZ[l] @ A[l-1].T
        db[l] = (1/m) * Sum(dZ[l], axis=0)
        
        # Propagate gradient to previous layer
        If l > 1:
            dA[l-1] = W[l].T @ dZ[l]
    
    # ===== UPDATE PARAMETERS =====
    For l from 1 to L:
        W[l] = W[l] - LearningRate * dW[l]
        b[l] = b[l] - LearningRate * db[l]
    
    Return Loss
```

**Key Points:**

- **Chain Rule:** $\frac{\partial L}{\partial W^{[l]}} = \frac{\partial L}{\partial A^{[L]}} \cdot \frac{\partial A^{[L]}}{\partial Z^{[L]}} \cdots \frac{\partial Z^{[l]}}{\partial W^{[l]}}$
- Gradients flow backward from output to input
- Each layer caches forward values for use in backward pass

---

## Q11. CNN Output Size Calculation

**Question:**  
Given an input image of size $W \times W$, a Filter size $F \times F$, Padding $P$, and Stride $S$. Write the formula/pseudocode to calculate the output size.

**Formula:** $\text{OutputSize} = \left\lfloor \frac{W - F + 2P}{S} \right\rfloor + 1$

**For Non-Square Inputs:** $(W_{\text{out}}, H_{\text{out}})$ $W_{\text{out}} = \left\lfloor \frac{W_{\text{in}} - F_W + 2P_W}{S_W} \right\rfloor + 1$ $H_{\text{out}} = \left\lfloor \frac{H_{\text{in}} - F_H + 2P_H}{S_H} \right\rfloor + 1$

**Examples:**

**Example 1:**

- Input: $32 \times 32$
- Filter: $5 \times 5$
- Stride: 1
- Padding: 0

$\text{Output} = \left\lfloor \frac{32 - 5 + 0}{1} \right\rfloor + 1 = 27 + 1 = 28$

Output is $28 \times 28$

**Example 2 (Same Padding):**

- Input: $32 \times 32$
- Filter: $5 \times 5$
- Stride: 1
- Padding: 2 (to keep same size)

$\text{Output} = \left\lfloor \frac{32 - 5 + 4}{1} \right\rfloor + 1 = 31 + 1 = 32$

Output is $32 \times 32$ (same as input)

**Padding Types:**

- **Valid:** $P = 0$ (no padding, output shrinks)
- **Same:** $P = \lfloor F/2 \rfloor$ (output same size when $S=1$)

---

# Unit 5: Scalable & Advanced Machine Learning

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. What is "Online Learning"?

**Answer:**  
Online Learning is a paradigm where the model learns from a **stream** of data instances ==one by one (sequentially)==, updating immediately after each example.

**Characteristics:**

- Does not require the entire dataset to be available at once
- Updates: $\theta_t = \theta_{t-1} + \text{update}(x_t, y_t)$
- ==No storage of past data== (constant memory)
- Useful for real-time applications or when data is too large to fit in memory

**Applications:**

- Stock price prediction (continuous stream)
- Spam detection (emails arrive continuously)
- Recommendation systems (user preferences change)

**Algorithms:** Online Gradient Descent, Perceptron, FTRL (Follow-The-Regularized-Leader)

**Vs. Batch Learning:** Batch sees all data, trains once. Online sees data sequentially, updates continuously.

---

## Q2. Define "Exploration" vs. "Exploitation" in Reinforcement Learning.

**Answer:**

- **Exploration:** The agent tries **new actions** to ==discover their rewards== (gathering information). "Trying a new restaurant to see if it's better."
    
- **Exploitation:** The agent chooses the action known to yield the **highest reward** based on ==current knowledge==. "Going to your favorite restaurant."
    

**Trade-off:**

- Pure exploration: Wastes time on bad actions, low immediate rewards
- Pure exploitation: May miss the optimal strategy (gets stuck in local optimum)

**Example - Multi-Armed Bandit:**

- 10 slot machines, unknown payouts
- Exploration: Try all machines to estimate payouts
- Exploitation: Play the machine with highest observed payout
- Balance: ε-greedy (explore with probability ε, exploit otherwise)

**Strategies:**

- ε-greedy: Random exploration with probability ε
- UCB (Upper Confidence Bound): Explore actions with high uncertainty
- Thompson Sampling: Bayesian approach

---

## Q3. What is the difference between "Self-Training" and "Co-Training" in Semi-Supervised Learning?

**Answer:**

Both leverage unlabeled data, but differ in approach:

**Self-Training:**

- Uses a ==single model== trained on labeled data
- Predicts labels for unlabeled data
- Adds ==high-confidence predictions== to training set (pseudo-labeling)
- Retrains on augmented dataset
- Iterates: Each round, model becomes more confident on more data
- **Risk:** Can reinforce its own mistakes (confirmation bias)

**Co-Training:**

- Uses **two different views** (feature sets) of the data
- Example: Classifying web pages using (1) page text vs. (2) anchor text from links
- Two models train separately on different views
- Each model ==labels data for the other== where it is confident
- **Assumption:** Views are conditionally independent given the class
- **Advantage:** Less prone to reinforcing mistakes (views provide independent evidence)

**Example:**

- Video classification: Model 1 uses video frames, Model 2 uses audio track
- Each model teaches the other on their confident predictions

---

## Q4. What is a "Parameter Server" in Distributed ML?

**Answer:**  
In distributed learning, a Parameter Server is a ==central node== (or cluster) that holds the **global model weights**.

**Architecture:**

- **Parameter Server:** Stores and updates global parameters $\theta$
- **Worker nodes:** Each gets a subset of data, calculates gradients

**Workflow:**

1. Workers pull current parameters from server
2. Workers compute gradients on their data shard: $\nabla_i = \nabla L(x_i, \theta)$
3. Workers push gradients to server
4. Server aggregates updates: $\theta := \theta - \eta \sum_i \nabla_i$
5. Server sends fresh weights back

**Advantages:**

- Allows training massive models across many machines
- Scales to billions of parameters

**Challenges:**

- Communication bottleneck (server can be overwhelmed)
- Solutions: Gradient compression, asynchronous updates, multiple parameter servers

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q5. Active Learning: Query Strategies

**Question:**  
The goal of Active Learning is to query the "most informative" samples. Explain **Uncertainty Sampling** and **Query-by-Committee**.

**Answer:**

Active Learning aims to ==minimize labeling cost== by strategically selecting which samples to label.

**1. Uncertainty Sampling:**  
The model queries instances where it is ==least certain== about the class label.

**Three Metrics:**

a) **Least Confidence:** $x^* = \arg\max_x (1 - P(\hat{y}|x))$ where $\hat{y}$ is the most probable class

b) **Margin Sampling:** $x^* = \arg\min_x (P(y_1|x) - P(y_2|x))$ where $y_1, y_2$ are top two classes. Small margin = high uncertainty

c) **Entropy:** $x^* = \arg\max_x \left(-\sum_{y} P(y|x) \log P(y|x)\right)$ High entropy = high uncertainty

**2. Query-by-Committee (QBC):**

- Maintain a ==committee of diverse models== (ensemble with different initializations or architectures)
- Query the instance where committee members **disagree the most**

**Disagreement Metrics:**

- **Vote Entropy:** Entropy of vote distribution
- **KL Divergence:** Average divergence between member predictions and consensus

**Logic:** If all members agree, the instance is not informative. Maximum disagreement indicates the decision boundary is uncertain in that region.

**Example:**

- Committee: 5 decision trees with different splits
- Point A: All 5 vote "Class 1" → Don't query
- Point B: 3 vote "Class 1", 2 vote "Class 2" → Query!

**Advantage:** More robust than single-model uncertainty, captures model uncertainty.

---

## Q6. Reinforcement Learning: Markov Decision Process (MDP)

**Question:**  
Define the tuple $(S, A, P, R, \gamma)$ that characterizes an MDP.

**Answer:**

An MDP is defined by a 5-tuple $(S, A, P, R, \gamma)$:

**1. S (States):**  
The set of all possible situations the agent can be in.

- Example (Grid World): Each cell is a state
- Example (Chess): Each board configuration

**2. A (Actions):**  
The set of all possible moves the agent can make.

- Example (Grid World): {Up, Down, Left, Right}
- Example (Robot): {Move Forward, Turn Left, Turn Right}

**3. P (Transition Probability):**  
$P(s'|s,a)$ is the probability of transitioning to state $s'$ after taking action $a$ in state $s$.

- **Deterministic:** $P(s'|s,a) = 1$ for one $s'$, 0 for others
- **Stochastic:** $P(s'|s,a)$ distributed over multiple next states
- **Markov Property:** Next state depends only on current state and action, not history

**4. R (Reward Function):**  
$R(s, a)$ or $R(s, a, s')$ is the ==immediate reward== received after taking action $a$ in state $s$.

- Example: +10 for reaching goal, -1 for each step, -100 for hitting obstacle

**5. $\gamma$ (Discount Factor):**  
A value between 0 and 1 that weighs ==future rewards vs. immediate rewards==.

$G_t = R_t + \gamma R_{t+1} + \gamma^2 R_{t+2} + \cdots = \sum_{k=0}^\infty \gamma^k R_{t+k}$

- $\gamma = 0$: Only immediate rewards matter (myopic)
- $\gamma = 1$: All future rewards equally important
- Typical: $\gamma = 0.9$ or $0.99$

**Goal:** Find policy $\pi(s)$ that maximizes expected cumulative discounted reward.

---

## Q7. Bayesian Learning: MAP vs. MLE

**Question:**  
How does Maximum A Posteriori (MAP) estimation differ from Maximum Likelihood Estimation (MLE)? When are they equivalent?

**Answer:**

Both estimate parameters $\theta$, but differ in what they optimize:

**MLE (Maximum Likelihood Estimation):**  
Finds parameters $\theta$ that ==maximize the likelihood== of the observed data:

$\hat{\theta}_{\text{MLE}} = \arg\max_\theta P(D|\theta)$

- Relies solely on observed data
- Treats $\theta$ as fixed (frequentist view)
- Equivalent to minimizing empirical risk

**MAP (Maximum A Posteriori):**  
Finds parameters $\theta$ that ==maximize the posterior probability==:

$\hat{\theta}_{\text{MAP}} = \arg\max_\theta P(\theta|D)$

Using Bayes' Theorem: $P(\theta|D) = \frac{P(D|\theta) \cdot P(\theta)}{P(D)} \propto P(D|\theta) \cdot P(\theta)$

$\hat{\theta}_{\text{MAP}} = \arg\max_\theta [P(D|\theta) \cdot P(\theta)]$

- Includes a **Prior** $P(\theta)$ (our belief before seeing data)
- Treats $\theta$ as random variable (Bayesian view)
- Prior acts as regularization

**Equivalence:**  
MAP becomes MLE when we assume a **Uniform Prior** $P(\theta) = \text{const}$:

$\hat{\theta}_{\text{MAP}} = \arg\max_\theta [P(D|\theta) \cdot \text{const}] = \arg\max_\theta P(D|\theta) = \hat{\theta}_{\text{MLE}}$

**Connection to Regularization:**

- MAP with **Gaussian Prior** $P(\theta) \sim \mathcal{N}(0, \sigma^2)$ is equivalent to **L2 regularization** (Ridge)
- MAP with **Laplace Prior** $P(\theta) \sim \text{Laplace}(0, b)$ is equivalent to **L1 regularization** (Lasso)

**In log space:** $\log P(\theta|D) = \log P(D|\theta) + \log P(\theta) - \log P(D)$

---

## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q8. Graph-Based Semi-Supervised Learning

**Question:**  
Explain the intuition behind "Label Propagation" in graph-based learning.

**Answer:**

**Core Idea:** Use the structure of data (similarity graph) to spread labels from labeled to unlabeled points.

**Graph Construction:**

- **Nodes:** Data points (both labeled and unlabeled)
- **Edges:** Connect similar points (e.g., k-nearest neighbors)
- **Edge Weights:** $w_{ij} = \exp(-||x_i - x_j||^2 / 2\sigma^2)$ (similarity)

**Assumptions:**

1. **Smoothness:** ==Points connected by an edge likely have the same label==
2. **Cluster:** Points in the same cluster likely have the same label
3. **Manifold:** Data lies on a low-dimensional manifold

**Label Propagation Algorithm:**

1. **Initialize:** Labeled nodes get their true labels, unlabeled nodes get uniform distribution
    
2. **Propagate:** Each node adopts a ==weighted average of its neighbors' labels==: $Y_i^{(t+1)} = \frac{\sum_{j \in N(i)} w_{ij} Y_j^{(t)}}{\sum_{j \in N(i)} w_{ij}}$
    
3. **Clamp:** Keep labeled nodes fixed at their true labels
    
4. **Iterate:** Repeat until convergence
    

**Effect:** Labels "flow" through high-density regions via edges. If unlabeled point has many labeled neighbors of "Class A", it becomes "Class A".

**Matrix Form:** $\mathbf{Y}^{(t+1)} = \alpha \mathbf{S} \mathbf{Y}^{(t)} + (1-\alpha) \mathbf{Y}^{(0)}$

where $\mathbf{S}$ is the normalized similarity matrix.

**Advantages:**

- Leverages data structure naturally
- Works well when clusters are well-separated
- Can handle complex decision boundaries

---

## Q9. Q-Learning (Off-Policy vs. On-Policy)

**Question:**  
Why is Q-Learning called an "Off-Policy" algorithm?

**Answer:**

**On-Policy (e.g., SARSA):**  
The agent learns the value of the ==policy it is currently executing== (including its exploration steps).

**SARSA Update:** $Q(s,a) \leftarrow Q(s,a) + \alpha [R + \gamma Q(s', a') - Q(s,a)]$

where $a'$ is the action **actually taken** in state $s'$ (could be random due to ε-greedy).

**Off-Policy (Q-Learning):**  
The agent learns the value of the **Optimal Policy** (greedy), ==regardless of the policy it is using to explore==.

**Q-Learning Update:** $Q(s,a) \leftarrow Q(s,a) + \alpha \left[R + \gamma \max_{a'} Q(s', a') - Q(s,a)\right]$

Note the $\max_{a'}$ term: it assumes we take the ==best action== in the next state, even if we actually explore randomly.

**Key Difference:**

- **SARSA:** "I took action $a$ in $s$, got reward $R$, then took action $a'$ in $s'$. How good was that sequence?"
- **Q-Learning:** "I took action $a$ in $s$, got reward $R$, reached $s'$. What's the best I could do from $s'$?"

**Why "Off-Policy"?**  
The policy being **evaluated** (optimal/greedy) is different from the policy being **followed** (ε-greedy exploration).

**Advantage:** Can learn optimal policy while exploring aggressively. Converges faster in practice.

**Disadvantage:** Higher variance, can be unstable with function approximation.

---

## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q10. Online Gradient Descent (Perceptron)

**Question:** Write the algorithm for Online Gradient Descent for a linear model.

**Pseudocode:**

```python
# Initialize
w = zeros(n_features)  # Weight vector
learning_rate = 0.01

# Process streaming data
For t = 1, 2, 3, ... (until stream ends):
    # Receive new instance
    Receive (x_t, y_t)
    
    # 1. Make Prediction
    y_pred = sign(dot(w, x_t))  # For classification
    # OR y_pred = dot(w, x_t) for regression
    
    # 2. Compute Loss/Error
    error = y_t - y_pred
    
    # 3. Update Immediately (no batch accumulation)
    # For classification (Perceptron):
    If y_pred != y_t:
        w = w + learning_rate * y_t * x_t
    
    # For regression (SGD):
    # w = w - learning_rate * (y_pred - y_t) * x_t
    
    # Optional: Decay learning rate
    learning_rate = learning_rate * decay_factor
```

**Perceptron Convergence Theorem:**  
If data is linearly separable, the perceptron algorithm converges in finite steps (mistake bound).

**Variants:**

- **Averaged Perceptron:** Keep running average of weights (more stable)
- **Passive-Aggressive:** Adaptive learning rate based on loss magnitude

---

## Q11. Q-Learning Algorithm

**Question:** Write the update loop for Q-Learning.

**Pseudocode:**

```python
Function QLearning(Environment, NumEpisodes, alpha, gamma, epsilon):
    # Initialize Q-table (or neural network)
    Q = zeros(num_states, num_actions)
    
    For episode = 1 to NumEpisodes:
        # Initialize environment
        s = Environment.reset()
        
        Repeat (for each step of episode):
            # 1. Choose action using epsilon-greedy policy
            If random() < epsilon:
                a = random_action()  # Exploration
            Else:
                a = argmax_a(Q[s, :])  # Exploitation
            
            # 2. Take action, observe reward and next state
            s_next, r, done = Environment.step(a)
            
            # 3. Q-Learning Update (Bellman Equation)
            # Update towards: Reward + discounted value of best next action
            target = r + gamma * max(Q[s_next, :])
            Q[s, a] = Q[s, a] + alpha * (target - Q[s, a])
            
            # 4. Move to next state
            s = s_next
            
            # Optional: Decay epsilon (explore less over time)
            epsilon = epsilon * decay_factor
            
        Until s is terminal (done == True)
    
    Return Q

# Extract Policy from Q-table
Function ExtractPolicy(Q):
    policy = {}
    For each state s:
        policy[s] = argmax_a(Q[s, :])
    Return policy
```

**Key Equation (Bellman Optimality):** 

$Q^\pi(s, a) = \mathbb{E}_\pi [R \ + \  \gamma \max{\alpha'}Q^*(s'a')]$

**Hyperparameters:**

- $\alpha$ (learning rate): How much to update Q-values (0.1 - 0.5)
- $\gamma$ (discount factor): Importance of future rewards (0.9 - 0.99)
- $\epsilon$ (exploration rate): Probability of random action (start 1.0, decay to 0.1)

---

# Unit 6: Recent Trends & Advanced Architectures

## 🟢 Section A: Short Answer / Definitions (2-3 Marks)

## Q1. What is "Self-Supervised Learning"?

**Answer:**  
It is a learning paradigm where the model ==generates its own labels from the data itself==, without human annotation. It's a form of unsupervised learning that creates supervised tasks.

**Key Idea:** Design a ==pretext task== where labels are automatically generated, then transfer learned representations to downstream tasks.

**Examples:**

1. **NLP (BERT):** Mask a word and predict it
    - Input: "The cat sat on the `[MASK]`"
    - Label: "mat" (automatically generated)
2. **Computer Vision (SimCLR):** Predict if two augmented versions of the same image match
    - Crop, rotate, color jitter same image → Positive pair
    - Different images → Negative pair
3. **Video:** Predict future frames from past frames

**Benefit:** Allows training on ==massive unlabeled datasets== (billions of images/documents), learning general representations that transfer to many tasks.

**Difference from Unsupervised:** Creates supervisory signal from data structure, not just finding patterns.

---

## Q2. Define "Contrastive Learning".

**Answer:**  
A technique where the model learns representations by ==comparing pairs of samples==, pulling similar samples together and pushing dissimilar samples apart in embedding space.

**Core Principle:**

- **Positive Pair:** Two augmented versions of the _same_ image/text. Model pulls representations ==close together==.
- **Negative Pair:** Two _different_ images/text. Model pushes representations ==far apart==.

**Loss Function (InfoNCE):** $\mathcal{L} = -\log \frac{\exp(\text{sim}(z_i, z_j^+)/\tau)}{\sum_{k=1}^{2N} \mathbb{1}_{k \neq i} \exp(\text{sim}(z_i, z_k)/\tau)}$

where $z_i, z_j^+$ are positive pair, $\tau$ is temperature.

**Objective:** Maximize agreement between positive pairs, minimize it for negative pairs.

**Popular Methods:**

- **SimCLR:** Simple framework for contrastive learning
- **MoCo:** Momentum Contrast (uses momentum encoder)
- **CLIP:** Contrastive Language-Image Pre-training

**Why it works:** Forces model to learn features that are invariant to augmentations but discriminative between different samples.

---

## Q3. What is the key difference between a CNN and a Vision Transformer (ViT)?

**Answer:**

**CNN:**

- Processes images using **local** filters (convolutions) that slide over the image
- Has built-in ==inductive biases==: translation invariance, locality
- Hierarchical: Early layers detect edges, later layers detect objects
- Receptive field grows gradually with depth
- ==Parameter efficient== (due to weight sharing)

**Vision Transformer (ViT):**

- Splits image into fixed-size **patches** (e.g., $16 \times 16$)
- Linearly embeds patches and processes as a ==sequence using Self-Attention==
- Has ==global receptive fields from layer 1== (every patch can attend to every other)
- No built-in spatial inductive bias (must learn from data)
- Requires ==more data to train== (less inductive bias = needs more examples)
- More computationally expensive ($O(n^2)$ for $n$ patches)

**Performance:**

- CNNs: Better on small datasets (ImageNet-1K)
- ViTs: Better on large datasets (ImageNet-21K, JFT-300M)
- Hybrid models (e.g., Swin Transformer) combine best of both

**Architecture:**

```
Image → Patch Embedding → [Transformer Encoder]×L → Classification Head
```

---

## 🟡 Section B: Core Algorithms & Theory (5-10 Marks)

## Q4. Transformer Architecture: Encoder vs. Decoder

**Question:**  
Transformers (like in BERT and GPT) use Encoder and Decoder blocks. Explain the difference in their attention masks and use cases.

**Answer:**

Both use self-attention but differ in ==masking strategy==:

**1. Encoder (e.g., BERT, ViT):**

**Mechanism:** Uses **Bidirectional** Self-Attention. Every token can attend to ==every other token== (left and right) simultaneously.

**Attention Matrix:** No masking (full attention)

```
       t1  t2  t3  t4
t1     ✓   ✓   ✓   ✓
t2     ✓   ✓   ✓   ✓
t3     ✓   ✓   ✓   ✓
t4     ✓   ✓   ✓   ✓
```

**Use Cases:**

- Text Classification
- Sentiment Analysis
- Named Entity Recognition
- Question Answering (understanding context)
- Image Classification (ViT)

**Training:** Typically uses Masked Language Modeling (predict masked tokens).

**2. Decoder (e.g., GPT, Transformer-XL):**

**Mechanism:** Uses **Masked (Causal)** Self-Attention. A token can only attend to tokens that came _before_ it (to the left).

**Attention Matrix:** Upper triangle masked

```
       t1  t2  t3  t4
t1     ✓   ✗   ✗   ✗
t2     ✓   ✓   ✗   ✗
t3     ✓   ✓   ✓   ✗
t4     ✓   ✓   ✓   ✓
```

**Use Cases:**

- Text Generation
- Language Modeling
- Next Word Prediction
- Code Generation
- Dialogue Systems

**Training:** Uses Autoregressive Language Modeling (predict next token given previous).

**3. Encoder-Decoder (e.g., T5, BART):**

Combines both:

- **Encoder:** Bidirectional attention on input
- **Decoder:** Causal attention on output, plus **cross-attention** to encoder outputs

**Use Cases:**

- Machine Translation
- Summarization
- Question Answering with generation

**Key Difference:** ==Masking determines what information flows where==, enabling different capabilities.

---
## Q5. Diffusion Models

**Question:**  
Explain the "Forward" and "Reverse" processes in Diffusion Models.

**Answer:**

Diffusion Models generate images by learning to ==reverse a noising process==.

**Forward Process (Diffusion/Noising):**  
Gradually add Gaussian **noise** to an image over $T$ steps until it becomes pure noise.

$x_0 \to x_1 \to x_2 \to \cdots \to x_T \text{ (Pure Noise)}$

**Mathematical formulation:** $q(x_t | x_{t-1}) = \mathcal{N}(x_t; \sqrt{1-\beta_t} x_{t-1}, \beta_t I)$

where $\beta_t$ is the noise schedule (increases with $t$).

**Closed form (nice property):** $q(x_t | x_0) = \mathcal{N}(x_t; \sqrt{\bar{\alpha}_t} x_0, (1-\bar{\alpha}_t) I)$

This process is ==fixed (no learning)==. It's a Markov chain that destroys information.

**Reverse Process (Denoising):**  
The neural network learns to **predict and remove the noise** added at each step, effectively reconstructing the image from pure noise.

$x_T \to x_{T-1} \to \cdots \to x_1 \to x_0 \text{ (Generated Image)}$

**Network learns:** $p_\theta(x_{t-1} | x_t) = \mathcal{N}(x_{t-1}; \mu_\theta(x_t, t), \Sigma_\theta(x_t, t))$

In practice, network predicts ==the noise== $\epsilon_\theta(x_t, t)$:

**Training Loss:** $\mathcal{L} = \mathbb{E}_{t, x_0, \epsilon} \left[ ||\epsilon - \epsilon_\theta(x_t, t)||^2 \right]$

**Sampling (Generation):**

1. Start with random noise $x_T \sim \mathcal{N}(0, I)$
2. For $t = T$ down to $1$:
    - Predict noise: $\hat{\epsilon} = \epsilon_\theta(x_t, t)$
    - Remove predicted noise: $x_{t-1} = \frac{1}{\sqrt{\alpha_t}}(x_t - \frac{1-\alpha_t}{\sqrt{1-\bar{\alpha}_t}}\hat{\epsilon}) + \sigma_t z$

**Advantages:**

- High-quality samples
- Stable training (no mode collapse like GANs)
- Can condition on text (DALL-E 2, Stable Diffusion)

---
## Q6. Representation Learning with Autoencoders

**Question:**  
Describe the structure of an Autoencoder and the role of the "Bottleneck".

**Answer:**

**Structure:**

An Autoencoder consists of two parts that learn to compress and reconstruct data:

1. **Encoder ($f$):** Compresses input $x$ into a lower-dimensional ==latent vector== $z$ $z = f_\phi(x)$
    
    Example: $784$ (28×28 image) → $32$ (latent code)
    
2. **Decoder ($g$):** Reconstructs input from latent vector $\hat{x} = g_\theta(z)$
    
    Example: $32$ (latent code) → $784$ (reconstructed image)
    

**Training Objective:** Minimize reconstruction error $\mathcal{L} = ||x - \hat{x}||^2 = ||x - g_\theta(f_\phi(x))||^2$

**Bottleneck (Latent Space):**  
The latent layer $z$ has ==fewer dimensions== than input $x$.

**Role:**

- Forces the model to learn the most **salient features** (compressed representation)
- Acts as ==information bottleneck==: Only most important info passes through
- Creates a meaningful low-dimensional embedding of data
- If bottleneck is too wide → model memorizes (identity function)
- If bottleneck is too narrow → poor reconstruction

**Types:**

1. **Vanilla Autoencoder:** Simple compression
    
2. **Denoising Autoencoder (DAE):**
    
    - Input: Corrupted $\tilde{x}$ (add noise)
    - Output: Clean $x$
    - Forces robustness to noise
3. **Variational Autoencoder (VAE):**
    
    - Latent $z \sim \mathcal{N}(\mu, \sigma^2)$ (probabilistic)
    - Can generate new samples by sampling $z$
    - Loss: Reconstruction + KL divergence
4. **Sparse Autoencoder:**
    
    - Adds sparsity penalty on $z$
    - Forces most activations to be zero

**Applications:**

- Dimensionality reduction
- Anomaly detection (high reconstruction error = anomaly)
- Pre-training for supervised tasks
- Generative modeling (VAE)

---
## 🔴 Section C: The "Overlooked" Topics (High Value)

## Q7. Vision Transformers (ViT): Patch Embedding

**Question:**  
How does a Vision Transformer handle a 2D image as a sequence?

**Answer:**

ViT transforms an image into a sequence of patch embeddings through several steps:

**Step 1: Patching**  
Divide image into fixed-size patches (e.g., $16 \times 16$ pixels).

Image: $H \times W \times C$ → $N$ patches of size $P \times P \times C$

Number of patches: $N = \frac{H \times W}{P^2}$

Example: $224 \times 224 \times 3$ image with $16 \times 16$ patches → $196$ patches

**Step 2: Flattening**  
Each patch is flattened into a 1D vector.

Patch: $P \times P \times C$ → vector of length $P^2 \cdot C$

Example: $16 \times 16 \times 3 = 768$ dimensions

**Step 3: Linear Projection (Patch Embedding)**  
Each flattened patch is multiplied by a ==learnable projection matrix== $E$ to create embeddings.

$z_i = E \cdot \text{flatten}(\text{patch}_i)$

where $E \in \mathbb{R}^{D \times (P^2 \cdot C)}$ and $D$ is the embedding dimension (e.g., 768).

**Step 4: Add `[CLS]` Token**  
Prepend a learnable ==classification token== (similar to BERT).

$z_0 = \text{[CLS]}$

This token's final state is used for classification.

**Step 5: Positional Embedding**  
Since transformers have ==no notion of order/position==, add learnable ==position embeddings== to retain spatial information.

$z_i^{\text{final}} = z_i + E_{\text{pos}}^i$

where $E_{\text{pos}} \in \mathbb{R}^{(N+1) \times D}$ is learned during training.

**Final Sequence:** $[\text{[CLS]}, \text{Patch}_1, \text{Patch}_2, \ldots, \text{Patch}_N] + \text{PositionalEmbedding}$

**Result:** The image is now a ==sequence of vectors==, just like words in a sentence, ready for transformer processing!

**Feed to Transformer:** $\text{TransformerEncoder}([z_0, z_1, \ldots, z_N])$

**Classification:** Use final state of `[CLS]` token for prediction.

---
## Q8. Large Language Models (LLMs): Fine-Tuning approaches

**Question:**  
What is "Instruction Tuning" in the context of LLMs?

**Answer:**

LLMs are trained in multiple stages to become useful assistants:

**Stage 1: Pre-training**  
The model learns to predict the next word on ==massive text corpora== (billions of tokens).

- Objective: Language modeling $P(w_t | w_1, \ldots, w_{t-1})$
- Data: Books, web pages, code (unlabeled)
- Result: Model learns grammar, facts, reasoning, but just "completes text"

**Stage 2: Instruction Tuning (Supervised Fine-Tuning)**  
The model is fine-tuned on a dataset of **(Instruction, Output)** pairs.

**Examples:**

```
Instruction: "Translate this to French: 'Hello world'"
Output: "Bonjour le monde"

Instruction: "Summarize this article: [text]"
Output: [summary]

Instruction: "Write a poem about spring"
Output: [poem]
```

**Goal:** Align the model's behavior with ==user intent==. Teach it to ==follow instructions== rather than just complete text.

**Training:** Standard supervised learning on instruction-following datasets:

- Flan (Google)
- InstructGPT dataset (OpenAI)
- Alpaca (Stanford)

**Stage 3: RLHF (Reinforcement Learning from Human Feedback) - Optional**

1. Collect human preferences: "Output A is better than Output B"
2. Train a reward model to predict human preferences
3. Use RL (PPO) to optimize LLM to maximize reward model score

**Result:** Model becomes helpful, harmless, and honest (like ChatGPT).

**Key Difference:**

- Pre-training: "The capital of France is" → "Paris"
- Instruction-tuned: "What is the capital of France?"

---
## 🔵 Section D: Algorithmic Pseudocode (Exam Ready)

## Q9. Self-Attention Mechanism (Simplified)

**Question:** Write the core equation/steps for Scaled Dot-Product Attention.

**Pseudocode:**

```python
Function ScaledDotProductAttention(Query, Key, Value):
    """
    Query: (batch, seq_len, d_k)
    Key: (batch, seq_len, d_k)
    Value: (batch, seq_len, d_v)
    """
    
    # 1. Calculate Similarity Scores (dot product)
    # Q * K^T gives pairwise similarity between all positions
    Scores = MatMul(Query, Transpose(Key))  # (batch, seq_len, seq_len)
    
    # 2. Scale by sqrt(d_k)
    # Prevents scores from becoming too large (softmax saturation)
    d_k = Dimension_of_Key_vectors
    ScaledScores = Scores / Sqrt(d_k)
    
    # 3. Apply Mask (optional, for decoder)
    # Mask future positions by setting to -infinity
    If Mask is provided:
        ScaledScores = ScaledScores + Mask  # Mask = -inf for invalid positions
    
    # 4. Softmax to get Attention Weights (probabilities)
    # Each row sums to 1 (probability distribution over positions)
    AttentionWeights = Softmax(ScaledScores, axis=-1)  # (batch, seq_len, seq_len)
    
    # 5. Weighted Sum of Values
    # Each position gets a weighted combination of all Value vectors
    Output = MatMul(AttentionWeights, Value)  # (batch, seq_len, d_v)
    
    Return Output, AttentionWeights

# Multi-Head Attention
Function MultiHeadAttention(Q, K, V, num_heads):
    d_model = Q.shape[-1]
    d_k = d_model // num_heads
    
    # Split into multiple heads
    # Each head learns different aspects of relationships
    For i from 1 to num_heads:
        Q_head_i = Linear_i(Q)  # Project to d_k dimensions
        K_head_i = Linear_i(K)
        V_head_i = Linear_i(V)
        
        head_i = ScaledDotProductAttention(Q_head_i, K_head_i, V_head_i)
    
    # Concatenate all heads
    MultiHead = Concatenate([head_1, head_2, ..., head_num_heads])
    
    # Final linear projection
    Output = Linear_output(MultiHead)
    
    Return Output
```

**Key Equations:**

$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$

**Why scaling?** Without $\sqrt{d_k}$, dot products grow large for high dimensions, pushing softmax into regions with vanishing gradients.

**Intuition:**

- **Query:** "What am I looking for?"
- **Key:** "What do I offer?"
- **Value:** "What information do I carry?"
- Attention score = how relevant each position is to current position

---

## Q10. Variational Autoencoder (VAE) - Conceptual Algorithm

**Question:** Explain the training process and sampling from a VAE.

**Answer:**

**VAE Architecture:**

Unlike standard autoencoders, VAE learns a ==probabilistic== latent space that enables generation.

**Training Process:**

```python
Function TrainVAE(Data, Epochs):
    # Encoder outputs mean and log-variance
    Encoder_mean = NeuralNet_mu(x)
    Encoder_logvar = NeuralNet_sigma(x)
    
    For each training example x:
        # 1. Encode to latent distribution parameters
        mu, log_var = Encoder(x)
        
        # 2. Reparameterization Trick (allows backprop)
        # Sample from N(mu, sigma^2) in a differentiable way
        epsilon = SampleNormal(0, 1)  # Standard normal
        z = mu + exp(0.5 * log_var) * epsilon
        
        # 3. Decode
        x_reconstructed = Decoder(z)
        
        # 4. Compute Loss (two terms)
        # a) Reconstruction Loss (how well decoded matches input)
        reconstruction_loss = MSE(x, x_reconstructed)
        # OR: BinaryCrossEntropy for binary data
        
        # b) KL Divergence (regularization, keeps latent close to N(0,1))
        # Forces encoder to output distributions close to standard normal
        KL_loss = -0.5 * Sum(1 + log_var - mu^2 - exp(log_var))
        
        # Total Loss
        total_loss = reconstruction_loss + beta * KL_loss
        
        # 5. Backpropagate and Update weights
        Backpropagate(total_loss)
        UpdateWeights()
    
    Return TrainedEncoder, TrainedDecoder

Function GenerateNewSample(Decoder):
    # Sample from prior (standard normal)
    z = SampleNormal(0, 1, latent_dim)
    
    # Decode to get new sample
    x_new = Decoder(z)
    
    Return x_new
```

**Mathematical Formulation:**

**ELBO (Evidence Lower BOund) - What we maximize:** $\mathcal{L} = \mathbb{E}_{q(z|x)}[\log p(x|z)] - D_{KL}(q(z|x) || p(z))$

**Loss function (what we minimize):** $\mathcal{L}_{\text{VAE}} = ||x - \hat{x}||^2 + \beta \cdot D_{KL}(q(z|x) || \mathcal{N}(0, I))$

where:

- First term: Reconstruction accuracy
- Second term: KL divergence between learned distribution and prior
- $\beta$: Weight (β-VAE uses $\beta > 1$ for disentanglement)

**KL Divergence (closed form for Gaussians):** $D_{KL} = -\frac{1}{2}\sum_{j=1}^J (1 + \log(\sigma_j^2) - \mu_j^2 - \sigma_j^2)$

**Reparameterization Trick:**  
Instead of sampling $z \sim \mathcal{N}(\mu, \sigma^2)$ directly (non-differentiable), we sample: $z = \mu + \sigma \odot \epsilon, \quad \epsilon \sim \mathcal{N}(0, I)$

This moves randomness to $\epsilon$, making $z$ differentiable w.r.t. $\mu, \sigma$.

**Applications:**

- Image generation
- Anomaly detection
- Latent space interpolation
- Disentangled representations (β-VAE)

---

## Additional Important Concepts & Tips

### Cross-Validation Best Practices

**When to use:**

- Small to medium datasets
- Model selection and hyperparameter tuning
- Assessing model stability

**Stratified K-Fold (Classification):**

```python
Function StratifiedKFold(Data, k):
    # Ensures each fold has same class distribution as full dataset
    For each class c:
        class_samples = Data[Data.label == c]
        Split class_samples into k equal parts
        Distribute parts across k folds
    
    Return k folds with balanced class distribution
```

**Time Series Split:**

```python
Function TimeSeriesSplit(Data, k):
    # Respects temporal order (no future data in training)
    n = len(Data)
    For i from 1 to k:
        train_end = n * i / (k+1)
        test_end = n * (i+1) / (k+1)
        
        TrainSet = Data[0 : train_end]
        TestSet = Data[train_end : test_end]
        
        Yield TrainSet, TestSet
```

---

### Gradient Descent Variants Comparison

**1. Batch Gradient Descent:**

- Uses entire dataset per update
- **Pros:** Stable convergence, accurate gradient
- **Cons:** Slow, memory intensive, stuck in local minima
- Update: $\theta := \theta - \eta \nabla J(\theta)$ where gradient computed over ALL data

**2. Stochastic Gradient Descent (SGD):**

- Uses single sample per update
- **Pros:** Fast, can escape local minima (noise helps)
- **Cons:** Noisy updates, oscillates around minimum
- Update: $\theta := \theta - \eta \nabla J(\theta; x^{(i)}, y^{(i)})$

**3. Mini-Batch Gradient Descent:**

- Uses small batch (32, 64, 128) per update
- **Pros:** Balance between speed and stability, leverages vectorization
- **Cons:** Requires tuning batch size
- Update: $\theta := \theta - \eta \nabla J(\theta; X_{\text{batch}}, Y_{\text{batch}})$

**4. Momentum:**

- Accumulates velocity from previous gradients
- Helps accelerate in consistent directions $v_t = \beta v_{t-1} + \eta \nabla J(\theta)$ $\theta := \theta - v_t$

**5. Adam (Adaptive Moment Estimation):**

- Combines momentum + adaptive learning rates
- Most popular in deep learning $m_t = \beta_1 m_{t-1} + (1-\beta_1)\nabla J(\theta)$ $v_t = \beta_2 v_{t-1} + (1-\beta_2)(\nabla J(\theta))^2$ $\theta := \theta - \eta \frac{m_t}{\sqrt{v_t} + \epsilon}$

---

### Bias-Variance Trade-off Visualization

**Decomposition of Expected Error:** $\mathbb{E}[(y - \hat{f}(x))^2] = \text{Bias}^2 + \text{Variance} + \text{Irreducible Error}$

**Understanding:**

- **High Bias, Low Variance:** Underfitting (too simple, misses patterns)
    - Example: Linear model on curved data
    - Fix: More complex model, more features
- **Low Bias, High Variance:** Overfitting (too complex, memorizes noise)
    - Example: Deep tree on small dataset
    - Fix: Regularization, more data, ensemble
- **Sweet Spot:** Balanced complexity for optimal generalization

**Ensemble Effects:**

- **Bagging:** Reduces variance (averages high-variance models)
- **Boosting:** Reduces bias (corrects errors sequentially)
- **Stacking:** Can reduce both if done correctly

---
### Confusion Matrix Deep Dive

For binary classification with classes {Positive, Negative}:

```
                Predicted
              Pos    Neg
Actual  Pos   TP     FN
        Neg   FP     TN
```

**Metrics:**

1. **Accuracy:** $\frac{TP + TN}{TP + TN + FP + FN}$
    
    - Misleading for imbalanced data
2. **Precision:** $\frac{TP}{TP + FP}$
    
    - Of predicted positives, how many are correct?
    - Use when FP is costly
3. **Recall (Sensitivity):** $\frac{TP}{TP + FN}$
    
    - Of actual positives, how many did we find?
    - Use when FN is costly
4. **Specificity:** $\frac{TN}{TN + FP}$
    
    - Of actual negatives, how many did we correctly identify?
5. **F1-Score:** $\frac{2 \cdot \text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$
    
    - Harmonic mean, good for imbalanced classes
6. **ROC-AUC:** Area under ROC curve (TPR vs FPR at different thresholds)
    
    - Measures ranking quality
    - 0.5 = random, 1.0 = perfect

**Choosing Threshold:**

- Default: 0.5
- High Recall: Lower threshold (classify more as positive)
- High Precision: Higher threshold (only very confident positives)

---
### Regularization Techniques Summary

**For Linear Models:**

1. **L1 (Lasso):** $\lambda \sum |w_i|$ → Sparse solutions
2. **L2 (Ridge):** $\lambda \sum w_i^2$ → Small weights
3. **Elastic Net:** $\lambda_1 \sum |w_i| + \lambda_2 \sum w_i^2$ → Both effects

**For Neural Networks:**

1. **Dropout:** Randomly drop neurons during training
2. **Batch Normalization:** Normalize layer inputs
3. **Early Stopping:** Stop when validation error increases
4. **Data Augmentation:** Artificially increase training data
5. **Weight Decay:** L2 penalty in optimizer
6. **Label Smoothing:** Soften one-hot labels (0.9 instead of 1.0)

**For Trees:**

1. **Max Depth:** Limit tree depth
2. **Min Samples Split:** Require minimum samples to split
3. **Max Features:** Random subset at each split (Random Forest)

---
### Important Activation Functions

**1. Sigmoid:** $\sigma(x) = \frac{1}{1 + e^{-x}}$

- Output: (0, 1)
- Use: Binary classification output, gates in LSTM
- Problem: Vanishing gradients for large |x|

**2. Tanh:** $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$

- Output: (-1, 1)
- Use: Hidden layers in RNNs
- Better than sigmoid (zero-centered)

**3. ReLU:** $\text{ReLU}(x) = \max(0, x)$

- Output: `[0, ∞)`
- Use: Most common for deep networks
- **Pros:** Fast, no vanishing gradient for x>0
- **Cons:** Dead neurons (x<0 always outputs 0)

**4. Leaky ReLU:** $\text{LeakyReLU}(x) = \max(\alpha x, x)$, $\alpha=0.01$

- Fixes dead ReLU problem
- Small gradient for negative values

**5. ELU:** $\text{ELU}(x) = \begin{cases} x & x > 0 \ \alpha(e^x - 1) & x \leq 0 \end{cases}$

- Smoother than ReLU, mean closer to zero

**6. Softmax:** $\text{softmax}(x_i) = \frac{e^{x_i}}{\sum_j e^{x_j}}$

- Output: Probability distribution (sums to 1)
- Use: Multi-class classification output

**7. Swish/SiLU:** $\text{Swish}(x) = x \cdot \sigma(x)$

- Smooth, non-monotonic
- Used in modern architectures (EfficientNet)

---
### Final Exam Tips

**Short Questions (2-3 marks):**

- ==Define key terms precisely== (1 sentence)
- Give one concrete example
- Mention use case or limitation
- Time: 2-3 minutes per question

**Medium Questions (5-10 marks):**

- ==Write algorithm or derive equation==
- Explain intuition behind math
- Compare alternatives (pros/cons)
- Draw diagram if helpful
- Time: 8-12 minutes per question

**Long Questions (15 marks):**

- Complete algorithm with pseudocode
- Explain each step
- Analyze complexity
- Discuss variants and applications
- Time: 20-25 minutes per question

**Strategy:**

1. Read all questions first, plan time allocation
2. Answer easiest questions first (build confidence)
3. Use ==bullet points== for clarity
4. ==Highlight keywords== (e.g., "greedy", "convex", "sparse")
5. If stuck, write what you know and move on
6. Save 10 minutes to review

**Common Mistakes to Avoid:**

- Confusing bias/variance
- Wrong regularization effect (L1 vs L2)
- Forgetting activation functions in backprop
- Mixing up on-policy/off-policy RL
- Not normalizing/standardizing data
- Ignoring imbalanced class distribution

**Key Formula Sheet - Memorize These:**

1. **Entropy:** $H(S) = -\sum p_i \log_2(p_i)$
2. **Normal Equation:** $\theta = (X^TX)^{-1}X^Ty$
3. **Logistic Sigmoid:** $\sigma(z) = \frac{1}{1+e^{-z}}$
4. **Cross-Entropy Loss:** $L = -\sum y \log(\hat{y})$
5. **Softmax:** $\frac{e^{z_i}}{\sum_j e^{z_j}}$
6. **Attention:** $\text{softmax}(\frac{QK^T}{\sqrt{d_k}})V$
7. **Conv Output:** $\frac{W - F + 2P}{S} + 1$
8. **F1-Score:** $\frac{2PR}{P+R}$
9. **Bellman:** $Q(s,a) = R + \gamma \max_{a'} Q(s',a')$
10. **KL Divergence:** $-\frac{1}{2}\sum(1 + \log\sigma^2 - \mu^2 - \sigma^2)$

---

