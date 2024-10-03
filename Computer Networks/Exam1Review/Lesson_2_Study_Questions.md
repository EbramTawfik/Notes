
# Lesson 2: Transport and Application Layers - Study Questions

### 1. What does the transport layer provide?
**Answer:** The transport layer provides end-to-end communication services for applications. It enables reliable data transfer, flow control, and multiplexing, ensuring data integrity and efficient use of the network.

### 2. What is a packet for the transport layer called?
**Answer:** In the transport layer, a packet is referred to as a **segment**.

### 3. What are the two main protocols within the transport layer?
**Answer:** The two main protocols in the transport layer are **Transmission Control Protocol (TCP)** and **User Datagram Protocol (UDP)**.

### 4. What is multiplexing, and why is it necessary?
**Answer:** Multiplexing is the process of combining data from multiple applications into a single transport layer stream. It allows multiple applications to share the same network resources by using unique port numbers, ensuring that data is directed to the correct application on the host.

### 5. Describe the two types of multiplexing/demultiplexing.
**Answer:** 
- **Connectionless Multiplexing/Demultiplexing:** Used by UDP, which does not establish a connection before sending data. Each packet contains the destination port number to direct data to the correct application.
- **Connection-oriented Multiplexing/Demultiplexing:** Used by TCP, which establishes a connection before data transfer. Each connection is identified by a four-tuple (source IP, source port, destination IP, destination port).

### 6. What are the differences between UDP and TCP?
**Answer:** 
- **TCP:** Connection-oriented, reliable, provides flow control, congestion control, and guarantees in-order delivery of data.
- **UDP:** Connectionless, does not guarantee reliability, in-order delivery, or provide congestion/flow control, but has low overhead and is faster for certain applications.

### 7. When would an application layer protocol choose UDP over TCP?
**Answer:** An application would choose UDP over TCP when low latency and minimal overhead are more important than reliability. Examples include real-time applications like video streaming, online gaming, and Voice over IP (VoIP).

### 8. Explain the TCP Three-way Handshake.
**Answer:** The TCP three-way handshake establishes a reliable connection:
1. **SYN:** Client sends a SYN segment to the server.
2. **SYN-ACK:** Server responds with a SYN-ACK segment.
3. **ACK:** Client sends an ACK, completing the connection setup.

### 9. Explain the TCP connection teardown.
**Answer:** TCP connection teardown involves four steps:
1. **FIN:** The client sends a FIN segment to initiate connection closure.
2. **ACK:** The server acknowledges the FIN.
3. **FIN:** The server sends a FIN segment to indicate it is ready to close.
4. **ACK:** The client acknowledges the server’s FIN, completing the teardown.

### 10. What is Automatic Repeat Request or ARQ?
**Answer:** ARQ is a mechanism that ensures reliable data transmission by requiring the receiver to acknowledge each packet. If the sender does not receive an acknowledgment within a certain time frame, it retransmits the packet.

### 11. What is Stop and Wait ARQ?
**Answer:** In Stop and Wait ARQ, the sender transmits one packet and waits for an acknowledgment before sending the next packet. This method is simple but can lead to low efficiency.

### 12. What is Go-back-N?
**Answer:** Go-back-N is an ARQ protocol where the sender can transmit multiple packets up to a specified window size without waiting for individual ACKs. If a packet is lost, all subsequent packets in the window are retransmitted.

### 13. What is selective ACKing?
**Answer:** Selective ACKing (SACK) allows the receiver to inform the sender about all the segments that have been received correctly, even if they are out of order. This enables the sender to retransmit only the missing segments.

### 14. What is fast retransmit?
**Answer:** Fast retransmit is a mechanism where the sender retransmits a packet if it receives three duplicate ACKs for the same data segment, indicating that the packet was likely lost.

### 15. What is transmission control, and why do we need to control it?
**Answer:** Transmission control manages the rate of data transmission to prevent overwhelming the network or the receiver. It is necessary to maintain network stability, avoid congestion, and ensure fair bandwidth distribution.

### 16. What is flow control, and why do we need to control it?
**Answer:** Flow control prevents the sender from overwhelming the receiver by adjusting the transmission rate to match the receiver's processing capability, avoiding buffer overflow.

### 17. What is congestion control?
**Answer:** Congestion control prevents network congestion by adjusting the sender's transmission rate based on network conditions, ensuring efficient use of network resources.

### 18. What are the goals of congestion control?
**Answer:** The goals of congestion control are to achieve high throughput, fairness among users, low delay, and fast convergence to optimal bandwidth allocation.

### 19. What is network-assisted congestion control?
**Answer:** Network-assisted congestion control relies on explicit feedback from the network (e.g., routers) to inform the sender about the state of network congestion.

### 20. What is end-to-end congestion control?
**Answer:** End-to-end congestion control does not rely on explicit feedback from the network. Instead, the sender infers congestion based on observed network behavior, such as packet loss or delays.

### 21. How does a host infer congestion?
**Answer:** A host infers congestion through signals like increased packet delays (higher RTT) and packet loss, which indicates potential network congestion.

### 22. How does a TCP sender limit the sending rate?
**Answer:** The TCP sender limits the sending rate using the congestion window (`cwnd`). It ensures that the amount of unacknowledged data does not exceed the minimum of the congestion window and the receive window.

### 23. Explain Additive Increase/Multiplicative Decrease (AIMD) in the context of TCP.
**Answer:** AIMD gradually increases the congestion window by one packet per RTT (additive increase) to probe for available bandwidth. Upon detecting packet loss, it cuts the window size in half (multiplicative decrease) to reduce congestion.

### 24. What is a slow start in TCP?
**Answer:** Slow start is a phase where the TCP sender increases the congestion window exponentially from a small size to quickly ramp up the transmission rate when starting a new connection or after a timeout.

### 25. Is TCP fair in the case where connections have the same RTT? Explain.
**Answer:** Yes, TCP is generally fair when connections have the same RTT because each connection increases its congestion window at the same rate, leading to an equal share of bandwidth.

### 26. Is TCP fair in the case where two connections have different RTTs? Explain.
**Answer:** No, TCP is not entirely fair when connections have different RTTs. Connections with shorter RTTs increase their congestion window faster, resulting in a larger share of bandwidth compared to connections with longer RTTs.

### 27. Explain how TCP CUBIC works.
**Answer:** TCP CUBIC uses a cubic polynomial growth function for the congestion window. After a loss, it initially grows aggressively when the window is far from the maximum size (`Wmax`). As the window approaches `Wmax`, the growth slows to cautiously probe the network's capacity.

### 28. Explain TCP throughput calculation.
**Answer:** TCP throughput can be estimated using the formula: `BW ≈ C / (RTT * sqrt(p))`, where `BW` is the throughput, `RTT` is the round-trip time, `p` is the packet loss probability, and `C` is a constant that accounts for network parameters.

