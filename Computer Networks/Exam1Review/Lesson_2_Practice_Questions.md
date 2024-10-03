
# Complete Practice Questions: Transport Layer and TCP 

## Question 1
**Q:** As we have seen, UDP and TCP use port numbers to identify the sending application and destination application. Why don’t UDP and TCP just use process IDs rather than define port numbers?

**A:** Using port numbers simplifies the process of multiplexing and demultiplexing data streams in the transport layer. It allows the transport layer to direct incoming segments to the correct application on a host based on the port number.

**Explanation:** Process IDs are specific to operating systems and change frequently, making protocols OS-dependent. Moreover, a single process can set up multiple communication channels, so using process IDs would not allow proper demultiplexing. Using well-known ports (e.g., 80 for HTTP) is also a convention that provides consistency.

---

## Question 2
**Q:** Why do UDP and TCP use 1’s complement for their checksums, and how does the receiver compute and detect errors using 1’s complement?

**A:** The 1's complement method is used for its ability to detect common bit errors in transmitted data. The receiver checks for errors by summing the 16-bit words in the segment. If the result is all 1's, the data is considered error-free; otherwise, an error is detected.

**Explanation:** 1's complement helps detect common errors, like flipped bits. The receiver adds the data, including the checksum. If the result is anything other than all 1's, it indicates an error occurred during transmission.

---

## Question 3
**Q:** TCP utilizes the Additive Increase/Multiplicative Decrease (AIMD) policy for fairness. How do other policies like AIAD, MIMD, and MIAD differ from AIMD?

**A:** Other policies adjust the congestion window in different ways:
- **AIAD (Additive Increase/Additive Decrease):** Increases and decreases the window linearly.
- **MIAD (Multiplicative Increase/Additive Decrease):** Multiplies the window size during increase and decreases it linearly.
- **MIMD (Multiplicative Increase/Multiplicative Decrease):** Uses multiplication for both increase and decrease.

**Explanation:** AIMD strikes a balance between aggressiveness in increasing the window size and caution in decreasing it, which contributes to network stability. The other policies either change the window size too aggressively or not aggressively enough, impacting fairness and network performance.

---

## Question 4
**Q:** Explain how in TCP CUBIC the congestion window growth becomes independent of RTTs.

**A:** In TCP CUBIC, the congestion window growth is based on the time elapsed since the last loss event rather than the receipt of ACKs. The cubic function of time provides a growth mechanism that is not directly tied to the RTT, making TCP CUBIC more efficient in high-bandwidth, high-latency networks.

**Explanation:** By focusing on elapsed time rather than round-trip times, TCP CUBIC ensures that connections with larger RTTs are not at a disadvantage, allowing for more equitable use of network resources.

---

## Question 5
**Q:** The transport layer protocols offer a logical connection between processes only if the hosts reside in the same network. True or False?

**A:** **False.** The transport layer provides logical end-to-end connections regardless of whether hosts are on the same or different networks.

**Explanation:** The transport layer abstracts the underlying network infrastructure, creating a logical connection between communicating applications, independent of physical network boundaries.

---

## Question 6
**Q:** A sending host receives a message from the application layer and encapsulates it with the transport layer header before passing it down to the network layer. True or False?

**A:** **True.** This process involves adding transport layer headers to create a segment that is then passed to the network layer.

**Explanation:** The transport layer encapsulates the data received from the application layer, adding necessary headers for transmission across the network.

---

## Question 7
**Q:** An application running on a host can bind to multiple sockets simultaneously. True or False?

**A:** **True.** Applications can bind to different ports to manage multiple network connections simultaneously.

**Explanation:** The use of ports allows a single application to establish multiple network channels, handling diverse network communications through separate sockets.

---

## Question 8
**Q:** The identifier of a UDP socket is a tuple of destination IP address and port. True or False?

**A:** **True.** UDP sockets are identified using a combination of the destination IP address and the port number.

**Explanation:** UDP uses a two-tuple (destination IP, port) for socket identification, allowing multiplexing and routing of data to the correct application.

---

## Question 9
**Q:** The identifier of a TCP socket is a tuple of source IP address and port. True or False?

**A:** **True.** TCP sockets are identified by a four-tuple: source IP, source port, destination IP, and destination port.

**Explanation:** This four-tuple provides a unique identifier for each connection, allowing multiple simultaneous connections to the same destination.

---

## Question 10
**Q:** UDP is considered more lightweight than TCP. True or False?

**A:** **True.** UDP is a simpler protocol that does not include mechanisms for error correction, flow control, or congestion control, making it lightweight.

**Explanation:** The absence of connection management and reliability features in UDP results in lower overhead compared to TCP.

---

## Question 11
**Q:** One of the functionalities that UDP offers is to increase or decrease the pace with which the sender sends data to the receiver. True or False?

**A:** **False.** UDP does not provide mechanisms for flow control; it simply sends packets without regulating the transmission rate.

**Explanation:** Flow control is a feature of TCP, not UDP. UDP's simplicity means it lacks controls for pacing data transmission.

---

## Question 12
**Q:** UDP offers basic error checking. True or False?

**A:** **True.** UDP includes a checksum in its header, providing basic error checking for the data it transmits.

**Explanation:** While UDP does not provide extensive error correction mechanisms like TCP, it still includes a simple checksum to detect errors in the transmitted data.

