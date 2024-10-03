# Computer Networks Practice Questions with Answers and Explanations

### Question 1
**How did Licklider and his team in the early 1960s experiment with a precursor to the Internet?**

- A. Building the HTTP protocol
- B. Prototyping Network Control Protocol (NCP)
- C. Creating the first web browser
- D. Connecting two computers over a dial-up telephone line

**Correct Answer:** D. Connecting two computers over a dial-up telephone line

**Explanation:** Licklider, along with his team, conducted experiments to connect computers, laying the groundwork for what would later become the Internet. The first experiment involved connecting two computers over a telephone line to test data exchange, which was a significant step in developing computer networks.

### Question 2
**What is the Domain Name System (DNS) designed to do primarily?**

- A. Create simple web pages
- B. Create more IP addresses
- C. Translate domain names into IP addresses
- D. Route traffic through a network

**Correct Answer:** C. Translate domain names into IP addresses

**Explanation:** DNS is like the Internet's phonebook. It translates human-friendly domain names (like www.example.com) into IP addresses that computers use to identify each other on the network.

### Question 3
**What is the architectural design of the Internet protocol stack based on?**

- A. Signals
- B. Applications
- C. Layers
- D. Networks

**Correct Answer:** C. Layers

**Explanation:** The Internet protocol stack, such as the OSI model and the five-layered Internet model, is organized into different layers, each providing specific network functions. This modular approach helps in managing network complexity.

### Question 4
**Both the data link and transport layer protocols may provide error correction.**

- A. True
- B. False

**Correct Answer:** A. True

**Explanation:** Error correction can occur at multiple layers. The data link layer handles error correction for data transmission over a physical link, while the transport layer (e.g., TCP) provides end-to-end error detection and correction across the network.

### Question 5
**What allows for communication between the application layer and transport layer?**

- A. Hosts
- B. Routers
- C. Sockets
- D. Bridges

**Correct Answer:** C. Sockets

**Explanation:** Sockets serve as an interface between the application layer and the transport layer, enabling applications to send and receive data over the network.

### Question 6
**Which of the following protocols belong to the application layer?**

- A. DNS (Domain Name Service)
- B. IP (Internet Protocol)
- C. Ethernet
- D. UDP (User Datagram Protocol)

**Correct Answer:** A. DNS (Domain Name Service)

**Explanation:** DNS is an application layer protocol that provides the translation of domain names into IP addresses, allowing users to access websites using human-readable names.

### Question 7
**Which two protocols belong to the transport layer? Select all that apply.**

- A. UDP
- B. HTTP
- C. TCP
- D. IP

**Correct Answers:** A. UDP, C. TCP

**Explanation:** Both TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) operate at the transport layer, providing different services for data transmission (e.g., reliable delivery with TCP and faster, connectionless communication with UDP).

### Question 8
**When an application sends a packet of information across the network, this packet travels down the IP stack and undergoes what process?**

- A. De-encapsulation
- B. Augmentation
- C. Encapsulation
- D. Transportation

**Correct Answer:** C. Encapsulation

**Explanation:** Encapsulation is the process of adding headers to data as it passes through each layer of the protocol stack, ensuring that the packet contains all necessary information for transmission across the network.

### Question 9
**According to the end-to-end principle, where should most of the Internet's functionality/intelligence be implemented?**

- A. Wherever convenient for the designer
- B. At middle boxes in a network
- C. At the edges of a network
- D. At the core of a network

**Correct Answer:** C. At the edges of a network

**Explanation:** The end-to-end principle advocates for keeping the core network simple and placing the majority of the functionality and intelligence (e.g., error checking, data recovery) at the end hosts (the edges) of the network.

### Question 10
**What is the difference between hubs, bridges, and routers?**

- A. Firewalls are built into all routers, but not the other devices.
- B. Some provide additional caching services.
- C. They remove malicious traffic at different tiers.
- D. They operate on different layers of the IP stack.

**Correct Answer:** D. They operate on different layers of the IP stack

**Explanation:** Hubs operate at the physical layer (L1), bridges operate at the data link layer (L2), and routers operate at the network layer (L3), each providing different network functions.

### Question 11
**Some data link layer protocols, such as 802.11 (WiFi), implement some basic error correction as the physical medium used is easily prone to interference and noise (such as a nearby running microwave). Is this a violation of the end-to-end principle?**

- A. Yes.
- B. No.

**Correct Answer:** B. No.

**Explanation:** Violations of the end-to-end (e2e) principle typically occur in scenarios where it is not possible to implement certain functionalities entirely at the end hosts, such as in the cases of NAT boxes and firewalls. In the case of data link layer protocols implementing error correction, this is not considered a violation of the e2e principle. Here, the lower-level protocol (e.g., WiFi) provides error checking to handle errors due to the physical medium's characteristics. This is a practical necessity to ensure data integrity and is not intended to impose application-specific logic or functionality on the network. Therefore, it does not conflict with the e2e principle.

### Question 12
**Which of the following are ramifications of the 'hourglass shape of the internet'?**

- A. Many technologies that were not originally designed for the internet have been modified so that they have versions that can communicate over the internet (such as Radio over IP).
- B. It has been a difficult and slow process to transition to IPv6, despite the shortage of public IPv4 addresses.
- C. Applications like BitTorrent leverage peer-to-peer networking instead of a more traditional client-server model for better performance.

**Correct Answers:** A and B

**Explanation:**
- **A is correct:** Modifying a technology so that it is compatible with the rest of the internet (i.e., by making it compatible with IP) greatly enhances market penetration (from the vendor’s perspective), and/or decreases the amount of extra development that would need to happen.
- **B is correct:** A big part of the Internet infrastructure uses IPv4 while the cost of transitioning is high. This reflects as a consequence of the narrow waist.
- **C is not relevant:** The hourglass shape of the Internet refers to Internet architecture in terms of protocols available at the different layers.

### Question 13
**Consider the following statements about the Spanning Tree Algorithm (STA), a network protocol used to organize and manage network paths. Which of these statements is correct?**

- A. The Spanning Tree Algorithm helps to manage data flow in networks to prevent overwhelming traffic, known as 'broadcast storms'.
- B. In the Spanning Tree Algorithm, the root of the spanning tree is always positioned centrally to minimize the distance to all other network nodes.
- C. When using the Spanning Tree Algorithm, data cannot be sent over a network link that the algorithm has deactivated or put into an inactive state.

**Correct Answer:** A. The Spanning Tree Algorithm helps to manage data flow in networks to prevent overwhelming traffic, known as 'broadcast storms'.

**Explanation:** The primary purpose of the Spanning Tree Algorithm is to prevent loops in the network topology, which, if left unchecked, can lead to broadcast storms. By disabling redundant paths, STA ensures a loop-free network, effectively managing data flow and preventing network flooding.
- **B is incorrect:** The root of the spanning tree is not necessarily positioned centrally. The selection of the root bridge is based on the bridge ID, not its location in the network.
- **C is incorrect:** While the STA disables certain links to prevent loops, data can still reach the physical link itself, but it will not be used for forwarding traffic.
