### 1. **Kalman Filter**  
A recursive algorithm that provides an efficient way to estimate the state of a system from noisy sensor data. It combines predictions from a model (motion update) with observations from sensors (measurement update) to produce an estimate of the current state and its uncertainty.

### 2. **State ($x$)**  
In the context of Kalman filters, the state represents all the variables necessary to describe the system at a given point in time. For example, in a self-driving car, the state could include position, velocity, and orientation.

### 3. **Mean ($\mu$)**  
The central estimate of the system’s state. In Kalman filters, the mean represents the best guess of the system’s state at a given time step.

### 4. **Variance ($\sigma^2$)**  
A measure of uncertainty associated with the state estimate. A higher variance means more uncertainty about the state, while a lower variance means more confidence in the estimate.

### 5. **Gaussian Distribution (Normal Distribution)**  
A continuous probability distribution characterized by a bell-shaped curve. In Kalman filters, the belief about the state is represented by a Gaussian distribution, defined by its mean ($\mu$) and variance ($\sigma^2$). It has two properties:
  - **Unimodal:** Single peak.
  - **Symmetrical:** Evenly spread around the mean.

### 6. **Covariance ($\Sigma$)**  
For multidimensional systems, the covariance matrix represents the uncertainty of each state variable and the correlation between them. It is a matrix that quantifies the uncertainty and correlation of the system's states.

### 7. **Multivariate Gaussian**  
A generalization of the Gaussian distribution to higher dimensions, where the state is represented by a mean vector and a covariance matrix.

### 8. **State Transition Matrix ($F$)**  
A matrix that describes how the state evolves over time. It models the relationship between the current state and the next state based on the motion of the system.

### 9. **Measurement Matrix ($H$)**  
A matrix that models the relationship between the state and the observations (sensor readings). It translates the state into the measurement space.

### 10. **Kalman Gain ($K$)**  
A weighting factor used during the measurement update. It balances the contributions from the prediction and the measurement to produce the updated state estimate.

### 11. **Measurement Update (Correction Step)**  
The step in the Kalman filter where sensor measurements are used to update the state estimate. This step combines the predicted state with the observed measurement to produce a corrected estimate.

### 12. **Prediction Update (Motion Step)**  
The step where the system’s state is predicted based on its previous state and motion model. This step updates the state and uncertainty based on how the system is expected to evolve over time.

### 13. **Unimodal vs Multimodal Distributions**  
- **Unimodal Distribution:** A distribution with a single peak, typical in Kalman filters.
- **Multimodal Distribution:** A distribution with multiple peaks, more common in Monte Carlo localization and particle filters.

### 14. **Bayes' Rule**  
A fundamental principle used in the measurement update step, where the Kalman filter multiplies the prediction (prior) with the measurement (likelihood) to obtain the updated estimate (posterior).

### 15. **Total Probability (Convolution)**  
The principle used in the motion update step, where the Kalman filter convolves the prediction with the uncertainty in the motion model.

### 16. **Separation of Variables: Observable vs Hidden**  
In Kalman filters, the state variables are often split into:
- **Observable Variables:** Can be directly measured (e.g., position).
- **Hidden Variables:** Cannot be directly measured but can be inferred (e.g., velocity).

### 17. **Importance of Covariance**  
The covariance (uncertainty) of the Gaussian becomes narrower (more certain) when new information is incorporated, such as through measurements, which reduces the variance.

### 18. **Predict and Update Cycle**  
Kalman filters iterate between two key steps:
- **Predict:** Uses the state transition matrix to predict the new state based on the motion model.
- **Update:** Combines the prediction with the measurement to refine the state estimate.

### 19. **Multidimensional Kalman Filter**  
In higher dimensions, Kalman filters can track multiple variables, such as position and velocity. The multivariate Gaussian allows correlation between these variables, improving predictions by considering relationships like how velocity affects future positions.

### 20. **Correlation in Multidimensional Systems**  
If the uncertainty of one variable (e.g., position) is correlated with another (e.g., velocity), changes in one can inform changes in the other, helping refine estimates.

### 21. **Motion Uncertainty ($r^2$)**  
The uncertainty associated with the system’s movement or motion commands, which is added to the overall uncertainty during the prediction step.

### 22. **Measurement Noise ($R$)**  
Noise or uncertainty inherent in the sensor measurements, represented by the matrix $R$ in the Kalman filter equations.
