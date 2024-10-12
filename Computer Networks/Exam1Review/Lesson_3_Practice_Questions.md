
# Lesson 3: Intradomain Routing - Practice Questions

## Group 1: 4 Questions
### Question 1
In this lecture, we discuss intradomain routing, where all the nodes and subnets are owned and managed by the same organization. (In contrast, interdomain routing is about routing between different organizations – such as between two ISPs.) Before we begin talking about intradomain routing algorithms, what could the weights on the graph edges represent in these diagrams, when we are seeking the least-cost path between two nodes?

- [ ] Length of the cable
- [ ] Time delay to traverse the link
- [ ] Monetary cost
- [ ] Business relationships
- [ ] Link capacity
- [ ] Current load on the link

**Answer:** Length of the cable, Time delay to traverse the link, Monetary cost, Link capacity, Current load on the link

**Explanation:** The weights on the graph edges can represent various metrics such as the physical length of the cable, the time delay to traverse a link, monetary costs for using the link, link capacity (bandwidth), or the current load on the link. These factors help determine the least-cost path between two nodes. Business relationships, while potentially influencing routing decisions in real-world networks, are not typically represented as graph edge weights in intradomain routing algorithms.

---

### Question 2
A packet is ___________ when it is moved from a router’s input link to the appropriate output link.
- [ ] Routed
- [ ] Forwarded
- [ ] Switched
- [ ] Acknowledged

**Answer:** Forwarded

**Explanation:** Forwarding refers to the process of moving a packet from an input link to an output link within a router.

### Question 3
Determine which action in network wide (i.e., involves multiple routers).
- [ ] Routing
- [ ] Forwarding

**Answer:** Routing

**Explanation:** Routing involves determining the paths packets take across a network of routers, whereas forwarding is the action of sending packets along a pre-determined path.

### Question 4
Intradomain routing itself involves multiple administrative domains.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Intradomain routing occurs within a single administrative domain. Interdomain routing occurs between different domains.

---




## Group 2: 3 Questions

### Question 1
In the previous example, node u was the source node, and distances were calculated from u to each other node. Consider the same example, but let x be the source node. Notice that node x has more direct neighbors than u does. Suppose x is executing the link-state algorithm as discussed, and has just finished the initialization step. Which of the following statements are true?

![Link-State Routing Example](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-3-2-1.png?raw=true)

- [ ] Node x will execute fewer iterations than node u did, as there were fewer "infinity distance nodes" after initialization.
- [ ] Node x will execute the same number of iterations that node u did, as the number of immediate neighbors has no impact on the number of iterations the algorithm requires.
- [ ] Node x will execute more iterations than node u did, as there are more immediate neighbors to consider.

**Answer:** Node x will execute the same number of iterations that node u did, as the number of immediate neighbors has no impact on the number of iterations the algorithm requires.

**Explanation:** In Dijkstra's link-state algorithm, the number of iterations is equal to the number of nodes in the network minus one, regardless of the number of immediate neighbors of the source node. The algorithm iterates over all nodes to find the shortest path tree, so having more direct neighbors does not change the total number of iterations. It simply affects the initialization step and the initial costs set for the direct neighbors.

### Question 2
Upon termination of Dijkstra's algorithm, all nodes in a network are aware of the entire network topology.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Dijkstra's algorithm itself does not provide awareness of the entire network topology to all nodes. It is executed by one node to compute the shortest paths to all other nodes. In a link-state routing protocol, each node must receive and share link-state information with other nodes to understand the full network topology. The awareness of the topology comes from the link-state protocol, not from the execution of Dijkstra's algorithm alone.

---

### Question 3
Consider the following topology. Let b be the source node. Use Dijkstra’s algorithm to determine the cost of the least-cost path from node b to all other nodes in the network upon termination of the algorithm.

