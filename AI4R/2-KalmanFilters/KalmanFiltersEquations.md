### 1. **Gaussian Probability Distribution Function**

A Gaussian distribution (or normal distribution) is used in Kalman filters to represent uncertainty about the state of a system. It is defined by the mean (μ) and the variance (σ²).

#### Equation:
\[
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
\]
- **μ (Mean):** The most likely value of the state.
- **σ² (Variance):** The uncertainty or spread of the distribution.
- The **Gaussian** is "peaky" when the variance is small (low uncertainty) and "wider" when the variance is large (high uncertainty).

---

### 2. **New Mean and Variance (Measurement Update)**

When new measurement data is received, the Kalman filter updates the mean and variance of the state estimate by combining the previous state (prior) and the measurement.

#### Mean Update Equation:
\[
\mu' = \frac{\sigma^2_{\text{measurement}} \cdot \mu_{\text{prior}} + \sigma^2_{\text{prior}} \cdot \mu_{\text{measurement}}}{\sigma^2_{\text{prior}} + \sigma^2_{\text{measurement}}}
\]
- **μ' (New Mean):** The updated state estimate after incorporating the measurement.
- **μ_prior:** The prior state estimate (before incorporating the measurement).
- **μ_measurement:** The value of the measurement.
- **σ²_prior:** The uncertainty of the prior estimate.
- **σ²_measurement:** The uncertainty of the measurement.

#### Variance Update Equation:
\[
\sigma'^2 = \frac{1}{\frac{1}{\sigma^2_{\text{prior}}} + \frac{1}{\sigma^2_{\text{measurement}}}}
\]
- **σ'² (New Variance):** The updated uncertainty after incorporating the measurement.
- The new variance is always smaller than the original variance, representing greater certainty in the estimate after combining the measurement and the prior.

---

### 3. **Motion Update (Prediction Step)**

The prediction step updates the state estimate based on the system’s motion model. The Kalman filter adds the expected movement to the current state and accounts for the uncertainty in the motion.

#### Mean Prediction Equation:
\[
\mu' = \mu + u
\]
- **μ' (New Mean):** The predicted new state after the motion.
- **μ:** The current state estimate.
- **u:** The motion or control input (e.g., how far the car moves).

#### Variance Prediction Equation:
\[
\sigma'^2 = \sigma^2 + r^2
\]
- **σ'² (New Variance):** The updated uncertainty after predicting the motion.
- **σ²:** The current uncertainty in the state.
- **r²:** The uncertainty in the motion.

In the motion update step, both the mean and variance are updated. The motion increases the uncertainty, as represented by the addition of the motion uncertainty \( r^2 \).

---

### 4. **Kalman Gain (K)**

The **Kalman Gain** controls how much weight the Kalman filter gives to the measurement compared to the prediction. It is used in the measurement update step.

#### Equation:
\[
K = \frac{P \cdot H^T}{H \cdot P \cdot H^T + R}
\]
- **K (Kalman Gain):** The weight assigned to the measurement.
- **P:** The covariance matrix (representing uncertainty in the state).
- **H:** The measurement matrix (maps the state to the measurement space).
- **R:** The measurement noise (uncertainty in the sensor data).
- **H^T:** The transpose of the measurement matrix.

The Kalman Gain adjusts how much the state is updated based on the measurement. If the measurement is highly uncertain (large R), less weight is given to the measurement.

---

### 5. **Measurement Update (Correction Step)**

After predicting the new state, the Kalman filter incorporates the actual measurement to correct the prediction. This step refines the state estimate by combining the predicted state with the measurement.

#### Equation for the State Update:
\[
x' = x + K \cdot (z - H \cdot x)
\]
- **x' (New State):** The updated state estimate.
- **x:** The predicted state estimate (before the measurement update).
- **z:** The actual measurement.
- **H:** The measurement matrix.
- **K:** The Kalman Gain (determines how much to adjust the estimate based on the measurement).

#### Equation for the Covariance Update:
\[
P' = (I - K \cdot H) \cdot P
\]
- **P' (Updated Covariance):** The updated uncertainty in the state after incorporating the measurement.
- **I:** The identity matrix.
- **K:** The Kalman Gain.
- **H:** The measurement matrix.

This update reduces the uncertainty in the state estimate, as the measurement provides new information about the system.

---

### 6. **State Transition (Prediction Step)**

In the prediction step, the Kalman filter updates the state using a state transition model. This model describes how the system evolves over time.

#### State Prediction Equation:
\[
x' = F \cdot x + u
\]
- **x' (Predicted State):** The state after the prediction.
- **F (State Transition Matrix):** Describes how the state evolves.
- **x:** The current state estimate.
- **u:** The control input or motion.

#### Covariance Prediction Equation:
\[
P' = F \cdot P \cdot F^T + Q
\]
- **P' (Predicted Covariance):** The uncertainty after the prediction.
- **P:** The current covariance.
- **F:** The state transition matrix.
- **F^T:** The transpose of the state transition matrix.
- **Q:** The process noise covariance (uncertainty in the process).

This step predicts the next state and updates the uncertainty before incorporating any measurements.

---

### 7. **Multivariate Gaussian (2D or Higher Dimensions)**

In a multidimensional system (e.g., tracking position and velocity), the state is represented by a **mean vector** and a **covariance matrix**. The multivariate Gaussian distribution generalizes the 1D Gaussian to multiple dimensions.

#### Probability Density Function for Multivariate Gaussian:
\[
f(x) = \frac{1}{\sqrt{(2\pi)^d |\Sigma|}} \exp\left( -\frac{1}{2} (x - \mu)^T \Sigma^{-1} (x - \mu) \right)
\]
- **x:** The state vector (e.g., position and velocity).
- **μ:** The mean vector.
- **Σ (Covariance Matrix):** Represents the uncertainty and correlations between different state variables (e.g., position and velocity).
- **d:** The number of dimensions in the state.
- **|Σ|:** The determinant of the covariance matrix.

This formula describes the likelihood of a state in a multidimensional system, where the state could include multiple variables, such as position and velocity.

---

### 8. **Correlation Between Variables**

In multivariate systems, the covariance matrix captures the correlation between variables (e.g., position and velocity). A positive correlation means that as one variable increases, the other likely increases as well.

#### Correlation Coefficient:
\[
\rho_{xy} = \frac{\text{Cov}(x, y)}{\sigma_x \sigma_y}
\]
- **ρxy (Correlation Coefficient):** Measures the strength of the relationship between two variables, x and y.
- **Cov(x, y):** The covariance between x and y.
- **σx, σy:** The standard deviations of x and y, respectively.

If ρ is positive, the two variables are positively correlated. If ρ is negative, they are negatively correlated. The closer ρ is to ±1, the stronger the correlation.

---