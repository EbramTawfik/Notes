# Router Design and Algorithms Study Questions and Answers

## 1. What are the basic components of a router?

A router consists of the following basic components:

1. **Input Ports:** Responsible for receiving packets from incoming links. Each input port performs several key functions, such as physical layer functions (bit-level reception) and data link layer functions (decapsulation and error detection). The port also contains lookup, forwarding, and queuing mechanisms to decide the appropriate output port based on the destination address.
2. **Switching Fabric:** Connects input ports to output ports within the router. It moves packets from the input side to the correct output port, functioning as the router’s internal network.
3. **Output Ports:** Responsible for sending packets to the outgoing links. Each output port performs buffering, forwarding, and link layer functions, including encapsulating packets for transmission over the physical link.
4. **Control Plane:** This is the software-based part of the router that manages routing protocols, maintains the routing table, and makes routing decisions. It communicates with the forwarding plane to update the forwarding table used by input ports for packet forwarding.
5. **Routing Processor:** Handles control plane functions, such as executing routing algorithms (e.g., OSPF, BGP), managing the routing table, and running network management software (e.g., SNMP).

## 2. Explain the forwarding (or switching) function of a router.

The **forwarding** (or switching) function is the process of transferring a packet from an input port to an output port within the router. The process follows these steps:

1. **Lookup:** When a packet arrives at an input port, the router examines its destination IP address. The input port consults the forwarding table to determine the appropriate output port based on the longest prefix match.
2. **Switching Fabric:** The packet is moved from the input port to the output port via the switching fabric. The fabric serves as the router's internal "network," enabling the transfer of packets from one port to another.
3. **Queuing and Buffering:** At the output port, the packet is queued and buffered if necessary, particularly during periods of congestion when the outgoing link is busy.
4. **Transmission:** Finally, the packet is transmitted out of the output port to the next hop along its path toward the destination.

## 3. The switching fabric moves the packets from input to output ports. What are the functionalities performed by the input and output ports?

### Input Port Functions:
1. **Line Termination:** Physically connects to the incoming link, receiving the packet bits from the network.
2. **Data Link Processing:** Decapsulates and processes the packet using the appropriate data link layer protocol.
3. **Lookup and Forwarding:** Examines the destination IP address in the packet header, consults the forwarding table, and identifies the correct output port for the packet.
4. **Queuing:** Temporarily stores packets in a queue before they are passed to the switching fabric if necessary.

### Output Port Functions:
1. **Queuing and Buffering:** Stores packets temporarily if the output link is busy or congested, managing the flow to avoid packet loss.
2. **Link Layer Processing:** Encapsulates packets for transmission, adding link layer headers and trailers.
3. **Line Termination:** Sends the packet bits over the outgoing physical link.

## 4. What is the purpose of the router’s control plane?

The **control plane** is responsible for the decision-making processes within a router. Its main purposes include:

1. **Routing Table Management:** Uses routing protocols (such as OSPF, RIP, BGP) to build and maintain the routing table.
2. **Routing Protocols Execution:** Communicates with neighboring routers to exchange routing information and calculate optimal paths based on the network topology.
3. **Forwarding Table Updates:** Provides the forwarding plane with an updated forwarding table that contains mappings of destination IP addresses to the appropriate output ports.

## 5. What tasks occur in a router?

A router performs several key tasks, including:

1. **Packet Reception:** Receives packets on input ports from external networks.
2. **Forwarding Decision:** Examines the packet header to determine the destination and consults the forwarding table for the correct output port.
3. **Switching:** Uses the switching fabric to transfer packets from the input port to the appropriate output port.
4. **Queuing and Buffering:** Manages packet queues at both input and output ports, buffering packets when necessary to handle congestion.
5. **Transmission:** Sends the packet out through the designated output port.
6. **Control Functions:** Executes routing protocols, maintains the routing table, and updates the forwarding table.

## 6. List and briefly describe each type of switching. Which, if any, can send multiple packets across the fabric in parallel?

