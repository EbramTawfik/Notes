
# Lesson 4: AS Relationships and Interdomain Routing - Study Questions and Answers

### 1. Describe the relationships between ISPs, IXPs, and CDNs.
- **ISPs (Internet Service Providers):** They are the primary providers of internet connectivity to end-users, businesses, and other networks. ISPs can be classified into different tiers:
  - **Tier-1 ISPs:** Global-scale networks that do not pay for internet access and instead interconnect with other Tier-1 ISPs. They form the internet's backbone.
  - **Tier-2 ISPs:** Regional ISPs that connect to Tier-1 ISPs and provide connectivity to smaller ISPs or directly to end-users.
  - **Tier-3 ISPs:** Local ISPs that connect directly to customers, providing last-mile connectivity.
  
- **IXPs (Internet Exchange Points):** These are physical infrastructures that allow multiple ISPs, CDNs, and other networks to interconnect and exchange traffic directly. The primary purpose of IXPs is to keep local traffic local, reducing latency and costs associated with routing traffic through external networks.

- **CDNs (Content Delivery Networks):** Networks managed by content providers to deliver content efficiently to end-users. CDNs use strategically placed servers worldwide to cache and deliver content. They often interconnect with ISPs and IXPs to optimize content delivery.

In summary, ISPs provide internet access, IXPs facilitate direct interconnection between networks, and CDNs optimize content delivery by interconnecting with both ISPs and IXPs.

---

### 2. What is an AS?
An **Autonomous System (AS)** is a collection of IP networks and routers under the control of a single organization that presents a common routing policy to the internet. Each AS is assigned a unique **Autonomous System Number (ASN)** by regional internet registries. ASes operate independently, making their own routing decisions and implementing specific traffic engineering policies. They can range from large ISPs to smaller enterprise networks or content providers.

---

### 3. What kind of relationship does an AS have with other parties?
An AS can establish various types of relationships:
- **Provider-Customer (Transit):** A customer AS pays a provider AS to forward its traffic to the wider internet. The provider advertises the customer’s routes widely.
- **Peering:** Two ASes agree to exchange traffic directly, usually without payment, for mutual benefit. Peering can occur between similar-sized networks or between different tiers of ISPs.
- **Multi-homing:** An AS connects to multiple providers or peers to increase redundancy, improve performance, or negotiate better connectivity terms.
These relationships are driven by business, economic, and technical objectives. 

---

### 4. What is BGP?
The **Border Gateway Protocol (BGP)** is the primary protocol used to exchange routing information between ASes on the internet. It is responsible for making core routing decisions, enabling ASes to determine the best paths for traffic across the complex, interconnected network of the global internet. BGP is a path vector protocol that uses multiple attributes, such as AS-PATH and NEXT-HOP, to select the most appropriate route for traffic.

---

### 5. How does an AS determine what routes to import/export?
An AS determines which routes to import/export based on:
- **Business relationships:** Routes learned from customers are generally advertised more broadly to attract traffic and revenue. Routes learned from peers are shared selectively, and routes learned from providers are typically only advertised to the AS's customers.
- **Routing policies:** Each AS has a routing policy influenced by economic incentives and technical objectives. These policies dictate route filtering, preference rankings, and other rules that decide which routes to import or export.
- **BGP Attributes:** Attributes such as LocalPref and MED are used to implement policies that influence route selection and export decisions.

---

### 6. What were the original design goals of BGP? What was considered later?
**Original Design Goals:**
- **Scalability:** BGP was designed to handle the growth of the internet in terms of the number of ASes, prefixes, and BGP traffic while providing loop-free paths.
- **Express Routing Policies:** BGP allows ASes to define and implement policies regarding which routes to import and export, keeping these decisions confidential.
- **Cooperation Among ASes:** Enables each AS to make independent routing decisions while facilitating cooperation for global connectivity.

**Later Considerations:**
- **Security:** Initially, BGP did not focus on security. As the internet grew, the need for security measures, such as protection against malicious attacks and misconfigurations, became crucial. Efforts to enhance BGP security include S-BGP, route registries, and public key infrastructure.

---

