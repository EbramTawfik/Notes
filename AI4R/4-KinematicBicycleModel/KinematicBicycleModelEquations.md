![](https://github.com/EbramTawfik/Notes/blob/main/AI4R/4-KinematicBicycleModel/Images/1.png)

### 1. **Turning Radius (\( R \))**

$$
R = \frac{L}{\tan(\alpha)}
$$


- **Explanation**: The turning radius \( R \) depends on the length of the vehicle \( L \) and the steering angle \( \alpha \). A larger steering angle results in a smaller turning radius. This equation allows us to calculate the radius of the circular path that the rear axle will follow during the motion.

---

### 2. **Central (Turning) Angle (\( \beta \))**


\beta = \frac{d}{R}


- **Explanation**: The central angle \( \beta \) is the angle subtended by the arc length \( d \) at the center of the circle, with \( R \) being the radius of the circle. It tells us how much the vehicle has turned as it travels along the arc.

---

### 3. **Location of the Circle Center**


\text{center}_x = x - \sin(\theta) \times R


\text{center}_y = y + \cos(\theta) \times R


- **Explanation**: The center of the circle (about which the robot is turning) is found using the robot's initial pose \( x, y, \theta \) and the turning radius \( R \). The center point is located by applying sine and cosine functions to determine the displacement in the x and y directions from the current position.

---

### 4. **Arc Length**


\text{Arc Length} = \beta \times R


- **Explanation**: The arc length is the distance the robot travels along the circular path, which can be calculated by multiplying the central angle \( \beta \) by the turning radius \( R \).

---

### 5. **New Position Offsets from Center**


x_{\text{offset}} = \sin(\theta + \beta) \times R


y_{\text{offset}} = \cos(\theta + \beta) \times R


- **Explanation**: After traveling along the arc, the robot's position can be updated by calculating the new offsets in the x and y directions relative to the center of the circle. These offsets depend on both the initial orientation \( \theta \) and the turning angle \( \beta \).

---

### 6. **New Position (Final Pose)**


x_{\text{new}} = \text{center}_x + x_{\text{offset}}


y_{\text{new}} = \text{center}_y - y_{\text{offset}}


- **Explanation**: The final x and y positions of the robot are found by adding the computed offsets to the coordinates of the center of the circle. The final position reflects where the robot is after traveling a distance along the circular path.

---

### 7. **New Orientation (Final Heading Angle)**


\theta_{\text{new}} = (\theta + \beta) \mod 2\pi


- **Explanation**: The final orientation \( \theta_{\text{new}} \) of the robot is computed by adding the central angle \( \beta \) to the initial orientation \( \theta \). The modulus operation ensures that the orientation remains within the range \( 0 \leq \theta_{\text{new}} < 2\pi \) radians.

---

### 8. **Distance to Return to the Same Point**


\text{Distance} = 2\pi \times R


- **Explanation**: This equation calculates the distance the robot must travel to return to its starting position after completing a full circle. The formula is simply the circumference of a circle with radius \( R \).

---

### 9. **Straight-Line Motion (for \( \beta \approx 0 \))**


x' = x + d \cdot \cos(\theta)


y' = y + d \cdot \sin(\theta)


\theta' = \theta


- **Explanation**: When the turning angle \( \beta \) is close to zero (i.e., the robot is moving in a straight line), the updated x and y positions are determined by adding the forward distance \( d \) multiplied by the cosine and sine of the current orientation \( \theta \), respectively. The orientation remains unchanged during straight-line motion.

---

### 10. **Final Set of Formulas for Circular Motion**


\beta = \frac{d}{R}


x_{\text{new}} = \text{center}_x + \sin(\theta + \beta) \times R


y_{\text{new}} = \text{center}_y - \cos(\theta + \beta) \times R


\theta_{\text{new}} = (\theta + \beta) \mod 2\pi


- **Explanation**: These are the final set of equations that combine all the steps for calculating the new pose of the robot after circular motion, starting from the steering angle and forward distance inputs. They provide the updated position and orientation after the robot completes its motion.
