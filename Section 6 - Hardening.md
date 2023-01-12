# 6.1 Unnecessary Applications
- Hardening is all about minimizing vulnerabilities and exposure to threats
- A SysAdmin will employ **least functionality** in a company as a step towards ensuring hardening.
	- Process of configuring workstation or server to only provide essential applications and services
- Personal computers often accumulate unnecessary programs over time
- Utilie a secure **baseline** image when adding new computers
- Use the Microsoft System Center Configuration Management (SCCM) to focus on hardening

# 6.2 Restricting Applications
- **Application whitelisting** occurs when only applications that are allowed on the filtered list are able to be installed or executed on the OS. Non-permitted apps are blocked. An explicit "allow" list
	- This will need to be updated for each version of an operating system
- **Application blacklisting** occurs when applications on this filtered list aren't allowed to be installed on the machine; an explicit "deny" list
	- This is more difficult to manage because it needs to consider new iterations of malware
- Whitelisting and blacklisting can be centrally managed

# 6.3/6.4 Trusted Operations Systems/Updates and Patches
- ### Operating Systems
	- **Trusted Operating Systems** is an operating system that meets the requirements set forth by a government and has multilevel security.
		- i.e. Windows 7+, MacOS 10.6+, TrustedBSD, RedHat Enterprise Server
		- To be considered a trusted operating system, these OSes have to routinely update and patch.
		- You need to identify the current version and build prior to updating a system
- ### Updates and patches
	- #### Types of patches
		- A **patch** is a single problem fixing piece of software for an application or operating system
		- A **hotfix** can be described similarly. However, a hotfix does NOT entail rebooting your system after installing.
		- Over time, these terms are used interchangably.
	- #### Types of Updates
		- A **security update** is issued for a product-specific security related vulnerability
		- A **critical update** is issued for a specific problem addressing a critical, non-security  bug in a service/system
		- A **service pack** is a tested, cumulative grouping of patches/hotfixes/security updates/critical updates and possibly some feature designs or changes	
			- OS updates
		- A **Windows Update** is a recommended update to fix a noncritical problem that users have 

# 6.5 Patch Management
- Process of planning, testing, implementing, and auditing of sofware patches.
- Verify that it's compatible with your systems and plan for how you will test/deploy it
- Use the Microsoft Baseline Security Analyzer (MBSA).
- Always test a patch before automating its deployment
- Manually or automatically deploy the patch to all of your clients to implement it
- Larger organizations use servers to centrally manage patches
- Disable the wauservice (Windows update service) to prevent Windows Update from running automatically
- Audit client status after patch deployment. 

# 6.6 Group Policies
- Group Policy editors have rules that can include password complexity, blacklists or whitelists, account lockout policies, and other app restrictions
- Active Directory domain controllers have a more advanced GPE
- A **security template** is a group of policies that can be loaded through one procedure
- Using **Group Policy Objectives** (GPO) aid in the hardening of the operating system
	- Through this, new devices can be added to your network in bulk
- **Baselining** is the process of measuring changes in the software, hardware, or network environments.
	- These baselines establish what is normal so you can find deviations

# 6.7 File systems and hard drives
- Level of security for a system is affected by its file system type
- File system formats include **NTFS**, **FAT32**, **ext4**, and **HFS4+**
	- New Technology File System (NTFS) is the default file system format for Windows. It supports logging, encryption, and larger partition sizes/file sizes than FAT32	
	- Linux systems use ext4 and OSX uses APFS
- Using whole-disk encryption on your hard drives is helpful
- Hard drives eventually fail. However, there are a few measures to extend lifetime
	- Remove temporary files with a cleanup utility
	- Periodic system file checks
	- Defragmenting your hard drive
	- Backup all data
	- Use and practice restoration techniques
	- 