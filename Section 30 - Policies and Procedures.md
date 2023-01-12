# 30.1 Policies and Procedures
- Governance provides a comprehensive security management framework
- **Policies**: defines the role of security in an organization and establishes the desired end state of the security program
	- These are very broad
	- **Organizational Policies**: provide general direction and goals, a framework to meet the business goals, adn define the roles/responsibilities/terms
	- **System-specific policies**: address the security eneds of a specific tech, app, network, or computer
	- **Issue-specific policies**: built to address a specific security issue, such as email privacy, employee termination procedures, or other specific issues
	- Policies may be regulatory, advisory, or informative
- Standards are used to implement a policy in an org
- **Baseline**: reference points which are documented as a method of comparison during an analysis conducted in the future
- Guidelines are used to recommend actions
- **Procedures**: detailed step-by-step isntructions that are created to ensure personnel can perform a given action
- POLICIES ARE GENERIC, PROCEDURES ARE SPECIFIC

# 30.2 Data Classifications
- Category based on the value to an org and the sensitivity of the info if it were disclosed
	- **Sensitive data**: any info that can result in a loss of security or advantage to a company if accessed by unauthorized users
- Commercial businesses and government use different classification systems
- **Public data**: has no impact to the company if released and is often posted in the open-source environment
	- Sensitive data might have a minimal impact if released
- **Private data**: contains data that should only be used internally
- **Confidential data**: highest classification level that contains items such as trade secrets, intellectual property, source code, etc.
- Government classifications:
	- **Unclassified**
		- Can be released to the public
	- **Sensitive but Unclassified**
		- Items that wouldn't hurt national security but could impact those whose data is contained in it
	- **Confidential**
		- Data that could seriously affect the government if exposed
	- **Secret**
		- Data that could seriously damage national security if disclosed
	- **Top Secret**
		- Could gravely damage national security if it were known to those who are not authorized for this level of info
- Data should NOT be stored forever

# 30.3 Data Ownership
- Process of ID-ing the person responsibile for CIA and privacy of information assets
- #### Data Owner
	- An executive role with ultimate responsibility for maintaining the CIA of information
	- Responsible for labeling this asset and ensuring it is protected accordingly
- #### Data Steward
	- Focused on the quality of the data and its associated metadata
- #### Data Custodian
	- Handles the management of the system on which the assets are stored
- #### Privacy Officer
	- Oversight of any PII/SPI/PHI assets managed by the company

# 30.4 Personally Identifiable Info (PII) and PHI
- **PII**: piece of data that can be used either by itself or in combination with other pieces to ID a single person
	- Can include full name, driver's license, DoB, PoB, biometric data, financial account numbers, and social media handles
	- Verify with your legal team what is considered PII
-  **Privacy Act of 1974**: affects US government computer systems that collects/stores/uses/disseminates PII
- **Health Insurance Portability and Accountability Act (HIPPA)**: affects healthcare providers, facilities, insurance companies, and medical data clearing houses
- **Sarbanes-Oxley (SOX)**: affects publicly-traded US corporations and erquires certain accounting methods and financial reporting requirements
- **Gramm-Leach-Bliley Act (GLBA)**: affects banks, mortgage companies, loan offices, insurance companies, investment companies, and card providers
- **Federal Information Security management (FISMA) Act of 2002**: requires each agency to develop, document, and implement agency-wide info systems security program to protect data
- **Payment Card Industry Data Security Standard (PCI DSS)**: a contractual obligation
- **Helo America Vote Act (HAVA) of 2002**: provides regulations that control security, C and I of the personal info collected, stored, or processed during elections/votes
- SB 1386 requires any business that stores personal data to disclose a breach

# 30.5 Legal Requirements
- Any info should consider how a compromise of it could threaten the CIA triad.
- Privacy vs. Security:
	- Security controls focus on the CIa attributes of the processing system
	- Privacy is a governance requirement for data that arises when collecting and processing personal info to ensure the rights of the subject's data
- Legal requirements will affect your corporate governance and policies in regards to privacy of your user's data
- **General Data Protection Regulation (GDPR)**: personal data cannot be collected, processed, or stored without the user's INFORMED consent
	- Provides the right for a user to withdraw consent, inspect, amend, or erase data held about them
	- Requires data breach notification within 72 hours
	- Data breaches can happen ACCIDENTALLY

# 30.6 Privacy Technologies
- **Deidentification**: methods and techs that remove ID-ing info from data before it's distributed
	- Often implemented as part of database design
- **Data masking**: a dID-ing method where generic or placeholder labels are substituted for real data while preserving the structure of the original data
- **Tokenization**: a dID-ing method where a unique token is subbed for real data
	- Allows for unique substitution
- **Aggregation/Banding**: a dID-ing technique where data is generalized to protect the people involved
- **Reidentification**: an attack that combined a dID-ed dataset with other data sources to discover how secure the dID-ing method used is

