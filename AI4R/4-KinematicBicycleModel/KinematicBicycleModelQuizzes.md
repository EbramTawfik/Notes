### **1. Kinematic Bicycle Model - 07 - Simple Movement - Diagonal (Question)**

**Question**: What is the final pose of the robot after applying a forward movement when the robot is oriented diagonally with respect to the x-axis?

**Given**:
- Initial Pose: $x = 2, y = 2, \theta = \frac{\pi}{3}$
- Forward Movement Distance: $d = 10$

**Answer**: 
- $x_{\text{final}} = 7$
- $y_{\text{final}} = 10.7$
- $\theta_{\text{final}} = \frac{\pi}{3}$

**Explanation**: 
- To calculate the final pose, we use trigonometry:
  - $y_{\text{dist}} = \sin(\theta) \times d$
  - $x_{\text{dist}} = \cos(\theta) \times d$
  - Add the calculated distances to the initial x and y positions.
- For this specific example, the forward movement is applied diagonally, meaning both the x and y positions change, while the orientation ($\theta$) remains the same.

---

### **2. Kinematic Bicycle Model - 09 - Distinct Tracks A (Question)**

**Question**: Will the movement produce a single track or two distinct tracks behind the robot? Assume a bicycle model with two wheels.

**Answer**: 
- Single Track

**Explanation**:
- In the bicycle model, both the front and rear wheels follow the same path when there is no change in steering angle, so the robot leaves a single track behind it, unlike a car model where each wheel could leave distinct tracks.

---

### **3. Kinematic Bicycle Model - 11 - Track Shape (Question)**

**Question**: If we use a positive steering angle and travel in forward motion, what shape will the track behind the robot make?
- A) Heart
- B) Triangle
- C) Circle
- D) Oval

**Answer**: 
- **C) Circle**

**Explanation**: 
- When the robot moves with a constant steering angle, it will follow a circular trajectory. The rear axle will trace out a circular path.

---

### **4. Kinematic Bicycle Model - 13 - Distinct Tracks B (Question)**

**Question**: Will there be a single distinct track or two tracks left behind by the wheels after this compound movement (steering angle and forward motion)?
- A) 1 track
- B) 2 tracks

**Answer**: 
- **B) 2 tracks**

**Explanation**: 
- In this compound movement, both the front and rear axles trace out circular paths. The front wheel follows a larger circle than the rear wheel, resulting in two distinct tracks, each with the same center point.

---

### **5. Kinematic Bicycle Model - 17 - Circle Center (Question)**

**Question**: What happens to the center of the circle as the steering angle increases?
- A) Moves closer to the robot
- B) Moves further from the robot
- C) Stays in the same place
- D) None of the above

**Answer**: 
- **A) Moves closer to the robot**

**Explanation**: 
- As the steering angle increases, the turning radius decreases, bringing the center of the circle closer to the robot. A larger steering angle corresponds to a tighter turn, reducing the radius of the circular trajectory.

---

### **6. Kinematic Bicycle Model - 22 - Return to Same Point (Question)**

**Question**: What distance must the robot travel in order to return to its current position (assuming a fixed steering angle)?
 
**Answer**: 
- $2\pi \times R$

**Explanation**: 
- The robot needs to complete a full circle to return to its starting point. The distance for a full circle is the circumference, which is given by $2\pi R$, where $R$ is the turning radius.

---

### **7. Kinematic Bicycle Model - 28 - Example Problem (Question)**

**Given**:
- Starting Pose: $x = 0.118, y = -0.54, \theta = 0.1$
- Steering Angle: $\alpha = 0.166$
- Forward Distance: $d = 1.07$
- Robot Length: $L = 0.2$

**Question**: What is the final pose of the robot after traveling the given distance with the specified steering angle?

**Answer**: 
- $x_{\text{new}} = 1$
- $y_{\text{new}} = 0$
- $\theta_{\text{new}} = 1$

**Explanation**:
- First, calculate the turning radius $R$ using $R = \frac{L}{\tan(\alpha)}$, which gives $R \approx 1.194$.
- Then, find the central angle $\beta = \frac{d}{R} \approx 0.896$.
- Using the equations for the new x, y position and orientation:
  - $x_{\text{new}} = \text{center}_x + \sin(\theta + \beta) \times R$
  - $y_{\text{new}} = \text{center}_y - \cos(\theta + \beta) \times R$
  - $\theta_{\text{new}} = (\theta + \beta) \mod 2\pi$
- The calculated final pose rounds to $x = 1$, $y = 0$, and $\theta = 1$.

---
