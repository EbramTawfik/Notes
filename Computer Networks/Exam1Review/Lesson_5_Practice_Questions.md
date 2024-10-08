# Router Design and Algorithms Practice Questions

## Group 1
### Question 1
The data plane functions of a traditional router are implemented in:
- A) Hardware
- B) Software

**Answer:** A
**Explanation:** The data plane functions, which involve packet forwarding, are implemented in hardware to achieve high-speed processing.

### Question 2
The control plane functions of a traditional router are implemented in:
- A) Hardware
- B) Software

**Answer:** B
**Explanation:** The control plane handles routing decisions and protocol management, which are typically implemented in software for flexibility and programmability.

### Question 3
Which plane operates on a shorter timescale?
- A) Data Plane
- B) Control Plane
- C) Management Plane

**Answer:** A
**Explanation:** The data plane operates at a much faster timescale because it is involved in the actual forwarding of packets, whereas the control plane handles routing decisions and updates, which are less time-sensitive.

### Question 4
Classify each function as an operation of either the data plane or control plane:

1. **A. Computing paths based on a protocol** = **Control Plane**
   - The control plane is responsible for making decisions about where packets should go. When computing paths using routing algorithms (like OSPF or BGP), it is determining the best route for data packets based on network conditions, which is a control plane function.

2. **B. Forwarding packets at Layer 3** = **Data Plane**
   - Layer 3 forwarding involves the actual movement of packets across a network, based on routing decisions made earlier. This is the responsibility of the data plane, as it deals with handling and forwarding packets from one node to another based on IP addresses.

3. **C. Switching packets at Layer 2** = **Data Plane**
   - Layer 2 switching refers to the process of forwarding data frames within the same network (using MAC addresses). This is purely a data plane operation because it involves physically forwarding the data based on predefined rules, without involving complex decision-making processes.

4. **D. Running protocols to build a routing table** = **Control Plane**
   - The control plane uses routing protocols like OSPF, RIP, or BGP to build and update routing tables, which determine the best paths for forwarding packets. Running these protocols is a decision-making task, so it belongs to the control plane.

5. **E. Running the Spanning Tree protocol** = **Control Plane**
   - The Spanning Tree Protocol (STP) prevents loops in a Layer 2 network by computing the most efficient loop-free path. Since it involves path selection and network topology decisions, it is part of the control plane.

6. **F. Decrementing Time To Live (TTL)** = **Data Plane**
   - TTL is a value in each IP packet that decreases by one at every router the packet passes through. This operation occurs as the packet is forwarded, which is a function of the data plane. No routing decision is being made here; it's a simple, mechanical part of the forwarding process.

7. **G. Computing an IP header checksum** = **Data Plane**
   - The checksum verifies the integrity of the IP header. It’s calculated as packets pass through routers and devices to ensure that the header hasn’t been corrupted. Since this is done in transit and involves forwarding, it’s a data plane function.

8. **H. Running a protocol/logic to configure a middle box device for load balancing** = **Control Plane**
   - Configuring or running the logic for a middlebox (e.g., a load balancer) involves decisions about how traffic should be distributed. The control plane handles this high-level logic because it requires making choices about which backend server should handle incoming requests.

9. **I. Forwarding packets according to installed rules in a middlebox device** = **Data Plane**
   - Middlebox devices (such as firewalls, NAT devices, or load balancers) often have predefined rules that dictate how packets should be forwarded. Once these rules are installed, the actual packet forwarding is handled by the data plane based on those rules.

### Question 5
Which of the following types of switching can send multiple packets across the fabric in parallel?
- A) Memory
- B) Bus
- C) Interconnection Network (Crossbar)
- D) None of the above

**Answer:** C
**Explanation:** The interconnection network (crossbar) allows multiple packets to be forwarded simultaneously, as long as they use different input and output ports.

## Group 2
### Question 1
Consider a router with the following forwarding table:
```
Prefix Match   Output Link
101*           A
111*           B
1100 1*        C
Otherwise      D
```
Given that the router uses longest prefix matching, determine the output link for each of the following destination IP addresses:
1) 11100001 10000000 0001 0001 0111 1001
2) 1111 0001 1111 0000 1010 0001 0111 0111
3) 1010 1010 1010 1010 1010 1010 1010 1010
4) 1100 1001 1000 0001 0001 0001 0111 0111

**Answers:**
1) B
2) B
3) A
4) C
**Explanation:** The router uses the longest prefix matching rule to select the appropriate output link.

### Question 2
Determine the mask for the address 192.168.0.1/24.
- A) 255.255.255.0
- B) 255.255.0.0
- C) 255.0.0.0
- D) 192.168.0.24

**Answer:** A
**Explanation:** A /24 subnet mask corresponds to 255.255.255.0, indicating that the first 24 bits represent the network portion of the IP address.

## Group 3
### Question 1
Consider the following unibit trie. Nodes in blue represent stored prefixes.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-5-3-1.png?raw=true)


For each prefix lookup, determine the node we return.
1. 0*:
2. 1*:
3. 01*:
4. 00*:
5. 0000*:
6. 00011*:

**Answers:**
1) a
2) b
3) c
4) a
5) e
6) h
**Explanation:** The lookup follows the binary trie, matching each bit of the input to determine the longest prefix match.

## Group 4
### Question 1
Consider the following prefix database:
```
P1 => 101*
P2 => 0*
P3 => 1*
P4 => 10101*
```
Consider expanding each prefix with stride length 3, so that we construct a fixed-length multibit trie.
Which of the following prefixes are associated with P3? Select all that apply.
- A) 110*
- B) 10*
- C) 100*
- D) 101*
- E) 001*
- F) 111*

