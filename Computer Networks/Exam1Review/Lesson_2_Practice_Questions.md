
# Complete Practice Questions: Transport Layer and TCP 
# In Lesson Questions
## Question 1
**Q:** As we have seen, UDP and TCP use port numbers to identify the sending application and destination application. Why don’t UDP and TCP just use process IDs rather than define port numbers?

**A:** Using port numbers simplifies the process of multiplexing and demultiplexing data streams in the transport layer. It allows the transport layer to direct incoming segments to the correct application on a host based on the port number.

**Explanation:** Process IDs are specific to operating systems and change frequently, making protocols OS-dependent. Moreover, a single process can set up multiple communication channels, so using process IDs would not allow proper demultiplexing. Using well-known ports (e.g., 80 for HTTP) is also a convention that provides consistency.

---

## Question 2
**Q:** Why do UDP and TCP use 1’s complement for their checksums, and how does the receiver compute and detect errors using 1’s complement?

**A:** This content provides a detailed explanation of why **1's complement** is used in UDP and TCP checksums, along with examples and error detection methods. Here's a summarized version of the explanation:

### Why Use 1’s Complement for Checksums Instead of Just the Sum?

The **1's complement** method is used in UDP and TCP because it provides a simple but effective way to detect errors in data transmission. It helps detect errors more reliably than just summing the data.

### How Does the Receiver Compute and Detect Errors Using 1’s Complement?

1. **Checksum Calculation**:
   - The sender sums all 16-bit words of the data. If there’s an overflow, the extra bits are added back to the sum.
   - The **1's complement** of this sum is then calculated by flipping all the bits (0s become 1s, and 1s become 0s).
   - The 1’s complement value is sent with the data as the checksum.

2. **Error Detection at the Receiver**:
   - The receiver adds all 16-bit words of the received data (including the checksum).
   - If no errors occurred, the result will be all 1s. If the result is anything else, an error is detected.

### Example:

- Two 16-bit words:
  - `0110 0101 1100 0011`
  - `1010 1001 0011 0101`
- Sum: `1000 1111 1111 1000`
- 1’s complement of the sum: `0111 0000 0000 0111`
- The value is sent as the checksum.

When the receiver adds all the received words, including the checksum, the result should be all 1s if no errors occurred.

### Error Detection:

- **1-bit Error**: A single-bit error changes the sum, and the 1’s complement result will not be all 1s, meaning the error is detected.
- **2-bit Error**: If two bits are flipped in complementary positions (e.g., one bit changes from 1 to 0 and another from 0 to 1), the error might go undetected.

### Conclusion:

- **1-bit errors** are very likely to be detected using 1’s complement checksum.
- **2-bit errors** can sometimes go undetected if they cancel each other out, but 1’s complement is still widely used due to its simplicity and effectiveness.

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
# Lesson 2 Quiz: Transport and Applications Layers 

## Question 1
**Q:** The transport layer protocols offer a logical connection between processes only if the hosts reside in the same network. True or False?

**A:** **False.** The transport layer provides logical end-to-end connections regardless of whether hosts are on the same or different networks.

**Explanation:** The transport layer abstracts the underlying network infrastructure, creating a logical connection between communicating applications, independent of physical network boundaries.

---

## Question 2
**Q:** A sending host receives a message from the application layer and encapsulates it with the transport layer header before passing it down to the network layer. True or False?

**A:** **True.** This process involves adding transport layer headers to create a segment that is then passed to the network layer.

**Explanation:** The transport layer encapsulates the data received from the application layer, adding necessary headers for transmission across the network.

---

## Question 3
**Q:** An application running on a host can bind to multiple sockets simultaneously. True or False?

**A:** **True.** Applications can bind to different ports to manage multiple network connections simultaneously.

**Explanation:** The use of ports allows a single application to establish multiple network channels, handling diverse network communications through separate sockets.

---

## Question 4
**Q:** The identifier of a UDP socket is a tuple of destination IP address and port. True or False?

**A:** **True.** UDP sockets are identified using a combination of the destination IP address and the port number.

**Explanation:** UDP uses a two-tuple (destination IP, port) for socket identification, allowing multiplexing and routing of data to the correct application.

---

## Question 5
**Q:** The identifier of a TCP socket is a tuple of source IP address and port. True or False?

**A:** **False.** TCP sockets are identified by a four-tuple: source IP address, source port, destination IP address, and destination port.

**Explanation:** This four-tuple uniquely identifies each TCP connection, enabling the system to distinguish between multiple connections between the same pair of hosts, as they may involve different ports. This is especially important in TCP since it is connection-oriented and supports multiple simultaneous connections.

---

## Question 6
**Q:** UDP is considered more lightweight than TCP. True or False?

