
# Practice Questions - Lesson 6: Router Design and Algorithms (Part 2)

## Question 1
**Using packet classification techniques we can perform packet forwarding based on multiple criteria, and not just based on destination IP address.**

### Choices
- True
- False

### Answer
True

### Explanation
Packet classification allows routers to identify and forward packets based on various parameters like source IP, destination IP, port numbers, and protocol type. This multi-criteria approach enhances network performance and allows for implementing QoS (Quality of Service) policies.

---

## Question 2
**The backtracking approach has a higher cost in terms of time, whereas the set-pruning approach has a higher cost in terms of memory.**

### Choices
- True
- False

### Answer
True

### Explanation
Backtracking requires the router to revisit previous decisions to find the correct forwarding path, resulting in higher time complexity. On the other hand, set-pruning tries to keep track of multiple paths at once, using more memory to store the additional information for quick lookups.

---

## Question 3
**The grid of tries technique offers a “middle ground” approach, merging the backtracking and the set-pruning techniques.**

### Choices
- True
- False

### Answer
True

### Explanation
The grid of tries technique combines aspects of both the backtracking and set-pruning methods. It allows the router to explore multiple possible paths without excessive memory use, thus striking a balance between time and space complexities.

---

## Question 4
**The head-of-line blocking refers to the problem when an entire queue remains blocked because the head of the queue is blocked.**

### Choices
- True
- False

### Answer
True

### Explanation
Head-of-line (HOL) blocking occurs when the first packet in the queue is unable to proceed, causing all subsequent packets to wait even if they could otherwise be forwarded. This issue is commonly seen in switches and routers with simple FIFO queues.

---

## Question 5
**One technique to avoid head of line blocking is with parallel iterative matching.**

### Choices
- True
- False

### Answer
True

### Explanation
Parallel iterative matching is a scheduling algorithm that matches input and output ports iteratively in parallel, reducing the likelihood of head-of-line blocking by ensuring multiple packets can be processed simultaneously.

---

## Question 6
**With parallel iterative matching the input links are “matched” with output links in a fixed manner that stays the same as the rounds are progressing.**

### Choices
- True
- False

### Answer
False

### Explanation
In parallel iterative matching, the input links and output links are dynamically matched in each round, based on the current state and requirements of both input and output queues. This dynamic process ensures fairness and efficient utilization of network resources.

---

## Question 7
**With the token bucket traffic approach, we can still have bursts of traffic entering the network, but these bursts are capped.**

### Choices
- True
- False

### Answer
True

### Explanation
The token bucket mechanism allows for bursts of traffic to be transmitted as long as there are enough tokens in the bucket. However, the size of these bursts is capped by the maximum number of tokens that can be stored in the bucket, ensuring controlled network utilization.

---

## Question 8
**With the leaky bucket approach, we only allow the traffic to enter the network in a configured rate.**

### Choices
- True
- False

### Answer
True

### Explanation
The leaky bucket algorithm allows traffic to flow out at a constant, pre-configured rate, regardless of the incoming traffic rate. This smoothing effect controls the output traffic rate and avoids congestion in the network.

---

## Question 9
**Traffic policers target to limit traffic bursts to a configured max, whereas traffic shapers target to smooth out the overall rate.**

### Choices
- True
- False

### Answer
True

### Explanation
Traffic policers drop or mark excess traffic to enforce a maximum burst size, whereas traffic shapers delay excess traffic by queuing it, smoothing out the flow to match a desired rate. This difference allows shapers to regulate the transmission more gently than policers.

---

## Question 10
**With the leaky bucket we can still have discarded packets.**

### Choices
- True
- False

### Answer
True

### Explanation
In the leaky bucket algorithm, packets that arrive when the bucket is full are discarded, as the bucket cannot accommodate more than its maximum capacity. This behavior is similar to how water overflows a full bucket.