1. **Switching via Memory:** The earliest form of router switching, where packets are copied to the router’s processor memory for forwarding. The processor reads the packet from the input port, determines the output port, and writes it to memory. This method is slow and limited by memory speed, allowing only one packet at a time to be processed.

2. **Switching via Bus:** A shared bus connects all input and output ports. Packets include an internal header that specifies the desired output port. The packet is sent over the bus, and only the specified output port accepts the packet. While faster than memory-based switching, only one packet can be transferred at a time, making it unsuitable for high-performance routers.

3. **Switching via Interconnection Network (Crossbar):** A matrix-style network connecting input ports to output ports, allowing multiple packets to be switched simultaneously as long as they do not require the same output port. This method supports parallel packet transfers and is used in high-performance routers to handle large volumes of traffic efficiently.

**Parallel Packet Transfer:** Switching via interconnection network (crossbar) can send multiple packets across the fabric in parallel.

## 7. What are two fundamental problems involving routers, and what causes these problems?

1. **Scalability:** Routers need to handle a large number of IP prefixes and flows in the network. As the number of connected devices and networks grows, the routing tables become larger. This requires routers to efficiently manage and update large routing tables, which can be a complex task due to frequent changes in network topology and routing policies. The primary cause is the exponential growth of the internet and the increasing number of prefixes in routing tables.

2. **Quality of Service (QoS):** Different types of network traffic (e.g., voice, video, data) have different requirements for delay, jitter, and loss. Routers must implement traffic prioritization and bandwidth management to meet these requirements. The complexity arises from the need to process and classify packets based on various criteria, such as source address, destination address, and QoS flags, all while maintaining high-speed processing.

## 8. What are the bottlenecks that routers face, and why do they occur?

Routers face several bottlenecks due to the demands of modern networks:

1. **Exact Lookups:** As link speeds increase, routers must perform fast lookups in large routing tables. The need for quick lookup operations in high-speed routers results in memory access speed becoming a limiting factor. Solutions like parallel hashing are necessary to overcome this issue.

2. **Prefix Lookups:** Routers need to match incoming packets to prefixes in a large and growing database. The challenge is to handle the increasing number of prefixes efficiently, which can lead to delays if not managed properly. Techniques like compressed multibit tries address this problem.

3. **Packet Classification:** Differentiating packets based on multiple criteria (e.g., source, destination, service type) is computationally intensive. As link speeds and the variety of traffic increase, routers struggle to classify packets fast enough to meet network demands.

4. **Switching:** Optical-electronic speed gaps and head-of-line blocking can create bottlenecks in packet forwarding. Using crossbar switches and virtual output queues can help mitigate these problems.

5. **Fair Queuing:** Managing congestion and providing fair bandwidth distribution becomes increasingly complex as link speeds and traffic diversity grow. Algorithms like weighted fair queuing and deficit round-robin are used to manage these issues.

## 9. Convert between different prefix notations (dot-decimal, slash, and masking).

### Example:
- **Dot-Decimal:** 192.168.1.0
- **Slash Notation:** 192.168.1.0/24
- **Masking:** 192.168.1.0 with a subnet mask of 255.255.255.0

### Explanation:
- **Dot-Decimal:** Represents the IP address in a human-readable form.
- **Slash Notation:** Indicates the network prefix length (e.g., /24 means the first 24 bits are the network part).
- **Masking:** Uses a subnet mask (e.g., 255.255.255.0) to specify the network portion of the address.

## 10. What is CIDR, and why was it introduced?

**Classless Inter-Domain Routing (CIDR)** was introduced in 1993 to replace the class-based IP addressing system. CIDR allows for variable-length subnet masking (VLSM), enabling more flexible IP address allocation. With CIDR, IP addresses are expressed in the form of 'IP address/Prefix Length' (e.g., 192.168.0.0/16). CIDR was introduced to reduce the size of routing tables, slow down the depletion of IPv4 addresses, and allow for more efficient and hierarchical address assignment.

