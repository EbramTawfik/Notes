
# Computer Networks Study Guide: Transport Layer and TCP

## Lesson 2 Overview
This guide covers the key concepts of the transport layer in computer networks, with a focus on TCP (Transmission Control Protocol). Topics include multiplexing, demultiplexing, reliability, flow control, congestion control, and TCP variants.

---

## Questions and Answers

### 1. What is multiplexing, and why is it necessary in the transport layer?
**Answer:** Multiplexing allows multiple applications to use the network simultaneously by assigning a unique port number to each application. It enables the transport layer to direct incoming data to the correct application on a host, ensuring different networked applications can operate at the same time.

### 2. How do UDP and TCP differ in terms of socket identification?
**Answer:** UDP uses a two-tuple (destination IP address and destination port number) to identify sockets, whereas TCP uses a four-tuple (source IP, source port, destination IP, destination port). This distinction allows TCP to manage multiple simultaneous connections effectively.

### 3. What is the purpose of the TCP three-way handshake?
**Answer:** The TCP three-way handshake establishes a connection between a client and server, synchronizing sequence numbers to ensure reliable communication. The steps include:
1. **SYN:** The client sends a segment with the SYN bit set.
2. **SYN-ACK:** The server responds with a SYNACK segment.
3. **ACK:** The client sends an acknowledgment, completing the connection setup.

### 4. How does TCP ensure reliable transmission?
**Answer:** TCP uses acknowledgments (ACKs) and retransmissions to ensure data is delivered reliably. When a sender transmits data, it waits for an acknowledgment from the receiver. If an acknowledgment is not received within a specified timeout, TCP assumes the packet was lost and retransmits it. This process is known as Automatic Repeat Request (ARQ).

### 5. What is flow control in TCP, and how does it protect the receiver's buffer?
**Answer:** Flow control prevents the sender from overwhelming the receiver by matching the sender's transmission rate to the receiver's ability to process data. TCP uses a receive window (`rwnd`), which indicates the available buffer space at the receiver. The sender ensures that the amount of unacknowledged data does not exceed `rwnd`.

### 6. Why is congestion control necessary, and how does TCP implement it?
**Answer:** Congestion control prevents excessive data transmission that can lead to network congestion, packet loss, and delays. TCP uses the congestion window (`cwnd`) to control the transmission rate. It employs a probe-and-adapt approach, increasing the window size when the network is stable and reducing it when packet loss signals congestion.

### 7. What are the main goals of congestion control?
**Answer:** The main goals of congestion control are:
- **Efficiency:** Maximizing network throughput.
- **Fairness:** Equal bandwidth allocation for flows sharing the same bottleneck link.
- **Low Delay:** Minimizing delays for delay-sensitive applications.
- **Fast Convergence:** Quickly adjusting to fair bandwidth allocation.

### 8. What are the two approaches to congestion control, and which does TCP use?
**Answer:** The two approaches are:
- **Network-Assisted Congestion Control:** Relies on explicit feedback from the network layer (e.g., routers) to indicate congestion.
- **End-to-End Congestion Control:** The sender infers congestion based on network behavior (e.g., packet loss, delay).
TCP primarily uses the end-to-end approach, relying on packet loss as a congestion signal.

### 9. How does a TCP sender infer network congestion?
**Answer:** A TCP sender infers congestion through two main signals:
- **Packet Delay:** Increasing RTTs indicate potential congestion due to buffer build-ups.
- **Packet Loss:** Detected through lost ACKs or duplicate ACKs, signaling that the network is congested.

### 10. How does TCP's congestion window (`cwnd`) affect the sending rate?
**Answer:** The congestion window (`cwnd`) controls the maximum amount of unacknowledged data the sender can transmit. TCP adjusts `cwnd` using the formula: `LastByteSent - LastByteAcked <= min{cwnd, rwnd}`. The sender cannot send data faster than the limit set by the congestion window or the receiver window.

### 11. Explain the Additive Increase/Multiplicative Decrease (AIMD) approach in TCP.
**Answer:** TCP increases the congestion window (`cwnd`) linearly by one packet per RTT (Additive Increase) to probe for available bandwidth. When packet loss is detected, it cuts `cwnd` in half (Multiplicative Decrease). This balance helps maintain network stability and fairness among multiple flows.

### 12. What is "slow start" in TCP, and when is it used?
**Answer:** "Slow start" is a phase in TCP that exponentially increases the congestion window size starting from one packet. It is used when a new connection is established or when a connection restarts after a timeout. Slow start continues until the congestion window exceeds a threshold (`ssthresh`), after which it transitions to the AIMD method.

### 13. How does TCP achieve fairness among multiple connections, and when might it fail?
**Answer:** TCP achieves fairness through the AIMD mechanism, ensuring equal bandwidth distribution among connections sharing a link. However, it may fail in cases where:
- Connections have different RTTs (shorter RTTs increase `cwnd` faster).
- Applications use multiple parallel TCP connections to gain an unfair share of bandwidth.

### 14. What is TCP CUBIC, and how does it differ from TCP Reno?
**Answer:** TCP CUBIC is a modern TCP variant designed for high-bandwidth, high-delay networks. It uses a cubic polynomial growth function for the congestion window, allowing more aggressive growth when the window is far from the maximum size (`Wmax`). This approach improves link utilization in modern network environments.

### 15. How can TCP throughput be modeled mathematically?
**Answer:** TCP throughput can be approximated using the formula: `BW ≈ C / (RTT * sqrt(p))`, where `BW` is the throughput, `RTT` is the round-trip time, `p` is the packet loss probability, and `C` is a constant less than 1. This model illustrates how throughput decreases with increasing RTT and packet loss.

---

## Additional References
- Kurose-Ross Edition 6
- Peterson Chapter 6.3
- [A Very Simple Model for TCP Throughput](https://blog.thousandeyes.com/a-very-simple-model-for-tcp-throughput/)
