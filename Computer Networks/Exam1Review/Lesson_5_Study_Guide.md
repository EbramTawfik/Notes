
# Router Design and Algorithms Study Material

This study guide covers essential topics in router operations, internal architecture, and prefix-match lookups. The content includes detailed explanations and examples to aid your understanding of these concepts.

## 1. Overview of Router Operations

Routers are a critical part of the Internet's physical infrastructure, responsible for forwarding data from the source to the destination by determining the correct path.

### Main Router Tasks:
- Transfer the received packet from an **input link interface** to the appropriate **output link interface** by examining the packet's **destination IP address** and consulting the **forwarding table**.
  
### Challenges in Router Operations:
1. **Scalability:** Handling large volumes of traffic efficiently, especially in high-speed networks.
2. **Advanced Traffic Handling:**
   - Special handling for **quality of service (QoS)** or **security guarantees**.
   - Process packets based on multiple criteria, such as QoS flags and packet classification.

### Algorithms Used by Routers:
- **Longest Prefix Matching:** Determines the best output link by finding the longest matching prefix in the forwarding table.
- **Packet Classification:** Differentiates packets based on multiple header fields to ensure appropriate handling (e.g., QoS or security).
- **Scheduling:** Manages packet forwarding based on priority or other rules to meet specific traffic requirements.

---

## 2. What’s Inside a Router

The router's internal architecture comprises two main functions: the **forwarding plane** (hardware-based) and the **control plane** (software-based). The forwarding plane handles fast packet transmission, while the control plane manages routing logic and protocols.

### 2.1 Forwarding Data Plane

Handles data packets and forwards them to their destinations, typically implemented in hardware for optimal performance.

#### - Input Ports:
  - **Line Termination:** Connects incoming data packets from external links.
  - **Data Link Processing:** Processes incoming packets using the data link layer protocol.
  - **Lookup, Forwarding, and Queuing:** Checks the forwarding table, selects the correct output port, and queues the packet.

#### - Switch Fabric:
  - **Memory-Based:** The oldest type, where packets are written to and read from memory.
  - **Bus-Based:** Transfers packets via a shared bus.
  - **Crossbar-Based:** A matrix system allowing multiple packets to be forwarded simultaneously.

#### - Output Ports:
  - Queues and buffers packets before sending them to the next destination.

### 2.2 Control Plane

Responsible for decision-making processes like routing table management and protocol implementation. Operates in software, generally working on a slower timescale.

#### - Routing Processor:
  - Manages routing protocols (e.g., OSPF, BGP) and calculates the best routes.
  - Maintains the routing table for the forwarding plane.

---

## 3. Router Architecture

A router processes packets through stages of lookup, switching, and scheduling.

### Key Components and Processes:
1. **Lookup:** Uses the Forwarding Information Base (FIB) to match destination IP prefixes.
2. **Switching:** Uses a crossbar switch for packet transfer to the output port.
3. **Queuing:** Buffers packets if the output link is congested.

---

## 4. Different Types of Switching

The switching fabric in a router can use memory, bus, or interconnection network (crossbar) methods.

### 4.1 Switching via Memory
- Copies packets through the CPU, leading to bottlenecks.

### 4.2 Switching via Bus
- Bypasses the processor using an internal header for routing packets.

### 4.3 Switching via Interconnection Network (Crossbar)
- Allows multiple packets to be switched simultaneously.

---

## 5. Router Bottlenecks

Challenges routers face in scaling to meet the demands of modern internet services.

- **Exact Lookups:** Parallel hashing.
- **Prefix Lookups:** Compressed multibit tries.
- **Packet Classification:** Decision tree algorithms, CAMS.
- **Switching:** Crossbar switches, virtual output queues.
- **Fair Queuing:** Weighted fair queuing, deficit round robin.
- **Security:** Traceback with Bloom filters.

---

## 6. Prefix-Match Lookups

### Prefix Notation:
- **Dot Decimal:** For example, `132.234` can be represented in binary.
- **Slash Notation:** `132.238.0.0/16`.
- **Masking:** `123.234.0.0` with a mask of `255.255.0.0`.

### Challenges:
- Handling up to 1 million prefixes in modern networks.
- Minimizing memory access during lookups.

---

## 7. Prefix-Match Lookups – Unibit Tries

Unibit tries use binary tree structures for efficient prefix matching.

### Example:
- Prefixes are structured in a binary tree for quick lookup.
- The trie processes one bit at a time to match the longest prefix.

---

## 8. Prefix-Match Lookups – Multibit Tries

### Why Multibit Tries?
- Reduces memory accesses during lookups.

### Types:
1. **Fixed-Length Stride:** Consistent stride simplifies implementation.
2. **Variable-Length Stride:** Optimizes memory usage by adjusting the number of bits processed at each node.

---

## 9. Prefix-Match Lookups – Fixed Stride

A fixed-stride trie processes a set number of bits at each step.

### Example (3-bit stride):
- Nodes represent multiple bits, reducing memory accesses.

---

## 10. Prefix-Match Lookups – Variable Stride

Variable strides allow different bits to be examined at each node, optimizing memory efficiency by tailoring stride lengths to specific prefix lengths.

---

### Key Takeaways

1. Routers use complex algorithms and architectures to handle data efficiently.
2. Switching methods (memory, bus, crossbar) offer trade-offs between speed and scalability.
3. Prefix-match lookups are optimized using various trie-based techniques to minimize memory usage and access times.
4. The choice of switching and lookup methods affects a router’s ability to handle high-speed network traffic and scalability challenges.
