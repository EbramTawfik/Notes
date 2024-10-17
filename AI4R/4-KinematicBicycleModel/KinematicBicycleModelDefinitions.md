# Kinematic Bicycle Model Definitions

Here are all the key concepts and definitions from the lesson on the **Kinematic Bicycle Model**:

### 1. **Kinematic Bicycle Model**
   - A simplified mathematical model used to describe the motion of vehicles. It approximates a vehicle with two wheels (like a bicycle) instead of four, making it easier to calculate movement and control.

### 2. **Robot Pose**
   - The pose of a robot is defined by three parameters:
     - $x$: The robot’s position along the x-axis.
     - $y$: The robot’s position along the y-axis.
     - $\theta$: The robot’s orientation, which is the angle between the robot’s direction and the positive x-axis.

### 3. **Steering Angle ($\alpha$)**
   - The angle at which the front wheel (or axle) is turned relative to the orientation of the vehicle. It directly affects the turning radius of the robot.

### 4. **Forward Movement (Distance Traveled)**
   - The distance traveled by the rear axle during the motion. This is a primary control input to move the robot along a desired trajectory.

### 5. **Turning Radius ($R$)**
   - The radius of the circle traced by the rear axle during a turn. It is influenced by the steering angle $\alpha$ and the length of the robot $L$. The formula is:

$$
R = \frac{L}{\tan(\alpha)}
$$


   - A larger steering angle results in a smaller turning radius.

### 6. **Center of the Circle**
   - When the robot moves along a circular path, the center of the circle is the point about which the robot is turning. The location of the center depends on the robot’s current position and orientation.

### 7. **Arc Length**
   - The distance traveled by the robot along the circumference of a circle during its motion. It is calculated as the product of the turning angle $\beta$ and the radius $R$:

$$
\text{Arc Length} = \beta \times R
$$

   - $\beta$ is the central angle subtended by the arc at the center of the circle.

### 8. **Central Angle ($\beta$)**
   - The angle by which the robot turns as it moves along a circular arc. It is calculated using the formula:

$$
\beta = \frac{d}{R}
$$

   where $d$ is the forward distance traveled by the robot.

### 9. **Offset from Center**
   - The offset refers to the robot's displacement from the center of the circle after moving. The x and y offsets can be computed using trigonometric functions:

$$
x_{\text{offset}} = \sin(\theta + \beta) \times R, \quad y_{\text{offset}} = \cos(\theta + \beta) \times R
$$

### 10. **New Pose**
   - The new pose (final position and orientation) of the robot after a compound movement. The new position ($x_{\text{new}}, y_{\text{new}}$) is derived by adding the offsets to the center point:

$$
x_{\text{new}} = \text{center}_x + x_{\text{offset}}, \quad y_{\text{new}} = \text{center}_y - y_{\text{offset}}
$$

   The new orientation is computed as:

$$
\theta_{\text{new}} = (\theta + \beta) \mod 2\pi
$$

### 11. **One Track vs. Two Tracks**
   - In the Kinematic Bicycle Model, one track is left by the rear wheel if only forward movement is applied. However, when a steering angle is used, two tracks are created by both the front and rear axles.

### 12. **Distance to Return to the Same Point**
   - To return to the starting point after a circular motion, the robot must travel the circumference of the circle:

$$
\text{Distance} = 2\pi \times R
$$

### 13. **Pose Estimation**
   - The process of determining the robot's new position and orientation after applying certain control inputs (steering angle and forward movement) using the derived kinematic equations.

### 14. **Trigonometric Relations in Bicycle Model**
   - Trigonometry is used to compute the movement in the x and y directions, as well as to determine the location of the center of the circle, based on the robot’s initial orientation.

### 15. **Modular Arithmetic in Orientation**
   - Since orientation is measured as an angle, it can exceed $2\pi$ radians (a full rotation). Modular arithmetic ensures that the angle stays within the range $0 \leq \theta < 2\pi$, allowing the robot's orientation to wrap around.
