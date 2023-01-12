# 1.3 Overview of Security
- Security != Convenience
	- Often, to make services more secure, sacrificing some convenience is a must.
	- **Information Security**: Act of protecting data and information from unauthorized access, unlawful modification, and disruption, disclosure, corruption and destruction.
	- **Information Systems Security**: Act of protecting systems that hold and process critical data

# 1.4 CIA Triad
- **Confidentiality**: Ensuring that information that has not been disclosed to unauthorized personnel
	- Encryption is a premier example of confidentiality: Only users with the keys associated with the message (in a secure algorithm) will be able to access the data.
	- Logging into a bank account, your password is the key
- **Integrity**: Ensuring that information has not been modified or altered without proper authorization
	- Say you're logged into your bank account: This means that you've passed the confidentiality. However, you can't just change your bank account balanced. Only banks and authorized institutions can do that.
	- Hashes are most associated with integrity
- **Accessibility**: Information is to be stored, accessed, or protected at all times.
	- If you've passed the confidentiality and integrity tests for your bank account, you still may not be able to reach the bank's page.

# 1.5 AAA
- **Authentication**: When an identity is established with proof and confirmed by a system
- 5 ways:
	- Something you know (password, username)
	- Something you have (token, driver's license, card)
	- Something you do (way you speak, voice recognition)
	- Somewhere you are (GPS data)
- **Authorization**: Occurs when a user is given access to a certain piece of data or certain areas of a location.
- **Accounting**: Tracking of data, computer usage, and network resources
	- Logfiles
	- This is how you can accrue non-repudiation: someone can't say they didn't send something, for example, because you have irrefutable proof
# 1.6 Security Threats
- **Malware**: Short-hand for malicious software	
- **Unauthorized access**: Occurs when data is accessed without consent of the owner
- **System failure**: When a system or application fails.
- **Social Engineering** Act of manipulatng users into submitting personal data.
	- Phishing, for example
# 1.7 Mitigiating threats
- **Physical controls**: Alarms systems, locks, cameras, ID cards, guards
- **Technical controls**: Encryption, network authentication, smart cards, etc.
- **Administrative controls**: Policies, procedures, security awareness training, disaster planning
	- User training is the most cost-effective security controls
# 1.8 Hackers
- **White-hat/Black-hat**: Usually independent users trying to break into a system. White-hats are employed by companies to test and triage vulnerabilitiy exploitation on their services. Black-hats are malicious and are unemployed by these companies.
- **Gray hats**, while accessing into systems unauthorized, are usually looking to find vulnerabilities and report them to companies, similar to white-hacks. They are not employed by this company.
- **Blue-hat**: They are not employed by the company, but are given authorization to break into their systems.
	-	Bug bounties, for example
- **Elite**: Hackers whom specialize in zero-days, often developing their own tools (1/10,000).
# 1.9 Threat Actors
- **Script kiddies**: Novice hackers or those with limited skills, attempting to hack into services. While this can swing into white hat or black hat territory, most of this is done out of curiosity.
- **Hacktivists**: Prompted to hack by a call for social change.
	- Anonymous
- **Organized Crime**: motivated by money, specializiing in ransomware. These groups are well-funded and highly sophisticated
- "**Advanced Persistent Threats (APT)**: Highly trained and funded groups of hackers, often funded by nation-states with covert / open-source intel at their disposal.
	- Russia hacking US elections, for example
# 1.10 Threat Intelligence and Sources
- **Timeliness**: Property of an intelligence source that ensures it is updated
- **Relevancy**: Property of an intelligence source that ensures it matches the use case intended for it.
- **Accuracy**: Property of an intelligence source that ensures it produces effective results.
	- Ensuring correct results means avoiding false positives and mitigating them as soon as possible, especially when working with automatic tools.
- **Confidence levels**: Property of an intelligence source that ensures it produces qualified statements about reliability.
	- i.e. 	MISP uses the Admiralty scale for grading data and estimative language.
		- Source reliability (A-F), and information content (1-6)
- #### Where can you get this intelligence?
	- **Proprietary**: Threat intelligence is provided as a commercial service, where updates and research are based upon a subscription (SaaS model).
	- **Closed-source**: Data that is derived from the provider's own research and analysis efforts
		- i.e. honeynets, anonymous customer device data
	- **Open-source**: Data that is available without a subscription, could include data similar to what a proprietary service can offer.
		-  Moreover, it can have other services such as a malware signature database.
		-  US-CERT, UK's NCSC, AT&T Security (OTX), VirusTotal, MISP, Spamhaus, Sans ISP Suspicious Domains
	- Most of these feeds are EXPLICIT knowledge. However, there's also IMPLICIT knowledge. 
	- **Open-source Intelligence (OSINT)**: Methods of obtaining information about a person or organization through the public record.
# 1.11 Threat Hunting
- Threat hunting is PROACTIVE, not REACTIVE.
- This shouldn't be confused with penetration testing, because existing data from your systems are being analyzed, you're not trying to exploit something.
- Establish a **hypothesis** by looking at the likelihood and impact an attack can impose upon your systems.
- Profiling Threat Actors and Activities: Involves the creation of scenarios that show how an intruder can attack our systems and what their motive is. Focus on their tactics, techniques, and procedures (TTP)
- Threat hunting relies upon consistently running security tools, particularly through a security information event management system (SIEM). 
- Important to assume that existing rules have failed.
- #### What we can do:
	- Analyzing network traffic 
		- this will give us the names of potentially suspicious hosts
	- Analyze the executables process list
		- there might be a rogue application running quietly on a system.
	- Analyze other hosts
		- is this user evading other hosts through different methods?
	- Identify how the malicious process was executed
		- use tactical approaches to handle this threat that's surpassed automatically enforced rules.
- #### Goals
	- Imrpove detection capabilities
		- Rewriting rules, detection algorithms, etc.
	- Integrated intelligence
		- Adding this external knowledge gained from the threat and integrating it with already existing databases
	- Reduce attack surfaces
	- Block attack vectors
	- Identify critical assets
		- Knowing what data is most-wanted by hackers, and learning how to mitigate attacks targeting this material.

# 1.9 Attack Frameworks
- #### Lockheed Martin Kill Chain
	- developed by Lockheed Martin, and describes the stages of a threat actor's progression during a network intrusion
	- 7 steps:
		- **Reconnaissance**
			- What methods should be used to complete the other phases of the attack?
		- **Weaponization**
			- Couples payload code that will enable access with exploit code that will use a vulnerability to execute on the target system
		- **Delivery**
			- The attacker identifies a vector by which to transmit the weaponized code to the target environment
		- **Exploitation**
			- The weaponized code is executed on the target system
				- i.e. when a user falls for a phishing email, clicking the link causes exploitation
		- **Installation**
			- The exploitation enables the weaponized code to run a remote access tool and achieve persistence on the target system
		- **Command and Control**
			- Weaponized code establishes an outbound channel to a remote server that can control this access tool and possibly download additional tools to progress the attack. Essentially, you own the system from here.
		- **Actions on Objectives**
			- The attacker will now pursue their goal.
	- **Kill-chain analysis** can be used to identify a defensive course-of-action matrix to counter the progress of an attack at each stage.
- #### MITRE ATT&CK FRAMEWORK
	- A knowledge base maintained by the MITRE Corporation for listing and explaining specific adversary tactics, techniques, and common knwoledge or procedures.
	- Unlike the linear structure of the Lockheed Martin Kill Chain, the ATT&CK Framework is matrix-based.
	- The **pre-ATT&CK** tatctics matrix aligns to the reconnaissance and weaponization phases of the kill chain
- #### Diamond Model of Intrusion Analysis
	- Analyzing cybersecurity incidents and intrusions by exploring the relationships between four core features: adversary, capability, infrastructure, and victim
	- Mapped like a diamond: 
	 ![[mitre.png]]
	 - E = \[\(Adversary, C$^{adversary}$), (Capability, C$^{capability}$)]