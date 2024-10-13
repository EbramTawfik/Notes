# Localization

---

### Key Points: Localization and GPS Limitations

- **Localization** is the process of determining the robot’s position.
- GPS errors (ranging from 2-10 meters) are too large for precise tasks like self-driving cars, which require **centimeter-level accuracy** (2-10 cm).
- **Accurate Localization**: Combining sensor data with advanced algorithms allows systems (e.g., Google's self-driving cars) to achieve this level of precision.

---

### Localization: Understanding the Core Concept

**Localization** is the process by which a robot determines its position in the environment. In the context of robotics, this is a critical problem because knowing where the robot is located in space is essential for tasks like navigation, path planning, and interacting with its environment.

#### Key Problem: Why is Localization Difficult?

1. **Imperfect Information**: 
   - The robot doesn't have perfect sensors. It receives noisy sensor data, meaning that the measurements it takes are not always accurate.
   - The movements made by the robot may not always go as planned, due to errors in actuators or external conditions like slippery floors or uneven terrain.

2. **Goal**: 
   - The goal of localization is to estimate the robot's position as accurately as possible despite these sources of uncertainty.
   - **Self-driving cars**, for example, require localization accuracy within **2 to 10 centimeters** to ensure safe navigation.

---

### Localization Process: Motion and Sensing

Localization typically involves two steps:
1. **Motion Update (Prediction)**: When the robot moves, it updates its belief about where it might be based on its previous position and how far it has moved. However, due to uncertainty in movement, the robot can't be sure exactly where it ended up.
   
2. **Sensing Update (Correction)**: The robot uses its sensors (like cameras, laser scanners, or sonar) to gather data from the environment. It compares this sensor data to a map or model of the world and updates its belief about where it is.

---

### Probability in Localization

The key to understanding localization lies in the use of **probability theory**. In localization, probability is used to represent the robot's belief about where it might be.

#### 1. **Belief Representation**: 
- The robot’s belief about its location is represented as a **probability distribution** over all possible locations.
- Initially, if the robot has no information, this distribution might be uniform, meaning it considers all positions equally likely.
  
#### 2. **Bayes' Rule**:
- **Bayesian filtering** is central to localization. The robot maintains a belief about its position, which gets updated based on new sensor information and movement data.
- Bayes' rule allows the robot to update its belief about its current state based on the likelihood of a measurement:
  
  \[
  P(X_i | Z) = \frac{P(Z | X_i) \cdot P(X_i)}{P(Z)}
  \]
  
  Where:
  - \( P(X_i | Z) \) is the updated belief (posterior probability) that the robot is in position \( X_i \), given the measurement \( Z \).
  - \( P(Z | X_i) \) is the likelihood of getting the measurement \( Z \) if the robot is actually in position \( X_i \).
  - \( P(X_i) \) is the prior belief that the robot is in position \( X_i \).
  - \( P(Z) \) is the probability of receiving the measurement \( Z \).

---

### Motion Model: Accounting for Movement Uncertainty

When the robot moves, it doesn’t move perfectly. Instead, the motion is subject to noise, such as slipping or inaccurate motors.

#### Key Points about Motion:
- The robot's belief spreads out when it moves, representing the fact that the exact position becomes less certain.
- **Convolution** is used in the motion update step. This process takes the prior belief and distributes it over a range of possible new positions according to the movement uncertainty.

For example, if the robot is certain it was in a particular cell, after moving one step, the belief will spread to nearby cells to reflect the uncertainty in the movement.

#### Total Probability in Motion:

The **total probability theorem** is used when the robot updates its belief based on the motion. It accounts for the fact that the robot could have come from multiple different locations.

The updated belief \( P(X_i^t) \) at time \( t \) is computed by summing the probabilities from all possible previous locations \( X_j^{t-1} \):

\[
P(X_i^t) = \sum_j P(X_j^{t-1}) \cdot P(X_i | X_j)
\]

---

### Sensing: Gaining Information

The robot gathers information using its sensors. These sensors are not perfect, so measurements also have uncertainty. When the robot senses, it compares the measurements it makes with the expected measurements for different positions in the world.

#### Key Points about Sensing:
- **Sensing reduces uncertainty**: After taking a sensor reading, the robot updates its belief to be more certain about where it is. 
- The robot adjusts its belief using the measurement likelihoods, i.e., how likely it is to get the observed measurement from each possible position.

#### Entropy in Localization:

- **Entropy** measures the uncertainty in the robot’s belief. Lower entropy means more certainty about the robot's position, while higher entropy means less certainty.
  
  The entropy of a probability distribution is given by:

  \[
  \text{Entropy} = - \sum p(x) \log p(x)
  \]

- **Movement increases entropy** because it introduces uncertainty (as the robot isn’t sure exactly where it ended up).
- **Sensing decreases entropy** because it provides additional information that refines the robot's belief about its position.

---

### Bayes' Rule in Action: Practical Example

Let’s apply Bayes' rule to a practical example:

#### Cancer Test Problem

In this example, you're given:
- \( P(C) = 0.001 \) (Probability of having cancer)
- \( P(\neg C) = 0.999 \) (Probability of not having cancer)
- \( P(\text{Pos} | C) = 0.8 \) (Probability of a positive test result given cancer)
- \( P(\text{Pos} | \neg C) = 0.1 \) (Probability of a positive result given no cancer)

The goal is to compute the probability of having cancer given a positive test result \( P(C | \text{Pos}) \).

**Solution**:

Using Bayes' Rule:

\[
P(C | \text{Pos}) = \frac{P(\text{Pos} | C) P(C)}{P(\text{Pos})}
\]

Where \( P(\text{Pos}) \) is the total probability of getting a positive test result:

\[
P(\text{Pos}) = P(\text{Pos} | C) P(C) + P(\text{Pos} | \neg C) P(\neg C)
\]

Substitute the known values:

\[
P(\text{Pos}) = (0.8 \times 0.001) + (0.1 \times 0.999) = 0.0008 + 0.0999 = 0.1007
\]

Finally, calculate \( P(C | \text{Pos}) \):

\[
P(C | \text{Pos}) = \frac{0.8 \times 0.001}{0.1007} \approx 0.0079
\]

So, there is a **0.79%** chance of having cancer given a positive test result.

---

### Limit Distribution in Localization

The **limit distribution** refers to the belief that results after several iterations of sensing and moving. Over time, if the robot continues to receive similar sensor readings, the belief distribution will converge to a stable state where each grid cell has an equal probability. This is called the **uniform distribution**, where each cell has the same probability, indicating maximum uncertainty.

---

### Conclusion

In summary, localization is a fundamental problem in robotics, and it relies heavily on probability theory to deal with uncertainties in both motion and sensing. Through techniques like **Bayesian filtering**, **convolution**, and **entropy calculations**, a robot can continuously refine its belief about its position, achieving more accurate localization over time despite the noise in its sensors and movements.

This detailed breakdown covers the core concepts discussed, focusing on the mathematical models, probability rules, and their application to real-world localization tasks.