# 21.1 Risk Assessments
- Threats are generally external and beyond your control
	- Vulnerabilities are completely WITHIN your control
![[riskvenn.png]]
- What can we do about the threat we've identified?
- Risk management is used to MINIMIZE the likelihood of a negative outcome from occurring
- **Risk avoidance**: A strategy that requires stopping the activity that has risk or choosing a less risky alternative
- **Risk transfer**: A strategy that passes the risk to a third party
- **Risk mitigation**: A strategy that seeks to minimize the risk to an acceptable level
- **Risk acceptance**: A strategy that seeks to accept the current level of risk and the costs associated with it if the risk were realized
- **Residual risk**: Ths rish remaining after trying to avoid, transfer, or mitigate it.
- Four steps:
	1. Identify all assets
	2. Identify vulnerabilities
	3. Identify threats
	4. Identify the impact
# 21.2 Qualitative Risk
- Qualitative analysis uses intuition, experience, and other methods to assign a relative value to a risk
- Experience is critical in this analysis
	- Using subjective experience is extremely useful in prioritizing various risks
	- Usually comparing probability to impact
# 21.3 Quantitative Risk
- Quantitative analysis can calculate a direct cost for each risk
- **Magnitude of impact**: An estimation of the amount of damage that a negative risk might achieve
- *Below are common calculations used*
- #### Single Loss Expectancy (SLE)
	- Cost associated with the realization of each individualized threat that occurs
	- ASSET VALUE \* EXPOSURE FACTOR
	- i.e. a server that costs $10k and is hit with a threat that reduces its efficiency to 20% means that the SLE = 10,000 \* 0.20
- #### Annualized Rate of Occurrence (ARO)
	- Number of times per year that a threat is realized
- #### Annualized Loss Expectancy (ALE)
	- Expected cost of a realized threat over a given year
	- SLE \* ARO
- i.e. is it worth spending $200k to ensure that your server room never loses power? Let's see the ROI of that. If the ALE is $6k because you lost power 3 times a year, it would take over three decades to get that return.
- There are hybrid qual/quant approaches that are commonly used
# 21.4 Methodologies
- **Security Assessment**: Verify that the organization's security posture is designed and configured properly to help thwart different types of attacks
- Assessments might be required by contracts, regulations, or laws
- They can be active or passive
	- **Active** use more intrusive techniques (scanning, hands-on testing, probing, etc.) on a network to determine vulnerabilities.
	- **Passive** use open-source info and passive collection/analysis on a network, as well as other unobtrusive methods without making direct contact with targeted systems
		- They are limited in the detail they can find, though
# 21.5 Security Controls
- Methods implemented to mitigate a particular risk
- **Physical controls**: are any security measure that are designed to deter or prevent unauthorized access to sensitive information or the systems that contain it
	- Locks, fences, etc.
- **Technical controls**: are safeguards and countermeasures used to avoid, detect, counteract, or minimize security risks to our systems/data
	- Encryption, MFA, 
- **Administrative controls**: are focused on changing the behavior of people instead of removing the actual risk
	- Policies, mandatory vacations, education
- NIST categories are management, operational, and technical
	- **Management controls**: are security controls that are focused on mdecision-making and the management of risk
	- **Operational controls**: focused on the things done by people
	- **Technical controls**: logical controls that are put int oa system to help secure it
- **Preventative controls**: installed before an event happens and are designed to prevent something from occurring
	- i.e. RAID, UPS
- **Detective controls**: used during the event to find out whether something bad might be happening
	- Any sort of surveillance/logging device
- **Corrective controls**: used after an event occurs
	- deploying backups after data loss
- A single control can be categorized into multiple types or categories
- **Compensating control**: used whenever you can't meet the requirement for a normal control
	- Residua risk not covered by this control is an accepted risk
# 21.6 Types of Risk
- #### External
	- Produced by non-human source and are beyond human control
	- i.e. wildfires hurricanes, blackouts and brownouts, hackers
- #### Internal
	- Formed within the organization, arise during normal operations, and are often forecastable
	- i.e. server crashes
- #### Legacy system
	- An old method, technology, computer system, or application which includes an outdated computer still in use
	- i.e. ICS and SCADA networks are running on legacy systems
- #### Multiparty
	- Concentration of multiple systems or organizations with each bringing their own inherent risks
		- i.e. when two companies merge and combine infrastructure
- #### IP theft
	- Business assets and property being stolen from an organization in which economic damage, loss of competitive edge, or slowdown of growth occurs
		- mitigations include data protection systems
- #### Software compliance and licensing
	- Company not being aware of what software or components are installed within its network