### 7. What are the basics of BGP?
- **BGP Sessions:** 
  - **eBGP (External BGP):** Sessions between border routers of different ASes to exchange routing information.
  - **iBGP (Internal BGP):** Sessions within the same AS to distribute externally learned routes.
- **BGP Messages:** 
  - **UPDATE:** Announces new routes or withdraws unavailable ones.
  - **KEEPALIVE:** Maintains the session between BGP peers.
- **BGP Attributes:** 
  - **AS-PATH:** Lists the ASes a route has passed through.
  - **NEXT-HOP:** Indicates the next router in the path.

---

### 8. What is the difference between iBGP and eBGP?
- **eBGP (External BGP):** Used between routers in different ASes to exchange routing information. The eBGP session is established between border routers of neighboring ASes.
- **iBGP (Internal BGP):** Used within an AS to disseminate externally learned routes to all internal routers. iBGP requires a full mesh of sessions between internal routers to prevent routing loops.

---

### 9. What is the difference between iBGP and IGP-like protocols (RIP or OSPF)?
- **iBGP:** Used for the dissemination of external routes within an AS. It relies on policies and attributes (e.g., AS-PATH, LocalPref) to select the best routes for traffic.
- **IGPs (Interior Gateway Protocols):** Such as RIP and OSPF, are used for routing within an AS. They focus on finding the shortest path based on a metric (e.g., hop count, link cost) without considering business relationships or external routing policies.

---

### 10. How does a router use the BGP decision process to choose which routes to import?
When a router receives multiple route advertisements to the same destination, it compares the routes using BGP attributes in a specific order:
1. **LocalPref:** Routes with higher LocalPref values are preferred, allowing ASes to prioritize specific paths.
2. **AS-PATH:** Shorter AS-PATHs are preferred, preventing routing loops.
3. **MED:** Used to select the preferred entry point for inbound traffic between two ASes.
The router continues evaluating attributes (e.g., NEXT-HOP, origin type) until a decision is made.

---

### 11. What are the 2 main challenges with BGP? Why?
1. **Scalability:** The rapid growth of the internet increases the number of ASes, prefixes, and routing changes that BGP must handle. Larger routing tables and frequent updates can strain router resources.
2. **Misconfigurations:** BGP is vulnerable to human error, which can lead to route leaks, instability, and even global outages. Limiting routing table sizes, implementing route filters, and using security measures like flap damping can mitigate these risks.

---

### 12. What is an IXP?
An **Internet Exchange Point (IXP)** is a physical infrastructure that allows multiple ASes, including ISPs, CDNs, and other networks, to interconnect and exchange traffic directly. IXPs reduce latency, improve performance, and lower costs by enabling direct peering between networks.

---

### 13. What are four reasons for IXP's increased popularity?
1. **Local Traffic Exchange:** Keeps local traffic within the region, reducing latency and avoiding the need for expensive third-party transit.
2. **Cost Efficiency:** Public peering at an IXP is generally cheaper than using transit services provided by other networks.
3. **Enhanced Network Performance:** Direct peering improves network performance by reducing the number of hops, resulting in lower latency.
4. **Incentives from Major Players:** Prominent content providers often require networks to connect at specific IXPs to peer with them.

---

### 14. Which services do IXPs provide?
- **Public Peering:** Allows networks to exchange traffic using the IXP’s infrastructure.
- **Private Peering:** Dedicated link for high-volume, stable traffic between two participants.
- **Route Servers:** Facilitate multi-lateral peering sessions, reducing the number of direct BGP sessions required.
- **DDoS Mitigation:** Some IXPs support BGP blackholing to protect against DDoS attacks.
- **Additional Services:** May include remote peering, mobile peering, service level agreements, and value-added services like DNS hosting.

---

### 15. How does a route server work?
A **route server (RS)** at an IXP simplifies the process of managing multiple BGP sessions:
1. ASes establish a BGP session with the RS.
2. The RS collects routing information from each participant.
3. It uses import filters to ensure that each AS advertises only the routes it should.
4. The RS then applies export filters based on each AS’s policies, controlling which routes are shared with other participants.
5. Finally, the RS re-advertises the selected routes to the appropriate ASes, facilitating the exchange of traffic without the need for direct bilateral peering agreements.

---

