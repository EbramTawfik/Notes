

### 1. **Localization Using Histogram Filter**

This code implements the localization process using a histogram filter. The robot moves in a 1D world, sensing its environment and moving probabilistically.

#### Code for Localization:

```python
p = [0, 1, 0, 0, 0]  # initial probability distribution
world = ['green', 'red', 'red', 'green', 'green']
measurements = ['red', 'green']
motions = [1, 1]
pHit = 0.6
pMiss = 0.2
pExact = 0.8
pOvershoot = 0.1
pUndershoot = 0.1

def sense(p, Z):
    q = []
    for i in range(len(p)):
        hit = (Z == world[i])
        q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
    s = sum(q)
    for i in range(len(q)):
        q[i] = q[i] / s
    return q

def move(p, U):
    q = []
    for i in range(len(p)):
        s = pExact * p[(i-U) % len(p)]  # exact move
        s = s + pOvershoot * p[(i-U-1) % len(p)]  # overshoot
        s = s + pUndershoot * p[(i-U+1) % len(p)]  # undershoot
        q.append(s)
    return q

for k in range(len(measurements)):
    p = sense(p, measurements[k])
    p = move(p, motions[k])

print(p)
```

### Explanation:

1. **Initial Setup**:
   - `p`: The initial belief that the robot is at position 1 (index 1) with 100% certainty.
   - `world`: The environment where the robot navigates (each position is either 'green' or 'red').
   - `measurements`: The sequence of observations made by the robot ('red', 'green').
   - `motions`: The sequence of moves the robot makes (1 step forward for each move).
   - `pHit`, `pMiss`, `pExact`, `pOvershoot`, `pUndershoot`: Parameters that describe the probabilities of correct sensing, incorrect sensing, exact moves, overshooting, and undershooting during movement.

#### **Step 1: Sense Function**

```python
def sense(p, Z):
    q = []
    for i in range(len(p)):
        hit = (Z == world[i])
        q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
    s = sum(q)
    for i in range(len(q)):
        q[i] = q[i] / s
    return q
```

- **Purpose**: This function updates the belief distribution `p` based on the sensor measurement `Z`.
  
- **Process**:
  - The variable `hit` checks if the measurement `Z` matches the current position in the `world` (true if the color matches).
  - If `hit` is true, the corresponding belief is multiplied by `pHit`; otherwise, it is multiplied by `pMiss`.
  - The list `q` stores the updated belief.
  - After computing the raw probabilities, the list is normalized by dividing each entry by the sum `s` to ensure the total probability sums to 1.

#### **Step 2: Move Function**

```python
def move(p, U):
    q = []
    for i in range(len(p)):
        s = pExact * p[(i-U) % len(p)]  # exact move
        s = s + pOvershoot * p[(i-U-1) % len(p)]  # overshoot
        s = s + pUndershoot * p[(i-U+1) % len(p)]  # undershoot
        q.append(s)
    return q
```

- **Purpose**: This function models how the belief distribution `p` changes when the robot moves by `U` positions.
  
- **Process**:
  - The belief that the robot moved exactly `U` positions is calculated using `pExact * p[(i - U) % len(p)]`. The modulo operator (`%`) ensures the movement wraps around the circular world.
  - If the robot overshoots or undershoots its target, those probabilities are added using `pOvershoot * p[(i - U - 1) % len(p)]` and `pUndershoot * p[(i - U + 1) % len(p)]`.
  - These terms are added to `s`, which represents the total belief at position `i` after movement.
  - The result `q` is the new belief distribution after the motion step.

#### **Trick: Modulo Arithmetic (`i - U`)**:
- **Purpose**: The modulo operator (`%`) is used to ensure that the indices wrap around the edges of the world. This is particularly important when the robot moves to the left (negative movement) or right (positive movement) in a circular world. For example:
  - `(i - U) % len(p)` calculates the new index for the exact move.
  - `(i - U - 1) % len(p)` is used for overshoot.
  - `(i - U + 1) % len(p)` is used for undershoot.
  
  These terms ensure that the robot's belief is updated correctly even when it moves beyond the bounds of the world array.

---

### 2. **2D Grid Localization Program**

This code localizes a robot in a 2D world based on sensor measurements and motions. It accounts for movement uncertainty and measurement errors.

#### Code:

```python
from typing import List, Tuple

def localize(colors: List[List[str]], measurements: List[str], motions: List[Tuple[int, int]], sensor_right: float, p_move: float) -> List[List[float]]:
    if len(measurements) != len(motions):
        raise ValueError("Measurements and motions must have the same length")
    
    num_rows = len(colors)
    num_cols = len(colors[0])
    uniform_prob = 1.0 / (num_rows * num_cols)
    
    p = [[uniform_prob for _ in range(num_cols)] for _ in range(num_rows)]

    for k in range(len(measurements)):
        p = move(p, motions[k], p_move)
        p = sense(p, colors, measurements[k], sensor_right)
    
    return p

def sense(p: List[List[float]], colors: List[List[str]], measurement: str, sensor_right: float) -> List[List[float]]:
    sensor_wrong = 1.0 - sensor_right
    q = [[0.0 for _ in range(len(p[0]))] for _ in range(len(p))]
    total_sum = 0.0

    for i in range(len(p)):
        for j in range(len(p[i])):
            hit = (measurement == colors[i][j])
            q[i][j] = p[i][j] * (hit * sensor_right + (1 - hit) * sensor_wrong)
            total_sum += q[i][j]
    
    for i in range(len(q)):
        for j in range(len(q[i])):
            q[i][j] /= total_sum
    
    return q

def move(p: List[List[float]], motion: Tuple[int, int], p_move: float) -> List[List[float]]:
    p_stay = 1.0 - p_move
    q = [[0.0 for _ in range(len(p[0]))] for _ in range(len(p))]

    for i in range(len(p)):
        for j in range(len(p[i])):
            q[i][j] = p_move * p[(i - motion[0]) % len(p)][(j - motion[1]) % len(p[i])] + p_stay * p[i][j]
    
    return q
```

### Explanation:

1. **Initial Setup**:
   - The function `localize` initializes a uniform probability distribution (`p`), assuming the robot has an equal chance of being in any cell.
   - For each measurement and motion step, it calls the `move` and `sense` functions to update the belief distribution.

#### **Step 1: Sense Function**:
```python
def sense(p: List[List[float]], colors: List[List[str]], measurement: str, sensor_right: float) -> List[List[float]]:
```
- **Purpose**: Updates the belief based on the sensor reading (color detection).
- **Key Idea**: If the robot's measurement matches the actual color at the grid cell (`hit`), the belief is multiplied by `sensor_right`; otherwise, it is multiplied by `sensor_wrong` (the probability of a wrong measurement).

#### **Step 2: Move Function**:
```python
def move(p: List[List[float]], motion: Tuple[int, int], p_move: float) -> List[List[float]]:
```
- **Purpose**: Updates the belief distribution after a motion, accounting for movement uncertainty (`p_move`).
- **Trick**: Modulo arithmetic (`(i - motion[0]) % len(p)`) is used to wrap around the grid boundaries, ensuring the robot can move circularly within the grid.

---

These codes showcase the application of probabilistic reasoning in localization, using **Bayes' rule** and **theorem of total probability** to handle sensing and movement

 uncertainty. The use of modulo arithmetic ensures proper handling of grid boundaries, and the sequential update of belief via the `sense` and `move` functions ensures that the robot's localization converges over time.