# Computer Networks Study Guide

## 1. Introduction
In this guide, we will explore the evolution of the Internet and its layered architecture. We'll delve into key concepts, protocols, and devices that form the backbone of computer networks.

### Overview of the Internet's Evolution and Architecture
The Internet has evolved from a research experiment into a global communications infrastructure, transforming almost every aspect of our lives. This rapid growth is due to its layered architecture, resembling an hourglass shape.

### Major Milestones in Internet History
- **1962:** J.C.R. Licklider proposed the 'Galactic Network' at MIT.
- **1969:** Creation of the ARPANET, the first network to implement packet-switching technology.
- **1973:** Introduction of the TCP/IP protocol, laying the foundation for Internet communication.
- **1983:** Launch of the Domain Name System (DNS), making Internet navigation easier.

## 2. Why Study Computer Networks?
The Internet's growth and transformative impact on society have made networking a vital field of study. The interdisciplinary nature of networks spans fields such as distributed systems, economics, and security.

### Internet Growth and Its Role in Society
- The Internet enables services like e-commerce, cloud computing, social networking, and virtual communication.
- By 2023, Internet users numbered over 5.3 billion.

### Interdisciplinary Research Opportunities
Networking intersects with distributed systems, operating systems, software engineering, algorithms, data structures, cryptography, and more. It offers research potential in areas like Internet security, economics, and social sciences.

## 3. Internet Architecture
The Internet architecture consists of layers that provide services to each other, enabling communication between diverse devices and applications. An example is shown in the diagram below:


### Application Programming Interfaces (API)
APIs facilitate communication between application endpoints, even when they use different media (e.g., Ethernet vs. WiFi).

### Layering and Functionality (Airline Analogy)
Layering in network architecture can be compared to the airline system. For example:
- **Departure:** Ticket purchase, baggage check, gate boarding, runway takeoff.
- **Intermediate:** Airplane routing and air-traffic control.
- **Arrival:** Gate unloading, baggage claim, and complaints.
Each layer implements specific functionality and relies on the layer below it, providing modularity, flexibility, and scalability.

## 4. OSI Model and Internet Protocol Stack
### Seven-Layer OSI Model
- **Application Layer**
- **Presentation Layer**
- **Session Layer**
- **Transport Layer**
- **Network Layer**
- **Data Link Layer**
- **Physical Layer**

### Five-Layer Internet Model
- **Application Layer**
- **Transport Layer**
- **Network Layer**
- **Data Link Layer**
- **Physical Layer**


### Advantages and Disadvantages of Layered Architecture
- **Advantages:** Modularity, flexibility, and scalability.
- **Disadvantages:** Potential duplication of functionalities and additional overhead due to abstraction between layers.

## 5. In-Depth Look at Each Layer
### Application Layer
- Provides various network services (e.g., HTTP, SMTP, DNS).
- Data units are referred to as 'messages'.

### Presentation Layer
- Formats and encrypts data for the application layer.
- Converts data between different encoding formats.

### Session Layer
- Manages sessions between applications (e.g., tying together audio and video streams in a teleconference).

### Transport Layer
- Responsible for end-to-end communication.
- Protocols: **TCP** (reliable, connection-oriented) and **UDP** (unreliable, connectionless).
- Data units are called 'segments'.

### Network Layer
- Manages data routing, addressing, and forwarding.
- Protocols: **IP** (Internet Protocol).
- Data units are called 'datagrams'.

### Data Link Layer
- Provides node-to-node data transfer.
- Protocols: **Ethernet**, **WiFi**.
- Data units are called 'frames'.

### Physical Layer
- Manages the physical connection between devices.
- Deals with raw bits transmitted over the physical medium.

## 6. Key Networking Concepts
### Encapsulation and De-encapsulation
Encapsulation involves adding headers to data as it passes through each layer of the protocol stack, ensuring proper data delivery. De-encapsulation is the reverse process, where each layer removes its respective header.

## 7. End-to-End (e2e) Principle and Violations
### What is the End-to-End Principle?
The e2e principle suggests that application-specific functions should only be implemented at the endpoints of a network, not within the intermediate network itself.

### Violations of the End-to-End Principle
- **NAT Boxes:** Break the e2e principle by altering packet headers to allow multiple devices on a private network to share a single public IP address.


## 8. Evolutionary Architecture Model
### Hourglass Shape of the Internet
The Internet's protocol stack is often depicted as an hourglass due to the small set of protocols at the 'waist' of the stack (IPv4, IPv6, TCP, UDP).

### Layered Acyclic Network
The EvoArch model helps explain the evolution and competition between network protocols. The most stable protocols occupy the 'waist' of the Internet hourglass.


## 9. Network Devices and Interconnection
### Repeaters, Hubs, Bridges, and Routers
- **Repeaters and Hubs:** Operate on the physical layer (L1). They forward signals to connect Ethernet segments but share the same collision domain.
- **Bridges and Layer-2 Switches:** Operate on the data link layer (L2). They forward frames based on MAC addresses and separate collision domains.
- **Routers and Layer-3 Switches:** Operate on the network layer (L3). They route packets using IP addresses.



### Bridges and Learning Bridges
Bridges maintain a forwarding table to learn which hosts are reachable through which ports. They use this table to forward frames to the appropriate ports.


## 10. Spanning Tree Algorithm
Bridges use the Spanning Tree Algorithm (STA) to eliminate loops in a network by selecting a subset of links that form a tree structure.
### How the Spanning Tree Algorithm Works
- Each bridge in the network has an ID and sends configuration messages to neighbors to identify the root of the topology.
- The algorithm proceeds in rounds, selecting the bridge with the smallest ID as the root and configuring paths to avoid loops.


