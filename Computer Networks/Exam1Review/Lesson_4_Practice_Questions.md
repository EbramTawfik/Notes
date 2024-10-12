
# Practice Questions: Lesson 4 - AS Relationships and Interdomain Routing

## Group 1: 4 Questions

### Question 1
The internet topology has been evolving from a __________ structure into a __________ structure.
- Hierarchical, flat
- Flat, hierarchical

**Answer:** Flat, hierarchical

**Explanation:** The internet was originally designed with a hierarchical structure, but with the advent of new interconnection strategies like peering at IXPs, the topology is evolving into a flatter structure to optimize traffic flow.

---

### Question 2
An Autonomous System is a group of routers that operate under __________ administrative __________.
- Multiple, authorities
- The same, authority

**Answer:** The same, authority

**Explanation:** An AS is a network under a single administrative domain that implements a unified routing policy.

---

### Question 3
Autonomous Systems implement their own set of policies, make their own traffic engineering decisions and interconnection strategies, and determine how traffic leaves and enters the network.
- True
- False

**Answer:** True

**Explanation:** Each AS is independently managed and sets its own routing policies based on its economic and technical objectives.

---

### Question 4
The BGP protocol is used within an AS and focuses on optimizing a path metric within the network. Examples of BGP protocols are Open Shortest Paths First (OSPF) and Routing Information Protocol.
- True
- False

**Answer:** False

**Explanation:** BGP is used for inter-AS routing and policy enforcement, not within an AS. OSPF and RIP are Interior Gateway Protocols used within an AS.

---

## Group 2: 5 Questions

### Question 1
In a peering relationship, the traffic exchanged between the two peers must be highly asymmetric so that there is enough incentive for both parties to peer with each other.
- True
- False

**Answer:** False

**Explanation:** 
In a peering relationship, the traffic exchanged between two peers is typically expected to be **balanced or symmetric**. If the traffic is **highly asymmetric**, one peer would send much more traffic than it receives, which may reduce the incentive for the other party to maintain the peering relationship, as they would not gain as much benefit from the arrangement. Symmetry in traffic helps ensure that both peers benefit equally from the exchange.


### Question 2
A customer-provider relationship between ASes is based on a financial settlement, which determines how much the customer will pay the provider. The provider takes care of connecting the customer network with destinations found in the provider’s routing table. The customer pays regardless of the direction of the traffic.
- True
- False

**Answer:** True

**Explanation:** In a provider-customer relationship, the customer pays the provider for access to the internet, and the provider forwards traffic both to and from the customer.

---

### Question 3
There is no incentive for smaller ISPs to peer with each other.
- True
- False

**Answer:** False

**Explanation:** Smaller ISPs can benefit from peering with each other by avoiding transit costs charged by larger ISPs and improving their network performance.

---

### Question 4
Provider ASes have a financial incentive to forward as much of their customers' traffic as possible.
- True
- False

**Answer:** True

**Explanation:** More traffic means more revenue for the provider, as they charge their customers based on the volume of traffic exchanged.

---

### Question 5
Select the correct order for an AS to import its routes based on their incentive.
- Routes learned from customers > peers > providers
- Routes learned from providers > customers > peers
- Routes learned from peers > providers > customers

**Answer:** Routes learned from customers > peers > providers

**Explanation:** Customer routes are preferred for revenue generation, followed by peer routes (which are usually cost-neutral), and finally provider routes, which involve costs.

---

## Group 3: 2 Questions

### Question 1
What is the difference between iBGP and eBGP?

**Answer:** 
- eBGP connects routers between different ASes to learn about external routes.
- iBGP ensures that all routers within an AS have up-to-date information on external routes learned through eBGP.

**Explanation:** Both flavors (iBGP and eBGP) take care of disseminating "external" routes. An eBGP session is established between two border routers that belong to different ASes. An iBGP session is established between routers within the same AS.

---

### Question 2
What is the difference between iBGP and IGP-like protocols (RIP or OSPF)?

**Answer:** 
- IGP-like protocols are responsible for finding the best paths between routers within the AS, typically based on cost or other metrics.
- iBGP, on the other hand, does not calculate paths within the AS; it is solely used to disseminate external routes learned from eBGP.

**Explanation:** IGP-like protocols establish paths within the AS based on specific costs, while iBGP is only used to disseminate external routes.

---

## Group 4: 5 Questions

### Question 1
A router within an AS decides which route to export by first applying import policies to exclude routes entirely from further consideration.
- True
- False

**Answer:** True

**Explanation:** Import policies are applied first to filter out routes, determining which ones can be considered for export.

---

### Question 2
The LocalPref attribute is used to prefer routes learned through a specific AS over other ASes for __________ traffic.
- Inbound
- Outbound

**Answer:** Outbound

**Explanation:** LocalPref is used to control the exit points for outbound traffic, preferring specific ASes over others.

---

### Question 3
Assume that AS X learns of a route to the same destination via AS Y and AS Z. If X prefers to route its traffic through Z due to peering or business, it can assign a __________ LocalPref value to routes it learns from Z.
- Lower
- Higher

**Answer:** Higher

