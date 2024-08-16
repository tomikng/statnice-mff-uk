---
tags:
  - databaze_a_web
  - web
  - tomas
dg-publish: true
---
Poznámky na přípravu na zkoušku z RS 2023/2024
## **Collaborative Filtering (CF)** (Lecture 1)
---

### **Pure CF Approaches**
- **Input:** User-item rating matrix
- **Output Types:**
  - Numerical prediction of user preference
  - Top-N list of recommended items

---

### **User-based Nearest-Neighbor Collaborative Filtering**
- **Technique:**
  1. Given an "active user" (Alice) and an item not yet seen by Alice.
  2. Find a set of users (peers/nearest neighbors) who liked the same items as Alice in the past and who have rated the item.
  3. Use the average of their ratings to predict if Alice will like the item.
  4. Recommend the best-rated items Alice has not seen.
- **Assumption:** User preferences remain stable over time.

---

### **Measuring User Similarity**
1. **Pearson Correlation:**
   $$
   \text{sim}(u, v) = \frac{\sum_{i \in I_{uv}} (r_{ui} - \bar{r}_u)(r_{vi} - \bar{r}_v)}{\sqrt{\sum_{i \in I_{uv}} (r_{ui} - \bar{r}_u)^2} \sqrt{\sum_{i \in I_{uv}} (r_{vi} - \bar{r}_v)^2}}
   $$
   - $r_{ui}$:  Rating of user $u$ for item $i$
   - $\bar{r}_u$: Average rating of user  $u$ 
   - $I_{uv}$: Set of items rated by both  $u$  and  $v$ 

2. **Jaccard Similarity:**
   $$
   J(A, B) = \frac{|A \cap B|}{|A \cup B|}
   $$ ^85f4f5
   - $A$ and $B$: Sets of items rated by users ^3a0177

---

### **Making Predictions**
- **Prediction Formula:**
  
  $$\hat{r}_{ui} = \bar{r}_u + \frac{\sum_{v \in N(u)} \text{sim}(u, v) (r_{vi} - \bar{r}_v)}{\sum_{v \in N(u)} |\text{sim}(u, v)|}$$
  
  -  $\hat{r}_{ui}$ : Predicted rating for user  $u$  for item  $i$ 
  -  $\bar{r}_u$ : Average rating of user  $u$ 
  -  $N(u)$ : Set of neighbors of user  $u$ 
  -  $\text{sim}(u, v)$ : Similarity between users  $u$  and  $v$ 

- **Improving Metrics:**
  - **Variance Weighting:**
    
    $$\text{weight} = \frac{\text{variance}}{\text{number of co-rated items}}$$
    

---

### **Memory-based vs. Model-based Approaches**
- **Memory-based:** Uses the rating matrix directly.
- **Model-based:** Builds models from data using techniques like matrix factorization.

---

### **Item-based Collaborative Filtering**
- **Technique:**
  1. Use the similarity between items to make predictions.
  2. Cosine Similarity:
     
     $$\text{cosine}(a, b) = \frac{\sum_{u} r_{ua} r_{ub}}{\sqrt{\sum_{u} r_{ua}^2} \sqrt{\sum_{u} r_{ub}^2}}$$
     
  3. Adjusted Cosine Similarity:
     
     $$\text{adjusted\_cosine}(a, b) = \frac{\sum_{u} (r_{ua} - \bar{r}_u) (r_{ub} - \bar{r}_u)}{\sqrt{\sum_{u} (r_{ua} - \bar{r}_u)^2} \sqrt{\sum_{u} (r_{ub} - \bar{r}_u)^2}}$$
     

---

### **Data Sparsity Problems**
- **Cold Start:** Use default voting or hybrid methods.
- **Default Voting:**
  
  $$\hat{r}_{ui} = \frac{\sum_{v} \text{sim}(u, v) r_{vi}}{\sum_{v} |\text{sim}(u, v)|}$$
  

---

### **Matrix Factorization**
- **Problem Formulation:**
  
  $$\min_{U, V} \sum_{(u, i) \in K} (r_{ui} - U_u^T V_i)^2 + \lambda (||U||^2 + ||V||^2)$$
  
  -  $r_{ui}$ : Known rating
  -  $U$ : User feature matrix
  -  $V$ : Item feature matrix
  -  $\lambda$ : Regularization parameter

- **Stochastic Gradient Descent (SGD):**
  ```python
  def stochastic_gradient_descent(X, y, theta, alpha, num_iters):
      m = len(y)
      for i in range(num_iters):
          for j in range(m):
              h = np.dot(X[j], theta)
              loss = h - y[j]
              gradient = X[j].T * loss
              theta = theta - alpha * gradient
      return theta
  ```

---

### **Matrix Factorization Algorithm**
On slides there are better pseudocode with more intuitive thinking
- **Algorithm Steps:**
  ```python
  def matrix_factorization(R, P, Q, K, steps=5000, alpha=0.0002, beta=0.02):
      Q = Q.T
      for step in range(steps):
          for i in range(len(R)):
              for j in range(len(R[i])):
                  if R[i][j] > 0:
                      eij = R[i][j] - np.dot(P[i, :], Q[:, j])
                      for k in range(K):
                          P[i][k] = P[i][k] + alpha * (2 * eij * Q[k][j] - beta * P[i][k])
                          Q[k][j] = Q[k][j] + alpha (2 * eij * P[i][k] - beta * Q[k][j])
          eR = np.dot(P, Q)
          e = 0
          for i in range(len(R)):
              for j in range(len(R[i])):
                  if R[i][j] > 0:
                      e = e + pow(R[i][j] - np.dot(P[i, :], Q[:, j]), 2)
                      for k in range(K):
                          e = e + (beta / 2) * (pow(P[i][k], 2) + pow(Q[k][j], 2))
          if e < 0.001:
              break
      return P, Q.T
  ```

