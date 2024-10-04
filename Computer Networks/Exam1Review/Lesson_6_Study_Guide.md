
# Computer Networks Study Material

## Table of Contents
1. Introduction to Packet Classification
2. Packet Classification Techniques
3. Scheduling and Head of Line (HOL) Blocking
4. Traffic Scheduling: Token Bucket and Leaky Bucket
5. Deficit Round Robin (DRR)
6. Conclusion

## 1. Introduction to Packet Classification
Packet classification is a crucial process in networking, where packets are forwarded based on multiple criteria, not just the destination IP address. Using packet classification, routers can inspect packet headers to determine the appropriate action, including forwarding, dropping, or prioritizing packets. 

### Example: 
A router may classify packets based on source IP address, destination IP address, port numbers, protocol type (TCP, UDP), or application-level criteria. For example, packets belonging to a video stream can be identified and given higher priority to ensure smooth playback, while bulk data transfers might be assigned a lower priority.

### Why Packet Classification?
- **Firewalls:** Packet classification allows routers to filter traffic based on security policies, blocking unwanted traffic.
- **Quality of Service (QoS):** Classifying packets helps in reserving bandwidth and prioritizing critical traffic (e.g., voice, video).
- **Routing Based on Traffic Type:** Certain types of traffic, such as video streaming, require lower latency, and packet classification allows routers to handle these packets accordingly.

## 2. Packet Classification Techniques
### Set-Pruning Tries
- **Concept:** This technique involves constructing a trie (a tree-like structure) on the destination prefixes. At each leaf node of the destination trie, source tries are "hung" to further classify packets based on their source addresses.
- **Advantages:** Improves search speed as it prunes the search space to a smaller set of possible matches.
- **Disadvantages:** It consumes a lot of memory because each source prefix can be stored in multiple destination tries, leading to redundancy.

### Backtracking Approach
- **Concept:** In the backtracking approach, the destination prefix points to a source trie containing only rules specific to that destination. During the lookup, the system searches the source tries of the destination prefix and its ancestors, "backtracking" to check multiple possibilities.
- **Advantages:** Requires less memory than the set-pruning method since each rule is stored only once.
- **Disadvantages:** The search time is longer as it involves checking multiple tries during backtracking.

### Grid of Tries
- **Middle-Ground Solution:** This approach reduces the time cost of backtracking by using precomputed switch pointers. When a search in the source trie fails, the switch pointer quickly directs the search to the next relevant source trie.
- **Advantages:** Reduces both the memory usage and time cost, offering a balance between set-pruning and backtracking.

## 3. Scheduling and Head of Line (HOL) Blocking
**Head of Line (HOL) Blocking** occurs when the first packet in a queue is blocked, preventing the rest of the packets in the queue from being processed. This situation can significantly reduce the efficiency of packet processing in routers, leading to delays and reduced network performance.

### Avoiding HOL Blocking: Parallel Iterative Matching
- **Parallel Iterative Matching:** This technique dynamically matches input links with output links in multiple rounds. During each round, inputs send requests to the outputs they want to connect to. Outputs then grant access to one of the requesting inputs, and inputs choose one of the granted outputs to connect.
- **Benefits:** By allowing multiple connections in each round and dynamically changing the matching, parallel iterative matching reduces the likelihood of HOL blocking, improving overall network throughput.

## 4. Traffic Scheduling: Token Bucket and Leaky Bucket
### Token Bucket
The **Token Bucket** algorithm is used to control the flow of packets, allowing bursts of traffic while capping the burst size. 

- **Mechanism:** The token bucket fills with tokens at a constant rate (R tokens per second). Each token corresponds to a unit of data (e.g., one bit). The bucket has a maximum capacity (B tokens). If the bucket is full, any additional tokens are discarded.
- **Packet Transmission:** When a packet arrives, it can only be transmitted if there are enough tokens in the bucket equal to the packet size. If not, the packet is either delayed (in shaping) or dropped (in policing).
- **Burst Control:** The maximum burst size is limited by the number of tokens (B) in the bucket, allowing for occasional bursts in traffic but capping them.

### Token Bucket Shaping vs. Policing
- **Shaping:** Excess packets are buffered and sent later when enough tokens accumulate. This smoothens out traffic flows, reducing sudden spikes.
- **Policing:** Excess packets are immediately dropped if there aren't enough tokens, strictly enforcing the traffic rate limit.

### Leaky Bucket
The **Leaky Bucket** algorithm is similar to the token bucket but allows for a steady, regulated flow of packets. It's analogous to water leaking out of a bucket at a fixed rate.

- **Mechanism:** Packets enter the bucket (queue) and leak out at a constant rate (r), regardless of the rate at which they arrive. If the bucket (queue) is full, incoming packets are dropped.
- **Uniform Flow:** The leaky bucket ensures that packets are sent at a steady, constant rate, leading to a uniform distribution of traffic in the network.
- **Implementation:** Often implemented as a single-server queue, where the server drains the bucket (sends packets) at a constant rate.

### Difference Between Token Bucket and Leaky Bucket
- **Token Bucket:** Allows bursts up to a maximum size (B tokens) and transmits packets as long as tokens are available.
- **Leaky Bucket:** Ensures a constant output rate, dropping packets if they arrive too fast and the bucket is full.

## 5. Deficit Round Robin (DRR)
**Deficit Round Robin (DRR)** is a packet scheduling algorithm that ensures fair bandwidth distribution among multiple flows by using a quantum size and a deficit counter.

### How DRR Works
1. **Quantum Size:** Each flow is allocated a fixed quantum size (Q), which determines the maximum amount of data it can send in one round.
2. **Deficit Counter:** Each flow has a deficit counter (D) that accumulates the leftover bandwidth if a packet cannot be sent due to size constraints. This counter is carried over to the next round.
3. **Sending Packets:** During each round, the flow sends packets as long as the total size is less than the sum of its quantum size and deficit counter (Q + D). If it cannot send a packet, the deficit is added to the counter for the next round.

### Example
- Suppose a flow has a quantum size of 500 bytes. In the first round, it sends a 200-byte packet. The remaining 300 bytes are added to its deficit counter.
- In the next round, the flow's available bandwidth becomes 500 + 300 = 800 bytes. If the next packet is 750 bytes, it can now be sent, leaving 50 bytes as the deficit for the following round.

### Advantages of DRR
- **Fairness:** Ensures that each flow gets its fair share of bandwidth over time.
- **Efficiency:** Operates in constant time, making it suitable for high-speed networks.
- **Handles Variable Packet Sizes:** The deficit counter allows flows with larger packets to send data fairly over multiple rounds.

## 6. Conclusion
Packet classification, scheduling, and traffic management techniques like token bucket, leaky bucket, and deficit round robin are vital for effective network performance. These methods help maintain fair bandwidth distribution, enforce QoS policies, and prevent network congestion.

Understanding these techniques is crucial for designing robust network systems capable of handling diverse traffic patterns and ensuring smooth data transmission.

