# 27.1 Secure/Multipurpose Internet Mail Extensions (S/MIME)
- A standard that provides cryptographic security for electronic messaging
- Most mail clients have the potential to support S/MIME
- Allows for, combined w certs, to give authentication, integrity, and non-repudiation
- S/MIME can encrypt all emails, even those with malware

# 27.2 Secure Socket Layer/Transport Layer Security (SSL/TLS)
- Cryptographic protocols that provide secure internet comms for browsing, texting, email, VoIP, and many other services
- SSL was last updated in 1996 (SSL v3)
	- TLS is the replacement
- HTTPS: HTTP tunnled w TLS over port 443.
- For email, this is via SMTP
- **Downgrade attack**: a protocol is tricked into using a lower quality version of itself
	- Mitigate this by not being backwards compatible
- It's a challenge for defenders, actually.
	- i.e. if you're sending a file via Dropbox on the secure site, a defender can't see what you're doing.
	- This can be mitigated through **break and inspect**. 
	- Put a proxy in between the user and Dropbox, for the user to authenticate a TLS tunnel with. 

# 27.3 Secure Shell (SSH)
- A protocol that can create a secure channel between two devices so one can control the other
- Designed as a replacement for Telnet
- Originally in Unix/Linux, but is now found in Windows
- SSH requires a server (daemon) to be run on one device and a client on the other
- Runs on port 22, along with secure copy and SFTP
	- The latter two operate on SSH
- v1, v1.5, and v2 are the big ones
	- the first had unauthorized insertion of content, improper forwarding of those secure connections to other servers, and integer overflows
	- v2 fixed these, as well as adding Diffie-Hellman key exchangees and Message Authentication Codes

# 27.4 VPN Protocols
- REMINDER: VPNs are a secure connection between two or more devices that aren't on the same private network
- **Point-to-point tunneling protcol (PPTP)**: a protocol that encapsulates PPP packets and ultimately sends data as encrypted traffic
	- Uses CHAP-based authentication, making it vulnerable to attacks
	- Use EAP-TLS or something like that
- **Layer 2 Tunneling Protocol (L2TP)**: a connection between two or more comps that are not on the same private network
	- No encryption/confidentiality on its own; uses IPSec to achieve this
	- Run on port 1701
- **IPSec**: TCP/IP protocol that authenticates and encrypts IP packets and effectively securing communications between computers and devices using this protocol
	- **Internet Key Exchange (IKE)**: method used by IPSec to create a secure tunnel by encrypting the connection between authenticated peers
	- Main: three separate exchanges; Aggressive: exchange will happen more quickly, but only with three packets; Quick: only negotiated IPSec parameters will be considered
	- *Phase 1*: establishes encryption/authentication protocols
	- ISAKMP will be established, and security associations will be created w Main or Aggressive
	- Both sides create a private key and derive a public key w Diffie-Hellman
	- *Phase 2*: shared secret key is created establishes encryption/integrity, creating a tunnel in a tunnel. Data will flow in here
- **Security Association**: establishment of secure connections and shared security info using certs or cryptographic keys
- **Authentication Header (AH)**: protocol used in IPSec that provides integrity and authentication
- **Encapsulating Security Payload (ESP)**: provides integrity, confidentiality, and authenticity of packets by encapsulating and encrypting them
- **Transport Mode**: H2H transport mode that only uses encryption of the payload of an IP packet, not the header
	- Used for transmission between hosts on a private network
- **Tunnel Mode**: a network tunnel is created which encrypts the entire IP packet
	- Commonly used for transmission between networks
