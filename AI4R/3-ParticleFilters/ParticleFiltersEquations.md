
### **1. Probability of a State Given a Measurement (Bayes’ Rule)**

The update rule for the probability of the robot's state $X$ given the measurement $Z$:


$$
P(X | Z) \propto P(Z | X) P(X)
$$


- **Explanation**: This is the **measurement update**. The posterior probability of the state given the measurement is proportional to the likelihood of the measurement given the state times the prior probability of the state.

---

### **2. Motion Update (Prediction Step)**

The predicted probability distribution after motion, denoted by $P(X')$:


$$
P(X') = \sum P(X' | X) P(X)
$$


- **Explanation**: This is the **motion update** or prediction step, where the state of each particle is updated based on the motion model and the prior belief. The predicted state $X'$ depends on the transition probability $P(X' | X)$ and the prior state distribution $P(X)$.

---

### **3. Weight Update (Measurement Update)**

Each particle is assigned a weight based on how well its predicted sensor reading matches the actual sensor measurement. The updated weight for particle $i$ is:


$$
w_i \propto P(Z | X_i)
$$


- **Explanation**: The importance weight $w_i$ is proportional to the likelihood of the actual sensor measurement $Z$ given the particle’s state $X_i$.

---

### **4. Normalizing Weights**

To normalize the importance weights of all particles:


$$
\alpha_i = \frac{w_i}{\sum_{j} w_j}
$$


- **Explanation**: The normalized weight $\alpha_i$ is the weight $w_i$ divided by the sum of all particle weights. The sum of all normalized weights should equal 1.

---

### **5. Total Weight of Particles**

The total weight of all particles, $W$, is computed as:


$$
W = \sum_{i=1}^{N} w_i
$$


- **Explanation**: The total weight $W$ is the sum of the weights of all particles. This is used in resampling to normalize the weights.

---

### **6. Resampling Probability**

In the resampling step, particles are drawn with probability proportional to their normalized weights. The probability of selecting particle $i$ during resampling is:


$$
P(i) = \frac{w_i}{\sum_{j} w_j}
$$


- **Explanation**: The probability of resampling particle $i$ is proportional to its weight relative to the sum of all particle weights.

---

### **7. Probability of Never Sampling a Particle (Resampling Step)**

The probability that a particle $P_i$ is never sampled after $N$ resampling steps is given by:


$$
P(\text{not selected}) = (1 - \alpha_i)^N
$$


- **Explanation**: This formula calculates the probability that a particle $i$, with a normalized weight $\alpha_i$, is never selected after $N$ resampling steps.

---

### **8. Measurement Probability for Importance Weight Calculation**

The likelihood of obtaining a specific sensor measurement $Z$, given the predicted measurement from a particle's state $X_i$, assuming Gaussian noise:


$$
P(Z | X_i) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp \left( -\frac{(Z - Z_i)^2}{2\sigma^2} \right)
$$


- **Explanation**: This is the Gaussian probability distribution function used to calculate the likelihood of a sensor measurement $Z$, given the predicted measurement $Z_i$ from particle $i$. $\sigma^2$ is the variance of the sensor noise.

---

### **9. Robot Motion with Noise**

When moving a robot with some control inputs and noise, the new state of the robot (particle) can be modeled as:


$$
x' = x + \delta_x + \text{noise}_x
$$


$$
y' = y + \delta_y + \text{noise}_y
$$


$$
\theta' = \theta + \delta_\theta + \text{noise}_\theta
$$


- **Explanation**: The new position $(x', y')$ and orientation $\theta'$ of a particle are the result of applying the motion model with some added noise to simulate the uncertainty in motion.

---

### **10. Resampling Wheel Algorithm**

In the **Resampling Wheel** algorithm, a running cumulative weight $\beta$ is used to select particles. For each resampling step, $\beta$ is updated:


$$
\beta = \beta + \text{random}(0, 2 \times w_{\text{max}})
$$


- **Explanation**: Here, $\beta$ is incremented by a random value between 0 and $2 \times w_{\text{max}}$, where $w_{\text{max}}$ is the maximum particle weight. The algorithm cycles through particles using this cumulative weight to select particles based on their importance weights.

---

### **11. Convolution in the Motion Update**

In the motion update step, the convolution of the prior belief with the transition model is used to predict the future state. Mathematically, convolution is applied as:


$$
P(X' | X) * P(X)
$$


- **Explanation**: Convolution here refers to combining the robot's prior belief with the transition probability (motion model) to generate the new predicted state distribution.

---

### **12. Gaussian Noise in Motion and Sensor Models**

Both the motion and sensor models include Gaussian noise, which can be described by the Gaussian distribution formula:


$$
P(x) = \frac{1}{\sqrt{2\pi \sigma^2}} \exp \left( -\frac{(x - \mu)^2}{2\sigma^2} \right)
$$


- **Explanation**: This formula is used to model the uncertainty in both the robot’s motion and sensor measurements. $\mu$ is the expected value (mean), and $\sigma^2$ is the variance (spread) of the noise.
