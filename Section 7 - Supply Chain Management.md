# 7.1 Supply Chain Assessment
- Secure working in an insecure environment involves mitigating the risks of the supply chain
- An organization must ensure that every component (be it hardware, firmware, OS, drivers, etc.) should be consistent and tamper resistant to ensure a trusted computing environment
- #### Due Dilligence
	- A legal principle identifying a subject has used best practices or reasonable care when installing, configuring, and maintaining a system
		- Properly resourced cybersecurity program
		- Security assurance and risk management processes
		- Product support life cycle
		- Security controls for confidential data
		- Incident response and forensics assistance
		- General and historical company information 
	- Should apply to ALL suppliers and contractors
- A **trusted foundry** is a microprocessor manufacturing utility that is part of a validated supply chain (one where hardware does not deviate from its documented function)
	- The **trusted foundry program** (TDP) is 	operated by the Department of Defense (DoD)
- **Hardware Source Authenticity** ensures that hardware produced is tamper-free from trustworthy suppliers

# 7.2 Root of Trust
- **Hardware root of trust** is a cryptographic module in a system which endorses trusted execution and attests to boot settings and metrics
	- It scans boot metrics and core OS files to verify the digital signature, which can then be signed on a report
	- Most common root of trust is [[Section 4 - Security Applications and Devices|TPM]]
		- TPM includes a secure I/O, cryptographic processor, persistent and volatile memory
	- A TPM can be managed inside of Windows through the tpm.msc console or through group policy
- A **hardware security module** is an appliance for generating and storing cryptographic keys and is less susceptible to tampering and insider threats than software-based storage.
- **Anti-tampering** methods make it difficult for an attacker to alter the authorized execution of software
	- Anti-tamper mechanisms include a field programmable gate array (FPGA) and a physically unclonable function (PUF)

# 7.3 Trusted Firmware
- Firmware exploits give the attacker an opportunity to run code at the highest level of CPU privilege.
- #### UEFI
	- A type of system firmware supporting 64-bit CPU operation at boot, as well as full GUI and mouse operation, and better bbot security.
- #### Secure boot
	- A feature of UEFI that prevents unwanted processes from executing during the boot operation by checking signatures.
- #### Measure Boot
	- A UEFI feature that gathers secure metrics to validate the boot process in an attestation report
- #### Attestation
	- A claim that the data presented in the report is valid by digitally signing it using the TPM's private key
- #### eFUSE
	- A mean for software or firmware to permanently alter the state of a transistor on a computer chip
	![[Pasted image 20220319214616.png]]
- #### Trusted Firmware Updates
	- A firmware update that is digitally signed by the vendor and trusted by the system before it's used
- #### Self-encrypting drives
	- A drive in which the controller can automatically encrypt data that's written to it

# 7.4 Secure Processing
- A mechanism for ensuring the confidentiality, integrity, and availability of software code and data as it is executed in volatile memory
- **Processor security extensions** are low-level CPU changes and instructions that enable secure processing.
	- AMD: Secure Memory Encryption (SME), Secure Encrypted Virtualiaztion (SEV)
	- Intel: Trusted Execution Technology (TET), Software Guard Extensions (SGX)
- **Trusted Execution** are a CPU's security extensions invoke a TPM and secure boot attestation to ensure that a trusted operating system is running
- A **secure enclave** is an extensions that allow a trusted process to create an encrypted container for sensitive data
- An **atomic execution** is an operation that should only be performed once or not at all, such as initializing a memory location
- **Bus encryption** ensures that data is encrypted prior to being placed on a data bus. However, we need to make sure that the other bus is trusted, as well.