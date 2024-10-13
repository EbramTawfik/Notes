# Localization

### **Video 001 - Localization and GPS Accuracy**

#### Key Points:
1. **Problem: Localization**
   - The main problem is that a robot (or a car) does not know where it is in space. The task of **localization** is to determine the robot's position accurately.
   - GPS (Global Positioning System) is often used to solve this problem, but GPS typically has errors ranging from **2 to 10 meters**, which is too large for precise tasks like staying within lanes on a road.

2. **GPS Limitations**
   - GPS is not accurate enough for self-driving cars, as even small deviations (meters of error) can result in dangerous lane departures or crashes. For a self-driving car, localization with centimeter-level accuracy (2 to 10 cm) is required.

3. **Accurate Localization**
   - Modern solutions, such as those used in **Google's self-driving cars**, combine sensor data and advanced algorithms to achieve much higher accuracy, which is crucial for safely navigating within lanes, even when lane markers are missing.
   
4. **Basic Principle**
   - This video focuses on providing an **intuitive understanding** of how robots can localize themselves accurately before diving into the mathematical theory. This knowledge will eventually allow students to build their own localization systems and self-driving car programs.



### Understanding Localization and How It Works in the Code

#### **What is Localization?**
Localization is the process through which a robot determines its position within a known environment. The robot uses sensor data to make an educated guess about where it might be, and as it moves and takes more measurements, it refines its guess. Localization is a critical capability for autonomous systems, enabling them to navigate and perform tasks in complex environments.

The main goal is for the robot to maintain and update a **belief** (probability distribution) over where it might be, based on its **sensors** and its **movement**.

### **How Localization Works (In General)**

1. **Initial Belief (Uniform Distribution)**:
   - At the start, the robot doesn't know where it is, so it assumes it could be equally likely in any possible location in its environment. This is represented as a **uniform probability distribution** over all possible locations (i.e., equal probabilities for all places).

2. **Sensing and Measurement Updates**:
   - The robot senses something about its environment, like detecting a color, a wall, or a landmark. Based on this sensor data, it updates its belief.
   - This is called the **measurement update** step. It increases the probability of the robot being at locations where the sensor data matches the environment and decreases it where it doesn’t match.

3. **Movement and Motion Updates**:
   - As the robot moves, it shifts its belief distribution. For instance, if the robot moves forward, the belief distribution will shift to the right (or in the direction of motion).
   - However, movement is uncertain, so the belief distribution also spreads out slightly due to potential errors in the motion, leading to uncertainty about how far the robot actually moved.

4. **Repeated Process**:
   - The robot continually alternates between **sensing** and **moving**, each time updating its belief about where it might be. Over time, the belief becomes more focused on the robot’s actual location as it gathers more information.

---

### **How Localization Works in the Code Example**

In the code you provided, we see a simplified example of the **measurement update** step in the localization process.


```python
p = [0.2, 0.2, 0.2, 0.2, 0.2]
world = ['green', 'red', 'red', 'green', 'green']
Z = 'red'
pHit = 0.6
pMiss = 0.2

def sense(p, Z):
    q = []
    for i in range(len(p)):
        hit = (Z == world[i])  # Check if the sensor reading matches the world color
        q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
    return q

print(sense(p, Z))
```

### Code Breakdown:

1. **Initial Probability Distribution (p)**:
   ```python
   p = [0.2, 0.2, 0.2, 0.2, 0.2]
   ```
   This represents the robot’s **initial belief** about its location. It assumes it has an equal probability (0.2) of being in any of the five positions in the world. This is a typical starting point in localization when the robot doesn't know where it is.

2. **World Setup**:
   ```python
   world = ['green', 'red', 'red', 'green', 'green']
   ```
   The environment is a sequence of five positions, each of which has a color (either 'red' or 'green'). The robot doesn’t know where it is, but it will use sensor readings to update its belief.

3. **Sensing and Measurement:**
   ```python
   Z = 'red'
   ```
   The robot senses its environment and detects that it’s next to a 'red' tile. This information will be used to update the belief distribution based on how likely it is for the robot to be in each position, given this measurement.

4. **Hit and Miss Probabilities:**
   ```python
   pHit = 0.6
   pMiss = 0.2
   ```
   - **pHit** (0.6) is the probability that the robot’s sensor correctly identifies the color ('red' in this case).
   - **pMiss** (0.2) is the probability that the robot’s sensor incorrectly identifies the color.

   These probabilities account for the uncertainty in the sensor readings. Even if the robot senses 'red', there’s a chance it could be wrong, and it may not actually be in a 'red' position.