![Network Topology for Dijkstra's Algorithm](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-3-2-3.png?raw=true)

- Cost from node a: _____
- Cost from node c: _____
- Cost from node d: _____
- Cost from node e: _____
- Cost from node f: _____

**Answer:**
- Cost from node 6 to node 2: 1
- Cost from node 6 to node 3: 2
- Cost from node 6 to node 4: 3
- Cost from node 6 to node 5: 4

**Explanation:** Using Dijkstra's algorithm, we calculate the shortest paths from node 6 to all other nodes based on the link costs provided in the topology diagram. The values are computed iteratively by selecting the nodes with the minimum path cost in each iteration.

**Explanation:** The link-state algorithm adds the node with the minimum cost path to the tree. In this network, node v has the minimum path cost in the first iteration.

---

## Group 3: 2 Questions
### Question 1
Select the words that can be used to describe the distance vector algorithm.
- [ ] Distributed
- [ ] Centralized
- [ ] Iterative
- [ ] Asynchronous
- [ ] Synchronous
- [ ] Non-terminating

**Answer:** Distributed, Iterative, Asynchronous

**Explanation:** The distance vector algorithm is decentralized (distributed), operates iteratively until convergence, and asynchronously updates its tables.

### Question 2
Determine which of the following can cause the count-to-infinity problem.
- [ ] Poison reversing
- [ ] Routing Loops
- [ ] Hot potato routing
- [ ] Dropped packets

**Answer:** Routing Loops

**Explanation:** Routing loops in distance vector routing can lead to the count-to-infinity problem, where routers continuously update incorrect route costs.

---

## Group 4: 3 Questions
### Question 1
Dijkstra's algorithm is a global routing algorithm, which is also referred to as a link-state algorithm.
- **Answer 1:** global
- **Answer 2:** link-state

**Explanation:** Dijkstra's algorithm requires knowledge of the entire network topology, hence it is considered a global link-state algorithm.

### Question 2
The Bellman Ford equation is used by the ___________ algorithm.
- [ ] link-state
- [ ] distance vector

**Answer:** Distance vector

**Explanation:** The Bellman-Ford equation is used by distance vector algorithms to calculate the shortest paths to each destination node.

### Question 3
Select all statements that correctly complete the sentence. The Routing Information Protocol (RIP) is an example of ___________.
- [ ] a link-state algorithm
- [ ] a distance vector algorithm
- [ ] poison reverse
- [ ] an interdomain routing algorithm
- [ ] an intradomain routing algorithm

**Answer:** A distance vector algorithm, an intradomain routing algorithm

**Explanation:** RIP is a distance vector protocol used within an autonomous system (intradomain).

---

## Group 5: 2 Questions
### Question 1
There may be multiple egress points from an administrative domain to an external destination.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** Large networks can have multiple egress points for traffic to exit the administrative domain and reach external networks.

### Question 2
Hot potato routing always selects the egress point that is geographically closest to the ingress point.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Hot potato routing chooses the closest egress point based on intradomain path cost (Interior Gateway Protocol/IGP cost), not necessarily the geographically closest point.

---


## Group 6: 20 Questions

### Question 1
"Routing" and "forwarding" are interchangeable terms.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Routing and forwarding are not the same. Routing involves the process of selecting paths in a network along which to send network traffic, while forwarding is the act of moving packets from the input to the output of the router.

### Question 2
Consider a source and destination host. Before packets leave the source host, the host needs to define the path over which the packets will travel to reach the destination host.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** The source host does not define the path that packets take. The network routers use routing algorithms to determine the path dynamically as packets traverse through the network.

### Question 3
Intradomain routing refers to routing that takes place among routers that belong to the same administrative domain. In contrast, when routers belong to different administrative domains, we refer to routing as interdomain routing.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** Intradomain routing is also known as interior gateway routing, operating within a single autonomous system, whereas interdomain (exterior gateway) routing occurs between different autonomous systems.

### Question 4
Consider the link-state routing protocol. The link costs are known to all nodes.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** In link-state routing, all nodes have a complete view of the network's topology, including the costs of all links. This information is shared and updated through link-state advertisements.

### Question 5
**Question:**
Consider the link-state routing protocol. The network topology is known to all nodes.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** In a link-state routing protocol, each node has complete knowledge of the network topology. This is achieved through the exchange of link-state advertisements (LSAs) between nodes. These LSAs contain information about the state of each node's links, allowing all nodes to construct an identical view of the entire network's topology. Once the topology is known, each node can use algorithms like Dijkstra’s to compute the shortest paths to all other nodes.

### Question 6
Consider the link-state routing protocol and a node u as our source node. The goal of the algorithm is to compute the least-cost paths from the source node u to every other node in the network.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** The purpose of the link-state routing algorithm, such as Dijkstra's algorithm, is to determine the shortest path tree from the source node to all other nodes in the network.

### Question 7
Consider the link-state routing protocol with a node u as our source node. Consider the initialization of the algorithm. We initialize the least-cost path from node u to directly attached neighbors to be the cost of the direct links, and for non-directly attached neighbors, we initialize the least-cost path to be infinity.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** During the initialization step of the link-state routing algorithm, the distances to directly connected neighbors are set to the cost of the direct links, while other nodes' distances are set to infinity.

### Question 8
The distance vector (DV) routing algorithm continues iterating as long as neighbors send new updates to each other.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** Distance vector routing algorithms rely on iterative updates between neighbors. They continue to exchange information until there are no more changes in the routing tables.

### Question 9
The distance vector (DV) routing algorithm is an example of a ___________ algorithm.
- [ ] centralized
- [ ] decentralized

**Answer:** Decentralized

**Explanation:** DV routing is decentralized because each router independently calculates its distance vectors based on information received from its directly connected neighbors.

### Question 10
The distance vector (DV) routing algorithm requires synchronization between routers.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** DV algorithms do not require synchronization between routers. They operate asynchronously, with routers updating their tables as they receive updates from neighbors.

### Question 11
In the distance vector (DV) routing algorithm, each node maintains and updates its own view of the network.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** In DV routing, each router maintains its own distance vector, which contains the cost to reach each network destination. This vector is updated based on information received from neighbors.

### Question 12
Consider the distance (DV) routing algorithm. Which is used by each node to update the node's distance vector?
- [ ] The spanning tree protocol
- [ ] Dijkstra's algorithm
- [ ] The Bellman Ford equation
- [ ] None of the above

**Answer:** The Bellman Ford equation

**Explanation:** The Bellman-Ford equation is used to update the distance vectors in DV routing. Each node calculates the cost to a destination via each of its neighbors and selects the minimum cost.

### Question 13
The count-to-infinity problem states that good news (e.g., a decrease in a link cost) propagates slowly among nodes in the network.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** The count-to-infinity problem specifically refers to how **bad news** (such as a link failure or increase in link cost) propagates slowly across the network in distance vector routing. Good news, such as a decrease in link cost, generally propagates quickly because nodes immediately update their routing tables to reflect the lower cost paths. The slow propagation of bad news is what causes routing loops and delayed convergence in distance vector protocols.


### Question 14
The poison reverse technique solves the count-to-infinity problem for all network topologies.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Poison reverse helps mitigate the count-to-infinity problem in simple topologies by advertising an infinite cost for routes that a router learned through a particular neighbor. However, it doesn't solve the problem entirely for more complex network topologies.

### Question 15
The Routing Information Protocol (RIP) is based on the Distance Vector protocol.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** RIP is a distance vector routing protocol that uses hop count as its metric and shares routing tables periodically with neighboring routers.

### Question 16
Open Shortest Path First (OSPF) is based on the link-state routing algorithm.
- [ ] True
- [ ] False

**Answer:** True

**Explanation:** OSPF is a link-state protocol that maintains a full map of the network topology in each router and uses Dijkstra's algorithm to calculate the shortest path.

### Question 17
The number of egress points that a network has is upper bounded, e.g., two or three egress points per network.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** The number of egress points in a network is not strictly bounded. It can vary based on network size, architecture, and design.

### Question 18
Consider a network with multiple egress points. Further, consider that these egress points offer different paths to the same external destinations. Then these paths must have different costs.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Paths can have the same cost depending on network configuration, even if they traverse different routes to reach the same destination.

### Question 19
According to the hot potato routing technique, it is in a network's best interest to route the traffic so that it exits the network at the router geographically closest to the one from which it entered the network.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Hot potato routing aims to offload traffic to the closest egress point based on intradomain path cost, not necessarily geographical proximity.

### Question 20
Assume a source and a destination host. As packets travel over a path from the source host to the destination host, the packets are handled by multiple routers over that path. If these routers belong to different administrative domains, they need to run the same intradomain routing algorithm, since they are on the same path for that pair of hosts.
- [ ] True
- [ ] False

**Answer:** False

**Explanation:** Routers in different administrative domains do not need to run the same intradomain routing algorithm. Instead, when traffic passes between different administrative domains, interdomain routing protocols, such as the Border Gateway Protocol (BGP), are used to handle the routing between the domains. Intradomain routing algorithms like OSPF or RIP are used within a single administrative domain (autonomous system). Different domains may use different routing protocols internally but still communicate effectively using interdomain protocols.
