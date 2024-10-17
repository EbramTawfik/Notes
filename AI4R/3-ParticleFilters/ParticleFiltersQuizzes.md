
### **1. Never Sampled 1 (Quiz)**

- **Question**: Is it possible that particle \( P_1 \), with an importance weight of \( 0.1 \), is never sampled in the resampling step?
    - **Options**: 
      - Yes
      - No

- **Answer**: **Yes**.
    - **Explanation**: In the random resampling process, a particle with a small importance weight, such as \( P_1 \), which has an importance weight of 0.1, has a lower probability of being sampled. Therefore, it is possible that it may never be sampled.

---

### **2. Never Sampled 2 (Quiz)**

- **Question**: Is it possible that particle \( P_3 \), with the largest importance weight of \( 0.4 \), is never sampled in the resampling step?
    - **Options**: 
      - Yes
      - No

- **Answer**: **Yes**.
    - **Explanation**: Even though \( P_3 \) has the largest importance weight (0.4), it is still possible that during the resampling process, it could be skipped due to randomness in the process. There's always a chance that other particles may be selected instead.

---

### **3. Never Sampled 3 (Quiz)**

- **Question**: What is the probability that particle \( P_3 \), with an importance weight of \( 0.4 \), is never sampled after five resampling steps?
  
- **Answer**: The probability of **never sampling \( P_3 \)** is **0.0777**.
    - **Explanation**: This probability is calculated using the formula:
      \[
      P(\text{not selected}) = (1 - \alpha_3)^N
      \]
      where \( \alpha_3 = 0.4 \) is the normalized weight, and \( N = 5 \) is the number of resampling steps. The probability is approximately 7.77%.

---

### **4. Resampling Quiz**

- **Question**: Suppose we have five particles with the following importance weights:
    - \( P_1 \): \( 0.6 \)
    - \( P_2 \): \( 1.2 \)
    - \( P_3 \): \( 2.4 \)
    - \( P_4 \): \( 0.6 \)
    - \( P_5 \): \( 1.2 \)
  
  What is the normalized probability of drawing each particle during the resampling step?

- **Answer**:
    - \( P(P_1) = 0.1 \)
    - \( P(P_2) = 0.2 \)
    - \( P(P_3) = 0.4 \)
    - \( P(P_4) = 0.1 \)
    - \( P(P_5) = 0.2 \)
    - **Explanation**: The total weight is 6, so the normalized probability of drawing each particle is calculated by dividing each particle's weight by the total weight (6).

---

### **5. Orientation 1 (Quiz)**

- **Question**: Will the orientation (heading direction) of the particles never play a role in the particle filter? 
    - **Options**: 
      - Yes, it will never play a role, so you always get a random set of orientations.
      - No, eventually orientation will matter.

- **Answer**: **No, eventually they will matter**.
    - **Explanation**: In the second step of particle filtering, as the robot moves and collects new sensor data, the orientation will play a role. Different orientations will lead to different predicted measurements, and particles with the correct orientation will become more important.

---

### **6. Filters Quiz**

- **Question**: Which filter did Sebastian use in his job talk at Stanford?
    - **Options**:
      - Histogram filters
      - Kalman filters
      - Particle filters
      - None of the above

- **Answer**: **Particle filters**.
    - **Explanation**: Sebastian used particle filters during his job talk, which was related to robotics and perception tasks. Particle filters are well-suited for dealing with non-linear and non-Gaussian processes, making them a practical choice for robotics applications.

---
