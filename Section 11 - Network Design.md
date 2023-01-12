# 11.1 The OSI Model
- Used to explain network communications between a host and remote device over LAN or WAN.
- #### Physical
	- Represents the actual network cables and radio waves to carry data over a network
	- Bits 
	- Fiber-optic, copper, coaxial, WiFi, Bluetooth
- #### Data Link
	- How a connection is established, maintained, and transferred over the physical layer and uses physical addressing (MAC Addresses)
	- Bits will be grouped into frames to be sent over the network
	- MAC addresses, switches, bridges
		- Switches are the successors to bridges and use MAC addresses as their physical addressing.
		- MAC addresses determine where a switch sends a frame to
- #### Network
	- Uses logical addresses to route or switch information betwee hosts, the network, and the internetworks.
	- Frames are grouped up into packets
	- IP addresses, layer 3 devices (i.e. routers) to connect our devices around the world
- #### Transport
	- Manages and ensures transmission of the packets occurs from a host to a estination using either TCP (connection full protocol) or UDP (connection less protocol).
	- TCP, or **Transomisison Control Protocol** uses a three-way handshake
		- SEGMENTS
		- SYN (Synchronize Secret Number) informs the esrver that the client is likely to start communication and what number it segments with
		- The SYN + ACK phase occurs when the server responds with SYN-ACK bits to acknowledge the client's request to connect
		- The ACK phase occurs when the client acknowledges this response and the connection is established
	- UDP, or **User datagram protocol** is just a fire and forget method. Send the data over and hope it gets there.
- #### Session
	- Manages the establishment, termination, and synchroniation of a session over the network
	- Creates a unique connection over the network to direct data from the host to the destination via a continual sequence 
	- Phone call analogy: when you call someone, you don't really care about the path of the signal, given that a good connection is made
- #### Presentation
	- Translates the information into a format that the sender and receiver both understand
		- i.e. if you send a text, you have to know if it's encoded in ASCII or UTF-8. The information will be read differently depending on this.
		- File formatting, encryption formatting, etc. occurs at this layer
- #### Application
	- Layer from which the message is created, formed, and originated
	- High-level protocols like HTTP, SMTP, and FTP
	- This is where the end-user genuinely interacts with the network

# 11.2 Switches
- Hub were used to connect devices to a network
- When data went out of one port, it repeated that for all the ports. This is known as a **broadcast message**
- Bridges were developed to mitigate this, seperating LAN and WAN or connecting two logical networks together
- Switches are the combined evolution of hubs and bridges
	- Each port on a switch acts as a bridged hub
	- Improves data transfer and security through MAC addresses and only using the specific ports
	- Reduces traffic
- Switches are susceptible to MAC flooding/spoofing/physical tampering
-  **MAC Flooding** is an attempt to overwhelm the limited switch memory set aside to store the MAC address for each port, or CAM table
	-  This means that a switch can fail-open when flooded and begin to act like a hub, broadcasting data out of every port
	-  Increases traffic and leaves more room for exploitation
- **MAC Spoofing** occurs when ana attacker pretends they have the MAC address of another device
	- This is a good way to bypass wireless access ports that filter MAC addresses
	- MAC spoofing is often combined with ARP spoofing
	- Prevention includes limiting static MAC addresses accepted, duration of time for ARP entry on hosts, and conducting ARP inspection
- **Physical Tampering**
	- When an attacker physically attacks a switch.
	- Lock switches in a room, limit personel

# 11.3 Routers
- Layer 3 device used to connect two ro more networks to form an internetwork
- Routers rely on a packet's IP address to determine the proper destination
- Once on the network, it conduct an ARP request to find the final destination
- Once the traffic reaches the destination or final router, it'll broadcast an ARP request to see which MAC address it needs to be sent to
- **Access Control Lists** (ACLs) are an ordered set of rules that a router uses to decide whether to permit or deny traffic based upon given characteristics
- **IP Spoofing** is used to trck a router's ACL
- Since routers are used on the external layer of a network and are the part the end-user interacts with the most, it's important to secure them.
	- Changing default user credentials, router tables, and internal IP addresses