**A:** **True.** UDP is a simpler protocol that does not include mechanisms for error correction, flow control, or congestion control, making it lightweight.

**Explanation:** The absence of connection management and reliability features in UDP results in lower overhead compared to TCP.

---

## Question 7
**Q:** One of the functionalities that UDP offers is to increase or decrease the pace with which the sender sends data to the receiver. True or False?

**A:** **False.** UDP does not provide mechanisms for flow control; it simply sends packets without regulating the transmission rate.

**Explanation:** Flow control is a feature of TCP, not UDP. UDP's simplicity means it lacks controls for pacing data transmission.

---

## Question 8
**Q:** UDP offers basic error checking. True or False?

**A:** **True.** UDP includes a checksum in its header, providing basic error checking for the data it transmits.

**Explanation:** While UDP does not provide extensive error correction mechanisms like TCP, it still includes a simple checksum to detect errors in the transmitted data.

## Question 9
**Q:** Assume Hosts A, B, and C. Host A has a UDP socket with port 123. Hosts B and C each send their own UDP segment to Host A. Hosts B and C cannot use the same destination port 123 for sending their UDP segment. True or False?

**A:** **False.** Hosts B and C can use the same destination port (123) to send data to Host A because the transport layer uses both source and destination ports to identify connections.

**Explanation:** Great question! Let's clarify this point.

When it is said that "the identifier of a UDP socket is a tuple of destination IP address and port," this applies to how **incoming** data is demultiplexed at the **receiving side**. The receiver uses the destination IP and port to identify which socket should handle the incoming packet.

However, in your example:

- **Host A** listens on UDP port 123 (destination port).
- **Hosts B and C** both send data to **Host A**'s port 123.

In this case, even though **Host A** uses the destination port (123) to handle incoming packets, **Hosts B and C** can still send data to the same destination port because their packets are differentiated by their **source IP addresses and source ports**. While **Host A** only uses the destination IP and port to route packets to the correct application, **the network as a whole** (including the sender's side) uses a full 4-tuple (source IP, source port, destination IP, destination port) to uniquely identify the connection.

At the **receiver's side**, the UDP socket is identified by the destination IP address and port, but when looking at a connection from an overall network perspective (both sender and receiver), a 4-tuple (source IP, source port, destination IP, destination port) differentiates the connection between different hosts. Hence, both Hosts B and C can use the same destination port but have unique source ports and IPs to differentiate their connections.

---

## Question 10
**Q:** TCP offers in-order delivery of the packets, flow control, and congestion control. True or False?

**A:** **True.** TCP provides mechanisms to ensure reliable, ordered delivery of packets, as well as flow and congestion control to manage data transmission effectively.

**Explanation:** These features distinguish TCP from UDP, making TCP suitable for applications requiring reliability.

---

## Question 11
**Q:** TCP detects packet loss using timeouts and triple duplicate acknowledgments. True or False?

**A:** **True.** TCP uses both timeouts and the detection of triple duplicate ACKs as signals to identify packet loss and trigger retransmissions.

**Explanation:** Triple duplicate ACKs signal to the sender that a specific packet has likely been lost, prompting a fast retransmit. Timeouts indicate a more severe case of packet loss, leading to a reduction in the congestion window.

---

## Question 12
**Q:** Flow control is a rate control mechanism to protect the receiver’s buffer from overflowing. True or False?

**A:** **True.** Flow control ensures that the sender's transmission rate does not exceed the receiver's ability to process data, preventing buffer overflow.

**Explanation:** By matching the sender's rate to the receiver's capacity, TCP prevents packet loss and ensures smooth data delivery.

---

## Question 13
**Q:** Congestion control is a rate control mechanism to protect the network from congestion. True or False?

**A:** **True.** Congestion control adjusts the sender's transmission rate to prevent network congestion, packet loss, and excessive delays.

**Explanation:** TCP adjusts the congestion window to adapt to network conditions, ensuring fair resource use and preventing congestion collapse.

---

## Question 14
**Q:** In TCP, the number of unacknowledged segments that a sender can have is the minimum of the congestion window and the receive window. True or False?

**A:** **True.** The sender limits the number of unacknowledged segments based on the smaller of the congestion window and the receiver's advertised window.

**Explanation:** This ensures that neither the network nor the receiver is overwhelmed by the sender's data transmissions.

---

## Question 15
**Q:** Consider the TCP Reno, congestion window is cut in half in both of the following events: a) a timeout occurs, b) a triple duplicate acknowledgement occurs. True or False?

**A:** **False.** In TCP Reno, the congestion window is cut in half only when a **triple duplicate acknowledgment** is received. When a **timeout** occurs, TCP Reno reduces the congestion window to its initial value (usually 1 Maximum Segment Size or MSS).

