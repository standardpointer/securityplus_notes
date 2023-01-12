# 15.1 Ports and Protocols
- - An **inbound port** is a logical communication opening on a server that is listening for a connection from a client
- An **outbound port** is a logical communication opening created on a client in order to call out to a server that is listening for a connection
![[ssh_example.png]]
- Ports can be any number between 0 and 65,535
- **Well-known ports** (the first 1024 ports; 0-1023) are considered well-known and are assigned by the Internet Assigned Numbers Authority (IANA).
	- i.e. HTTPS (443), Telnet (23)
- **Registered Ports** cover 1024-49,151 are considered registered and are usually assigned to proprietary protocols
	- i.e. Microsoft's SQL server (1433), remote desktop (3389)
- **Dynamic or private ports** cover 49,152-65,535 and can be used by any app without being registered with IANA

# 15.2 Memorization of Ports
- Review: 65,536 ports available for use
- **22: SSH, SCP, SFTP**: Secure Shell is used to remotely administer network devices and systems. SCP is used for secure copy and SFTP for secure FTP. TCP/UDP
- **23: Telnet**: Unencrypted method to remotely administer network devices (should not be used) TCP/UDP
- **25: SMTP**: Simple Mail Transfer Protocol is used to send email over the internet. TCP
- **53: DNS**: Domain Name Service is used to resolve hostnames to IPs and vice versa. TCP/UDP
- **69: TFTP**: Trivial FTP is used as a simplified version of FTP to put a file on a remote host or get a file from a remote host. UDP
- **80: HTTP**: Hyper Text Transfer Protocol is used to transmit web page data to a client for unsecured web browsing TCP
- **88: Kerberos**: Used for network authentication using a system of tickets within a Windows domain. TCP/UDP
- **110: POP3**: Post Office Protocol v3 is used to receive email from a mail server. TCP
- **119: NNTP**: Network News Transfer Protocol is used to transport Usenet articles. TCP
- **135: RPC/DCOM-scm**: Remote Procedure Call is usedto locate DCOM Ports to request a service fro ma prgoram on another computer on the network. TCP/UDP
- **137-139: NetBIOS**: Used to conduct name querying, sending of data, and other functions over a NetBIOS connection. TCP/UDP
- **143: IMAP**: Internet Message Access Protocol is used to receive email from a mail server with more features than POP3. TCP
- **161: SNMP**: Simple Network Management Protocol is used to remotely monitor network devices. UDP
- **162: SNMPTRAP**: Used to send TRAP and informrequests to the SNMP manager on a network. TCP/UDP
- **389: LDAP**: Lightweight Directory Access Protocol is used to maintain directories of users and other objects. TCP/UDP
- **443: HTTPS**: Used to transmit web page data over to a client over a SSL/TLS encrypted connection. TCP
- **445: SMB**: Server Message Block is used to provide shared access and other resources via a network. TCP
- **465/58: SMTP with SSL/TLS**: Simple Mail Transfer Protocol used to send email over the internet via an SSL/TLS connection
- **514: Syslog**: Used to conduct computer message logging, especially for routers and firewalls. UDP.
- **636: LDAP SSL/TLS**: LDAP over SLS/TLS
- **860: iSCSI**: Used for linking data storage facilities over IP. TCP
- **980/990: FTPS**: Used to send files from host to host via a secure connection
- **993: IMAP4 with SSL/TLS**: IMAP4 via encrypted SSL/TLS
- **995: POP3 with SSL/TLS**: POP3 via SSL/TLS. TCP
- **1433: Ms-sql-s**: Microsoft SQL serveri s used to erceive SQL database queries from clients. TCP
- **1645/46: RADIUS**: Remote Authentication Dial-In User Service is used for authentication and authorization (1645) and accounting (1646). UDP
- **1701: L2TP**: Layer 2 Tunnel Protocol is used as an underlying VPN protocol but has no inherent security. UDP
- **1723: PPTP**: Point-to-Point Tunneling Protocol is an underlying VPN protocol with built-in security. TCP/UDP
- **1812/1813** RADIUS. UDP
- **3225: FCIP**: Fibre Channel IP is used to encapsulate Fibre Channel frames within TCP/IP packets. TCP/UDP
- **3260: iSCSI Target**: iSCSI Target is a listening port for iSCSI target devices when linking data storage facilities over IP TCP
- **3389 RDP**: Remote Desktop Protocol is used to remotly view and control other Windows systems via a GUI. TCP/UDP
- **3868: Diameter**: A more advanced AAA protocol that's a replacement for RADIUS. TCP
- **6514: Syslog over TLS**: It is used to conduct computer message logging via a TLS encrypted connection. TCP 

