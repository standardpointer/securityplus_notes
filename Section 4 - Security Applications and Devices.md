# 4.2 Software firewalls
- **Personal firewalls**, also known as a **host-based firewall**  protect a single user from unwanted internet traffic
	- These firewalls apply a set of rules or policies that dictate which kind of traffic can be received.
- Most operating systems have their own standard firewalls
	- Windows Firewall
	- PF and IPFW (MacOSX)
	- iptables (Linux)
- It's best to use both a personal software firewall as well as a hardware network firewall to provide two layers of security, strengthening your defense in-depth.

# 4.3 IDS
- An **IDS**, or intrusion detection system, monitors a system or network and analyzes the data passing through it in order to identify an incident or attack.
	- HIDS (host-based), NIDS (Network-based
- #### Host-based
	- Usually a piece of software that sits and logs everything that may be a suspicious.
- #### NIDS
	- A copy of all traffic to your company goes through this network switch which will log anything suspicious.
- **Signature-based** detection alerts users based on a string of bytes within a piece of code.
- **Policy-based** detection relies on a specific security declaration (i.e. a company might enforce a "no Telnet" rule).
- **Anomaly-based** detection analyzes current traffic and an established baseline and triggers an alert if it falls outside of the statistical mean
- **True positive** means that a malicious attack is identified as such. Similarly, a **true negative** describes a legiitmate process or activity as such.
- A **false positive** is the opposite of a true negative. Similarly, a **false negative** is the opposite of a true positive.
- An IDS can only ALERT and LOG suspicious activity. To further act on protection, you'll have to invest in an IPS (intrusion prevention system).
- HIDS are used to recreate the events after an attack has occurred.

# 4.4 Pop-ups
- Pop-ups are generally annoying, but they're not inherently malicious. Websites may require pop-ups to be enabled in order for their core services to function
- Malicious attackers can purchase ads (pay-per-click model) through these networks.
- Adblock extensions can be used, but websites may have been designed to not show content if ads are blocked
- Content filters are used in workplaces, schools, etc., to block "waste of time" or pornographic sites.

# 4.5 Data Loss Prevention
- Monitors the data of a system while in use, in transit, or at rest, detecting attempts to steal the data
- An **endpoint DLP system** is a software-based client that monitors the data being used on a computer and can stop a file transfer or alert an admin of the occurrence
- A **network DLP system** is a software or hardware-based solution installed on the edge of a network to detect data in transit
- A **storage DLP system** is software installed in data centers to inspect the data at rest
- A **cloud DLP system** is SaaS that protects data being stored in cloud services.

# 4.6 Securing the BIOS
- BIOS, or Basic Input Output System, is firmware that provides instructions for the system on how to accept input and send output.
	- Most modern systems have a Unified Extensible Firemware Interface (UEFI). For most situation, especially in this exam, these will be used interchangably.
- The BIOS can control boot order, processor clock speeds, memory frequencies, etc.
- Flash your BIOS, use a BIOS password, configure the boot order, and disable any unused ports or devices, and enable secure boot protocols.

# 4.7 Securing Storage Devices
- It's good practice to always encrypt files on external storage devices
- #### Removable Media Controls
	- Technical limitation placed on a system in regards to having the utilization of USB storage devices and other removable media
	- Denying read access from USB drives and denying write access to CDs/DVDs
- #### NAS (Network Attached Storage) and SAN (Storage Area Network)
	- NAS devices often implement RAID arrays to ensure high availability and reliability
	- SANs are designed specifically to perform block storage functions that consist of NAS devices
	- Secure your device by using data encryption, secure authentication, and logging NAS access

# 4.8 Disk Encryption
- Encryption scrambles data into unreadable information, only available to the user with the proprietary key.
 - A **self-encrypting drive** (SED) is a storage device that performs whole disk encryption by using embedded hardware. Since these disks are expensive, most people use software-based disk encryption (i.e. MacOSX's FireVault or Windows' BitLocker).
 - **Trusted Platform Module** (TPM) is a chip on the motherboard that contains an encryption key. If a motherboard doesn't have TPM, a USB drive can be used for the key.
 - **Advanced Encryption Standard** (AES) is a symmetric key encryption (128-bit, 256-bit). 
 - Encryption enhances security at the cost of performance
 - To mitigate the performance costs of full-disk encryption, users can have **File-level encryption** (i.e. Windows' EFS).
 - Users can also have hardware-based encryption, known as the **hardware security module**. The HSM describes physical media that act as a secure cryptoprocessor during the encryption process

# 4.9 Endpoint Analysis
- Conducting monitoring, analysis, and logging on endpoints (i.e. phones, laptops, user computers)
- #### Anti-virus
	- Software capable of detecting and removing virus infections and other types of malware (i.e. worms, trojans, rootkits, spyware, adware, nmaps, cracks, DoS tools, etc.)
- #### Host-based intrusion detection/prevention systems (HIDS/HIPS)
	- A type of IDS or IPS that monitors computers for unexpected behavior or drastic changes to the system's state on an endpoint.
	- These will usually use signature-based detection or file system integrity monitoring.
- #### Endpoint Protection Platforms (EPP)
	- A software agent and monitoring system that performs multiple security tasks such as anti-virus, HIDS/HIPS, firewall, DLP, and file encryption
	- Magic Quadrant at Gartner shows the biggest players in the EPP market.
- #### Endpoint Detection and Response (EDR)
	- A software agent that collects system data and logs for analysis by a monitoring system to provide early detection of threats. More focused on behavioral or anomaly analysis.
- #### User and Behavior Analytics (UEBA)
	- A system that can provide automated identification of suspicious activity by user accounts and computer hosts.
	- Focused on analytics, so a lot of data that needs to be processed, so these services rely on AI and machine learning. Microsoft and Splunk are great resources to point to