---

### **Hyperparameter Tuning**
- **Grid Search / Random Search / Bayesian Optimization / Evolutionary Algorithms**

---

### **Advanced Collaborative Filtering Techniques**
- **Recursive CF:**
  - Apply CF-method recursively for sparse datasets.
- **Graph-based Methods:**
  - "Spreading activation" to use longer paths in user-item graphs.

---

### **Collaborative Filtering Issues**
- Requires a user community.
- Suffers from data sparsity.
- Limited integration with other knowledge sources.
- Challenges in explaining results.

---

### **Matrix Factorization Techniques**
- **Problem Formulation:**
  
  $$\min_{U, V} \sum_{(u, i) \in K} (r_{ui} - U_u^T V_i)^2 + \lambda (||U||^2 + ||V||^2)$$
  
  - Minimize sum of squared errors with regularization.

- **Gradient Descent:**
  ```python
  def gradient_descent(X, y, theta, alpha, num_iters):
      m = len(y)
      for i in range(num_iters):
          h = np.dot(X, theta)
          loss = h - y
          gradient = np.dot(X.T, loss) / m
          theta = theta - alpha * gradient
      return theta
  ```

- **Stochastic Gradient Descent:**
  ```python
  def stochastic_gradient_descent(X, y, theta, alpha, num_iters):
      m = len(y)
      for i in range(num_iters):
          for j in range(m):
              h = np.dot(X[j], theta)
              loss = h - y[j]
              gradient = X[j].T * loss
              theta = theta - alpha * gradient
      return theta
  ```

---

### **Optimizing Matrix Factorization**
- **Factors to consider:**
  - Number of latent factors
  - Learning rate
  - Amount of regularization
  - Stopping criteria

---

### **Ranking-oriented Optimization**
- **Bayesian Personalized Ranking (BPR):**
  - Focuses on ranking correctness.
  - Maximizes distance in rating of good and bad objects.
  - Uses implicit feedback for optimization.

---
## Content Based Recommendation (Lecture 2)

#### Overview
- Content-based recommendation systems utilize item attributes and user profiles to make recommendations.
- Requires some information about the items and user preferences.

#### Definitions
- **Content**: Attributes such as genre, author, type, price, and keywords.
- **User Profile**: Describes what the user likes, based on previous interactions or explicit input.

---

### Item Representation and Content

#### Structured vs. Unstructured Data
- **Structured**: Each item described by the same set of attributes.
- **Unstructured**: Free-text descriptions.

#### Examples
- Example items with attributes like title, genre, author, type, price, and keywords.

---

### Simple Content Representation

#### Keyword Overlap
- **Simple Approach**: Compute similarity based on keyword overlap using metrics like the Dice coefficient.

