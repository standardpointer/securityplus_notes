# 12.1 Perimeter Security
- Security devices focused on the line between the LAN and WAN in your network

# 12.2 Firewalls
- Screen traffic between two portions of a network
- There are software, hardware, and embedded firewall solutions
	- Note on embedded: they're one piece of the larger device (i.e. in a home router)
- **Packet filtering** inspects each packet passing through the firewall and accepts or rejects it depending on the rules
	- **Stateless**: Will enact rules upon the packet only based on IP and port numbers
	- **Stateful** tracks the requests leaving the network
		- This almost removes IP spoofing as a threat because it'll inspect the header of each packet and compare that to what it was expecting from the request going out
- **NAT Filtering** filters traffic based on the port number and type of connection (i.e. TCP or UDP).
- **Application-layer gateway** conducts an in-depth inspection based upon the app being used
	- Resource-intensive, but powerful process
	- Layer 7 because they operate on the app level
- **Circuit-level gateway**  operates at the sesion layer and only inspects the traffic during the establishment of the initial session over TCP or UDP
- **MAC Filtering** can limit specific devices based on their MAC addresses 
- **Explicit allow**: traffic is allowed to enter or leave the network because the ACL specifically allows it
	- i.e. "allow TCP 10.0.0.2 any port 80", "deny TCP any any port 23"
- **Implicit Deny**: traffic is denied to enter or leave a network because there isn't a *specific* rule that allows it
	- i.e. deny any any port any
- Firewalls operate mostly on layer 3/4 (blocking IPs/ports)
- **Web-app Firewall** is installed to inspect traffic being sent to a hosted web app

# 12.3 Proxy Servers
- Acts as a middle man between a device and a remote server
- Allows the company of the hosted service to monitor and log all traffic
- #### IP Proxy
	- Secures a network by keeping its machines anonymous during web browsing
	- Using NAT to translate request from a user's machine into a proxy request
- #### Caching Proxy
	- Attempts to serve client requests by delivering content from itself without actually contacting the remote server
	- Reduces costs and is more efficient, but in a Web 2.0 world, it's less effective because of targeted advertising
	- Disable Proxy Auto-Configuration
- #### Content Filter
	- Prohibits certain sites and activities within a company
- #### Web Security Gateway
	- A go-between device that scans for viruses, filters unwanted content, and performs data loss prevention functions

# 12.4 Honeypots and Honeynets
- Are used to attract and trap potential attackers
- **Honeypots** are usually a single computer (or file, group of files, IP range, etc.) that might be attractive to a hacker
- **Honeynets** are a group of computers, servers, or networks used to attract an attacker
- These tools are used in security research

# 12.5 Data Loss Prevention
- Systems designed to protect data by conducting content inspection of data being sent out of a network
- Also known as **Information Leak Protection**(ILP) or **Extrusion Prevention Systems** (EPS)

# 12.6 NIDS and NIPS
- **NIDS**: Attempts to detect, log, and alert on malicious network activities
	- Can be placed before or after a firewall, but is usually better after because the firewall will take care of a good amount of traffic already
	- Use promiscuous mode to see all network traffic on a segment
- **NIPS**: Attempts to recover, detain, or redirect malicious traffic
	- NIPS should be installed in-line of the network traffic flow.
	- Should a NIPS fail open or shut?
		- It's usually more common to have a NIPS fail open
	- Can also perform functions as a protocol analyzer (capture/analyze/troubleshoot packets)

# 12.7 Unified Threat Management
- Was introduced in the last 5-10 years
- Relying on a single firewall is certainly not enough
- Combination of network security devices and technologies to provide more defense-in-depth within a single device
	- may include a firewall, NIDS/NIPS, content filter, anti-malware, DLP, and/or VPN.
- UTMs are also known as Next Generation Firewalls (NGFW). This is a marketing phrase, though