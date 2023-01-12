# Section 19.1 Authentication
- **MFA**: Use of two or more authentication factors to prove a userr's identity
	- Knowledge
	- Ownership
	- Characteristic
	- Location
	- Action
- Username and password are only considered single-factor authentication
- **Time-based One Time Password**: (TOTP) a password is computed from a shared secret and current time
-**HMAC-based One Time Password**: (HOTP) a password is computed from a shared secret and is synchronized between the client and the server

# 19.2 Authentication Models
- #### Context-aware 
	- Process to check the user's or system's attributes or characteristics prior to allowing it to connect
- #### Single Sign-On
	- A default user profile for each user is created and linked with all of the resources needed
	- Compromised SSO credentials cause a big breach in security
- #### Federal Identity Management
	- A single identity is created for a user and shared with all of the organizations in a federation
- **Cross-certification**: utilizes a web of trust between organizations where each one certifies others in the federation
- **Trusted third-party**: organizations are able to place their trust in a single third=party (also called the bridge model)
- **Security Assertion Markup Langauge**: (SAML) attestation model built upon XML used to share federated identity management info between systems
- **OpenID**: an open standard and decentralized protocol that is used to authenticate users in a FIDm system
- User logs into an **Identity Provider** and uses their account at **Relying Parties**
- SAML is more efficient than OpenID, but OpenID is easier to implement
# 19.3 802.1x
- Standardized framework used for port-based authentication on wired and wireless networks
- RADIUS and TACACS+ run on 802.1x
- **Supplicant**: device or user that's requesting access
- **Authenticator**: device through which the supplicant is attempting to access the network (switch, WAP, VPN)
- **Auth server**: centralized server that performs the authentication (RADIUS or TACACS)
- Can prevent rogue devices
- **Extensible Authentication Protocol**: (EAP) a framework of protocols that allows for num,erous methods of authentication including passwords, digital certs, and PKI
- EAP-MD5 uses simple passwords for its challenge-authentication
- EAP-TLS uses digital certs for mutual authentication
- EAP-TTLS uses a server-side digital cert and a client-side password for mutual authentication
- EAP-FAST: provides flexible auth via secure tunnelign (FAST) by using a protected access credential instead of a cert for mutual authentication
- Protected EAP: (PEAP) supports mutual authentication by using server certs and Microsoft's Actiev Directory to auth a client's password
- LEAP is proprietary to Cisco-based networks
# 19.4 LDAP and Kerberos
- **Lightweight Directory Access Protocol**: is a database used to centralize info about clients and objects on the network
- On ports 389 and 636 (unencrypted/encrypted)
- **Active Directory** is Microsoft's version
- **Kerberos**: an auth protocol used by Windows to provide two-way auth using a system of tickets
	- User contacts domain controller when they log in, which acts like the key distribution center (KDC)
	- The KDC will offer the domain controller a Ticket-granting ticket (TGT) if it's successful, which the client can use any time it needs to access resources
	- Runs on port 88
	- Domain controller can be a single point of failure
# 19.5 Remote Desktop Services
- **Remote Desktop Protocol**: (RDP) Microsoft's proprietary protocol that allows admins and users to remotely connect to another coputer via a GUI
	- Doesn't provides encryption, but not authentication natively
	- Port 3389
- **Virtual Network Computing**: Cross-platform version of the RDP for remote user GUI access
	- Requires a client, server, and protocol be configured
	- Port 5900
# 19.6 Remote Access Service
- #### PAP
	- Used to provide authentication but is not considered secure since it transmits the login credentials unencrypted (in the clear)
	- Old protocol, so little security in mind
		- Didn't even encrypt user creds when authentication was occurring
- #### CHAP
	-  **Challenge Handshake Authentication Protocol**: used to provide authentication by using the user's password to encrypt a challenge string of random numbers
	![[chap.png]]
	- Microsoft's version of CHAP is MS-CHAP
- #### EAP
	- Mentioned earlier
- PAP and CHAP used mostly with dial-up
# 19.7 VPN
- Allow end users to create a tunnel over an untrusted network and connect remotely and securely back into the enterprise network
- Used often by teleworkers (client-to-site or remote access)
- Site-to-site VPNs use the internet as the connector between two sites, as opposed to a lease line, which can be expensive
	- Both routers on this connection possess keys
- Rely on two different tunneling protocols: point-to-point and layer 2. 
- **VPN Concentrator**: a specialized hardware device that allows for simultaneous VPN connections for remote workers
- **Split tunneling**: a remote worker's machine diverts internal traffic over the VPN but external traffic over their own internet connection.
	- Efficient when considering bandwidth, but opens an alternative path to the internet, inheriting all risks
	- Use proper configs and network segmentation to do this
# 19.8 RADIUS vs TACACS+
- **Remote Authentication Dial-In User Service**:  Provides centralized admin of dial-up, VPN, and wireless authentication services for 802.1x and the EAP
	- Runs on app layer (layer 7)
	- Ensures AAA
	- Uses UDP for its connection
	- Port on 1812 for authentication, 1813 for accounting (sometimes, 1645/1646)
- TACACS+ is a proprietary version of RADIUS
	- A bit slower because it operates over port 49 on TCP
	- Independently conducts AAA
	- Supports all network protocols
# 19.9 Summary
- **802.1x**: IEEE standard that defines Port-based Network Access Control and is a data link layer authentication technology used to connect 
- **LDAP** App layer protocol for accessing and modifying directory services data
- **Kerberos**: Authenticaion protocol in Windows to identify clients to a server using mutual auth
- **Challenge Handshake Protocol (CHAP)**: Auth scheme that is used in dial-up connections
- **Remote Access Services (RAS)**: Service that enables dial-up and VPN connections to occur from remote clients
- **RADIUS** is a centralization admin system for dial-up, VPN, and wireless authentication that uses ports 1812/1813, 1645/1646 (both UDP)
- **TACACS+**: Cisco's proprietary version of RADIUS that provides separate authentication and authorization functions over port 49(TCP)
# 19.10 Authentication Attacks
- **Man-in-the-Middle**: an attack where the attacker sits between two communicating hosts and transparently captures, monitors, and relays all communication between the hosts
	- **MitB** is a variation of this attack that intercepts API calls between the browser process and its DLLs
- Password cracking is a common and "fun" task. 
	- Passwords are usually hashed w MD5, SHA1, SHA256, etc.
	- To mitigate this, look at audit logs and consider restricting the number or rate of longon attempts
- **Password spraying**: brute force attack in which multiple user accounts are tested with a dictionary of common passwords
- **Credential Stuffing**: brute force attack in which stolen user account credentials are tested against multiple websites
- **Broken Authentication**: A software vulnerability where the authentication mechanism allows an attacker to gain entry
- Weak passwords, password reset methods, session hijacking, and credential exposure are all causes of these types of attacks