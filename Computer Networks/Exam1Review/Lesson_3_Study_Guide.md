
# Intradomain Routing Study Guide

## 1. Introduction to Intradomain Routing
- **Intradomain Routing** refers to routing within a single administrative domain using protocols that determine the "good" path for data to travel.
- Focuses on link-state and distance-vector algorithms and protocols such as OSPF (Open Shortest Path First) and RIP (Routing Information Protocol).
- **Key challenges:** convergence delay, traffic engineering to avoid congestion.

---

## 2. Routing Algorithms
- **Routing** is about how routers collaborate using protocols to find the best paths for data to travel from source to destination.
- **Forwarding** involves transferring packets from an incoming link to an outgoing link within a router.
- **Intradomain Routing** occurs within the same administrative domain using Interior Gateway Protocols (IGPs).
- **Two major classes of algorithms:** Link-state and Distance-vector algorithms.
- Network modeled as a graph with routers as nodes and links as edges, each with an associated cost.

---

## 3. Link-State Routing Algorithm
### a. Overview
- **Link-state algorithms**, such as Dijkstra's algorithm, use known network topologies to compute the shortest path.
- All nodes in the network have access to the link costs and topology (often through broadcasting).

### b. Terminology
- **D(v):** Cost of the least-cost path from the source node (u) to node (v).
- **p(v):** Previous node along the least-cost path from u to v.
- **c(u, v):** Cost from u to a directly connected neighbor v.
- **N':** Subset of nodes along the current least-cost path from u.

### c. Algorithm Steps
1. **Initialization:** Set all least-cost paths from u to its direct neighbors. Set non-neighbor nodes' costs to infinity.
2. **Loop:** Find the node w with the minimum cost in N'. Add w to N'. Update the cost D(v) for each neighbor v of w not in N'.

### d. Computational Complexity
- **Complexity:** O(n^2) due to searching through all nodes to find the node with the minimum path cost in each iteration.

### e. Example
- A network graph where a source node computes the shortest paths to all other nodes using the link-state algorithm.

---

## 4. Link-State Algorithm Example
- Uses a network graph to compute least-cost paths from a source node.
- Starts by setting the costs to direct neighbors and updates iteratively.
- The algorithm exits when all nodes' least-cost paths are found.

---

## 5. Distance Vector Routing
### a. Overview
- **Distance Vector (DV) Routing** is iterative, asynchronous, and distributed.
- Each node maintains its own distance vector, updating it based on information from its neighbors.
- Uses the **Bellman-Ford equation**: `Dx(y) = minv{c(x, v) + Dv(y)}` to calculate the cost of reaching each destination node through various neighbors.

### b. Example
- Nodes exchange distance vectors and update tables iteratively until all nodes converge to their shortest paths.

### c. Count-to-Infinity Problem
- When link costs increase drastically, nodes can get trapped in a loop where they continuously update costs based on each other's outdated information.
- Example: Node y thinks it can reach x through z, and vice versa, leading to continuous back-and-forth updates until the actual cost stabilizes.

### d. Poison Reverse
- **Poison reverse** is a solution where a node advertises an infinite cost for routes through a neighbor to prevent routing loops.
- This technique can prevent count-to-infinity issues for two nodes but doesn’t solve the problem for scenarios involving more than two nodes.

---

## 6. Distance Vector Routing Protocol Example: RIP
- **Routing Information Protocol (RIP)** is a DV protocol using hop count as a metric.
- Routers exchange updates periodically through RIP response messages called advertisements.
- Each router maintains a **routing table** with:
  - Destination subnet
  - Next hop router
  - Number of hops to destination
- RIP challenges include route updating, reducing convergence time, and avoiding loops.

### a. Example
- A network with routers using RIP to exchange routing tables and find the shortest paths.

---

## 7. Link-State Routing Protocol Example: OSPF
- **Open Shortest Path First (OSPF)** uses a link-state routing algorithm to determine the best path between routers.
- **Key Features:**
  - Uses Dijkstra's algorithm for shortest path computation.
  - Provides hierarchy within the routing domain.
  - Uses Link State Advertisements (LSAs) for topology information sharing.
- **OSPF Hierarchy:** Can be divided into areas, with one backbone area responsible for inter-area routing.
- **OSPF Operations:**
  1. Constructs a topological map of the Autonomous System (AS).
  2. Uses Dijkstra's algorithm to compute the shortest path.
  3. Broadcasts link-state information whenever there is a change in the network.
- **LSAs:** Used to communicate local routing topology within an OSPF area.

### a. Example
- An OSPF network with a backbone area and internal areas, illustrating how OSPF uses LSAs to maintain topology information.

---

## 8. Processing OSPF Messages in the Router
- Routers consist of a route processor and interface cards for packet forwarding.
- **Processing Steps:**
  1. LS updates containing LSAs are received and stored in the link-state database.
  2. Shortest Path First (SPF) algorithm is applied to calculate the shortest path.
  3. The resulting information is used to update the Forwarding Information Base (FIB).
  4. New LSAs are flooded to neighboring routers.

### a. Example
- The flow of processing OSPF messages in a router, starting from receiving LS updates to updating the FIB.

---

## 9. Hot Potato Routing
- **Hot Potato Routing:** A technique where a router forwards traffic to the closest egress point based on IGP costs.
- **Example:** A router chooses between two egress points (e.g., New York and San Francisco) based on the intradomain path cost.
- Simplifies computations for routers by focusing on IGP costs and aims to get traffic out of the network as quickly as possible.

---

This study guide covers the essentials of intradomain routing, including link-state and distance-vector algorithms, OSPF and RIP protocols, and routing challenges like the count-to-infinity problem. Diagrams and examples should be reviewed in the provided lecture slides for a more comprehensive understanding.