## Question 13
**Q:** Assume Hosts A, B, and C. Host A has a UDP socket with port 123. Hosts B and C each send their own UDP segment to Host A. Hosts B and C cannot use the same destination port 123 for sending their UDP segment. True or False?

**A:** **False.** Hosts B and C can use the same destination port (123) to send data to Host A because the transport layer uses both source and destination ports to identify connections.

**Explanation:** UDP connections are identified by the combination of source IP, source port, destination IP, and destination port, allowing multiple hosts to send data to the same port on the receiver.

---

## Question 14
**Q:** TCP offers in-order delivery of the packets, flow control, and congestion control. True or False?

**A:** **True.** TCP provides mechanisms to ensure reliable, ordered delivery of packets, as well as flow and congestion control to manage data transmission effectively.

**Explanation:** These features distinguish TCP from UDP, making TCP suitable for applications requiring reliability.

---

## Question 15
**Q:** TCP detects packet loss using timeouts and triple duplicate acknowledgments. True or False?

**A:** **True.** TCP uses both timeouts and the detection of triple duplicate ACKs as signals to identify packet loss and trigger retransmissions.

**Explanation:** Triple duplicate ACKs signal to the sender that a specific packet has likely been lost, prompting a fast retransmit. Timeouts indicate a more severe case of packet loss, leading to a reduction in the congestion window.

---

## Question 16
**Q:** Flow control is a rate control mechanism to protect the receiver’s buffer from overflowing. True or False?

**A:** **True.** Flow control ensures that the sender's transmission rate does not exceed the receiver's ability to process data, preventing buffer overflow.

**Explanation:** By matching the sender's rate to the receiver's capacity, TCP prevents packet loss and ensures smooth data delivery.

---

## Question 17
**Q:** Congestion control is a rate control mechanism to protect the network from congestion. True or False?

**A:** **True.** Congestion control adjusts the sender's transmission rate to prevent network congestion, packet loss, and excessive delays.

**Explanation:** TCP adjusts the congestion window to adapt to network conditions, ensuring fair resource use and preventing congestion collapse.

---

## Question 18
**Q:** In TCP, the number of unacknowledged segments that a sender can have is the minimum of the congestion window and the receive window. True or False?

**A:** **True.** The sender limits the number of unacknowledged segments based on the smaller of the congestion window and the receiver's advertised window.

**Explanation:** This ensures that neither the network nor the receiver is overwhelmed by the sender's data transmissions.

---

## Question 19
**Q:** Consider the TCP Reno, congestion window is cut in half in both of the following events: a) a timeout occurs, b) a triple duplicate acknowledgement occurs. True or False?

**A:** **True.** TCP Reno uses a multiplicative decrease strategy to reduce the congestion window in response to both timeouts and triple duplicate ACKs.

**Explanation:** This reduction helps TCP adapt to signs of network congestion, maintaining stability.

---

## Question 20
**Q:** Consider a TCP connection and a diagram showing the congestion as it progresses. From the diagram, when we observe the congestion window drop to its initial value, we infer that a packet loss occurred. True or False?

**A:** **True.** A drop in the congestion window to its initial value indicates that the TCP sender detected a packet loss, possibly due to a timeout.

**Explanation:** TCP reduces the congestion window to the initial size to probe the network for available capacity after a loss event.

---

## Question 21
**Q:** TCP CUBIC increases the congestion window in every RTT. True or False?

**A:** **False.** TCP CUBIC uses a cubic growth function that depends on the time since the last congestion event, not directly on RTT.

**Explanation:** The cubic function allows for more flexible and aggressive window growth, especially in high-bandwidth networks, without being constrained by RTT.

---

## Question 22
**Q:** TCP CUBIC was designed for better network utilization. True or False?

**A:** **True.** TCP CUBIC is tailored for high-bandwidth, high-latency networks to make better use of available network capacity.

**Explanation:** Its cubic window growth function enables faster recovery after congestion events, optimizing throughput in modern networks.

---

## Question 23
**Q:** TCP CUBIC congestion window growth function is designed to not overflow the receiver’s buffer. True or False?

**A:** **False.** TCP CUBIC focuses on optimizing network throughput and is not specifically designed to avoid overflowing the receiver’s buffer; that is managed by TCP's flow control mechanism.

**Explanation:** Flow control ensures the receiver's buffer is not overwhelmed, while TCP CUBIC's growth function manages the sending rate to maximize network utilization.

---

## Question 24
**Q:** TCP CUBIC uses a cubic function to increase the congestion window. True or False?

**A:** **True.** TCP CUBIC employs a cubic polynomial function to manage the growth of the congestion window over time.

**Explanation:** This approach allows for more aggressive growth when far from the congestion point and more cautious growth near the previous maximum, balancing efficiency and stability.

---

## Question 25
**Q:** Explain how TCP throughput is calculated in a network with packet loss probability.

**A:** TCP throughput can be approximated using the formula: 


\[
BW \approx \frac{C}{RTT \sqrt{p}}
\]

Where:
- \( BW \) is the throughput,
- \( RTT \) is the round-trip time,
- \( p \) is the packet loss probability,
- \( C \) is a constant that accounts for network parameters.

**Explanation:** This model demonstrates that TCP throughput decreases with higher RTTs and packet loss probabilities, showing the impact of network conditions on data transmission rates.