# 15.3 Unnecessary Ports
- Any port that is associated with a service or function that is non-essential to the operation of your computer or network
- Any open port represents a possible vulnerability that might be exposed
- On Windows, mitigate this using `C:\ net stop service`. On Unix systems `sudo stop service`

# 15.4 DoS
- Term used to describe many different types of attacks which attempt to make a computer or server's resources unavailable
- #### Flood Attacks
	- A specialized type of DoS which attempts to send more packets to a single server or host than they can handle
- #### Ping Flood
	- An attacker attempts to flood the server by sending too many ICMP echo request packages
- #### Smurf Attack
	- Attacker sends a ping to subnet broadcast address and devices reply to spoofed IP, eating up resources
- #### Fraggle Attack
	- Attacker sends a UDP echo packet to port 7 (ECHO) and port 19 (CHARGEN) to flood a server with UDP packets
- #### SYN Flood
	- Variant on a DoS attack where attacker initiates multiple TCP sessions but never completes the 3-way handshake
	- Flood guards, time outs, and an IPS can prevent SYN Floods
- #### XMAS Attack
	- A specialized network scan that sets the FIN, PSH, and URG flags and can cause a device to crash or reboot
- #### Ping of Death
	- An attack that sends an oversized and malformed packet to another computer or server
- #### Teardrop Attack
	- Breaks apart packets into IP fragments, modifies them with overlapping and oversized payloads, sending them to a victim
- #### Permanent DoS
	- Exploits security hole to permanently damage a networking device by reflashing its firmware
- #### Fork Bomb
	- Attack that creates a large number of processes to use up the available processing power on a machine

# 15.5/6 DDoS / Prevention
- A group of compromised systems attack a single target simultaneously to create a DoS
- **DNS Amplification**: Attack which relies on the large amount of DNS information that is sent in response to a spoofed query on behalf of the victim
- GitHub was once victim to a 1.35Tbps DDoS. How do you prevent something like this?
	- **Blackholding or sinkholing** can identify any attacking IP address and routes all their rtaffic to a non-existent server via the null interface
	- An IPS can prevent a small-scale DDoS
	- Specialied security services cloud providers can stop DDoS attacks

# 15.7 Spoofing
- Any unique identifiers can be spoofed 
- Proper authentication is used to detect and prevent spoofing

# 15.8 Hijacking
- Exploitation of a computer session in an attempt to gain unauthorized access to data, services, or other resources on a computer server
- #### Session Theft
	- Attacker guesses the session ID for a web session, enabling them to takeover the already authorized session of the client
- #### TCP/IP hijacking
	- Occurs when an attacker takes over a TCP session between two computers without the need of a cookie or other host access
- #### Blind hijacking
	- An attacker blindly injects data into the communication stream without being abel to see if it is successful or not
- #### Clickjacking
	- Uses multiple transparent layers to trick a suer into clicking on a button or link on a page when they were intending to click on the actual page
- #### Man-in-the-Middle
	- Attack that causes data to flow through the attacker's computer where they can intercept or manipulate it
- #### Man-in-the-Browser
	- A Trpjan infects a vulnerable web browser and modifies the web pages or transactions being done within the browser
- #### Watering hole
	- When malware is placed on a website that the attacker knows their potential victims will access

# 15.9 Replay Attack
- Network-based attack where a valid data transmission is fradulently or maliciously rebroadcast, repeated, or delayed
- Ensure websites and other services are using tokens to uniquely identify a legitimate session

# 15.10 Transitive Attacks
- More of a conceptual method
- **Transitive Property**: A = B = C
	- Similarly, if network1 trusts network2 and network2 trusts network3, network1 SHOULD trust network3.
	- If an attacker can get into one of these networks, they have access to all three of them
- When you connect to another network via a trust relationship, all security benefits and/or risks are inherited

# 15.11 DNS Attacks
- #### DNS Poisoning
	- Occurs when the name resolution information is odified in the DNS server's cache
- #### Unauthorized Zone Transfers
	- Occurs when an attacker requests replication of the DNS information to their systems for use in planning future attacks
- #### Altered Hosts Files
	- Occurs when an attacker modifies the host fileto have the client bypass the DNS server and redirects them to an incorrect or malicious website
- #### Pharming
	- Occurs when an attacker redirects one website's traffic into a malicious website
- #### Domain Name Kiting
	- Attack that exploits a process in the way a domain name is registered so that the domain name is kept in limbo and cannot be registered by an authenticated buyer

# 15.12 ARP Poisoning
- Protocol for mapping an IP address to a MAC address that is recognized in the local network
- Attack that exploits the IP address to MAC resolution in a network to steal, modify, or redirect frames within the local area network
- Allows an attacker to essentially take over any sessions within the LAN