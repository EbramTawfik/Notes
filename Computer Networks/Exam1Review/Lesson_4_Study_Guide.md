
# Computer Networks Study Guide: Lesson 4

## Introduction to AS Relationships and Interdomain Routing

The internet is a complex ecosystem that consists of thousands of independently operated networks. Each network, known as an **Autonomous System (AS)**, operates independently with its own economic and traffic engineering objectives. Despite this independence, these networks must interconnect to provide global connectivity.

In this lesson, we explore how data travels between networks, focusing on the **Border Gateway Protocol (BGP)**. BGP acts as the glue holding the internet together, facilitating inter-AS routing. We will also examine different types of interconnections based on business relationships between ASes, such as **Provider-Customer** and **Peering** relationships. Lastly, we delve into **Internet Exchange Points (IXPs)**, infrastructures that allow participant networks to exchange traffic directly.

---

## Autonomous Systems (AS) and Internet Interconnection

The internet is a network of networks, primarily consisting of:
- **Internet Service Providers (ISPs):**
  - **Tier-1 ISPs:** Global-scale networks that form the backbone of the internet (e.g., AT&T, NTT). They have the unique characteristic of not paying any other network for internet connectivity because they interconnect with other Tier-1 ISPs.
  - **Tier-2 ISPs:** Regional ISPs that connect to Tier-1 ISPs. They act as intermediaries, providing connectivity to smaller, local ISPs.
  - **Tier-3 ISPs:** Also known as access ISPs, they connect directly to end-users and rely on Tier-2 ISPs for broader internet access.

- **Internet Exchange Points (IXPs):** Physical infrastructures that provide the means for multiple networks (ISPs, CDNs) to interconnect and exchange traffic locally. IXPs are crucial for reducing latency and cost by allowing direct traffic exchange.

- **Content Delivery Networks (CDNs):** Networks managed by content providers (e.g., Google, Netflix) designed to have better control over content delivery and to reduce connectivity costs. CDNs have multiple data centers distributed worldwide to serve content efficiently to end-users.

### Hierarchical Internet Topology
The internet's topology traditionally follows a hierarchical structure. However, with the growth of IXPs and CDNs, this structure is evolving toward a more flattened topology. Smaller networks (e.g., Tier-3 ISPs) connect to larger ones (e.g., Tier-1 and Tier-2 ISPs), creating a complex mix of competition and cooperation among these entities.

### Competition and Cooperation Among Networks
ISPs compete with each other to provide services, but they must also cooperate to ensure global internet connectivity. For instance, a Tier-1 ISP cannot function independently without interconnecting with other Tier-1 ISPs. They deploy various interconnection strategies, such as multi-homing (connecting to multiple ISPs) and peering (direct traffic exchange).

---

## AS Business Relationships

### 1. **Provider-Customer Relationship (Transit):**
In this relationship, a smaller AS (customer) pays a larger AS (provider) for internet connectivity. The provider forwards the customer's traffic to the wider internet. The provider advertises the customer’s routes to other networks, maximizing the customer's accessibility.

### 2. **Peering Relationship:**
Two ASes agree to exchange traffic for free, usually for traffic destined for each other’s networks or their respective customers. Peering agreements are often formed to save on transit costs and improve efficiency by keeping local traffic local. 

Peering relationships can exist between:
- **Tier-1 ISPs:** Require similar size and traffic volume to ensure fairness.
- **Smaller ISPs:** Directly peer to avoid transit costs charged by providers.

### Provider Charging Mechanisms
- **Fixed Price:** Providers may charge customers a flat fee based on bandwidth usage within a predefined range.
- **Bandwidth-Based:** Charges depend on the 95th percentile of bandwidth usage, calculated from periodic measurements.

---

## BGP Routing Policies: Importing and Exporting Routes

**BGP** routing policies are shaped by AS business relationships. An AS makes decisions about which routes to import and export based on the economic incentives involved.

### Exporting Routes
- **Routes Learned from Customers:** ASes widely advertise these routes to attract more inbound traffic toward the customer, thus increasing revenue.
- **Routes Learned from Providers:** These routes are typically not advertised to peers or other providers to avoid unnecessary traffic and costs. However, they may be advertised to the AS’s customers.
- **Routes Learned from Peers:** Shared selectively. An AS would not advertise a peer route to another peer or provider as it could lead to free-riding, where one network uses another's resources without compensation.

