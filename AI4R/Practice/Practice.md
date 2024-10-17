
### Question 1:
**[True or False]**  
The Kalman gain is calculated in the prediction step of the Kalman filter.

#### **Answer:** False

#### **Explanation & Steps:**
- The **Kalman gain** is calculated in the **update step**, not in the prediction step.
- **Prediction step**: The filter predicts the next state and the associated uncertainty (covariance).
- **Update step**: After receiving a measurement, the Kalman gain is computed to determine how much weight to give to the prediction versus the measurement. The Kalman gain is then used to correct the state estimate.

---

### Question 2:
Consider a robot whose state $\bar{x}$ is its $(x, y)$ position. If it starts at state $\bar{x}_0 = [4, 7]^T$ at time $t=0$ and moves according to the state transition model 

$$
F = \begin{bmatrix} 0.7  &  0.3  \\  0.1  &  0.5 \end{bmatrix}
$$

, what is the $y$-component of its predicted state, $\bar{x}_1$, at time $t = 1$? (Specify to 1 decimal place.)

#### **Answer:** 3.9

#### **Steps:**
1. The initial state $\bar{x}_0 = [4, 7]^T$ gives us $x_0 = 4$ and $y_0 = 7$.
2. The state transition model 

$$
F = \begin{bmatrix} 0.7  &  0.3  \\  0.1  &  0.5 \end{bmatrix}
$$

.
3. To predict the next state $\bar{x}_1$, use the equation $\bar{x}_1 = F \cdot \bar{x}_0$:
   
$$
\begin{bmatrix} 0.7 & 0.3 \\ 0.1 & 0.5 \end{bmatrix} \cdot \begin{bmatrix} 4 \\ 7 \end{bmatrix} = \begin{bmatrix} 4.9 \\ 3.9 \end{bmatrix}
$$

4. The $y$-component of the predicted state is **3.9**.

---

### Question 3:
**[True or False]**  
In GraphSLAM, landmarks must be distinguishable from one another.

#### **Answer:** True

#### **Explanation & Steps:**
- **GraphSLAM** stands for Simultaneous Localization and Mapping using graph-based techniques.
- In order for the robot to correctly associate sensor measurements to map landmarks, the landmarks must be **distinct**.
- If landmarks are not distinguishable, the robot may confuse one landmark for another, causing errors in both the map and its location estimate.

---

### Question 4:
For each equation below, determine whether the equation is part of the **measurement update step** or the **prediction step** of a Kalman Filter. If the equation is not part of either step, select "Other."

(A) $P' = (I - KH) P$  
(B) $y_i = y_i + \alpha(x_i - y_i) + \beta(y_{i-1} - 2y_i + y_{i+1})$  
(C) $P' = F P F^T$  
(D) $x' = x + K(z - Hx)$  
(E) $K = P H^T (H P H^T + R)^{-1}$  
(F) $x' = Fx + u$

#### **Answer & Steps:**
- **Equation A**: **Measurement update step**  
   - $P' = (I - KH) P$ is part of the **measurement update step**. It represents the update of the covariance matrix after incorporating the measurement.

- **Equation B**: **Other**  
   - This equation is unrelated to the Kalman filter and likely comes from a different type of system.

- **Equation C**: **Prediction step**  
   - $P' = F P F^T$ is part of the **prediction step**, where the covariance is predicted based on the system model.

- **Equation D**: **Measurement update step**  
   - $x' = x + K(z - Hx)$ is part of the **measurement update step**. This equation represents the state update after incorporating the measurement.

- **Equation E**: **Measurement update step**  
   - $K = P H^T (H P H^T + R)^{-1}$ is part of the **measurement update step**. This equation calculates the Kalman gain.

- **Equation F**: **Prediction step**  
   - $x' = Fx + u$ is part of the **prediction step**, where the state is predicted based on the system's dynamics.

---

### Question 5:
**[True or False]**  
According to Sebastian, the localization problem is to determine a robot's location ____.

- within a certain level of accuracy
- given no prior map of the world
- without using another positioning system such as GPS

#### **Answer:** within a certain level of accuracy

#### **Explanation & Steps:**
- Localization involves estimating the robot's position within a known environment with a specific **level of accuracy**.
- In robotics, this is often done using various sensors and algorithms such as Kalman filters or SLAM techniques to refine the location estimate while considering noise and uncertainties.

---