**Answer:** A, C, F
**Explanation:** During the expansion, P3 covers prefixes that start with '1'. As it is expanded, these include 110*, 100*, and 111*.

## Group 5
### Question 1
Consider the following prefix database that provides a mapping between nodes a, b, c, ..., g:
Construct the following variable-stride multibit trie. Based on the above database, fill in the nodes n8, n12, etc., with the corresponding nodes from the database.

**Answers:**
1) None
2) a
3) c
4) d
5) None
6) b
7) e
8) f
**Explanation:** The variable-stride multibit trie is constructed to match prefixes as they appear in the database, mapping nodes accordingly.

### Question 2
A multibit trie is shorter than a unibit trie representing the same prefix database and requires fewer memory accesses to perform a lookup.
**Answer:** Shorter, Fewer
**Explanation:** Multibit tries process multiple bits at each step, reducing both the depth of the trie and the number of memory accesses needed for a lookup.

### Question 3
Fixed-length multibit tries can support an arbitrary number of prefix lengths.
- A) True
- B) False

**Answer:** B
**Explanation:** Fixed-length multibit tries require prefix expansion to match the given stride length, thus limiting the direct support for arbitrary prefix lengths without modification.

## Group 6
### Question 1
The data plane functions of a traditional router are implemented in hardware.
- A) True
- B) False

**Answer:** A
**Explanation:** Data plane functions require high-speed processing and are implemented in hardware for fast packet forwarding.

### Question 2
The control plane functions of a traditional router are implemented in software.
- A) True
- B) False

**Answer:** A
**Explanation:** Control plane functions involve complex computations, routing protocols, and table management, which are handled by software.

### Question 3
The forwarding plane operations take place in shorter time scales than the control plane operations.
- A) True
- B) False

**Answer:** A
**Explanation:** The forwarding plane handles immediate packet forwarding, which operates on a faster timescale compared to the less frequent control plane operations.

### Question 4
The forwarding functions of a traditional router refer to transferring packets from the input ports to the appropriate output ports.
- A) True
- B) False

**Answer:** A
**Explanation:** Forwarding is the process of moving packets through the router based on the routing table's decisions.

### Question 5
The control plane functions can either be implemented in the router's processor or they can be 'outsourced' for implementation at a remote controller.
- A) True
- B) False

**Answer:** A
**Explanation:** With the advent of Software-Defined Networking (SDN), control plane functions can be managed centrally by a remote controller.

### Question 6
In traditional routers, traffic forwarding is performed based on:
- A) Destination IP address only
- B) Source IP address only
- C) Both source and destination IP addresses

**Answer:** A
**Explanation:** Traditional IP forwarding uses the destination IP address to decide the next hop for the packet.

### Question 7
Consider a router with the following forwarding table:
```
Prefix Match         Output Link
11100000 00*         A
11100000 01000000*   B
11100000*            C
11100001 1*          D
Otherwise            E
```
Given that the router uses longest prefix matching, determine the output link for packet with destination IP address: 10001000 11110001 01010001 11110101
- A) A
- B) B
- C) C
- D) D
- E) E

**Answer:** E
**Explanation:** None of the listed prefixes match the given IP address; therefore, the default route (Otherwise) is chosen.

### Question 8
Consider a router with the following forwarding table:
```
Prefix Match         Output Link
11100000 00*         A
11100000 01000000*   B
11100000*            C
11100001 1*          D
Otherwise            E
```
Given that the router uses longest prefix matching, determine the output link for packet with destination IP address: 11100001 01000000 11000011 00111100
- A) A
- B) B
- C) C
- D) D
- E) E

**Answer:** C
**Explanation:** The destination IP address matches the prefix '11100000*', which is the longest matching prefix in the table.

### Question 9
Consider a router with the following forwarding table:
```
Prefix Match         Output Link
11100000 00*         A
11100000 01000000*   B
11100000*            C
11100001 1*          D
Otherwise            E
```
Given that the router uses longest prefix matching, determine the output link for packet with destination IP address: 11100001 10000000 00010001 01110111
- A) A
- B) B
- C) C
- D) D
- E) E

**Answer:** D
**Explanation:** The destination IP address matches the prefix '11100001 1*', which is the longest matching prefix in the table.

### Question 10
Consider the following unibit trie.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-5-6-10.png?raw=true)


What is the longest prefix match for 111?
- A) P2
- B) P4
- C) P5

**Answer:** P2
**Explanation:** The lookup process in the unibit trie leads to the node corresponding to prefix P2 for the input 111.

### Question 11
Consider the following unibit trie.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-5-6-10.png?raw=true)


What is the longest prefix match for 11011?
- A) P2
- B) P4
- C) P5
- D) P9

**Answer:** P9
**Explanation:** The input 11011 matches with the prefix corresponding to P9 in the unibit trie.

### Question 12
Consider the following unibit trie.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-5-6-10.png?raw=true)


What is the longest prefix match for 10?
- A) P1
- B) P4
- C) P8
- D) None

**Answer:** P4
**Explanation:** The longest prefix match for the input 10 in the unibit trie corresponds to prefix P4.

### Question 13
By stride we refer to the number of bits that we check at every step when traversing a trie.
- A) True
- B) False

**Answer:** A
**Explanation:** In multibit tries, stride refers to the number of bits processed at each level, which affects the trie's structure and search efficiency.

