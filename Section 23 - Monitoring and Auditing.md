# 23.1 Monitoring Types
- #### Signature-based
	- Network traffic is analyzed for predetermined attack patterns
- #### Anomaly-based
	- A baseline is established and any network traffic that is outside of the baseline is evaluated
- #### Behavior-based
	- Activity is evaluated based on the previous behavior of apps, executables, and the operating system in comparison to the current activity of the system
	- Problem: tends to result in a lot of false positives
- Methods maybe should be combined into a hybrid approach in some IDS?IPS systems
# 23.2 Performance Baselining
- **Baselining**: process of measuring changes in networking, hardware, software, and applications
	- This is going to define what normal is, allowing us to monitor for anomalies
- **Baseline reporting**: documenting and reporting on the changes in a baseline
- **Security posture**: risk level to which a system or other technology element is exposed
	- This will dictate the level at which you configure, update, patch, etc. a given device
- Focused on operation and functionality, so this isn't as concerned with security as other measures
	- i.e. investigating processor load: if it's higher, it may be indicative of malware
- `Perfmon.exe` is the Windows program for Performance Monitoring

# 23.3 Protocol Analyzers
- Used to capture and analyze network traffic
- **Promisicuous Mode**: network adapter is able to capture all of the packets on the network regardless of the destination MAC address of the frames carrying them
	- Use this mode to capture the most info
- **Non-promiscuous Mode**: network adapter can only capture packets addressed to itself directly
- **Port mirroring**: one or more switch ports are configured to forward all of their packets to another port on the switch (usually called a SPAN port)
	- If you can't configure a SPAN, use a **network tap**
	- When a SPAN port is being used, it's using a logical method to transfer traffic
	- Very intensive, can cause packet drop
- **Network tap**: a physical device that allows interception of the traffic between two points on the network

# 23.4 Simple Network Management Protocol (SNMP)
- TCP/IP protocol that aids in the monitoring of network-attached devices
- Incorporated into a network management and monitoring system
- **Managed devices**: computers and other network-attached devices monitored through the use of agents bya network maangement system
- **Agents**: software that is loaded on a managed devices to redirect info to the network management system
- **Network Management System**: software run on one or more servers to control the monitoring of network-attached devices and computers
![[nms.png]]
- **v1/v2**: insecure versions of SNMP due to the use of community strings to access a device
- **v3**: provides integrity, authentication, and DES encryption of the messages being sent over a network
	-  Over the network (in-band); via secondary network (out-of-band); ooB is more secure

# 23.5 Auditing
- Technical assessment conducted on applications, systems, or networks; detective control
- To conduct an audit manually, monitor:
	- Security logs
	- ACLs
	- User rights/perms
	- Group policies
	- Vuln scans
	- Written organizational policies
	- Interviewing personnel
- Built-in Linux/Windows auditing 

# 23.6 Logging
- **Logs**: data files that contain the accounting and audit trail for actions performed by a user on a device or network
- `/var/log` = log directory in Linux
- On Windows, **security**, **system**, and **application** logs should be audited
	- **Security logs**: logs the events such as successful and unsuccessful user logons to the system
	- **System logs**: logs the events such as a system shutdown and driver failures
	- **Application logs**: logs the events for the operating system and third-party applications
- To consolidate all the logs in a single repo, SYSLOG can be used
	- **SYSLOG**: a standard format used for computer message logging that allows for the separation of the software that generates messages, the system stores them, and the software that reports and analyzes them.
	- DHCP, DNS, auth server, client workstation can all send logs to a centralized monitoring system
	- Uses port 514 (UDP)

# 23.7 Log Files
- Important to reconstruct an event after it occurs
- **Log file maintenance**: actions taken to ensure the proper creation and storage of a log file, such as proper configuration, saving, backing up, securing, and encrypting of the log files
- Logs should be saved to a different partition or an external server
- **Overwrite events**: when a maximum log size is reached, the system can begin overwriting the oldest events in the log files to make room
- Logs should be archived and backed up to ensure they are available when required
- **Write Once Read Many**: Tech like a DVD-R that allows  data to be written only once but read unlimited times
	- If someone hacks into a server, they can't modify these logs

# 23.8 Security Information and Event Management (SIEM)
- Log review is a critical part of security assurance; look at them regularly
- A SIEM is a solution that provides real-time or near-real-time analysis of security alerts generated by network hardware and applications
- SIEMs help correlate events
- These solutions can be implemented as software, hardware appliances, or outsourced managed services
- To effectively deploy a SIEM:
	- Log all relevant events and filter out irrelevant material
	- Establish and document the scope of events
	- Develop use cases to define a threat
	- Plan incident responses for an event
	- Establish a ticketing process to track events
	- Schedule regular threat hunting
	- Providing auditors and analysts an evidence trail
- Popular SIEMs include: 
	- #### Splunk
		- Market-leading big data info gathering and analysis tool that can import machine-generated data via a connector or visibility add-on
		- Great for connecting lots of different data systems
		- Uses the search processing language to index through real-time and historical data
		- Can be installed locally or as a cloud-based solution
	- #### ELK/Elastic
		- Collection of free and open-source SIEM tools that provides storage, search, and analysis functions
		- Incoludes Elasticsearch, Logstash, Kibana, Beats
	- #### ArcSight
		- Log maangement and analytics software that can be used for compliance reporting for legislation and regulations like HIPPA, SOX< and PCI DSS
	- #### QRadar
		- Log management, analytics, and compliance reporting platform created by IBM
	- #### AlientVault/OSSIM
		- Originally developed by Alien Vault, now owned by AT&T
		- OSSIM can integrate other open-source tools, such as the Snort IDS and OpenVAS vuln scanner, and provide integrated web administrative tool to manage the whole security environment.
	- #### Graylog
		- Open-source SIEM with an enterprise version focused on compliance and supporting IT operations and DevOps

# 23.9 Syslog
- Protocol enabling different appliances and applications to transmit logs or event records to a central server
- Follows a client-server model and is the de factor standard for logging of events from distributed systems
- Runs on most OSes and network equipment using port 514 (UDP) over TCP/IP
- A syslog message contains a PRI code, a header, and a message portion
	- A PRI code is calculated from the facility and severity level of the data
	- A header contains the timestamp of the event and the hostname
	- The message portion contains the source process of the event and related content
- ORIGINAL DRAWBACK: 
	- Since syslog relied on UDP, delivery issues can be caused via congestion
	- Basic security like encryption and authentication are not included by default
- FIXES:
	- Newer implementations can use port 1468 (TCP) for consistent delivery
	- Use TLS to encrypt messages sent to servers
	- Newer implementations can use MD-5 or SHA-1 for authentication and integrity
	- Some newer implementations can use message filtering, automated log analysis, event response scripting, and alternate message formats
- Syslog can refer to the protocol, the server, or the log entries themselves

# 23.10 Security Orchestration, Automation, and Response (SOAR)
- Class of security tools that facilitates incident response threat hunting and security configuration by orchestrating automated runbooks and delivering data enrichment
- Primarily used for incident response
- **Next-gen SIEM**: security information and event monitoring system with an integrated SOAR. This allows you to:
	- Scan security/threat data 
	- Analyze it with machine learning
	- Automate data enrichment
	- Provision new resources
- **Playbook**: checklist of actions to perform to detect and respond to a specific type of incident
- **Runbook**: an automated version of a playbook that leaves clearly defined interaction points for human analysis