**Explanation:** A higher LocalPref value indicates a preferred route, influencing the AS's decision for outbound traffic.

---

### Question 4
The MED (Multi-Exit Discriminator) value is used by ASes connected by multiple links to designate which of those links are preferred for __________ traffic.
- Inbound
- Outbound

**Answer:** Inbound

**Explanation:** MED is an indication to a neighboring AS of which entry point it prefers for incoming traffic.

---

### Question 5
Assume that AS X prefers routes advertised to AS Y to go through R1 as opposed to R2. For AS Y to be influenced to choose R1, AS X must have a __________ MED value.
- Lower
- Higher

**Answer:** Lower

**Explanation:** A lower MED value indicates a more preferred route, influencing the neighboring AS's routing decisions.

---

## Group 5: 6 Questions

### Question 1
One of the services offered by IXPs is protection against __________ attacks.
- BGP Hijacking
- DDoS
- Malware
- Phishing

**Answer:** DDoS

**Explanation:** Many IXPs offer DDoS mitigation services to protect their members against distributed denial-of-service attacks.

---

### Question 2
Participation of an AS in an IXP is free.
- True
- False

**Answer:** False

**Explanation:** Participation in an IXP usually involves membership fees and port charges for using the IXP's infrastructure.

---

### Question 3
IXPs handle large volumes of traffic.
- True
- False

**Answer:** True

**Explanation:** IXPs facilitate direct traffic exchange between multiple networks, allowing them to handle high volumes efficiently.

---

### Question 4
One of the reasons why networks choose to peer at IXPs is because critical players in today’s Internet ecosystem often “incentivize” other networks to connect at IXPs.
- True
- False

**Answer:** True

**Explanation:** Major content providers and networks often peer at IXPs to improve performance and reduce costs, incentivizing other networks to join.

---

### Question 5
Private peering PIs do not use the IXP’s public peering infrastructure.
- True
- False

**Answer:** True

**Explanation:** Private peering involves a direct connection between two networks, bypassing the public peering infrastructure of the IXP.

---

### Question 6
IXPs users may use route servers for an additional cost.
- True
- False

**Answer:** False

**Explanation:** Route servers are usually a free service provided by IXPs to facilitate multi-lateral peering among their participants.

---

## Group 6: 2 Questions

### Question 1
Route Servers keep track of the BGP sessions they maintain with each participant AS through RIBs.
- True
- False

**Answer:** True

**Explanation:** Route servers use Routing Information Bases (RIBs) to manage and store routing information from all connected peers.

---

### Question 2
__________ filters are applied to ensure that each member AS only advertises routes that it should advertise.
- Import
- Export

**Answer:** Import

**Explanation:** 
**Import filters** are applied to ensure that each member AS only advertises routes that it is allowed to advertise. These filters check the routes as they are received by the route server or another AS to ensure compliance with policies before adding them to the routing table.



# Group 7: 23 Questions

### Question 1
The Internet topology has been evolving to an increasingly prominent hierarchical structure.
- True
- False

**Answer:** False

**Explanation:** The internet topology has been evolving from a hierarchical structure into a flatter structure due to the use of IXPs and peering strategies.

---

### Question 2
An Autonomous System operates across multiple administrative domains.
- True
- False

**Answer:** False

**Explanation:** An Autonomous System (AS) operates under a single administrative domain, managing its own routing policies.

---

### Question 3
For two ASes to form a peering agreement, they need to find common ground regarding the internal policies and traffic engineering approaches that each AS implements.
- True
- False

**Answer:** False

**Explanation:** Peering agreements are based on the mutual benefits of traffic exchange, not on internal policies or traffic engineering strategies.

---

### Question 4
A Content Distribution Network (CDN) or an ISP can operate over multiple Autonomous Systems.
- True
- False

**Answer:** True

**Explanation:** CDNs and ISPs may operate across multiple ASes to extend their network reach and optimize traffic delivery.

---

### Question 5
Consider the figure below that denotes ASes and their relationships.  
**Note:** C1, C2, C3 are customers of ISP-X. ISP-P is a provider of ISP-X.  
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-5.png?raw=true)
ISP-X has the incentive to advertise routes for C3 to Y.
- True
- False

**Answer:** True

**Explanation:** ISP-X benefits from advertising its customers' routes to attract more traffic and potential revenue.

---

### Question 6
Consider the figure below that denotes ASes and their relationships.  
**Note:** C1, C2, C3 are customers of ISP-X. ISP-P is a provider of ISP-X.  
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-5.png?raw=true)
ISP-X has the incentive to advertise the routes for P’s customers to Y and Z.
- True
- False

**Answer:** False

**Explanation:** ISP-X generally does not advertise the routes it learns from its provider to other peers as there is no financial incentive.

---

### Question 7
Consider the figure below:  
**Note:** C1, C2, C3 are customers of ISP-X. ISP-P is a provider of ISP-X.  
Assume that AS-X learns multiple routes for the same external destination W. These multiple routes are advertised from C3, from Y, and from P. How would AS-X rank these routes before deciding which one to import?

