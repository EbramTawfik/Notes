
### Problem Practice Examples

---

#### 1. **Cancer Test Problem (Bayes' Rule Application)**
This problem illustrates how Bayes' rule can be applied in a real-world medical context:

**Problem**:  
- Suppose you are given the following probabilities:
  - \( P(C) = 0.001 \): Probability of a person having cancer.
  - \( P(\neg C) = 0.999 \): Probability of not having cancer.
  - \( P(\text{Pos} | C) = 0.8 \): Probability of testing positive given the person has cancer.
  - \( P(\text{Pos} | \neg C) = 0.1 \): Probability of testing positive given the person does not have cancer.
  
**Question**:  
- If a person tests positive, what is the probability that they actually have cancer? In other words, compute \( P(C | \text{Pos}) \).

**Solution**:  
Using Bayes' Rule:
\[
P(C | \text{Pos}) = \frac{P(\text{Pos} | C) P(C)}{P(\text{Pos})}
\]
First, calculate \( P(\text{Pos}) \) (the total probability of testing positive):
\[
P(\text{Pos}) = P(\text{Pos} | C) P(C) + P(\text{Pos} | \neg C) P(\neg C)
\]
Substituting the values:
\[
P(\text{Pos}) = (0.8 \times 0.001) + (0.1 \times 0.999) = 0.0008 + 0.0999 = 0.1007
\]
Now, calculate \( P(C | \text{Pos}) \):
\[
P(C | \text{Pos}) = \frac{0.8 \times 0.001}{0.1007} \approx 0.0079
\]
Thus, the probability of having cancer given a positive test is **0.79%**.

---

#### 2. **Coin Flip Quiz (Total Probability Example)**

**Problem**:
- You have a coin where the probability of heads \( P(H) \) is \( 0.5 \) and the probability of tails \( P(T) \) is also \( 0.5 \).
- The rule is: if tails \( T \) occurs, accept the result. If heads \( H \) occurs, flip the coin again and accept the second outcome.

**Question**:  
- What is the probability of getting two heads in two consecutive flips?

**Solution**:  
The probability of getting heads on both flips is:
\[
P(H^2) = P(H) \times P(H) = 0.5 \times 0.5 = 0.25
\]
Thus, the probability of getting two heads in two flips is \( 0.25 \), or **25%**.

---

#### 3. **Two-Coin Problem (Bayesian Inference)**

**Problem**:  
- Suppose you have two coins:
  - A fair coin with a probability \( P(H) = 0.5 \) of landing heads.
  - A loaded coin with a probability \( P(H) = 0.1 \) of landing heads.
- You randomly select a coin with a 50% chance of choosing the fair coin and a 50% chance of choosing the loaded coin.
- After flipping the selected coin, you observe heads.

**Question**:  
- What is the probability that the coin you selected was the fair coin given that you observed heads?

**Solution**:  
Using Bayes' rule:
\[
P(\text{fair} | H) = \frac{P(H | \text{fair}) P(\text{fair})}{P(H)}
\]
Where \( P(H) \) (the total probability of observing heads) is:
\[
P(H) = P(H | \text{fair}) P(\text{fair}) + P(H | \text{loaded}) P(\text{loaded})
\]
Substitute the known values:
\[
P(H) = (0.5 \times 0.5) + (0.1 \times 0.5) = 0.25 + 0.05 = 0.30
\]
Now, calculate \( P(\text{fair} | H) \):
\[
P(\text{fair} | H) = \frac{0.5 \times 0.5}{0.3} = \frac{0.25}{0.3} \approx 0.833
\]
Thus, the probability that the coin is fair given that it landed heads is approximately **0.833**, or **83.3%**.

---

#### 4. **Limit Distribution in Localization (Convergence Example)**

**Problem**:  
- Imagine a robot moving in a world with five possible positions. The robot starts with a belief that it is equally likely to be in any position (i.e., a uniform distribution of probabilities).
- The robot repeatedly makes uncertain movements, each time shifting one position either left or right, with equal probability.

**Question**:  
- After many movements, what will be the robot’s belief distribution over the five positions?

**Solution**:  
This is an example of a **limit distribution** problem. Since the robot has an equal chance of moving left or right and its movement is uncertain, its belief distribution will eventually converge to a **uniform distribution** across all positions:
\[
P(\text{position}) = 0.2 \text{ for each position}
\]
After many steps, the robot believes that it is equally likely to be in any of the five positions.

---

#### 5. **Theorem of Total Probability (Motion Update in Localization)**

**Problem**:  
- A robot can move between three grid cells, labeled \( X_1, X_2, X_3 \).
- At time \( t \), the robot is uncertain about which cell it is in. The probability distribution for its position is \( P(X_1^t), P(X_2^t), P(X_3^t) \).
- The robot moves to a new position based on its current position with some motion uncertainty.

**Question**:  
- How can we compute the probability \( P(X_i^{t+1}) \) that the robot is in cell \( i \) after the move?

**Solution**:  
Using the **theorem of total probability**, the probability of the robot being in cell \( X_i^{t+1} \) is computed by summing the probabilities from all possible previous locations:
\[
P(X_i^{t+1}) = \sum_j P(X_j^t) \cdot P(X_i^{t+1} | X_j^t)
\]
Where \( P(X_i^{t+1} | X_j^t) \) is the probability of moving from cell \( j \) to cell \( i \). This formula accounts for the robot's uncertainty in its movement.

---

#### 6. **Bayes' Rule and Non-Normalized Posterior in Localization**

**Problem**:  
- A robot has two hypotheses about its position: \( H_1 \) (position \( X_1 \)) and \( H_2 \) (position \( X_2 \)).
- The robot uses a sensor that provides noisy measurements, and based on these measurements, it wants to update its belief about where it is.

**Question**:  
- How can the robot update its belief using Bayes' rule and a non-normalized posterior?

**Solution**:  
The robot updates its belief about being in position \( X_1 \) based on the measurement using Bayes' rule:
\[
P(X_1 | Z) = \frac{P(Z | X_1) P(X_1)}{P(Z)}
\]
If the posterior is not normalized, we compute:
\[
P'(X_1 | Z) = P(Z | X_1) P(X_1)
\]
And:
\[
P'(X_2 | Z) = P(Z | X_2) P(X_2)
\]
To normalize, we compute the total probability of the measurement \( P(Z) \) and divide the unnormalized posteriors:
\[
P(Z) = P'(X_1 | Z) + P'(X_2 | Z)
\]
Finally, the normalized posteriors are:
\[
P(X_1 | Z) = \frac{P'(X_1 | Z)}{P(Z)}, \quad P(X_2 | Z) = \frac{P'(X_2 | Z)}{P(Z)}
\]
This allows the robot to correctly update its belief based on the noisy measurement.
