
# Lesson 6: Router Design and Algorithms (Part 2) - Study Questions

## 1. Why is packet classification needed?
Packet classification is needed to handle packets based on multiple criteria (beyond just the destination IP address) to provide quality of service (QoS), enforce security policies, and manage different types of traffic flows effectively. By using various header fields such as source address, protocol type, and port numbers, routers can prioritize, block, or reroute packets according to the policies set by the network administrators.

## 2. What are three established variants of packet classification?
The three established variants of packet classification are:
1. **Firewalls**: Firewalls use packet classification to filter unwanted traffic, blocking certain types of packets based on security rules.
2. **Resource Reservation Protocols (e.g., DiffServ)**: These protocols use packet classification to reserve bandwidth for specific types of traffic between source and destination pairs, ensuring QoS.
3. **Traffic Type Routing**: Different types of traffic (e.g., video streaming, web browsing) are classified and routed based on their needs, such as lower latency or higher reliability.

## 3. What are the simple solutions to the packet classification problem?
Some simple solutions include:
1. **Linear Search**: A straightforward method where each rule is checked sequentially until a match is found. This method is efficient for small rule sets but becomes time-consuming for larger databases.
2. **Caching**: Results from previous classifications are stored to speed up future lookups. However, cache misses still require searching, and performance drops significantly when the cache miss rate is high.
3. **Passing Labels (MPLS and DiffServ)**: A method where classification is performed once, and packets are labeled (e.g., using MPLS headers) for further processing by intermediate routers without reclassification.

## 4. How does fast searching using set-pruning tries work?
Set-pruning tries work by building a hierarchical trie for the **destination prefixes** first. At each leaf node of the destination trie, a **source trie** is attached. When a packet arrives, the destination prefix is matched first, pruning down the search space, and then the appropriate source trie is traversed to find the longest matching source prefix.

## 5. What’s the main problem with the set pruning tries?
The main issue with set-pruning tries is **memory explosion**. Since each destination trie has its own set of source tries, source prefixes can be duplicated across multiple tries. This duplication results in a high memory usage, especially when there are many overlapping rules for different destination prefixes.

## 6. What is the difference between the pruning approach and the backtracking approach for packet classification with a trie?
- **Pruning Approach (Set-Pruning Tries)**: The destination trie is traversed, and then a source trie is searched for that specific destination node. Each source prefix can be duplicated in multiple tries, resulting in high memory usage but faster lookup times.
- **Backtracking Approach**: Only one source trie is associated with each destination prefix. If the longest matching destination prefix fails to find a match, the algorithm backtracks to search the source tries of ancestor nodes. This reduces memory usage but increases the lookup time.

## 7. What’s the benefit of a grid of tries approach?
The **grid of tries** approach offers a middle ground between pruning and backtracking. By precomputing **switch pointers** that guide the search directly to the next possible matching source trie, the grid of tries reduces the time overhead associated with backtracking while also minimizing memory duplication.

## 8. Describe the “Take the Ticket” algorithm.
The **Take the Ticket** algorithm is a simple scheduling method where each output line maintains a queue of input lines requesting to send packets. When an input line wants to connect to an output, it requests a "ticket." Tickets are processed in order, allowing the input line to connect with the output link when its turn comes. This ensures fairness but can lead to head-of-line (HOL) blocking if one input line holds up others waiting for the same output.

## 9. What is the head-of-line problem?
**Head-of-Line (HOL) Blocking** is when the first packet in a queue blocks subsequent packets from being processed, even if other packets could be sent to different outputs. This happens when the head packet's requested output is not available, causing the entire queue to be stalled, reducing throughput.

## 10. How is the head-of-line problem avoided using the knockout scheme?
The **Knockout Scheme** avoids HOL blocking by limiting the burst size and over-provisioning internal switching fabric to handle potential burst traffic. Packets are broken into smaller fixed-sized cells, allowing the switch to handle them more efficiently. If too many cells attempt to leave through the same output simultaneously, excess cells are dropped, randomly reducing HOL blocking.

## 11. How is the head-of-line problem avoided using parallel iterative matching?
**Parallel Iterative Matching** allows input and output links to be dynamically paired across multiple rounds. Each input sends parallel requests to all outputs it wants to connect with. The outputs grant access to one of the inputs in each round, allowing connections to form iteratively, thus reducing HOL blocking by maximizing the use of available output links.

## 12. Describe FIFO with tail drop.
**FIFO (First-In-First-Out) with Tail Drop** is a basic packet scheduling mechanism where packets are processed in the order they arrive. If the queue reaches its maximum capacity, any new incoming packets are dropped from the "tail" of the queue. This approach is simple to implement but can result in packet loss and does not provide fairness or prioritization.

## 13. What are the reasons for making scheduling decisions more complex than FIFO?
Reasons include:
- **Fairness Among Competing Flows**: Ensuring that all flows get a fair share of bandwidth, especially when multiple flows are contending for limited resources.
- **Congestion Control**: Improving network performance during congestion by ensuring critical flows are not starved and are given priority.
- **Quality of Service (QoS) Guarantees**: Providing different levels of service to various types of traffic, such as ensuring low-latency for real-time video streaming or guaranteed bandwidth for important data flows.

## 14. Describe Bit-by-bit Round Robin scheduling.
In **Bit-by-Bit Round Robin**, a hypothetical scheduling algorithm, each active flow sends one bit in each round in a round-robin manner. Though it's impractical to send single bits in real networks, the algorithm conceptually provides fairness by calculating packet finish times based on how many bits would be sent in each round.

## 15. Bit-by-bit Round Robin provides fairness; what’s the problem with this method?
The main issue with **Bit-by-Bit Round Robin** is its **time complexity**. To provide fairness, it needs to keep track of the finish times for each packet across all active flows, requiring complex data structures and computations. This makes it hard to implement in real-world networks with high-speed data rates.

## 16. Describe Deficit Round Robin (DRR).
**Deficit Round Robin (DRR)** is a scheduling algorithm designed to ensure fair bandwidth distribution among flows. Each flow is assigned a **quantum size** (Q) and a **deficit counter** (D). In each round, the flow sends as much data as allowed by its quantum and deficit. If the flow cannot send a packet because it’s too large, the remaining deficit is carried over to the next round, allowing it to send more data later.

## 17. What is a token bucket shaping?
**Token Bucket Shaping** controls the traffic flow by using a bucket filled with tokens at a constant rate (R). Each token allows the transmission of one bit. If enough tokens are available, packets are sent. If not, packets are buffered until tokens accumulate. The burst size is capped by the bucket capacity (B), allowing short bursts while maintaining a long-term average rate.

## 18. In traffic scheduling, what is the difference between policing and shaping?
- **Policing**: Drops or marks packets if the traffic rate exceeds the configured limit. It enforces a strict maximum rate without buffering excess packets, often leading to packet loss.
- **Shaping**: Buffers excess packets and smooths out bursts by sending the packets at a steady rate over time. This delays packets rather than dropping them, resulting in a more uniform traffic flow.

## 19. How is a leaky bucket used for traffic policing and shaping?
The **Leaky Bucket Algorithm** works by allowing packets to be transmitted at a fixed rate, irrespective of the rate at which they arrive. Packets are added to a bucket that leaks at a constant rate. If the bucket overflows, packets are dropped (policing), but if the bucket can hold the packets, they are sent at a uniform rate (shaping), smoothing out the traffic flow.
