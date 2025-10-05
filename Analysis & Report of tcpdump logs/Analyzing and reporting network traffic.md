# TCPDump Network Analysis Report – DNS and ICMP Investigation

---

## 1. Overview
At approximately 1:24 PM, multiple customers reported being unable to access the website **“yummyrecipesforme.com”**, receiving a **“Destination port unreachable”** message.  
An investigation was initiated using **tcpdump** to analyze live network traffic between client systems and the DNS server.  

Captured traffic indicated that the DNS server was not responding to requests on **UDP port 53**, resulting in DNS resolution failures and service unavailability.

---

## 2. Findings from Packet Capture
### Observed Protocols:
- **UDP (User Datagram Protocol):**  
  Used by the client’s browser to send DNS queries to the DNS server.
- **ICMP (Internet Control Message Protocol):**  
  Used by the server to return error messages indicating communication failures.

### Log Observations:
- Each tcpdump event contained **two outbound UDP packets** from the client to the DNS server followed by **two inbound ICMP responses** from the server.  
- The ICMP messages contained the error **“udp port 53 unreachable.”**  
- The **“A?”** flag in the UDP message indicated a request for an IPv4 address (A record).  
- The **“+”** flag following the query ID (35084) signified DNS query options.  
- Repeated query IDs confirmed multiple failed attempts by the client to contact the DNS server.

These patterns confirm that the DNS server was rejecting or unable to process UDP requests on port 53.

---

## 3. Analysis and Interpretation
The ICMP “Port Unreachable” message signifies that **UDP traffic to port 53 could not reach an active DNS service**.  
Since port 53 is the default for DNS queries, this directly caused the DNS lookup failures observed by users.  

The root issue lies in the network path between the client and the DNS server — either the DNS service itself is unavailable, or the traffic is being blocked by a firewall or intermediate network device.  

---

## 4. Possible Causes
1. **Firewall or ACL Misconfiguration:**  
   UDP port 53 may be blocked or filtered by a local or perimeter firewall.
2. **Server Unavailability:**  
   The DNS server may be offline, unresponsive, or misconfigured.
3. **Network Device Interference:**  
   A router, switch, or proxy could be filtering or dropping DNS packets.
4. **Potential DoS Attack:**  
   ICMP “port unreachable” messages can appear when a DNS server is overwhelmed or targeted by a DoS attack, resulting in dropped requests.

---

## 5. Recommendations
| Category | Recommended Action |
|-----------|--------------------|
| **Firewall Configuration** | Verify that UDP port 53 is open for DNS queries; review ingress/egress rules. |
| **Server Monitoring** | Check DNS server uptime, service status, and configuration files. |
| **Network Devices** | Inspect routers and switches for filtering or packet loss. |
| **Security Review** | Analyze ICMP and UDP logs for unusual traffic patterns suggesting DoS activity. |
| **Post-Fix Testing** | Use `nslookup`, `dig`, and `ping` to confirm DNS resolution post-mitigation. |

