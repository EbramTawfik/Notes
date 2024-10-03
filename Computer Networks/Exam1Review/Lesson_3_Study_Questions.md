
# Lesson 3: Intradomain Routing - Study Questions and Answers

## 1. What is the difference between forwarding and routing?
- **Forwarding** refers to the process of transferring a packet from an incoming link to an outgoing link within a single router. When a packet arrives at a router, the router consults its forwarding table to decide which interface to send the packet out on.
- **Routing**, on the other hand, is the process by which routers determine the best path through the network for packets to travel from the source to the destination. Routing involves the exchange of routing information between routers using routing protocols and the creation of forwarding tables. Essentially, routing determines "how" packets will move through the network, while forwarding is the "act" of moving the packets.

## 2. What is the main idea behind a link-state routing algorithm?
- The main idea of a **link-state routing algorithm** is that every router in the network has complete knowledge of the network's topology. Each router independently computes the shortest path to every other router in the network using this knowledge. Routers use a distributed algorithm to share information about the state of their links (costs, status) with every other router in the network.
- In the link-state algorithm, each router builds a map of the network in the form of a graph, with routers as nodes and links as edges with associated costs. Using this information, each router computes the shortest paths to all destinations using algorithms like Dijkstra's algorithm.

## 3. What is an example of a link-state routing algorithm?
- An example of a link-state routing algorithm is **Dijkstra's algorithm**. Dijkstra's algorithm computes the shortest path from a single source node to all other nodes in the network, constructing the shortest path tree.

## 4. Walk through an example of the link-state routing algorithm.
1. **Initialization:** The algorithm starts at a source node (e.g., node u). The initial costs to directly connected neighbors are set, and all other nodes are set to have an infinite cost.
2. **Loop:** The algorithm looks for the node that has the smallest cost path from the source node and adds it to the set of nodes for which the shortest path has been found. Then, it updates the path costs to all other nodes using the newly added node's connections.
3. **Updating Costs:** For each node, the algorithm compares the known path cost to the cost of a newly discovered path through an adjacent node. It chooses the lesser of the two.
4. **Completion:** The algorithm iterates over all nodes in the network, updating paths and adding nodes until all nodes are included in the shortest path tree.
- For example, if a network has nodes u, v, w, and x, and each edge has an associated cost, the link-state algorithm would start at u, find the shortest cost to directly connected nodes, then use that information to find the next shortest paths iteratively until all nodes are covered.

## 5. What is the computational complexity of the link-state routing algorithm?
- The **computational complexity** of the link-state routing algorithm, particularly Dijkstra's algorithm, is O(n^2), where n is the number of nodes in the network. This complexity arises from the need to search through all nodes to find the node with the minimum path cost at each step of the algorithm.

## 6. What is the main idea behind the distance vector routing algorithm?
- The main idea of the **distance vector routing algorithm** is that each router maintains a table (vector) of the minimum distances (costs) to every other node in the network. Each router periodically shares its distance vector with its directly connected neighbors.
- Routers use the Bellman-Ford equation to update their own distance vector based on the information received from neighbors. Specifically, they look at the possible paths to each destination through each neighbor, calculate the costs, and select the minimum cost path.
- Unlike link-state algorithms, routers do not have a complete view of the network topology; they only have information about the distances to their neighbors.

## 7. Walk through an example of the distance vector algorithm.
1. **Initialization:** Each router starts by having its own distance vector table, which contains the cost to each directly connected neighbor. Costs to non-neighbor nodes are initially set to infinity.
2. **Exchange Information:** Each router sends its current distance vector to all of its neighbors.
3. **Update Table:** When a router receives distance vectors from its neighbors, it uses the Bellman-Ford equation to calculate the cost of reaching each destination through each neighbor. It updates its table with the minimum cost path.
4. **Convergence:** This process continues iteratively, with routers exchanging updates and recalculating costs until no more changes occur, indicating convergence.
- Example: In a network with three nodes x, y, and z, each node initially only knows the cost to its immediate neighbors. After several exchanges of distance vectors, each node learns the costs to reach all other nodes.

## 8. When does the count-to-infinity problem occur in the distance vector algorithm?
- The **count-to-infinity problem** occurs in the distance vector algorithm when there is an increase in the link cost or a link failure in the network. This problem arises because routers continuously exchange information based on their neighbors' distance vectors. If a router mistakenly believes that it can reach a destination through a neighbor when a direct link fails, it will keep updating its cost to the destination based on outdated information, causing the cost to "count to infinity."
- For example, if the link cost between nodes x and y suddenly increases, y may still think it can reach x through z, and z might think it can reach x through y, resulting in a continuous loop of updates.

## 9. How does poison reverse solve the count-to-infinity problem?
- **Poison reverse** is a technique used to prevent the count-to-infinity problem by advertising an infinite cost to a destination if the path to that destination is through a particular neighbor. Essentially, when a router tells its neighbor that it cannot reach a destination (by setting the cost to infinity), the neighbor will not try to route packets through this path, thus breaking potential loops.
- This technique works well for small loops (e.g., two nodes) but is not a complete solution for larger network topologies.

## 10. What is the Routing Information Protocol (RIP)?
- **Routing Information Protocol (RIP)** is a distance vector routing protocol that uses hop count as a metric to determine the best path between routers. Each router periodically shares its routing table with its neighbors using RIP advertisements.
- RIP limits the maximum hop count to 15 to prevent routing loops, and if a router does not receive updates from a neighbor within a certain period (180 seconds), it considers the route as unreachable.

## 11. What is the Open Shortest Path First (OSPF) protocol?
- **Open Shortest Path First (OSPF)** is a link-state routing protocol that uses Dijkstra's algorithm to find the best path between routers. OSPF maintains a map of the network topology and floods link-state information using Link State Advertisements (LSAs) to build this map.
- OSPF supports hierarchical routing, dividing the network into areas. The backbone area connects different areas, facilitating efficient and organized routing within the network.

## 12. How does a router process advertisements?
- When a router receives an advertisement (e.g., LSA in OSPF or RIP response message), it:
  1. Checks whether the information is new or a duplicate by consulting its current routing table or link-state database.
  2. If the advertisement contains new information, it updates its routing table (or link-state database in the case of OSPF).
  3. It recalculates the best paths using the updated information. In OSPF, this involves running Dijkstra's algorithm.
  4. It then propagates this updated information to its neighboring routers.

## 13. What is hot potato routing?
- **Hot potato routing** is a strategy used within an intradomain routing protocol to forward traffic to the nearest egress point based on the lowest intradomain path cost. The router "gets rid" of the traffic as soon as possible, forwarding it to an egress point closest to it.
- For example, if a router in Dallas must forward traffic destined for an external network, and it has two egress points (New York and San Francisco) to choose from, it will select the egress point with the lowest path cost (e.g., the closer one).