## 11. Name 4 takeaway observations around network traffic characteristics. Explain their consequences.

1. **High Number of Concurrent Flows:** Routers in the network backbone must handle a vast number of concurrent flows, making caching ineffective. This necessitates the use of fast algorithms for packet processing since each flow may have different characteristics and priorities.

2. **High Volume of Small Packets (TCP ACKs):** A significant portion of network traffic comprises small packets, such as TCP acknowledgments. Routers need to perform wire-speed lookups to process these packets quickly, as delays can affect the overall network performance.

3. **Lookup Speed Affected by Memory Access:** The speed of prefix lookups in routers is often limited by the memory access time. Efficient data structures, such as multibit tries and compressed tries, are needed to minimize memory accesses and optimize lookup speed.

4. **Increasing Prefixes:** As the number of prefixes in routing tables grows (due to more networks and subnetting), routers need to handle up to a million prefixes efficiently. This requires scalable data structures and lookup algorithms to manage the increasing complexity.

## 12. Why do we need multibit tries?

**Multibit tries** are needed to reduce the number of memory accesses during IP prefix lookups. In a unibit trie, each bit of the IP address is processed one at a time, which can result in up to 32 memory accesses for a 32-bit address. Multibit tries, however, examine multiple bits at each step (stride) of the lookup, significantly reducing the total number of memory accesses. This optimization is crucial for maintaining high-speed routing performance, especially in large networks with extensive routing tables.

## 13. What is prefix expansion, and why is it needed?

**Prefix expansion** is the process of adjusting the length of all prefixes in a trie to match a fixed stride length. In a multibit trie, if the prefixes do not align with the fixed stride boundaries, they are expanded to fit into the trie nodes. This is needed to ensure that each node in the trie can be traversed efficiently using a fixed number of bits (stride) for lookups. Prefix expansion helps simplify the lookup process and improve the speed of routing decisions.

## 14. Perform a prefix lookup given a list of pointers for unibit tries, fixed-length multibit tries, and variable-length multibit tries.

- **Unibit Tries:** Start at the root of the trie and traverse one bit at a time. Use each bit of the IP address to decide the next node to visit. The longest matched prefix during this traversal is used to determine the forwarding decision.
- **Fixed-Length Multibit Tries:** Divide the IP address into segments based on the fixed stride length (e.g., 4 bits). At each step, use the corresponding segment of the IP address to traverse the trie. The traversal continues until no further match is found, and the longest matched prefix is returned.
- **Variable-Length Multibit Tries:** Use a variable stride length at each level of the trie. The lookup process is similar to fixed-length multibit tries, but the number of bits used at each step varies depending on the structure of the trie. This method provides more flexibility and can optimize memory usage.

## 15. Perform a prefix expansion. How many prefix lengths do old prefixes have? What about new prefixes?

**Performing Prefix Expansion:** Involves converting prefixes to a uniform length by adding extra bits as necessary. For example, a prefix of length 8 (e.g., 192.0.0.0/8) could be expanded to a length of 16 by appending zeros.

- **Old Prefixes:** Typically have fixed lengths (e.g., /8, /16, /24) based on classful addressing.
- **New Prefixes:** Have variable lengths due to the introduction of CIDR. They can range from very short (e.g., /4) to very long (e.g., /30), depending on network requirements.

## 16. What are the benefits of variable-stride versus fixed-stride multibit tries?

**Variable-Stride Multibit Tries:** Allow different numbers of bits to be examined at each level of the trie, optimizing memory usage and lookup speed. By using variable strides, routers can adapt the trie structure to the distribution of prefixes, reducing memory consumption and improving search efficiency.

**Fixed-Stride Multibit Tries:** Use a consistent stride length across all levels of the trie, which simplifies implementation. However, they may not be as memory-efficient as variable-stride tries since they do not adapt to the distribution of prefixes in the network.

**Benefits of Variable-Strides:**
- More flexibility in adjusting trie structure based on prefix distribution.
