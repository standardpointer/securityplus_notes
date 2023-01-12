# 13.1 Cloud Computing
- A way of offering on-demand services that extend the traditional capabilities of a computer or network
- Relies on virtualization to gain efficiencies and cost savings
	- One of the biggest benefits to cloud computing is this dynamic provisioning of resources
- **Hyperconvergence** allows providers to fully integrate the storage, network, and servers
- **Virtual Desktop Infrastructure** allows a cloud provider to offer a full desktop operating system to an end user from a centralized server
- **Secure Enclaves** use two distinct areas that the data can be stored and accessed from to be processed by the proper resources.
	- Used by Azure
- **Secure Volumes** keep data at rest, secure from hackers. When it's needed, it's mounted and decrypted for use. 
	- Use by FireVault, BitLocker

# 13.2 Cloud Types
- #### Public
	- A service prodivder makes resources available to end users via the internet
- #### Private
	- A company creates its own cloud environment that only it can utilize
	- Used when security > cost
- #### Hybrid
	- Essentially, designed like a private cloud, but may use third-party resources much like a public cloud can
- #### Community
	- Resources and costs are shared among several different organizations who have common service needs

# 13.3 As a Service
- #### Software (SaaS)
	- Provides all the hardware, OS, software, and apps needed for a complete service to be delivered
	- Vendor: App/data/runtime/middleware/OS/Virtualization/Servers/Storage/Networking
- #### Infrastructure (IaaS)
	- Provides all the hardware, OS, software, and backend software needed in order to develop your own software or service
	- Customer: App/Data/Runtime/Middleware/OS
- #### Platform (PaaS)
	- Provides your organization with the hardware and software needed for a specific service to operate
	- Customer: App/Data
- ### Security (SECaaS)
	- Provides your organization with various types of security services without the need to maintain a cybersecurity staff
	- Anti-malware solutions were one of the first SECaaS products
	- Some solutions may not scan ALL the files on your system
	- Cloud-based vulnerability scans can better provide the attacker's perspective.
	- Your vulnerability data may be stored on the cloud provider's server
	- **Sandboxing** utilizes separate virtual networks to allow security professionals to test suspicious or malicious files
		- This allows dynamic analysis of malware to be conducted
	- i.e. when a company signs up for a content filter, their traffic is diverted through a VPN before reaching the internet. The service can then offer rules and whatnot
	- Identity Management, DLP, monitoring, access control, etc. can also be provided by these services

# 13.4 Cloud Security
- Need to realize that data might rest on shared servers
- **Collocated data** can become a security risk
- Configure, manage, and audit user access to virtualized servers
- Monitoring resources across resource paritions to make sure data is being processed efficiently and properly
- Utilizing the cloud securely requires good policies
- Data remnants may be left behind after deprovisioning when demand for the service is reduced.
	- This can be an  issue on shared servers

# 13.5 Defending Servers
- #### File Servers
	- Used to store, transfer, migrate, synchronize, and archive files for your organization
	- Monitoring, host-based IDS, encryption on resting data, DLP, and normal hardening should be used here
- #### Email Servers
	- Frequent target of attacks because of the data being held
	- i.e. Pop3, IMAP, SMTP for MacOS, Linux, and Windows for Exchange. This means that there could be at least three ports subject to attacks
- #### Web Servers
	- Should be placed in a DMZ
	- For Windows, Information Internet Services (IIS) server. For Unix, this is usually Apache
	- Log, monitor, patch, audit
- #### FTP Server
	- Specialized type of file server that is used to host files for distribution across the web
	- Might want anonymous FTP for software distribution
	- Might want secure for uploads/downloads
	- Force encrypted connection via TLS
	- Ports 20 and 21 are default, as well as UDP (unencrypted!)
- #### Domain Controller
	- A server that acts as a central repo of all the user accounts and their passwords for the network
	- Windows: Active Directory; Unix: LDAP
	- Primary target for privilege escalation and lateral movement attacks