### Question 6:
Assume we have two Gaussian distributions G1 and G2. G1 has a large variance and G2 has a small variance. G1 represents the prior, and G2 represents the measurement probability. Suppose we combine these Gaussians in order to obtain an updated state estimate. Where would the center of the resulting distribution most likely be located?

- closer to G1
- closer to G2
- in the middle of G1 and G2
- not enough information

#### **Answer:** closer to G2

#### **Explanation & Steps:**
- **G1** has a large variance (more uncertainty), while **G2** has a small variance (less uncertainty).
- When combining the two distributions, the final estimate will be **weighted** by the inverse of the variances.
- Since **G2** has smaller variance (higher confidence), the resulting distribution will be **closer to G2**.

---

### Question 7:
**[True or False]**  
In SLAM, the probability distribution representing the final robot location after a sequence of noisy movements can be calculated by adding together the individual distributions representing each movement.

#### **Answer:** False

#### **Explanation & Steps:**
- In **SLAM**, the probability distributions are not simply added; instead, they are **convolved** with each other.
- This convolution

process considers the uncertainty from each step, updating the overall probability distribution by combining the effects of each movement. This is essential for incorporating the noise and uncertainty in the robot's motion model.

---

### Question 8:
The Kalman gain is the weight applied to the measurements and ______________ when updating the state.

- prior probability
- correlation coefficient
- predicted state
- Gaussian distribution

#### **Answer:** predicted state

#### **Explanation & Steps:**
- The **Kalman gain** is used to combine the **predicted state** and the new **measurement** to update the state estimate.
- The Kalman gain decides how much influence the measurement will have compared to the prediction when determining the final estimate.
- The updated state is a weighted combination of the predicted state and the measurement, where the Kalman gain governs this balance.

---

### Question 9:
The weight associated with a particle is calculated from:

- The probability of the particle state matching the robot's state given the measurement
- The probability of the observed measurements given the state of the particle
- The Euclidean distance from the particle to the robot
- The squared error of the measurement

#### **Answer:** The probability of the observed measurements given the state of the particle

#### **Explanation & Steps:**
- In **particle filters**, each particle is assigned a weight based on how well its state explains the observed measurements.
- This weight is proportional to the **likelihood** of the measurement given the particle’s state.
- The higher the probability that a particle's state matches the observed measurement, the higher its weight.

---

### Question 10:
**[True or False]**  
The particle with the highest weight is always sampled.

#### **Answer:** False

#### **Explanation & Steps:**
- In a **particle filter**, the particles are sampled based on their weights using a **probabilistic resampling** method.
- While particles with higher weights are more **likely** to be sampled, it is not guaranteed that the particle with the highest weight will always be selected.
- This probabilistic approach ensures diversity in the particle set, preventing the filter from collapsing onto a potentially incorrect state.


### Question 11:
In Sebastian's lecture on Localization, Bayes' Rule applies to the motion (move function), whereas the Law of Total Probability applies to the measurement (sense function).

- True
- False

#### **Answer:** False

#### **Explanation:**
- In the context of **robot localization**, **Bayes' Rule** is applied to the **measurement (sense function)**, as it is used to update the belief about the robot's position after receiving a new sensor measurement.
- The **Law of Total Probability** applies to the **motion (move function)**, as it is used to predict the new state of the robot by summing over all possible previous states, weighted by the probability of moving from those states to the current state.
- Thus, the correct assignment is that Bayes' Rule is used for the **sense function**, and the Law of Total Probability is used for the **move function**.



### Question 12:
If a single noisy measurement throws off your particle filter, which of the following changes to your particle filter tuning parameters are likely to improve the situation? (Choose ALL that apply.)

- Increase the number of particles
- Decrease the number of particles
- Increase sigma of your importance weighting function
- Decrease sigma of your importance weighting function
- Use deepcopy

### Question 13:
When using the resampling wheel technique discussed in the lecture videos, the same particle will never be picked twice in a row. [Assume the largest particle weight makes up 25% of the total sum of the weights.]

- True
- False

#### **Answer:** False

#### **Explanation:**
- In the **resampling wheel** technique, particles are selected with a probability proportional to their weights. While particles with higher weights are more likely to be selected, it is still possible for a particle to be picked multiple times in a row.
- In this scenario, since the largest particle weight makes up 25% of the total sum of the weights, it is likely that this particle will be picked frequently, but it is **not impossible** for it to be selected twice or more consecutively.
- This randomness is part of the probabilistic nature of the resampling process.

### Question 14:
If A and B are independent random variables, and $P(A) = 0.2$ and $P(B) = 0.3$, what is $P(A \text{ or } B)$? Note that "A or B" means "Only A, only B, or both A and B."