# 30.7 Security Policies
- Privacy policies govern the labeling and handling of data
- **Acceptable Use Policy (AUP)**: defines the rules that restrict how a computer, network, or other systems may be used
- **Change Management Policy**: defines the structured way of changing the state of a computer system, network, or IT procedure
- Separation of Duties is a preventative type of admin control
- **Job rotation**: different users are trained to perform the tasks of the same position to help prevent ID fraud that could occur if only one employee had the job
- **Onboarding/Offboarding Policy**: dictates what type of things need to be done when an employee is hired, fired, or quits
- **Due Diligence**: ensuring that IT infrastructure risks are known and properly managed
- **Due Care**: mitigation actions that an org takes to defend against the risks that have been uncovered during diligence
- **Due Process**: a legal term that refers to how an org must respect and safeguard personnel's rights

# 30.8 Vendor Relationships
- **Non-disclosure Agreement (NDA)**: between two parties that defines what data is considered confidential and cannot be shared outside of the relationship
	- Binding contract
- **Memorandum of Understanding (MOU)**: a non-binding agreement between two or more orgs to detail an intended common line of action
	- Can be between multiple orgs
- **Service-level Agreement  (SLA)**: agreement concerned with the ability to supoprt and respond tim problems within a given timeframe and continuing to provide the agreed upon level of service to the user
	- May promise up to 99.99% uptime
- **Interconnection Security Agreement (ISA)**: agreement for the owners and operators of the IT systems to document what technical requirements each org must meet
- **Business Partnership Agreement (BPA)**: conducted between two business partners that establishes teh conditions of their relationship
	- Can include security requirements

# 30.9 Disposal Policies
- Asset disposal occurs whenver a system isn't needed anymore
- **Deguassing**: exposes the HDD to a powerful magnetic field which causes written data to be wiped
- **Purging**: act of removing data in suc ha way that it cannot be reconstructed by any known forensic techniques
- **Clearing**: removal of data wit ha certain amount of assurance that it cannot be reconstructed
- Data remnants are big security concern
- Possible reuse of the device will influence the disposal method
- Five things to consider with disposal policies:
	1. What data needs to be disposed?
	2. Determine a storage location until disposal
	3. Analyze equipment to determine disposal - reuse, resell, or destruction
	4. Sanitize the device and remove all its data
	5. Throw away, recycle, or resell the device

# 30.10 IT Security Frameworks
- **Sherwood Aplpied Business Security Architecture (SABSA)**: risk-driven architecture
- **Control Objectives for Information and Related Technology (COBIT)**: a security framework that divides IT into 4 domains: Plan/Organize, Acquire/Implement, Deliver/Support, and Monitor/Evaluate
- **NIST SP 800-53**: control framework developed by the Department of Commerce
- International standard for infoSec requirements is the ISO-27000
- **Information Technology Infrastructure Library (ITIL)** is the de facto standard for IT service management

# 30.11 Key Frameworks
- **Center for Internet Security (CIS)**: concensus-developed secure config guideliens for benchmarks and prescriptive, prioritized, and simplified sets of security best practices
- **Risk Management Framework**: process that integrates security and risk amangement activities into the system development life cycle through an approach to security control selection and specification that considers effectiveness, efficiency, and constraints due to applicable laws, directives, orders, policies, standards, and/or regulations
- **Cybersecurity Framework (CSF)**: a set of indsutry standards and best practices created by NIST to help orgs manage cybersecurity risks
	- Identify, Protect, Detect, Respond, Recover
- **ISO 27001**: internation standard that details requiremetns for establishing, implementing, maintaining, and updating an information security management system (ISMS)
	- **27002**: provides best practices on infoSec controls for use by those responsible for initiating, implementing, or maintaining ISMS
	- **27701**: acts as a privacy extension to 27001 to enhance exisiting ISMS with additinoal requirements in accordance with improving Privacy Information Management System (PIMS)
	- **31000**: enterprise risk management that provides universally recognized paradigm for practitioners and companies employing risk management processes; replaces exisitng standards, methodologies, and paradigms that differed between industries
- **System and Organization Controls (SOC)**: a suite of reports produced during an audit which is used by service organizations to issue valdiated reports of internal controls over those information systems to the users of those services
	- **SOC 2**: Trust Services Criteria
	- **Type II**: addresses the operational effectiveness of the specified controls over a period of time (usually 9-12 months)
- **Cloud Security Alliance's Cloud Control Matrix**: provides fundamental security principles to help cloud vendors and assesses overall security risks of a cloud provider
- **Cloud Security Alliance's Reference Architecture**: set of tools that enable architects and risk management officials to leverage a common set of solutions that fulfill common needs. 
	- Through this, they can assess where their IT and cloud providers are in terms of security capabiltiies and can plan accordingly