# 11.4 Network zones
- Most networks are divided into three separate zones (LAN, DMZ, WAN)
	- LANs are secured using private IPs, antimalware, and proper ACLs
	- WAN should be monitored and firewalled
	- Internet is the largest WAN
	-  Any traffic you wish to keep confidential crossing the internet should use a VPN
	-  De-Militarized Zone (DMZ) is focused on providing controlled access to publicly available servers taht are hosted within your organizational network
		-  Strict ACL rules, public IP address for each server on the DMZ
		-  Sub-zones can be created to provide additional protection for some servers
- Extramet is a specialized type of DMZ that is created for your partner organizations to access over a wide area network
	-  i.e. if you need to order exam vouchers for students, you can go to a site that only training organizations are able to access
- Intranets = 1 company involved; Extranets = > 1 company involved

# 11.5 Jumpbox
- **Internet-facing host** is any host that accepts inbound connections from the internet
	- A webserver in a DMZ is an internet facing host
	- These servers accept information regardless of requests
- A DMZ is a segment isolated from the rest of a private network by one or more firewalls that is connected to the internet from specific ports
	- Everything behind this is invisible to the WAN
- What goes in the DMZ?
	- Any communication or proxy server should be in the DMZ. Anything that someone would need to connect to your service
	- Harden these as best as you can.
- **Bastion hosts**
	- Hosts or servers in the DMZ which are not configured with any services that run on the local network
- **Jumpboxes** are used to configure devices in the DMZ
	- Hardeneed server that provides access to other hosts within the DMZ
	- An admin connects to the jumpbox which connects to hosts in the DMZ
	- i.e. Virtual Machines
	- Jumpbox/management workstations should only have least privilege and be hardened

# 11.6 Network Access Control (NAC)
- Security technique in which devices are scanned to determine its current state porior to being allowed access onto a given network
- A device is being placed on virtual call while it's being scanned.
	- Once it passes, it gets access to all resources provided by that network
	- It's placed into quarantine otherwise
- **Persistent agents** are software that are installed on the device requesting NA
- **Non-persistent agents** uses a piece of software that scans the device remotely or is installed and deleted once the scan is completed
- **IEEE 802.1x** standard is used in port-based NAC

# 11.7 VLANs
- VLANs are used to segment network, reduce collisions, organize the network, boost performance, and increase security
- **Switch spoofing** occurs when an attacker pretends to be a switch and uses it to negotiate a trunk link to break out of a VLAN
- **Double tagging** occurs when an attacker adds an additional VLAN tag to create an outer and inner tag
	- As traffic goes through a switch, the outer tag is removed and the malicious inner tag becomes the destination
	- Prevent this by moving all ports out of the default VLAN group

# 11.8 Subnetting
- Act of creating subnetworks logically through the manipulation of IP addresses
- It's compartmentalized, has efficient use of IP addresses, reduces broadcast traffic, and reduces collisions
- Subnet policies and monitoring can aid in the security of a network
	- i.e. printers, servers, and desktops in an office might have different rules on the various subnets
	- Moreover, if an attacker breaks into an employee's computer, they'll be stuck in that subnet until further notice

# 11.9 Network Address Translation (NAT)
- Process of changing an IP address while it transits across a router
- Using NAT can helps us hide our network IPs
- **Port Address Translation** (PAT) means that the router keep track of requests from internal hsots by assigning them random high number ports for each request
- **Class A**: 10.0.0.0 to 10.255.255.255
- **Class B**: 172.16.0.0 to 172.31.255.255
- **Class C**: 192.168.0.0 to 192.168.255.255

# 11.10 Telephony
- A **modem** is a device that can modulate digital information into an analog signal for transmissino over a dial-up phone line
- **War-dialing** occurs when an attacker persistently calls random numbers to see if they reach a modem
	- If you have modems (you likely don't), implement a callback feature to mitigate this
- **Public Branch Exchange** (PBX) is an internal phone system used in large institutions
- **Voice over Internet Protocol** (VoIP) is a digital phone service provided by software or hardware on a network
	- Quality of Service (QoS) ensures availability across VOIP.