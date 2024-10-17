

### 1. **Tracking Intro Quiz**
**Question:**  
You are given a sequence of object detections at time steps t=0, 1, 2, and 3. Where do you predict the object will be at t=4?

**Answer:**  
The object will likely continue moving along the same trajectory. By analyzing the velocity (direction and speed) between the previous time steps, you can predict where the object will be at t=4.

**Explanation:**  
Kalman filters use observations of previous positions to estimate the object's velocity. Based on this velocity, the filter predicts the next position.

---

### 2. **Gaussian Intro Quiz**
**Question:**  
Which of the following functions are Gaussian?  
1. A bell-shaped curve with a single peak.
2. A function with two peaks.
3. A steep, narrow curve with one peak.

**Answer:**  
1 and 3 are Gaussians, as they both have a single peak and exhibit the characteristic bell shape of a Gaussian distribution.

**Explanation:**  
A Gaussian distribution is unimodal (has one peak) and symmetrical. Bimodal distributions (two peaks) are not Gaussians.

---

### 3. **Variance Comparison Quiz**
**Question:**  
Given three Gaussian curves, one wide, one narrow, and one in between, rank their variances.

**Answer:**  
- The widest curve has the largest variance.
- The narrowest curve has the smallest variance.
- The middle curve has medium variance.

**Explanation:**  
The variance represents the spread of the Gaussian. A wider curve means more uncertainty (larger variance), while a narrower curve indicates more confidence (smaller variance).

---

### 4. **Preferred Gaussian Quiz**
**Question:**  
When tracking another car, which Gaussian would you prefer: a wide one, a narrow one, or a medium one?

**Answer:**  
You would prefer the narrowest Gaussian because it represents the most certainty about the car’s location.

**Explanation:**  
The smaller the variance, the more confident you are about the state estimate. In a self-driving car, high certainty reduces the risk of collision.

---

### 5. **Evaluate Gaussian Quiz**
**Question:**  
Given the following parameters:
- μ = 10
- σ² = 4
- x = 8  
What is the value of the Gaussian function at x?

**Answer:**  
Approximately 0.12.

**Explanation:**  
The equation for the Gaussian function is:
\[
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
\]
Substituting the values gives approximately 0.12.

---

### 6. **Maximize Gaussian Quiz**
**Question:**  
How do you modify x to get the maximum return value for the Gaussian function \( f(x) \)?

**Answer:**  
Set \( x = \mu \), which maximizes the Gaussian function.

**Explanation:**  
The Gaussian reaches its peak when \( x = \mu \), because the exponent term becomes zero, giving the maximum value of the function.

---

### 7. **Measurement and Motion 1 Quiz**
**Question:**  
Which update step requires a product, and which one requires a convolution: measurement or motion?

**Answer:**  
- **Measurement:** Product
- **Motion:** Convolution

**Explanation:**  
- The measurement update uses **Bayes’ Rule**, which involves multiplying the prior with the likelihood (product).
- The motion update uses the **Total Probability Theorem**, which involves summing over all possible future states (convolution).

---

### 8. **Measurement and Motion 2 Quiz**
**Question:**  
Does Bayes' Rule apply to measurements or motion? Does total probability apply to measurements or motion?

**Answer:**  
- **Bayes' Rule:** Applies to measurements.
- **Total Probability:** Applies to motion.

**Explanation:**  
- In the measurement update, Bayes' Rule is used to combine the prior belief and the likelihood.
- In the motion update, total probability is used to predict the next state.

---

### 9. **Shifting the Mean Quiz**
**Question:**  
Given a prior and a measurement with different means, where will the new mean be after combining them?

**Answer:**  
The new mean will be between the prior mean and the measurement mean, closer to the one with the smaller variance (more certainty).

**Explanation:**  
The new mean is a weighted average of the prior and measurement means, with weights determined by their variances. The more certain measurement (smaller variance) pulls the mean closer.

---

### 10. **Predicting the Peak Quiz**
**Question:**  
Will the updated Gaussian after combining two Gaussians be:
1. Wider,
2. Narrower,
3. The same as the prior Gaussian?

**Answer:**  
Narrower.

**Explanation:**  
When combining two Gaussians, the variance decreases, representing increased certainty. The result is a narrower, more "peaky" Gaussian.

---

### 11. **Parameter Update Quiz**
**Question:**  
Given two Gaussians with equal variance but different means, compute the new mean and variance.

**Answer:**  
- **New Mean:** The average of the two means.
- **New Variance:** Half of the original variance.

**Explanation:**  
When the variances are equal, the new mean is simply the average of the two means. The new variance is smaller than either of the original variances, as you are more certain after combining them.

---

### 12. **Separated Gaussians Quiz**
**Question:**  
What happens to the resulting variance when you combine two separated Gaussians?

**Answer:**  
The variance decreases, making the resulting Gaussian narrower and more certain.

**Explanation:**  
The Kalman filter combines the prior and measurement distributions, and the combined result has less uncertainty than either one individually.

---

### 13. **New Mean and Variance Quiz**
**Question:**  
Given two Gaussians with means 10 and 13, and variances 8 and 2, calculate the new mean and variance after combining them.

**Answer:**  
- **New Mean:** 12.4
- **New Variance:** 1.6

**Explanation:**  
The more certain measurement (with variance 2) has a greater influence on the new mean. The new variance is smaller than both original variances, indicating greater certainty.

---

### 14. **Gaussian Motion Quiz**
**Question:**  
Given a Gaussian with mean 8 and variance 4, and a motion with uncertainty 6, what is the new predicted mean and variance after applying the motion?

**Answer:**  
- **New Mean:** 18
- **New Variance:** 10

**Explanation:**  
The motion adds 10 units to the mean, and the uncertainties (variances) are added together to produce a new variance of 10.

---

### 15. **Kalman Prediction Quiz**
**Question:**  
Given a state transition matrix \( F \) and an initial state estimate, predict the next state.

**Answer:**  
The next state is calculated by multiplying the state transition matrix \( F \) with the current state.

**Explanation:**  
The prediction step involves applying the state transition model to the current state to predict the next state.

---

### 16. **Another Prediction Quiz**
**Question:**  
What happens to the uncertainty after the prediction step?

**Answer:**  
The uncertainty increases because the motion introduces additional uncertainty.

**Explanation:**  
The prediction step increases the variance as the motion adds more uncertainty to the state estimate.

---
