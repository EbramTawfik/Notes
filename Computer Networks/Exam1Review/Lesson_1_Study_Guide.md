# Computer Networks - Lesson 1 Comprehensive Study Guide
## Table of Contents
- [1. What were the main topics covered in the first lecture?](#1.-what-were-the-main-topics-covered-in-the-first-lecture?)
- [2. Why is studying computer networks important?](#2.-why-is-studying-computer-networks-important?)
- [3. Who proposed the 'Galactic Network' and what was its significance?](#3.-who-proposed-the-'galactic-network'-and-what-was-its-significance?)
- [4. What is the role of the ARPANET in the history of the Internet?](#4.-what-is-the-role-of-the-arpanet-in-the-history-of-the-internet?)
- [5. What is the hourglass model in Internet architecture?](#5.-what-is-the-hourglass-model-in-internet-architecture?)
- [6. What is a layered network architecture, and what analogy can explain it?](#6.-what-is-a-layered-network-architecture,-and-what-analogy-can-explain-it?)
- [7. What are the advantages and disadvantages of a layered network architecture?](#7.-what-are-the-advantages-and-disadvantages-of-a-layered-network-architecture?)
- [8. Describe the OSI model and the traditional Internet protocol stack.](#8.-describe-the-osi-model-and-the-traditional-internet-protocol-stack.)
- [9. What protocols operate at the application layer, and what is its role?](#9.-what-protocols-operate-at-the-application-layer,-and-what-is-its-role?)
- [10. What is the role of the presentation and session layers?](#10.-what-is-the-role-of-the-presentation-and-session-layers?)
- [11. What are the two main transport protocols, and how do they differ?](#11.-what-are-the-two-main-transport-protocols,-and-how-do-they-differ?)
- [12. What is the role of the network layer?](#12.-what-is-the-role-of-the-network-layer?)
- [13. Describe the function of the data link layer.](#13.-describe-the-function-of-the-data-link-layer.)
- [14. What is the physical layer's role in network communication?](#14.-what-is-the-physical-layer's-role-in-network-communication?)
- [15. What is encapsulation in network communication?](#15.-what-is-encapsulation-in-network-communication?)
- [16. What is de-encapsulation?](#16.-what-is-de-encapsulation?)
- [17. How do intermediate devices handle encapsulation and de-encapsulation?](#17.-how-do-intermediate-devices-handle-encapsulation-and-de-encapsulation?)
- [18. Why do end-hosts implement all five layers of the network stack while intermediate devices do not?](#18.-why-do-end-hosts-implement-all-five-layers-of-the-network-stack-while-intermediate-devices-do-not?)
- [19. What is the end-to-end (e2e) principle in network design?](#19.-what-is-the-end-to-end-(e2e)-principle-in-network-design?)
- [20. How is the end-to-end principle summarized?](#20.-how-is-the-end-to-end-principle-summarized?)
- [21. Why did the end-to-end principle contribute to the rapid growth of the Internet?](#21.-why-did-the-end-to-end-principle-contribute-to-the-rapid-growth-of-the-internet?)
- [22. What was the original motivation behind the end-to-end principle?](#22.-what-was-the-original-motivation-behind-the-end-to-end-principle?)
- [23. What are some examples of violations of the end-to-end principle?](#23.-what-are-some-examples-of-violations-of-the-end-to-end-principle?)
- [24. What is the purpose of NAT boxes in network communication?](#24.-what-is-the-purpose-of-nat-boxes-in-network-communication?)
- [25. How does a NAT-enabled router manage communication between a private network and the public Internet?](#25.-how-does-a-nat-enabled-router-manage-communication-between-a-private-network-and-the-public-internet?)
- [26. Why do NAT boxes violate the end-to-end principle?](#26.-why-do-nat-boxes-violate-the-end-to-end-principle?)
- [27. What are some workarounds for initiating connections to hosts behind NATs?](#27.-what-are-some-workarounds-for-initiating-connections-to-hosts-behind-nats?)
- [28. What does the hourglass shape of the Internet protocol stack represent?](#28.-what-does-the-hourglass-shape-of-the-internet-protocol-stack-represent?)
- [29. Was the Internet architecture always shaped like an hourglass?](#29.-was-the-internet-architecture-always-shaped-like-an-hourglass?)
- [30. Why have innovations been more frequent at the higher or lower layers of the hourglass?](#30.-why-have-innovations-been-more-frequent-at-the-higher-or-lower-layers-of-the-hourglass?)
- [31. How can new protocols potentially outperform and replace existing network layer protocols?](#31.-how-can-new-protocols-potentially-outperform-and-replace-existing-network-layer-protocols?)
- [32. What is the Evolutionary Architecture model (EvoArch)?](#32.-what-is-the-evolutionary-architecture-model-(evoarch)?)
- [33. What is the Evolutionary Architecture model (EvoArch) in the context of Internet architecture?](#33.-what-is-the-evolutionary-architecture-model-(evoarch)-in-the-context-of-internet-architecture?)
- [34. What are the key components of the EvoArch model?](#34.-what-are-the-key-components-of-the-evoarch-model?)
- [35. How does EvoArch explain the difficulty in replacing protocols like TCP/IP?](#35.-how-does-evoarch-explain-the-difficulty-in-replacing-protocols-like-tcp/ip?)
- [36. What does the EvoArch model predict about the evolution of future Internet architectures?](#36.-what-does-the-evoarch-model-predict-about-the-evolution-of-future-internet-architectures?)
- [37. What role do substrates and products play in the EvoArch model?](#37.-what-role-do-substrates-and-products-play-in-the-evoarch-model?)
- [49. What are the advantages and disadvantages of a layered architecture?](#49.-what-are-the-advantages-and-disadvantages-of-a-layered-architecture?)
- [50. What are the differences and similarities between the OSI model and the five-layered Internet model?](#50.-what-are-the-differences-and-similarities-between-the-osi-model-and-the-five-layered-internet-model?)
- [51. What are sockets?](#51.-what-are-sockets?)
- [52. Describe each layer of the OSI model.](#52.-describe-each-layer-of-the-osi-model.)
- [53. Provide examples of popular protocols at each layer of the five-layered Internet model.](#53.-provide-examples-of-popular-protocols-at-each-layer-of-the-five-layered-internet-model.)
- [54. What is encapsulation, and how is it used in a layered model?](#54.-what-is-encapsulation,-and-how-is-it-used-in-a-layered-model?)
- [55. What is the end-to-end (e2e) principle?](#55.-what-is-the-end-to-end-(e2e)-principle?)
- [56. What are the examples of a violation of the e2e principle?](#56.-what-are-the-examples-of-a-violation-of-the-e2e-principle?)
- [57. What is the EvoArch model?](#57.-what-is-the-evoarch-model?)
- [58. Explain a round in the EvoArch model.](#58.-explain-a-round-in-the-evoarch-model.)
- [59. What are the ramifications of the hourglass shape of the Internet?](#59.-what-are-the-ramifications-of-the-hourglass-shape-of-the-internet?)
- [60. Repeaters, hubs, bridges, and routers operate on which layers?](#60.-repeaters,-hubs,-bridges,-and-routers-operate-on-which-layers?)
- [61. What is a bridge, and how does it 'learn'?](#61.-what-is-a-bridge,-and-how-does-it-'learn'?)
- [62. What is a distributed algorithm?](#62.-what-is-a-distributed-algorithm?)
- [63. Explain the Spanning Tree Algorithm.](#63.-explain-the-spanning-tree-algorithm.)
- [64. What is the purpose of the Spanning Tree Algorithm?](#64.-what-is-the-purpose-of-the-spanning-tree-algorithm?)

## 1. What were the main topics covered in the first lecture?

The first lecture covered major milestones in the history of the Internet, original design choices of Internet architecture, and the hourglass model of the Internet. It also discussed how the design could be changed using a 'clean-slate' approach, optimizing for network control, management, and accountability.

## 2. Why is studying computer networks important?

Computer networks, particularly the Internet, have transformed society by impacting business, communication, defense, and legal structures. The Internet also provides an interdisciplinary research playground, involving fields like distributed systems, algorithms, machine learning, cryptography, and more.

## 3. Who proposed the 'Galactic Network' and what was its significance?

J.C.R. Licklider proposed the 'Galactic Network' in 1962. It was the first vision of a network that interconnected computers, laying the foundation for the modern Internet.

## 4. What is the role of the ARPANET in the history of the Internet?

The ARPANET, created in 1969, was the first network to use packet-switching technology. It connected multiple nodes (UCLA, Stanford, UCSB, and the University of Utah), serving as a precursor to the modern Internet.

## 5. What is the hourglass model in Internet architecture?

The hourglass model represents the design of the Internet, where diverse applications and network technologies converge at a minimal set of protocols, like IP, before expanding again into different services and applications.

## 6. What is a layered network architecture, and what analogy can explain it?

A layered network architecture separates functionalities into layers, each providing services to the layer above it. An analogy is the airline system, where various steps (ticketing, baggage, loading, routing) represent different layers of services for a passenger's journey.

## 7. What are the advantages and disadvantages of a layered network architecture?

Advantages include scalability, modularity, and flexibility. Disadvantages include layer dependencies, possible duplication of functionalities (e.g., error recovery), and additional overhead due to abstraction.

## 8. Describe the OSI model and the traditional Internet protocol stack.

The OSI model has seven layers: Application, Presentation, Session, Transport, Network, Data Link, and Physical. The traditional Internet protocol stack combines the Presentation and Session layers into the Application layer, resulting in five layers.

## 9. What protocols operate at the application layer, and what is its role?

Protocols like HTTP, SMTP, FTP, and DNS operate at the application layer. This layer provides services depending on the application and interacts through an interface (e.g., sockets). It refers to the data packet as a 'message'.

## 10. What is the role of the presentation and session layers?

The presentation layer formats information (e.g., video streams, integer translation), while the session layer manages different transport streams that belong to the same session (e.g., tying audio and video streams in teleconferencing).

## 11. What are the two main transport protocols, and how do they differ?

The transport layer includes TCP (connection-oriented, reliable delivery, flow control, congestion control) and UDP (connectionless, best-effort service, no reliability). It refers to data packets as 'segments'.

## 12. What is the role of the network layer?

The network layer is responsible for moving datagrams from a source host to a destination host. It includes the IP protocol for routing and addressing, as well as routing protocols to determine paths for datagrams.

## 13. Describe the function of the data link layer.

The data link layer moves 'frames' from one node to the next, delivering datagrams to the next node across a network path. Protocols include Ethernet, PPP, and WiFi, offering services like reliable delivery across one link.

## 14. What is the physical layer's role in network communication?

The physical layer interacts with actual hardware to transfer bits within a frame over a physical link. Protocols depend on the transmission medium, such as twisted-pair copper, coaxial cable, or fiber optics.

## 15. What is encapsulation in network communication?

Encapsulation is the process where each layer of the network stack appends its own header information to the data received from the layer above it. For example, the transport layer adds a transport header to the application message, forming a 'segment'. This process continues through the network and data link layers, creating datagrams and frames, respectively.

## 16. What is de-encapsulation?

De-encapsulation is the reverse process of encapsulation. As data arrives at the receiving host, each layer removes its corresponding header, passing the remaining data up to the next layer. This process continues until the application layer receives the original message.

## 17. How do intermediate devices handle encapsulation and de-encapsulation?

Intermediate devices like routers and switches also perform encapsulation and de-encapsulation. Routers implement layers one to three (physical, data link, and network), while switches implement layers one and two (physical and data link). These devices process data by stripping off and adding headers as required.

## 18. Why do end-hosts implement all five layers of the network stack while intermediate devices do not?

This design choice ensures that the Internet architecture places complexity and intelligence at the network's edges (end-hosts), keeping the core simple. This approach aligns with the end-to-end principle in network design.

## 19. What is the end-to-end (e2e) principle in network design?

The end-to-end principle suggests that application-specific functions should not be built into the lower levels of the system at the network core. Instead, the network core should be simple, while the end systems should handle the intelligence and complexity.

## 20. How is the end-to-end principle summarized?

The network core should be minimal and simple, while the intelligence and specific functionalities should reside at the network's edges, in the end systems.

## 21. Why did the end-to-end principle contribute to the rapid growth of the Internet?

The principle allowed for evolving innovation at the network's edge, resulting in numerous applications and services. By not embedding specific features in the network core, modifications and innovations could occur without altering the core infrastructure.

## 22. What was the original motivation behind the end-to-end principle?

By moving functions closer to the application, designers gain flexibility and autonomy to tailor services to specific needs. The lower-level protocol layers can then focus on organizing network resources efficiently, independently of specific applications.

## 23. What are some examples of violations of the end-to-end principle?

Examples include firewalls and Network Address Translation (NAT) boxes. Firewalls monitor network traffic and can block communication between hosts, while NAT boxes modify IP addresses to manage traffic between private networks and the public Internet.

## 24. What is the purpose of NAT boxes in network communication?

NAT boxes help address the shortage of public IP addresses by allowing multiple devices on a private network to share a single public IP address. They manage communication between private network hosts and public Internet hosts by rewriting source and destination IP addresses and ports.

## 25. How does a NAT-enabled router manage communication between a private network and the public Internet?

A NAT-enabled router has a public-facing interface with a public IP address assigned by an ISP and a private-facing interface with a private subnet IP address. It maintains a NAT translation table, rewriting source and destination addresses/ports for traffic passing between the private network and the public Internet.

## 26. Why do NAT boxes violate the end-to-end principle?

NAT boxes violate the end-to-end principle because hosts behind NATs are not globally addressable or routable. This means that hosts on the public Internet cannot initiate connections to devices behind NATs without intervention from the NAT box.

## 27. What are some workarounds for initiating connections to hosts behind NATs?

Workarounds include tools like Session Traversal Utilities for NAT (STUN) to discover NATs and public IPs allocated for communication, and UDP hole punching to establish bidirectional UDP connections between hosts behind NATs.

## 28. What does the hourglass shape of the Internet protocol stack represent?

The hourglass shape of the Internet protocol stack represents its layered architecture. The wider sections at the top and bottom represent the diversity of application and physical layer protocols, while the narrow 'waist' represents the core network layer protocols (primarily IPv4, TCP, and UDP).

## 29. Was the Internet architecture always shaped like an hourglass?

No, the Internet architecture was not always shaped like an hourglass. In the early 1990s, there were multiple network layer protocols competing with IPv4, such as Novell's IPX and the X.25 protocol used in Frame Relay.

## 30. Why have innovations been more frequent at the higher or lower layers of the hourglass?

Innovations are more frequent at the higher (application) and lower (physical) layers because the core protocols at the waist (e.g., IPv4, TCP, and UDP) are deeply entrenched and widely used. Replacing these core protocols is challenging due to their essential role in the network's operation and the need for widespread adoption of any alternatives.

## 31. How can new protocols potentially outperform and replace existing network layer protocols?

To replace existing and widely used protocols, new protocols must provide significant advantages over incumbents. The EvoArch model helps researchers study layered architectures and the evolutionary dynamics that lead to the persistence of certain protocols.

## 32. What is the Evolutionary Architecture model (EvoArch)?

The Evolutionary Architecture model, or EvoArch, is a model that helps study layered network architectures in a quantitative manner. It provides insights into how the hierarchical structure of the network architecture led to the hourglass shape and the evolution of protocols.

## 33. What is the Evolutionary Architecture model (EvoArch) in the context of Internet architecture?

EvoArch is a model that illustrates layered architectures and their evolution in a quantitative manner. It considers components such as layers, nodes (representing protocols), edges (dependencies between protocols), substrates, products, and generality probabilities.

## 34. What are the key components of the EvoArch model?

The key components include:
- Layers: Represented as a directed, acyclic network.
- Nodes: Represent network protocols, each with a specific layer.
- Edges: Show dependencies between protocols (node connections).
- Substrates: Protocols used by another node.
- Products: Protocols that depend on a given protocol.
- Generality: Probability of a layer selecting substrates, which decreases as we move to higher layers.

## 35. How does EvoArch explain the difficulty in replacing protocols like TCP/IP?

EvoArch suggests that protocols like TCP/IP have high evolutionary value due to their extensive use by many higher-layer protocols. This value makes it challenging for new protocols to compete and survive. Additionally, the narrowness of the transport layer acts as an 'evolutionary shield' for IPv4, protecting it from replacement by new network layer protocols.

## 36. What does the EvoArch model predict about the evolution of future Internet architectures?

The model predicts that even if new architectures don't start with an hourglass shape, they will likely evolve into one, leading to the ossification of certain protocols. To avoid this, network architects should design the waist of the architecture to include several non-overlapping but general services to reduce competition among protocols.

## 37. What role do substrates and products play in the EvoArch model?

Substrates refer to the set of protocols a node uses for its services, while products are protocols that depend on a given protocol. The evolutionary value of a protocol is driven by the value of its products, influencing whether it survives competition within its layer.

## 49. What are the advantages and disadvantages of a layered architecture?

Advantages include scalability, modularity, and flexibility, allowing for the independent development and troubleshooting of network functions. Disadvantages include layer dependencies, possible duplication of functionalities (e.g., error recovery), and additional overhead due to abstraction.

## 50. What are the differences and similarities between the OSI model and the five-layered Internet model?

The OSI model has seven layers (Application, Presentation, Session, Transport, Network, Data Link, Physical), while the five-layered Internet model combines the Presentation and Session layers into a single Application layer. Both models provide a structured approach to network architecture, with each layer serving a specific purpose.

## 51. What are sockets?

Sockets are an interface between the application layer and the transport layer in the Internet protocol stack. They allow applications to send and receive data across a network, defining the endpoint of communication.

## 52. Describe each layer of the OSI model.

1. **Application Layer**: Provides network services directly to applications (e.g., HTTP, SMTP).
2. **Presentation Layer**: Formats data for the application layer (e.g., encryption, data compression).
3. **Session Layer**: Manages sessions between applications.
4. **Transport Layer**: Ensures reliable data transfer (e.g., TCP, UDP).
5. **Network Layer**: Manages data routing and forwarding (e.g., IP).
6. **Data Link Layer**: Provides node-to-node data transfer (e.g., Ethernet).
7. **Physical Layer**: Transmits raw bitstream over a physical medium.

## 53. Provide examples of popular protocols at each layer of the five-layered Internet model.

1. **Application Layer**: HTTP, SMTP, DNS.
2. **Transport Layer**: TCP, UDP.
3. **Network Layer**: IP (IPv4, IPv6).
4. **Data Link Layer**: Ethernet, WiFi.
5. **Physical Layer**: Coaxial cable, Fiber optics.

## 54. What is encapsulation, and how is it used in a layered model?

Encapsulation is the process of wrapping data with the necessary protocol information at each layer of the network stack. As data descends through the layers, headers are added to provide instructions on how to handle the packet at each layer, ensuring successful communication between sender and receiver.

## 55. What is the end-to-end (e2e) principle?

The e2e principle suggests that application-specific functions should reside at the network's edges (end systems) rather than the network core. The network core is kept simple, while complexity is managed at the endpoints, allowing for greater flexibility in application design.

## 56. What are the examples of a violation of the e2e principle?

Examples include firewalls and Network Address Translation (NAT) boxes. Firewalls monitor and can block communication between hosts, while NAT boxes modify IP addresses to manage traffic between private and public networks.

## 57. What is the EvoArch model?

The Evolutionary Architecture model (EvoArch) illustrates the layered network architectures and their evolution. It models components such as layers, protocols (nodes), edges (dependencies), substrates, products, and generality probabilities.

## 58. Explain a round in the EvoArch model.

In each round of the EvoArch model, new nodes are introduced, placed randomly within layers, and connected based on the generality probability of the layer below. Node values are updated, and nodes that should 'die' are removed based on competition within their layer.

## 59. What are the ramifications of the hourglass shape of the Internet?

The hourglass shape creates a narrow 'waist' at the network and transport layers, where protocols like IPv4, TCP, and UDP are entrenched. This makes it difficult to replace or modify these protocols, leading to protocol ossification and limiting innovation at the network's core.

## 60. Repeaters, hubs, bridges, and routers operate on which layers?

Repeaters and hubs operate on the Physical layer (L1). Bridges and Layer-2 switches operate on the Data Link layer (L2). Routers and Layer-3 switches operate on the Network layer (L3).

## 61. What is a bridge, and how does it 'learn'?

A bridge is a network device that transfers frames between different segments of a network. It 'learns' by examining the source addresses of frames it receives and noting the port through which each host is reachable, building a forwarding table for efficient traffic management.

## 62. What is a distributed algorithm?

A distributed algorithm is a process in which nodes in a network coordinate with each other to solve a problem. In the context of networking, distributed algorithms allow devices like bridges and routers to share information and make decisions independently to maintain network functionality.

## 63. Explain the Spanning Tree Algorithm.

The Spanning Tree Algorithm is used by bridges to prevent loops in a network by selectively blocking certain ports. The algorithm creates a loop-free subset (tree) of the network. Bridges communicate with each other using configuration messages to select a root bridge and determine the shortest path to the root, ensuring loop-free data forwarding.

## 64. What is the purpose of the Spanning Tree Algorithm?

The purpose of the Spanning Tree Algorithm is to eliminate network loops by creating a tree structure. This prevents broadcast storms and ensures reliable data transmission in networks where bridges interconnect multiple LAN segments.