# 13.6 Cloud-based Infrastructure
- Must be configured to provide the same level of security as a local solution
- **Virtual Private Cloud** (VPC): a private network sergment made available to a single cloud consumer within a public cloud
	- Provision virtual resources within a virtual service hosted on a public cloud
	- Get SOME private cloud security while reducing cost
- The consumer is responsible for configuring the IP address space and routing within the cloud
- Hosted via Google Cloud, AWS, Azure, etc., but are separated from other customers
- VPC is typically used to provision internet-accessible apps that need to be accessed from remote sites
- **On-premise** solutions maintain their servers locally within the network
- Many security products offer both cloud and on-premise based versions
- Consider compliance or regulatory limitations of storing data in a cloud-based security solution
- Be aware of vendor lock in

# 13.7 Cloud Access Security Broker (CASB)
- Enterprise management software designed to mediate access to cloud services by users across all sorts of devices
- SSO and other authorizations, scan malware/rogue devices, monitor/audit user activity, and mitigate data exfiltration
- Provide visibility into how clients and other network nodes use cloud services
- #### Forward Proxy
	- Security app or host positioned at the client network edge that forwads user traffic to the cloud network if the contents of that rtaffic comply with policy
		- i.e. this can be useful with younger children, whom will likely need to be monitored on the internet for a bit
	- Users can evade the pxoy and connect directly
- #### Reverse Proxy
	- App positioned on the cloud network edge and directs traffic to cloud services if the content complies with policies
	- This can only be used if the cloud app has proxy support
- #### API Access
	- Uses the broker's connections between the service and the cloud consumer
	- Dependent on the API supporting the functions that your policies demand

# 13.8 Application Programming Interface (API)
- Library of programming utilities used to enable software devs to access functions of another app
- Allow for the automated administration, management, and monitoring of a cloud service
	- i.e. FreshDesk is used at the instructor's training to collect and report student tickets. They also get questions from Udemy, which has its own API to gather data and create student tickets.
- **curl** is a tool to transfer data from or to a server, using one of the supported protocols (HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, DICT, TELNET, LDAP, FILE)

# 13.9 Function as a Service (FAAS) and Serverless
- Cloud service mdoel that supports serverless software architecture by provisioning runtime containers in which code is executed in a particular programming language
- **Serverless** is a software architecture that runs functions within virtualized runtime containers in a cloud rather than on dedicated server instances
	- Everything is deployed as a function or microservice
	- Netflix relies on AWS serverless environments to serve its cusomters
	- Eliminates the need to manage physical or virtual servers
	- Underlying architecture is managed by the cloud service provider
- Ensure that the clients accessing the services have not been compromised
- Orchestration is key

# 13.10 Cloud Threats
- #### Insecure API
	- An API must ONLY be used over an encrypted channel (SSL or TLS over HTTPS)
	- Data received by an API must go through rigorous server-side validation
	- Implement throttling/rate-limiting mechanisms to protect from a DoS
- #### Improper Key Management
	- APIs should use secure authentication and authorization such as Security Assertion Markup Language (SAML) or Open Authorization (OAuth)/OpenID Connect SSO (OIDC) before accessing data
	- Don't hardcode stuff in your source
	- Delete unnecesasry keys and regenerate new ones when moving to production environments
- #### Logging and Monitoring
	- SaaS may not supply access to log files or monitoring tools
	- Logs must be copied to non-elastic storage for long-term retention
- #### Unprotected Storage
	- Cloud storage containers are referred to as buckerts or blobs
	- Access control to storage is administered through container policies, IAM authorizations, and object ACLs
	- Wrong permissions may occur due to default read/write permissions left over from creation
	- Incorrect origin settings may occur when using content delivery networks
- **Cross Origin Resource Sharing (CORS) Policy** is a CDN policy that instruct the brwoser to treat requests from nominated domains as safe
	- Weak CORS policies expose the site to stuff like XSS