![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-5.png?raw=true)
- Route learned from C3, route learned from Y, route learned from P
- Route learned from Y, route learned from C3, route learned from P
- Route learned from P, route learned from C3, route learned from Y
- Route learned from P, route learned from Y, route learned from C3

**Answer:** Route learned from C3, route learned from Y, route learned from P

**Explanation:** ASes prefer routes learned from customers first, followed by peers, and lastly, providers.

---

### Question 8
Consider the topology below and the types of BGP sessions the routers form.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true)  
Select the true statements.
- R-A1 ↔ R-A3 : iBGP
- R-B1 ↔ R-A3 : eBGP
- R-B3 ↔ R-D2 : iBGP
- R-D3 ↔ R-D2 : eBGP

**Answer:** R-A1 ↔ R-A3 : iBGP, R-B1 ↔ R-A3 : eBGP

**Explanation:** iBGP is used for internal routers within the same AS, while eBGP is used for routers between different ASes.

---

### Question 9
Assume that router R-D2 learns about a route to a destination in AS-A. How would router R-D2 disseminate this route to R-D3 and R-D1?
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true) 
- Using iBGP
- Using eBGP
- Using IGP

**Answer:** Using iBGP

**Explanation:** iBGP is used within an AS to disseminate routes learned from eBGP sessions.

---

### Question 10
Assume that router R-D2 learns about a route to an internal destination in AS-D. How would router R-D2 disseminate this route to R-D3 and R-D1?
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true) 
- Using iBGP
- Using eBGP
- Using IGP

**Answer:** Using IGP

**Explanation:** IGP protocols like OSPF or RIP are used to share internal routes within an AS.

---

### Question 11
Assume that router R-B1 learns about a route to AS-C. How would router R-B1 disseminate this route to R-A3?
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true) 
- Using iBGP
- Using eBGP
- Using IGP

**Answer:** Using eBGP

**Explanation:** The route is shared between different ASes, so eBGP is used.

---

### Question 12
Since the BGP path selection process is fixed, an AS has no control over which routes are selected.
- True
- False

**Answer:** False

**Explanation:** An AS can control route selection through attributes like LocalPref, MED, and AS-PATH.

---

### Question 13
Assume that AS-B learns about an external destination both from AS-C and from AS-A. AS-B can show preference to use the route heard from AS-C by assigning a higher LocalPref value to that route.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true) 
- True
- False

**Answer:** True

**Explanation:** LocalPref is used to influence the selection of outbound routes, with higher values being preferred.

---

### Question 14
Assume that AS-B advertises the routes to its internal destination to AS-A using the routers R-B1 and R-B4. AS-B can communicate to AS-A that it prefers R-B1 as an entry point to the network by assigning lower MED values to these routes.
![](https://github.com/EbramTawfik/Notes/blob/main/Computer%20Networks/Exam1Review/images/Q-4-7-8.png?raw=true) 
- True
- False

**Answer:** True

**Explanation:** Lower MED values indicate a more preferred entry point for inbound traffic from neighboring ASes.

---

### Question 15
An AS can use LocalPref to control which routes are used as exit points (for the outgoing traffic), and it can use the MED attribute to control which routers are used as entry points (for the incoming traffic).
- True
- False

**Answer:** True

**Explanation:** LocalPref affects outbound routing decisions, while MED influences inbound routing preferences.

---

### Question 16
One of the services provided by IXPs is additional security protections such as mitigation of DDoS (Distributed Denial of Service) attacks.
- True
- False

**Answer:** True

**Explanation:** Many IXPs offer DDoS mitigation services to protect their members from attacks.

---

### Question 17
There are no costs involved for an AS to participate at an IXP.
- True
- False

**Answer:** False

**Explanation:** IXPs typically charge fees for membership, port access, and other services.

---

### Question 18
Since local traffic stays local at IXPs, the IXP infrastructures deal with limited volumes of traffic.
- True
- False

**Answer:** False

**Explanation:** IXPs handle large volumes of traffic as they facilitate direct peering between many networks.

---

### Question 19
When a large provider or Content Delivery Network joins an IXP, this can act as an incentive for other networks to join as well.
- True
- False

**Answer:** True

**Explanation:** The presence of major players at an IXP attracts other networks for direct peering opportunities.

---

### Question 20
At an IXP, the members have the choice to peer privately or publicly.
- True
- False

**Answer:** True

**Explanation:** IXPs offer both public peering (using a shared switch) and private peering (direct connections between networks).

---

### Question 21
IXPs' leading incentive to establish route servers was to charge the participants for using it.
- True
- False

**Answer:** False

**Explanation:** Route servers were established to simplify peering arrangements, not to generate direct revenue.

---

### Question 22
An IXP route server does not need to run the BGP protocol to facilitate the establishment of multi-lateral peering sessions.
- True
- False

**Answer:** False

**Explanation:** Route servers must run BGP to facilitate route exchange between participants in multi-lateral peering.

---

### Question 23
For multi-lateral BGP peering sessions at an IXP, the participants have the choice to advertise routes, either directly to other participants, or to the route server.
- True
- False

**Answer:** True

**Explanation:** Participants at an IXP can advertise routes directly or through a route server to simplify peering arrangements.