#### **Answer:** 
$$
P(A \text{ or } B) = 0.44
$$

#### **Explanation & Steps:**
The formula for the probability of $A \text{ or } B$ (i.e., the union of A and B) is:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

Since A and B are independent events, the probability of both A and B happening (i.e., $P(A \cap B)$) is:

$$
P(A \cap B) = P(A) \times P(B) = 0.2 \times 0.3 = 0.06
$$

Now, substitute the values into the formula for $P(A \cup B)$:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B) = 0.2 + 0.3 - 0.06 = 0.44
$$

Thus, $P(A \text{ or } B) = 0.44$.



### Question 15:
**[True or False]**  
In particle filters, during each iteration, we should resample the particles before determining their importance weights to make sure we are only calculating weights for the particles that matter.

#### **Answer:** False

#### **Explanation:**
- In a particle filter, the **importance weights** are calculated **before resampling**. The weights represent how well each particle matches the observed measurements. Resampling is done **after** the weights are computed to focus on particles that have higher weights (i.e., those that better match the observations).
- Resampling before calculating weights would defeat the purpose, as you wouldn’t know which particles are more important without first determining the weights based on the current measurement. Therefore, particles are resampled **after** the weight calculation step.



### Question 16:
Label each of the Gaussian distributions based on its relative value of \( \sigma \) (sigma).
![](https://github.com/EbramTawfik/Notes/blob/main/AI4R/Practice/Images/16.png)
- **A:** [Choose]  
- **B:** [Choose]  
- **C:** [Choose]

#### Options:
- Small
- Medium
- Large

#### **Answer:**
- **A:** Medium  
- **B:** Small  
- **C:** Large  

#### **Explanation:**
- The standard deviation \( \sigma \) controls the spread of a Gaussian distribution.
  - A **small** \( \sigma \) results in a narrow, tall peak (as shown in distribution **B**).
  - A **large** \( \sigma \) results in a wide, flat curve (as shown in distribution **C**).
  - **A** represents a medium \( \sigma \) with a distribution between these two extremes.

### Question 17:
**[True or False]**  
When using online Graph SLAM, any included measurements with an error that exceeds the modeled measurement uncertainty will cause future position estimates to have increased error.

#### **Answer:** True

#### **Explanation:**
- In **Graph SLAM**, errors in the measurements are propagated through the system. If a measurement has an error that exceeds the modeled uncertainty and is not properly accounted for, it can lead to incorrect position estimates.
- This incorrect information can affect future position estimates as the graph becomes more constrained based on these measurements. The system will integrate this erroneous information into the map, increasing the overall error.
- Ensuring accurate measurement models and outlier detection mechanisms helps mitigate such issues.

### Question 18:
**[True or False]**  
In SLAM, the probability distribution representing the final robot location after a sequence of noisy movements can be calculated by adding together the individual distributions representing each movement.

#### **Answer:** False

#### **Explanation:**
- In **SLAM**, the final probability distribution is not calculated by simply adding the individual distributions.
- Instead, these distributions are combined using **convolution** to properly account for the accumulation of uncertainty over time. Convolution ensures that the resulting distribution reflects the combined effects of all movements and their respective uncertainties.
- Adding distributions would not appropriately handle the probabilistic nature of movement, leading to an incorrect final estimate.


### Question 19:
**[True or False]**  
A particle filter with no motion noise, no fuzzing, and a constant number of resampled particles will usually have all particles converge to a single point.

#### **Answer:** True

#### **Explanation:**
- Without **motion noise** and **fuzzing** (random perturbation), a particle filter will continuously resample the particles based solely on their weights. 
- Since there is no noise to spread the particles, the particles will tend to accumulate and **converge** to a single point that represents the most likely estimate of the state.
- In the absence of noise and variation, particles lose diversity over time and concentrate around the best estimate, leading to convergence.


### Question 20:
A mapping from all states (such as each of the particular squares in a gridworld) to the actions to take in those states is called:

- a policy
- an admissible heuristic
- a plan
- a state space

#### **Answer:** a policy

#### **Explanation:**
- A **policy** in the context of reinforcement learning or decision-making is a mapping from **states** to **actions**.
- In a **gridworld** or similar environments, a policy dictates the action that the agent should take for each specific state it encounters.
- Other options, such as "plan" or "state space," refer to broader concepts, while an "admissible heuristic" is used in search algorithms but doesn't refer to action mapping directly.