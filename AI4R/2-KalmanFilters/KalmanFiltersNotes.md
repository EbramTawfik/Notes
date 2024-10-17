### 1. **Kalman Filters Introduction**

**Overview:**
- **Location:** Stanford University, VALE (Stanford's Automotive Research Center)
- **Focus:** Introduction to Kalman Filters using Stanford's self-driving cars.
- **Example:** "Junior" is Stanford’s most recent self-driving car, using sensors to detect other vehicles and prevent collisions.

**Key Equipment:**
- **Laser Range Finder:** Takes distance scans 10 times per second (about a million data points). Crucial for detecting obstacles and cars.
- **Cameras:** Stereo camera system and a GPS system, used to localize the car and input into the Kalman filter.

### 2. **Tracking Intro**

**Overview:**
- Google’s self-driving car uses sensors (lasers, radars) to track the movement of other cars, pedestrians, and cyclists.
- The Kalman filter helps predict both the location and velocity of moving objects based on sensor data.

**Kalman Filter Characteristics:**
- **Continuous State Estimation:** Unlike Monte Carlo localization, Kalman filters operate in a continuous state space.
- **Unimodal Distribution:** Kalman filters assume a single, continuous peak of probability, representing the state estimate.

### 3. **Tracking Intro (Answer)**

**Object Tracking:**
- When an object is detected at various time steps, the Kalman filter can estimate its velocity and predict where it will be in the next step.
- The filter relies on data from noisy sensors (like radar and laser data) to track moving objects accurately.

### 4. **Gaussian Intro**

**Overview:**
- Kalman filters represent uncertainty using Gaussian distributions (normal distributions).
- Each distribution is defined by two parameters:
  - **Mean (μ):** Represents the most likely state.
  - **Variance (σ²):** Represents the uncertainty of the estimate.

**Gaussian Equations:**
- The probability density function of a Gaussian:
  \[
  f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
  \]
  where \( \mu \) is the mean, and \( \sigma^2 \) is the variance.

### 5. **Variance Comparison**

- **Small Variance:** A smaller variance indicates higher certainty about the state estimate (i.e., the Gaussian is more "peaky").
- **Large Variance:** A larger variance means more uncertainty (i.e., a wider Gaussian curve).

### 6. **Preferred Gaussian**

- When tracking another car, you would prefer the Gaussian with the smallest variance because it represents the most certainty about the car’s position and velocity.

### 7. **Evaluate Gaussian**

**Overview:**
- A function f(x) evaluates the probability density of a given state.
- Example:
  \[
  \text{For } \mu = 10, \sigma^2 = 4, \text{ and } x = 8, f(x) \approx 0.12
  \]
  This function helps estimate the likelihood of the car being at a specific position.

### 8. **Maximize Gaussian**

- To maximize the Gaussian, set \( x = \mu \), which gives the peak of the curve where the probability is highest.

### 9. **Measurement and Motion 1**

- In Kalman filters, there are two key updates:
  - **Measurement Update:** Incorporates sensor readings to correct the state.
  - **Motion Update (Prediction):** Incorporates the system’s motion model to predict the next state.

### 10. **Measurement and Motion 2**

- **Measurement Update:** Uses **Bayes’ Rule** (multiplication) to combine prior knowledge with the measurement data.
- **Motion Update:** Uses **Total Probability** (convolution) to add the predicted motion to the current state.

### 11. **Shifting the Mean**

- When you combine two Gaussians, the new mean lies between the prior mean and the measurement mean, weighted by their uncertainties. The smaller the variance, the more weight the measurement carries.

### 12. **Predicting the Peak**

- After the measurement update, the peak of the Gaussian shifts towards the more certain measurement, and the variance decreases, representing increased certainty.

### 13. **Parameter Update**

- The update equations for the Kalman filter are:
  - **New Mean:** 
    \[
    \mu' = \frac{\sigma^2_{\text{measurement}} \cdot \mu_{\text{prior}} + \sigma^2_{\text{prior}} \cdot \mu_{\text{measurement}}}{\sigma^2_{\text{prior}} + \sigma^2_{\text{measurement}}}
    \]
  - **New Variance:**
    \[
    \sigma'^2 = \frac{1}{\frac{1}{\sigma^2_{\text{prior}}} + \frac{1}{\sigma^2_{\text{measurement}}}}
    \]

### 14. **Separated Gaussians**

- When combining two Gaussian distributions, the resulting variance is always smaller than either of the original variances, indicating increased certainty.

### 15. **New Mean and Variance**

- Example of how the new mean and variance are calculated using the update equations:
  \[
  \mu' = 12.4, \sigma'^2 = 1.6
  \]
  The mean is closer to the more certain measurement, and the variance decreases.

### 16. **Gaussian Motion**

- The **motion update** adds the system’s predicted movement to the current state:
  - **New Mean:** \( \mu' = \mu + u \)
  - **New Variance:** \( \sigma'^2 = \sigma^2 + r^2 \)
  where \( u \) is the motion, and \( r^2 \) is the motion uncertainty.

### 17. **Predict Function**

- Python code to predict the new state after motion:
  ```python
  def predict(mean, var, motion, motion_var):
      new_mean = mean + motion
      new_var = var + motion_var
      return [new_mean, new_var]
  ```

### 18. **Kalman Filter Code**

- A Python implementation of the Kalman filter to predict the state:
  ```python
  def kalman_filter(x, P):
      for n in range(len(measurements)):
          # Measurement update
          Z = matrix([[measurements[n]]])
          y = Z - (H * x)
          S = H * P * H.transpose() + R
          K = P * H.transpose() * S.inverse()
          x = x + (K * y)
          P = (I - (K * H)) * P

          # Prediction
          x = (F * x) + u
          P = F * P * F.transpose()
      return x, P
  ```

### 19. **Kalman Prediction**

- The Kalman filter alternates between **prediction** (motion update) and **correction** (measurement update) to refine its estimate of the state.

### 20. **Kalman Filter Land**

- In a higher-dimensional Kalman filter, we estimate multiple variables, such as position and velocity. The state is represented by a **mean vector** and a **covariance matrix**.

### 21. **Kalman Filter Prediction**

- The prediction step uses the state transition matrix \( F \) to predict the future state:
  \[
  x' = F \cdot x + u
  \]
  The covariance is updated as:
  \[
  P' = F \cdot P \cdot F^T + Q
  \]

### 22. **Another Prediction**

- The Kalman filter can handle multiple predictions over time, refining its estimates as more measurements become available.

### 23. **More Kalman Filters**

- **Hidden States:** In Kalman filters, variables that cannot be directly observed (e.g., velocity) are inferred using the correlation between state variables.

### 24. **Kalman Filter Design**

- The Kalman filter requires two key models:
  1. **State Transition Model:** Describes how the system evolves.
  2. **Measurement Model:** Describes how the measurements relate to the state.

### 25. **Kalman Matrices**

- **State Transition Matrix (F):** Describes how the state evolves over time.
- **Measurement Matrix (H):** Describes how the state is measured.
- **Covariance (P):** Represents the uncertainty in the state estimate.
- **Kalman Gain (K):** Determines how much to weigh the prediction vs the measurement in updating the estimate.

### 26. **Conclusion**

- The Kalman filter is a fundamental tool in control systems, robotics, and AI for estimating the state of a system from noisy sensor data. It balances predictions from motion models with real-world sensor measurements to produce accurate state estimates over time.