5. **The `sense` Function (Measurement Update):**
   ```python
   def sense(p, Z):
       q = []
       for i in range(len(p)):
           hit = (Z == world[i])  # Check if the sensor reading matches the world color
           q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
       return q
   ```
   This function implements the **measurement update** step in localization:
   - It takes the current belief `p` and the sensor reading `Z`.
   - For each position in the world, it checks if the color of the position matches the sensor reading (`hit = (Z == world[i])`).
     - If it matches (`hit == True`), it multiplies the corresponding belief by `pHit`.
     - If it doesn’t match (`hit == False`), it multiplies the belief by `pMiss`.
   - The result is a new belief distribution `q` that reflects the likelihood of the robot being in each position after accounting for the sensor measurement.

6. **Resulting Belief Distribution:**
   After sensing 'red', the belief distribution changes:
   ```
   [0.04, 0.12, 0.12, 0.04, 0.04]
   ```
   - The belief is **higher** at the positions where the world is 'red' because the sensor detected 'red'.
   - The belief is **lower** at positions where the world is 'green' because the sensor detected 'red', which doesn’t match.

---

### **How the Robot Uses This Code for Localization**
1. **Sensing**: The robot uses its sensors to detect some feature of the environment (in this case, the color of the tile it’s on).
   
2. **Updating Belief**: After sensing, it updates its belief about its location using the measurement update step. The belief in locations matching the sensor data increases, and the belief in locations that don’t match decreases.

3. **Refining Localization**: By repeating this process (sensing, updating belief, moving, and sensing again), the robot can refine its estimate of its position and eventually localize itself accurately.

This process is the foundation of probabilistic localization used in mobile robots and self-driving cars. Let me know if you'd like more details on any specific part!

___

The key mathematical concept is **Bayesian update** for localization, where the robot updates its belief based on sensor data. The equations used in this process are based on **probability theory**. Here’s a breakdown of the equations and how they relate to the code:

### 1. **Initial Probability (Belief) Distribution**

Before the robot senses anything, it assumes that it has equal probability of being in any location. This is represented as:
\[
p[i] = \frac{1}{N}
\]
Where:
- \( p[i] \) is the probability that the robot is in location \( i \).
- \( N \) is the total number of locations (in this case, \( N = 5 \)).

This results in the initial uniform distribution:
\[
p = [0.2, 0.2, 0.2, 0.2, 0.2]
\]

### 2. **Measurement Update (Bayesian Update)**

When the robot senses something (in this case, 'red'), it updates its belief using the following equation:

\[
q[i] = p[i] \times P(Z | X_i)
\]
Where:
- \( q[i] \) is the updated belief after sensing.
- \( p[i] \) is the prior belief (before sensing).
- \( P(Z | X_i) \) is the likelihood that the sensor reading \( Z \) (e.g., 'red') matches the environment at location \( X_i \).

This can be broken down as:
- **Hit case (correct sensor reading)**: If the sensed color matches the color at location \( i \), \( P(Z | X_i) = pHit = 0.6 \).
- **Miss case (incorrect sensor reading)**: If the sensed color does not match, \( P(Z | X_i) = pMiss = 0.2 \).

In the code, this equation is implemented in the `sense` function:

```python
q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
```

Where:
- `p[i]` is the prior belief for location \( i \).
- `hit` is a Boolean variable that is 1 if \( Z \) matches the world at location \( i \) and 0 otherwise.
- `pHit` and `pMiss` are the probabilities of a correct and incorrect sensor reading, respectively.

This equation adjusts the belief at each location based on how well the sensor reading matches the expected environment.

### 3. **Normalization (Not Included in Code, but Essential)**

In a real probabilistic system, the resulting belief \( q[i] \) must be **normalized** so that the sum of all probabilities equals 1. The normalization equation is:

\[
q[i] = \frac{q[i]}{\sum_{j=1}^{N} q[j]}
\]

This ensures that the updated probabilities form a valid probability distribution. Although this step isn't shown in this simple example, it is critical in real implementations of localization.

---

### Summary of Equations in the Code:

1. **Initial Probability**:
   \[
   p[i] = \frac{1}{N}
   \]
   (Uniform distribution across all locations.)

2. **Measurement Update** (Bayesian Update):
   \[
   q[i] = p[i] \times \left( hit \times pHit + (1 - hit) \times pMiss \right)
   \]
   (Update the belief based on whether the sensor reading matches the environment at each location.)

3. **Normalization** (in practice):
   \[
   q[i] = \frac{q[i]}{\sum q[j]}
   \]
   (Ensure the sum of probabilities equals 1.)

The code you've provided handles the **measurement update** step in the localization process, where the robot adjusts its belief based on sensor data using these equations.