**Explanation:** TCP Reno treats these two congestion signals differently. A triple duplicate ACK indicates mild congestion, so TCP reduces the congestion window by half to probe the network for available capacity. A timeout, however, signals severe congestion, so TCP responds by resetting the congestion window to 1 MSS and entering slow start mode.

---

## Question 16
**Q:** Consider a TCP connection and a diagram showing the congestion as it progresses. From the diagram, when we observe the congestion window drop to its initial value, we infer that a packet loss occurred. True or False?

**A:** **True.** A drop in the congestion window to its initial value indicates that the TCP sender detected a packet loss, possibly due to a timeout.

**Explanation:** TCP reduces the congestion window to the initial size to probe the network for available capacity after a loss event.

---
## Question 17
**Q:** Consider a TCP connection, and a diagram that shows how the congestion window progresses over time. From the diagram, we can identify the time periods of slow start when the congestion window increases by 1 every RTT. True or False?

**A:** **False.** During the slow start phase, the congestion window increases **exponentially** (doubles with each RTT), not by 1 every RTT. It only starts increasing linearly by 1 MSS per RTT after reaching the slow start threshold, which is when TCP transitions to the congestion avoidance phase.

---

## Question 18
**Q:** TCP CUBIC was designed for better network utilization. True or False?

**A:** **True.** TCP CUBIC aims to improve network performance, especially in high-bandwidth, high-latency networks.

---

## Question 19
**Q:** TCP CUBIC congestion window growth function is designed to not overflow the receiver's buffer. True or False?

**A:** **False.** TCP CUBIC is a **congestion control** algorithm, and its purpose is to optimize throughput based on network congestion. It does not handle flow control, which is responsible for preventing the receiver's buffer from overflowing. Flow control is managed by the receiver’s advertised window (rwnd), which limits the amount of data the sender can transmit based on the receiver's capacity.

---

## Question 20
**Q:** TCP CUBIC uses a cubic function to increase the congestion window. True or False?

**A:** **True.** TCP CUBIC uses a cubic function for adjusting its congestion window to optimize network performance.

---

## Question 21
**Q:** TCP CUBIC increases the congestion window in every RTT. True or False?

**A:** **False.** TCP CUBIC does not increase the congestion window strictly with every RTT. Instead, CUBIC uses a **cubic function** to adjust the congestion window based on the time since the last congestion event. While the congestion window typically increases during each RTT, the rate of increase is not linear or uniform. The window may also **decrease** after detecting congestion, like packet loss.

### Explanation:
TCP CUBIC's growth function can be represented as:

\[
W(t) = C \times (t - K)^3 + W_{\text{max}}
\]

Where:
- \(W(t)\) is the congestion window size at time \(t\),
- \(C\) is a constant that controls the growth rate,
- \(t\) is the time elapsed since the last congestion event,
- \(K\) is the inflection point (time after the last congestion event where the window growth slows),
- \(W_{\text{max}}\) is the previous maximum window size before the congestion event.

### Example with Numbers:

Let's say:
- The maximum congestion window size before a packet loss was \(W_{\text{max}} = 100\) MSS (Maximum Segment Size).
- The cubic function governs how the window grows after a packet loss.
- \(C\) is a constant, say 0.4 (simplified for example purposes).
- Initially, after packet loss, the congestion window is halved to \(W = 50\) MSS, following the congestion event.

#### **Growth after Packet Loss:**

1. **After 1 RTT** (after the congestion event):
   - \( t = 1 \)
   - Window size growth is slow since the window is still close to \(W_{\text{max}}\).
   - CUBIC would slowly increase the congestion window to, say, \(W = 52\) MSS, showing cautious probing of the network.

2. **After 5 RTTs**:
   - \( t = 5 \)
   - The cubic function starts to increase the window faster as the network is likely underutilized after the congestion event.
   - At this point, \(W\) might reach \(W = 80\) MSS.

3. **After 10 RTTs**:
   - \( t = 10 \)
   - Now far from the last congestion event, the window grows aggressively.
   - The window might be \(W = 120\) MSS, surpassing the previous maximum of \(W_{\text{max}} = 100\).

#### **Reduction during Congestion:**
- If another packet loss occurs at this point (with \(W = 120\) MSS), TCP CUBIC would **reduce** the congestion window sharply (e.g., halving it), dropping it back to \(W = 60\) MSS. 
- Afterward, it resumes growth using the cubic function to probe the available bandwidth again.

### Key Takeaways:
- TCP CUBIC increases the window **most of the time**, but the **rate of increase varies** based on the time since the last congestion event.
- The window will **decrease** when congestion is detected (e.g., packet loss), after which the cubic function resumes window growth.
- This dynamic adjustment allows TCP CUBIC to efficiently utilize high-bandwidth networks while reducing the risk of overloading the network after congestion.