### Importing Routes
When an AS receives multiple route advertisements to the same destination, it ranks them as follows:
1. **Customer Routes:** Preferred because they generate revenue.
2. **Peer Routes:** Used next as they are usually "free" under the peering agreement.
3. **Provider Routes:** Least preferred since they involve costs.

---

## BGP Protocol Basics

**BGP** is the protocol that governs how ASes exchange routing information and manage policies for selecting the best paths. 

### BGP Sessions
- **eBGP (External BGP):** Connects routers in different ASes, facilitating the exchange of routing information between autonomous networks.
- **iBGP (Internal BGP):** Used within the same AS to distribute externally learned routes to internal routers. Each router in the AS forms a full mesh of iBGP sessions to ensure complete dissemination of routing information.

### BGP Messages
- **UPDATE Messages:** Notify peers about new routes or changes in existing routes. They contain attributes that influence route selection.
  - **Announcements:** Advertise new or updated routes.
  - **Withdrawals:** Inform peers that a previously advertised route is no longer available.
- **KEEPALIVE Messages:** Periodically exchanged to maintain the BGP session.

### BGP Attributes
- **AS-PATH:** Lists all the ASes a route has passed through. It is critical in preventing routing loops and is used to choose the shortest path.
- **NEXT-HOP:** Identifies the IP address of the next router in the path. This attribute helps internal routers forward traffic through the most appropriate gateway.

---

## iBGP and eBGP

While both **iBGP** and **eBGP** disseminate external routing information, they differ in their scope:
- **eBGP:** Exchanges routes between border routers of neighboring ASes.
- **iBGP:** Disseminates these external routes to all routers within the AS, using a full mesh of iBGP sessions.

It is important to note that iBGP does not establish paths like Interior Gateway Protocols (IGPs) such as OSPF. Instead, it merely distributes externally learned routes.

---

## BGP Decision Process: Selecting Routes

When a router receives multiple advertisements for the same destination, it must decide which route to import. The decision process involves evaluating several attributes:
1. **Local Preference (LocalPref):** Determines the preferred outbound path. Higher values are preferred, allowing an AS to prefer routes through specific ASes.
2. **Multi-Exit Discriminator (MED):** Used to select the preferred entry point for inbound traffic when multiple connections exist between two ASes.

By setting these attributes, an AS can influence traffic flow according to its business interests and network performance.

---

## Challenges with BGP: Scalability and Misconfigurations

### Scalability
The global growth of the internet means that the BGP protocol must handle an increasing number of ASes and prefixes. Methods to address scalability include:
- **Route Filtering:** Limits routing table size by filtering out long prefixes.
- **Flap Damping:** Suppresses unstable routes that experience frequent changes to reduce network churn.

### Misconfigurations and Faults
BGP can be prone to misconfigurations, leading to routing instability, processor overloads, and even outages. ASes can mitigate these risks by using strict route filtering, limiting advertised prefixes, and employing security measures.

---

## Peering at IXPs

**IXPs** provide the infrastructure for ASes to interconnect and directly exchange traffic. They offer several advantages:
- **Cost Savings:** Peering at an IXP is typically cheaper than third-party transit.
- **Improved Performance:** Reduces delay and keeps local traffic within the local region.

### Steps for an AS to Peer at an IXP
1. Obtain a public Autonomous System Number (ASN).
2. Connect a router to the IXP switch.
3. Use BGP to exchange routes across the IXP infrastructure.

### Services Offered by IXPs
1. **Public Peering:** ASes use the IXP’s network to exchange traffic.
2. **Private Peering:** Direct traffic exchange over a dedicated link, bypassing the public infrastructure.
3. **Route Servers:** Simplify peering by maintaining routing information and filtering based on participant policies.
4. **DDoS Mitigation:** Some IXPs offer services like BGP blackholing to protect against DDoS attacks.

---

## Conclusion

Understanding inter-AS relationships and routing mechanisms is crucial for managing global internet infrastructure. The **BGP** protocol offers the flexibility needed for different business models but also presents challenges in scalability, security, and proper route management. IXPs continue to play an essential role in the evolving topology of the internet.

---

## References
- Kurose-Ross, 6th Edition
- [BGP routing policies in ISP networks](http://www.cs.princeton.edu/~jrex/papers/policies.pdf)
- [Peering at Peerings: On the Role of IXP Route Servers](https://conferences2.sigcomm.org/imc/2014/papers/p31.pdf)