#### Jaccard Similarity
- A method to measure similarity between items based on shared attributes.
- [[#^3a0177]]
### Example
- Describing books with a set of keywords and calculating overlap with user profiles.

---

### Term-Frequency - Inverse Document Frequency (TF-IDF)

#### TF-IDF Overview
- **TF (Term Frequency)**: Measures how often a term appears in a document.
- **IDF (Inverse Document Frequency)**: Reduces the weight of terms that appear in many documents.

#### Formula
- TF:  $tf(t, d) = \frac{f_t}{N_d}$
  -  $f_t$: Frequency of term  $t$  in document  $d$ 
  -  $N_d$ : Total number of terms in document  $d$ 
- IDF:  $idf(t) = \log\left(\frac{N}{df_t}\right)$
  -  $N$ : Total number of documents
  -  $df_t$ : Number of documents containing term  $t$ 
- TF-IDF:  $tf\_idf(t, d) = tf(t, d) \times idf(t)$

#### Example
- Term frequency matrix and combined TF-IDF weights for documents.

---

### Improving the Vector Space Model

#### Techniques
- **Stop Words Removal**: Eliminate common words like "a", "the".
- **Stemming**: Reduce words to their root form.
- **Size Cut-offs**: Use top representative words to reduce noise.

#### Advanced Methods
- **Lexical Knowledge**: Feature selection using domain knowledge or tools like WordNet.
- **Phrase Detection**: Identify meaningful phrases rather than single words.

---

### Content-Based RS Beyond Text

#### Numeric and Nominal Attributes
- Handling of attributes such as multimedia, categorical, and numeric attributes.

#### Example Approaches
- **Fixed Weighting**: Questioning the use of TF-IDF for certain attributes like gender or age.
- **State-of-the-Art**: Usage of attention layers and embeddings for multimedia.

---

### Content-Based RS: Multimedia and Attribute Data

#### Combined Approach
- Aggregation of attribute-based and visual similarity using algorithms like Fuzzy D’Hondt.

#### Practical Examples
- Examples of combining similarities for recommendation tasks.

---

### Query-Based Retrieval: Rocchio's Method

#### Overview
- Users provide feedback on relevant/irrelevant documents.
- The system adjusts the query based on feedback.

#### Formula
-  $$Q_{i+1} = \alpha Q_i + \beta \frac{1}{|D^+|} \sum_{d_j \in D^+} d_j - \gamma \frac{1}{|D^-|} \sum_{d_j \in D^-} d_j$$
  -  $\alpha$ : Weight for original query
  -  $\beta$ : Weight for positive feedback
  -  $\gamma$ : Weight for negative feedback

#### Bayesian Relevance Feedback
- Evaluate all points in the solution space based on distance to positive examples.

---

### Explicit Decision Models

#### Decision Trees
- Trees are constructed from training data using item features to partition test examples.

#### Rule Induction
- Based on algorithms like RIPPER, effective for certain types of classification tasks.

---

### Feature Selection

#### Strategies
- Use domain knowledge, frequency-based selection, and measures like mutual information.

#### Practical Tips
- Evaluate the utility of keywords and construct ranked lists.

---

### Limitations and Challenges

#### Common Issues
- Overspecialization, ramp-up phase, and limited content extraction capabilities.

#### Solutions
- Use additional sources for user preferences, employ diversity re-ranking methods.

#### Summary
- Content-based techniques do not require a user community but may overfit and provide overly similar recommendations.

---

### Knowledge-Based Recommendation

#### Basic I/O Relationship
- Systems that recommend based on explicit user needs.

#### Types
- **Constraint-Based**: Based on a set of recommendation rules.
- **Case-Based**: Items retrieved using similarity measures.

#### Examples
- Constraint-based GUI and practical use cases for critiquing in case-based systems.

---
## Evaluation of Recommender Systems (Lecture 4)
### Overview
- Evaluating recommender systems is essential to determine their effectiveness and identify areas for improvement.
- Numerous evaluation techniques exist, each suited for different application domains.

### Motivation
- Key research questions include:
  - Is a recommender system more efficient in terms of accuracy, user satisfaction, response time, serendipity, online conversion, ramp-up efforts, etc.?
  - Do customers like or buy recommended items?
  - Are customers satisfied with recommendations after purchase?
  - Do recommendations increase site usage?

### Scientific Requirements for Evaluation

#### Reproducibility
- Scientific experiments must ensure reproducibility to verify findings.
- **Methodology**: Describe the methodology thoroughly, follow systematic procedures, and document all decisions.

#### Evaluation Criteria
- **Validity**:
  - **Internal Validity**: Effects are due to controlled conditions, not participant differences or environmental factors.
  - **External Validity**: Results are generalizable to other groups or situations.
- **Reliability**: Consistency and absence of errors in data and measurements.
- **Sensibility**: Different evaluations should reflect in differences in measurements.

### Components of Evaluation Research

#### Subjects
- Typically specific subgroups like online customers or web users receiving personalized recommendations.

#### Settings
- **Lab Studies**:
  - Created for the study with controlled variables.
  - Potential issues with participant motivation.
- **Field Studies (Online Evaluation)**:
  - Conducted in real-world environments with intrinsically motivated users.
  - Can be costly.
- **Offline Studies**:
  - Based on real-world data, analyzing after-the-fact.
  - Recent improvements towards de-biasing and multi-criterial evaluation.

#### Measured Variables
- **Independent Variables**: Static throughout the experiment, controlled by the evaluation design (e.g., recommendation algorithm).
- **Dependent Variables**: Influenced by independent variables and control conditions.

#### Design Types
- **Experimental**: Manipulates independent variables to observe their impact on dependent variables.
- **Quasi-Experimental**: Lacks random assignment of subjects to treatments.
- **Non-Experimental**: Uses observational research methods like surveys or case studies.
- **Cross-Sectional**: Analyzes relations among variables measured in different groups.
- **Case Studies**: Combines various methods to investigate real-life contexts.

### Evaluation Settings and Techniques

#### Online Experiments
- **A/B Testing**:
  - Users are randomly directed to recommendations from different algorithms.
  - Evaluate metrics close to the target behavior (e.g., profit for retailers, subscriptions for Netflix).

#### Lab Studies
- Includes preference elicitation phases and features like questionnaires or interviews to capture harder-to-detect aspects like trust and novelty.

#### Offline Evaluation
- **Datasets**: Collections of synthetic or historical user interaction data, with considerations for dataset size, sparsity, and domain.

#### Methodology
- **Data Splits**:
  - **Holdout**: Randomly withholds a set of ratings as the test set.
  - **N-fold Cross-Validation**: Divides data into partitions, each used once as the test set.
  - **Leave-P-out Validation**: Tests one rated item at a time for each user.

#### Bias and Variance
- Understanding biases in data is crucial as they affect evaluation. Mitigation strategies include using temporal data splits and recording impressions.

### Metrics for Evaluating Recommender Systems

#### Relevance and Ranking Metrics
- **Precision and Recall**:
  - **Precision**: A measure of exactness, determining the fraction of relevant items retrieved out of all items retrieved.
    $$
    \text{Precision} = \frac{\text{True Positives (TP)}}{\text{True Positives (TP)} + \text{False Positives (FP)}}
    $$
  - **Recall**: A measure of completeness, determining the fraction of relevant items retrieved out of all relevant items.
    $$
    \text{Recall} = \frac{\text{True Positives (TP)}}{\text{True Positives (TP)} + \text{False Negatives (FN)}}
    $$

#### Rank-Based Metrics
- **Normalized Discounted Cumulative Gain (nDCG)**: Uses a logarithmic reduction factor.
  $$
  \text{DCG}_p = \sum_{i=1}^{p} \frac{2^{\text{rel}_i} - 1}{\log_2(i + 1)}
  $$
  $$
  \text{IDCG}_p = \sum_{i=1}^{p} \frac{2^{\text{rel}_i} - 1}{\log_2(i + 1)}
  $$
  $$
  \text{nDCG}_p = \frac{\text{DCG}_p}{\text{IDCG}_p}
  $$

#### Advanced Metrics
- **Mean Average Precision (MAP)**: Average precision values after each successful prediction.
  $$
  \text{MAP} = \frac{1}{|Q|} \sum_{q \in Q} \text{AP}(q)
  $$
- **Novelty and Diversity**:
  - **Novelty**: Measures how new items are to the user.
  - **Diversity**: Measures similarity among recommended items.
  - **Serendipity**: Combines relevance and unexpectedness.

### Practical Challenges and Solutions

#### Causality and Biases
- Evaluation must account for causality and biases in data.
- **Strategies**: Use temporal data splits, simulate evaluation, and apply de-biasing techniques.

#### Offline Evaluation Metrics
- Metrics depend on research questions and hypotheses, including relevance, rating error, novelty, diversity, coverage, and serendipity.

### Summary and Best Practices

#### Key Takeaways
- Proper evaluation requires a combination of experimental design, methodology, and metrics tailored to specific research questions.
- Awareness of biases and selection of appropriate metrics are critical for meaningful evaluations.

#### Future Directions
- Explore beyond-accuracy metrics and ensure evaluations consider long-term effects and user trust.

---

###   Recap

- **Relevance and Ranking Metrics**:
  - Precision:
    $$
    \text{Precision} = \frac{\text{True Positives (TP)}}{\text{True Positives (TP)} + \text{False Positives (FP)}}
    $$
  - Recall:
    $$
    \text{Recall} = \frac{\text{True Positives (TP)}}{\text{True Positives (TP)} + \text{False Negatives (FN)}}
    $$
  - F1 Score:
    $$
    \text{F1 Score} = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
    $$
  - Mean Average Precision (MAP):
    $$
    \text{MAP} = \frac{1}{|Q|} \sum_{q \in Q} \text{AP}(q)
    $$

- **Rank-Based Metrics**:
  - Rank Score:
    $$
    \text{Rank Score} = \frac{\sum_{i=1}^{N} \frac{1}{\log_2(i+1)}}{\sum_{i=1}^{N} \frac{1}{\log_2(i+1)}}
    $$
  - Liftindex:
    $$
    \text{Liftindex} = \frac{1}{k} \sum_{i=1}^{k} \text{Lift}_i
    $$
  - Normalized Discounted Cumulative Gain (nDCG):
    $$
    \text{DCG}_p = \sum_{i=1}^{p} \frac{2^{\text{rel}_i} - 1}{\log_2(i + 1)}
    $$
    $$
    \text{IDCG}_p = \sum_{i=1}^{p} \frac{2^{\text{rel}_i} - 1}{\log_2(i + 1)}
    $$
    $$
    \text{nDCG}_p = \frac{\text{DCG}_p}{\text{IDCG}_p}
    $$

- **Advanced Metrics**:
  - Novelty:
    $$
    \text{Novelty} = \frac{1}{N} \sum_{i=1}^{N} \text{novelty}(i)
    $$
  - Diversity

:
    $$
    \text{Diversity} = \frac{1}{N} \sum_{i=1}^{N} \sum_{j=i+1}^{N} \text{diversity}(i, j)
    $$
  - Serendipity:
    $$
    \text{Serendipity} = \frac{1}{N} \sum_{i=1}^{N} \text{serendipity}(i)
    $$
## Linear Monotone Preference Model (Lecture 5)

### Overview
- The Linear Monotone Preference Model (LMPM) is used to handle user requirements and conflicting multicriterial preferences.
- Focus on creating an ordering system that is intuitive and explainable to users.

### Conflicting Requirements
- Often, no single product can satisfy all user requirements perfectly.
- The goal is to find products that come close to meeting user preferences.

---

### Ordering and Preference Scales

#### Human-Intuitive Ordering
- Ordering should be explainable and relatable to users.
- Example: Likert scale, which is a common method for capturing user preferences (e.g., from 1 to 5).

#### User Preferences
- User preferences are often scaled and have ideal values.
- In competitions, clear winners exist, but in e-commerce, user preferences vary significantly.
- Marketing segmentation and faceted browsing are used to specify ideal values for different user segments.

---

### Preferential Sets and Fuzzy Sets

#### Preferential Sets
- Preferential sets are a variant of fuzzy sets intended to model human linear preferences.
- Example: Price categories can be modeled as fully cheap, reasonable, and expensive on a linear scale from low to high.

#### Preference Scale
- A typical preference scale ranges from 0 to 1, where 0 is least preferred and 1 is most preferred.

---

### Decathlon Data Example

#### Multi-Criterial Scale Points
- Decathlon points can be used as a basis for making different attributes commensurable.

#### Dominance and Pareto Ordering
- Dominance in multi-criteria decision making is similar to Pareto ordering, where an item is considered better if it is not worse in any criterion.
- Example: In a Decathlon, an athlete who scores higher in all events dominates others.

#### Data Cube and Preference Cube
- **Data Cube**: Represents raw data.
- **Preference Cube**: Transforms data into a preference-based format.

#### Sum of Points
- The sum of points can be used to make a Decathlon linear by aggregating individual event scores.

---

### Linear Monotone Preference Model (LMPM)

#### Definition
- LMPM is a method to order items based on multiple criteria by transforming attributes into preference scores.
- The model aggregates these scores to provide an overall preference rating.

#### Aggregation Function
- The aggregation function \( t \) is used to combine individual attribute preferences into a global preference score:
  $$
  t(x_1, x_2) = w_1 \cdot x_1 + w_2 \cdot x_2 \quad \text{where} \quad w_1 + w_2 = 1
  $$

#### Contour Lines
- Contour lines connect points with the same preference score in the preference cube and can be visualized in the data cube.

---

### Building the LMPM Step-by-Step

#### Triangular Preference Functions
- Local preferences can be modeled using triangular functions:
  $$
  f_j(x_j) = 
  \begin{cases} 
  0 & \text{if } x_j = \min D_j \\
  \frac{x - x_j}{i_j - x_j} & \text{if } x_j \leq x \leq i_j \\
  1 & \text{if } x = i_j \\
  \frac{y_j - x}{y_j - i_j} & \text{if } i_j \leq x \leq y_j \\
  0 & \text{if } x_j = \max D_j 
  \end{cases}
  $$

#### Trapezoidal Preference Functions
- Trapezoidal functions provide a more flexible way to model preferences with ideal intervals:
  $$
  f_j(x_j) = 
  \begin{cases} 
  0 & \text{if } x_j = \min D_j \\
  \frac{x - i_{jl}}{i_{jr} - i_{jl}} & \text{if } i_{jl} \leq x \leq i_{jr} \\
  1 & \text{if } x = i_{jr} \\
  \frac{y_j - x}{y_j - i_{jr}} & \text{if } i_{jr} \leq x \leq y_j \\
  0 & \text{if } x_j = \max D_j 
  \end{cases}
  $$

---

### Calculating Preference Degrees

#### Mapping Data to Preferences
- Objects are mapped from the data cube to the preference cube based on their attribute values and user preference functions.

#### Aggregation and Ordering
- Overall preference is given by:
  $$
  r_{ft}(\text{objectID}) = t\left(\{f_i(\text{objectID.A}_i)\}_{i=1}^m\right)
  $$
- Contour lines in the data cube represent items with the same preference degree.

#### Example Calculation
- For user $u$ with preferences $f_1$ and $f_2$:
  $$
  \text{Bu} = (b_{1u}, b_{2u})
  $$
- Objects B, D, E are mapped to preference degrees based on their attribute values.

---

### Dynamical Model and Time Simulation

#### Moving Ideal Points
- User preferences can evolve over time, with ideal points shifting based on user interactions.
- The model can simulate this dynamic preference adjustment.

#### Example Sessions
- Starting with initial preferences \( f_0 \) and aggregation \( t_0 \):
  - Time 0: Initial preference contour.
  - Time 1: User clicks update the ideal point.
  - Time 2: New ideal point after further interactions.

---

### Aggregation and Visualization

#### Aggregation Function
- The aggregation function combines attribute preferences into a global preference score, ensuring Pareto ordering:
  $$
  t(x_1, x_2) = w_1 \cdot x_1 + w_2 \cdot x_2
  $$

#### Contour Line Visualization
- Contour lines represent levels of global preference and help visualize the preference landscape in both data and preference cubes.

#### Practical Applications
- Used in web e-shops to order items based on user-specific preference models.
- Each user can have their own preference scales and aggregation methods, allowing for personalized recommendations.

---

### Extensions and Practical Considerations

#### Handling Complex Preferences
- Extend the basic model to handle more complex preference shapes (e.g., trapezoidal, mixed shapes).

#### Market Segmentation
- Different user segments can have different ideal points and aggregation functions, reflecting diverse preferences.

#### Real-World Applications
- Applications in e-commerce, personalized recommendations, and user preference modeling.

####  Simulation and Extensions
- Simulations can show how preferences evolve over time and how different aggregation methods impact the ordering of items.

---
## Querying Threshold Algorithm (Lecture 6)
#### Overview
- Focuses on querying techniques to retrieve the top-k results from a dataset.
- Includes various data models and algorithms for efficient querying without scanning the entire dataset.

### User Preferences and Data Cube

#### Preference Model
- **Function $R_{ft}$**: 
  $$
  R_{ft}: PD_i \rightarrow [0, 1], \quad R_{ft}(a_1, \ldots, a_m) = t(f_i(a_i))
  $$
  where $t$ is a combination function and $f_i$ are preference functions.

#### Visualization
- Contour lines represent different levels of preferences.
- Example:
  $$
  (a) \ge_{ft} (b) \quad \text{iff} \quad R_{ft}(a) \ge R_{ft}(b)
  $$

### Threshold Algorithms (FLN TA)

#### Web Service Motivation
- FLN data model viewed as Linear Monotone Preference Model (LMPM).
- FLN TA (Threshold Algorithm) is designed for top-k querying.

#### Data Model
- **Objects**: $\{R_i : i \leq N\}$ with $m$ attributes.
- **Scores**: $x_{1R}, \ldots, x_{mR} \in [0, 1]$
- **Combination Function**:
  $$
  t: [0, 1]^m \rightarrow [0, 1], \quad \text{monotone}
  $$

#### Threshold Algorithm Steps
1. **Sorted Access**:
   - Access each list $L_i$ sequentially.
   - Perform random access to other lists to find grades.
   - Compute:
     $$
     t(R) = t(x_{1R}, \ldots, x_{mR})
     $$
   - Remember the top-k objects.

2. **Define Threshold**:
   - For each list $L_i$, let $x_i$ be the grade of the last object seen.
   - Define threshold $t$:
     $$
     t = t(x_1, \ldots, x_m)
     $$

3. **Output**:
   - Set $Y$ containing top-k objects with highest grades.

### Algorithm Illustration

#### Example
- Sequential and random access steps illustrated graphically.
- Demonstrates computation and comparison of object grades to maintain top-k list.

### Heuristics and Optimizations

#### Incremental Threshold Algorithm
- Adjustments to threshold algorithm for incremental improvements.
- Uses frequency and depth of sequential access to optimize performance.

### FLN Data Model and Multiuser Extensions

#### Multiuser Model
- Extends FLN data model to multiuser scenarios.
- **Overall Preference**:
  $$
  r_{ft}(oid) = t(f_1(oid.A_1), \ldots, f_m(oid.A_m))
  $$

### Proof of Correctness

#### FLN Theorem 4.1
- **Monotone Aggregation Function**: 
  $$
  \text{If } t \text{ is monotone, then TA correctly finds the top } k \text{ answers.}
  $$

#### Proof Outline
- Assume an object $R \notin Y$.
- Use bounds:
  $$
  x_{iz} \leq x_i \quad \text{for every } i \quad \implies \quad t(x_{1z}, \ldots, x_{mz}) \leq t
  $$
  where $t$ is the threshold value.

### No Random Access (NRA) Algorithm

#### NRA Algorithm Steps
1. **Access Each List**:
   - Calculate $x_{1d}, \ldots, x_{md}$.
   - For each item $R$, calculate $S_d(R), W_d(R), B_d(R)$

2. **Viability Check**:
   - An object $R$ is viable if:
     $$
     B_{Sd}(R) > M_{kd}
     $$

3. **Output Set**:
   - The set $T_{kd}$ contains the top-k objects.

### Further Notes

#### Correctness of NRA
- Theorem: NRA correctly finds top-k objects if the aggregation function is monotone.

### Conclusion

- Comparison of different access methods, optimization strategies, and multiuser scenarios.
- Discussion on FLN TA and NRA optimality, and practical implementations.

---
## Hybrid Recommender Systems (Lecture 7)

#### Overview
- Hybrid recommender systems combine various recommendation methods to enhance performance and mitigate the shortcomings of individual methods.
- **Knowledge-based**: Recommends items based on explicit user requirements.
- **Content-based**: Recommends items similar to those the user liked in the past.
- **Collaborative**: Recommends items that are popular among similar users.

### Hybridization Designs

#### Hybridization Design Types
- **Parallel Use**: Several recommendation systems run simultaneously, and their results are combined.
- **Monolithic**: A single recommendation component exploits features from multiple paradigms.
- **Pipelined**: A sequence of recommendation systems where each system processes the output of the previous one.

### Monolithic Hybridization Design

#### Feature Augmentation
- **Content-Boosted Collaborative Filtering**:
  - Uses content features to create additional synthetic ratings.
  - Example:
    - Alice likes Item 1 and Item 3.
    - Item 7 is similar to Items 1 and 3 by a degree of 0.75.
    - Therefore, Alice is predicted to like Item 7 with a rating of 0.75.
  - This approach reduces sparsity in the user-item rating matrix.
  - Peers with more co-rated items have more influence.
  - Higher confidence in predictions when the user has many ratings.

#### Visual Bayesian Personalized Ranking (BPR)
- A latent factor model that integrates visual features.
- Part of the item embedding is static, based on pre-trained visual feature extractors.
- Dimensionality reduction is applied to balance collaborative filtering and content-based tradeoffs.
- Trained using BPR loss to rank items effectively.

### Parallelized Hybridization Design

#### Weighted Combination
- Combines the output of multiple recommendation systems using a weighting scheme.
- **Example**:
  $$
  \text{Weighted Score} = w_1 \cdot \text{Score}_1 + w_2 \cdot \text{Score}_2
  $$
- Weights can be dynamically adjusted based on performance metrics.
- **Dynamic Adjustment**:
  - Initial uniform weight distribution.
  - Weights are adapted to minimize the prediction error for each user.
  - Uses multi-armed bandit strategies to optimize weights based on empirical data.

#### Estimating Weights
- **Empirical Bootstrapping**:
  - Historic data is used to compute different weightings.
  - The best-performing weighting scheme is selected.
- **Dynamic Adjustment Example**:
  - Start with uniform weights.
  - Adjust weights incrementally to reduce Mean Absolute Error (MAE).

### Switching and Mixed Hybridization

#### Switching
- Uses an oracle to decide which recommender to use based on predefined criteria.
- All weights except one are set to zero.
- **Example**:
  - If there are too few ratings, use a knowledge-based recommender.
  - Otherwise, use a collaborative filtering approach.

#### Mixed
- Results from different recommenders are combined at the user interface level.
- Each technique's results are presented together.
- **Example**:
  - **Thompson Sampling**:
    - Uses Beta distribution to model the success probability of each recommender.
    - Recommender with the highest sampled value is selected for each position in the recommendation list.

### Pipelined Hybridization Design

#### Cascade
- Successive recommenders refine the recommendations of the predecessors.
- **Example**:
  - The first recommender removes no-go items.
  - The second recommender assigns scores and refines the list.
- This method is effective in large-scale scenarios where initial filters reduce the candidate set.

#### Meta-Level
- A recommender system builds a model used by the subsequent system.
- **Example**:
  - A content-based recommender builds user models with weighted term vectors.
  - A collaborative filter uses these models to find similar users and make recommendations.

### Limitations and Considerations

#### Limitations of Hybrid Strategies
- Few empirical studies compare different hybrid strategies.
- Most datasets lack the required data to compare multiple recommendation paradigms effectively.
- **Considerations**:
  - **Monolithic Hybrids**: Require preprocessing but incorporate more knowledge.
  - **Parallel Hybrids**: Need careful score matching across different recommenders.
  - **Pipelined Hybrids**: Work well when combining antithetic approaches.

### Example Formulas and Metrics

#### Weighted Combination Formula
$$
\text{Weighted Score} = w_1 \cdot \text{Score}_1 + w_2 \cdot \text{Score}_2
$$

#### Dynamic Weight Adjustment
- Mean Absolute Error (MAE) calculation:
$$
\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|
$$
where $y_i$ is the actual rating and $\hat{y}_i$ is the predicted rating.

## Reciprocal Recommender Systems (Lecture 8)
### People Recommender Systems

#### Overview
- Focuses on recommending people, such as friends in social networks, mentors, teammates, or dating partners.
- Reciprocal recommender systems consider mutual preferences, aiming to find matches where both parties have a high likelihood of liking each other.

### Reciprocal Recommender Systems in Online Dating

#### Modeling Likes and Dislikes
- **Unified Model for Compatibility**:
  $$
  C(AB) = \frac{1 + C_{\text{pos}}(AB) - C_{\text{neg}}(AB)}{2}
  $$
  - \( C_{\text{pos}}(AB) \): Compatibility based on liked attributes.
  - \( C_{\text{neg}}(AB) \): Compatibility based on disliked attributes.

- **Harmonic Mean for Compatibility**:
  - Penalizes high differences in compatibilities between parties.
  - Uses a harmonic mean to aggregate compatibility scores:
    $$
    H(C_{\text{pos}}(AB), C_{\text{pos}}(BA)) = \frac{2 \cdot C_{\text{pos}}(AB) \cdot C_{\text{pos}}(BA)}{C_{\text{pos}}(AB) + C_{\text{pos}}(BA)}
    $$

#### Insights from Recent Studies
- **2016 Study**: Design of Reciprocal Recommendation Systems for Online Dating
  - Emphasizes the importance of balancing likes and dislikes.
  - Uses socio-demographic links to improve recommendations.

#### Practical Considerations
- **Re-ranking for Active Users**:
  - Prioritize recently active and registered users to improve engagement.
- **Pseudo Embeddings**:
  - Generate embeddings for new users based on metadata such as location.
- **Pre-computed Recommendations**:
  - Store recommendations for existing users for faster query responses.
- **Cold-Start Problem**:
  - Run inference servers for new users to generate recommendations in real-time.

### People Recommender Systems in Job Recruitment

#### Job Recommender Systems
- **Dual Stakeholders**:
  - Recruiters and job seekers both have preferences that need to be considered.
- **Sources of Knowledge**:
  - Interaction data (e.g., clicks, applications).
  - CVs (content-representation of users).
  - Job descriptions (content-representation of items).

#### Effectiveness of Job Title-Based Embeddings
- **Embedding Methods**:
  - Pre-trained Word2Vec.
  - Self-trained Word2Vec.
  - Self-trained Doc2Vec.
- **Results**:
  - ItemKNN performs best when there is sufficient interactional data.
  - Job title-based embeddings outperform resume-based embeddings in cold-start scenarios.
  - Self-trained embeddings perform better than pre-trained ones.

### Follow-Up Studies

#### Sentence-Pair Classification for Algorithmic Recruiting (2023)
- **Addressing the Semantic Gap**:
  - Different language styles between resumes and job postings create a semantic gap.
  - Use BERT's next-sentence-prediction feature to bridge this gap.
- **Approach**:
  - Train a model to map resumes to job postings using sentence-pair classification.

### Career Path Prediction

#### Task Definition
- **Career Path Prediction**:
  - Predict the next career step based on a sequence of past experiences.
  - Each experience is represented by a title, description, and ESCO occupation labels.

#### Approach
- **Skill-Based Prediction**:
  - Use the ESCO ontology for skill-based matching.
- **Description-Based Prediction**:
  - Employ contrastive learning to transform embeddings of past experiences to predict the next job title.
  - Linear transformation maps previous experiences to the current job posting.

### Practical Considerations and Challenges

#### Challenges in Reciprocal Recommender Systems
- **Data Privacy**:
  - Ensuring user data privacy while collecting interaction data.
- **Cold-Start Problem**:
  - Generating accurate recommendations for new users with minimal interaction data.
- **Semantic Gap**:
  - Bridging the gap between different language styles in resumes and job postings.

#### Improving Recommendations
- **Contrastive Learning**:
  - Learn to distinguish between similar and dissimilar job titles and descriptions.
- **Language-Agnostic Networks**:
  - Develop models that can handle different languages and dialects to improve job matching.
---
## Deep learning (Lecture 9)
Here are the detailed notes extracted from the provided slides on "Deep Learning for Recommender Systems" with headers indented one level deeper and all mathematical expressions formatted with double dollar signs for LaTeX rendering.

---

### Deep Learning for Recommender Systems

#### Why Deep Learning?
- Deep learning has achieved significant success in various fields, including image recognition (e.g., ImageNet challenge).
- Deep learning models can handle complex architectures and are universal function approximators.

### Neural Networks and Learning

#### Neural Model
- **Neuron**: The basic unit in a neural network, which processes inputs and produces an output through an activation function.

#### Feedforward Multilayered Network
- **Stochastic Gradient Descent (SGD)**:
  $$
  \theta = \theta - \eta \nabla J(\theta)
  $$
  where \( \theta \) represents model parameters, \( \eta \) is the learning rate, and \( \nabla J(\theta) \) is the gradient of the cost function.

- **Backpropagation**:
  - Used to compute gradients for each layer to update the model parameters.
  - Challenges include vanishing gradients and slow learning.

### Modern Deep Networks

#### Key Ingredients
- **Rectified Linear Activation (ReLU)**:
  $$
  f(x) = \max(0, x)
  $$
- **Dropout**: A technique to prevent overfitting by randomly setting some neuron outputs to zero during training.
- **Mini-batches**: Using small subsets of the training data to compute gradients and update weights.

### Deep Learning for Recommender Systems

#### Main Topics as of 2017
- Learning item embeddings
- Deep collaborative filtering
- Feature extraction from content
- Session-based recommendations with Recurrent Neural Networks (RNNs)

### Research Directions

#### Best Practices
- Start simple and add complexity gradually.
- Optimize code for GPU/CPU performance.
- Ensure scalability and use open-source code.
- Avoid very small datasets and irrelevant tasks like rating prediction.

### Item Embeddings and 2vec Models

#### Embeddings
- **Definition**: A learned real-value vector representing an entity.
- **Use in Recommenders**: Initialization of item representation in advanced algorithms, item-to-item recommendations.

#### Matrix Factorization (MF)
- **Learning User and Item Embeddings**:
  $$
  \text{User-Item Interaction Matrix} \approx \text{User Embedding} \times \text{Item Embedding}^T
  $$

### Word2Vec

#### Continuous Bag of Words (CBOW)
- **Model**:
  - Maximizes the probability of a target word given its context.
  - **Input**: One-hot encoded words.
  - **Output**: Likelihood of words given the context using softmax.

#### Skip-gram
- **Model**:
  - Maximizes the probability of context words given a target word.
  - Uses shared weights for input and output words.
  - **Negative Sampling**: Efficiently trains the model by updating a subset of negative samples.

### Paragraph2Vec (Doc2Vec)
- Learns representations for paragraphs/documents based on the CBOW model, adding global context.

### Prod2Vec

#### Skip-gram on Products
- **Model**:
  - Input: \(i\)-th product purchased by the user.
  - Context: Other purchases of the user.
  - User embeddings added as global context.

### Meta-Prod2Vec
- Extends Prod2Vec by incorporating item metadata into embeddings, improving recommendations by using side information.

### Feature Extraction from Content

#### Images, Text, and Audio
- **Convolutional Neural Networks (CNNs)**: Extract features from images.
- **RNNs and BERT**: Extract features from text.
- Applications include fashion, video, and product reviews.

### Music Representations

#### Audio Features in Recommender Systems
- **Integration with MF**:
  - Minimize the distance between music features and MF’s feature vectors.
  - Replace item features with music features to minimize the original loss.

### Neural Collaborative Filtering (NCF)

#### NeuMF (He et al. 2017)
- Uses a Multi-Layer Perceptron (MLP) instead of a simple dot product to learn more complex dependencies.

### Session-Based Recommendations with RNNs

#### GRU4Rec (Hidasi et al. 2015)
- **Network Structure**:
  - Input: One-hot encoded item ID.
  - GRU layer(s) to process sequential data.
  - Output: Scores over all items, targeting the next item in the session.
- **Techniques**:
  - Session-parallel mini-batching.
  - Output sampling to handle large item sets.

### Follow-Up Development
- Adoption of new networks from Natural Language Processing (NLP) to Recommender Systems.
- Transformers4Rec by NVIDIA Merlin for modern deep learning in recommendations.

### Utilizing More Information

#### Meta-Prod2Vec and Content2Vec
- **Meta-Prod2Vec**: Embeds metadata along with items to improve recommendations.
- **Content2Vec**: Uses multimodal information (e.g., images, text) to learn pairwise item similarities.

### Context-Aware Recommender Systems
- Incorporate context into matrix factorization and other models for personalized recommendations.

### Fairness and Bias in Recommender Systems

#### Addressing Biases
- **Selection Bias**: Users choose which items to rate, causing non-representative samples.
- **Exposure Bias**: Users only interact with exposed items.
- **Conformity Bias**: Users tend to behave similarly to others.
- **Position Bias**: Users interact more with items in higher positions on the recommendation list.

### Outlook

#### Future Directions
- Complex, task-specific architectures.
- Scalability challenges and solutions (e.g., sparse EASE variants).
- Incorporating user control and large language models (e.g., conversational recommender systems).
- Emphasizing the evaluation of recommender systems in a broader ecosystem context.