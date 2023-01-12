	# 28.1 Preparing For The Worst
- Redundancy usually refers to when you have something extra or unnecessary
- However, it helps ensure fault-tolerance to continue operations
- **Single Point of Failure**: the individual elements of a system that would cause the whole system to fail if they failed

# 28.2 Redundant Power
- **Redundant PSU**: an enclosure that provides two or more complete PSUs
- RPSUs mitigate a single point of failure
- **Surge**: an unexpected increase in the amount of voltage provided (in the US, above 120v)
- **Spike**: a short transient in voltage that can be due to a short circuit, tripped breaker, outage, or lightning
- **Sag**: An unexpected decrease in the amount of voltage provided
- **Brownout**: when voltage drops low enough that some electronics will shut off
- **Blackout**: total loss of power for a long time

# 28.3 Backup Power
- **UPS**: combines the functionality of a surge protector with a battery backup
- **Backup generator**: emergency power system used when there is an outage of regular grid power

# 28.4 Data Redundancy
- **Redundant Array of Independent Disks (RAID)**: allows the combination of multiple physical hard disks into a single logical HDD that is recognized by the OS
	- **0**: provides data striping across multiple disks to increase performance
	- **1**: provides redundancy by mirroring the data identically on two hard disks.
		- Least amount of downtime; great fault tolerance
	- **5**: provides redundancy by striping data and parity data across the disk drives
		- Requires at least 3 drives
		- If one drive fails, the data is rebuilt on another drive.
	- **6**: modded RAID5. Provides *double* parity
		- Requires at least 4 drives
	- **10**: creates a striped RAID of two mirrored RAIDs (combined 1 and 0).
		- Requires at least 4 disks
		- Fast like 0, redundant like 1
	- **Fault-resistant**: protects against the loss of the array's data if a single disk fails (1, 5)
	- **Fault-tolerant**: protects against the loss of teh array's data if a single component fails (1, 5, 6)
	- **Disaster-tolerant**: provides two independent zones with full access to the data (10)

# 28.5 Network Redundancy
- Focused on ensuring that network remains up
- i.e. in a server with 5 network cards and 4 installed cables, they can be split into groups:
	- 1 single card and 4 redundant cards
	- The 4 can combined throughput

# 28.6 Server Redundancy
- **Cluster**: two or more servers working together to perform a particular job function
- **Failover cluster**: a secondary server can take over the function when the primary one fails
- **Load-balancing cluster**: servers are clustered in order to share system resources
	- Used to combine resources to crack passwords and for busy servers

# 28.7 Redundant Sites
- **Hot site**: a near duplicate of the original site that can be up and running within minutes
- **Warm site**: has computers, phones, and server, but might require some config before users can start working
- **Cold site**: a site that has tables, chairs, bathrooms, and some technical items like cabling

# 28.8 Data Backup
- Crucial to disaster recovery
- Types of backups:
	- **Full**: all of the contents are a drive are backed up
	- **Incremental**: only conducts a backup of data that has changed since the last full or incremental backup
	- **Differential**: only conducts a backup of data that has changed since the last FULL backup

# 28.9 Tape Rotation
- #### 10 Tape Rotation
	- Each tape is used once per day for two weeks and then the entire set is reused
	- After 2 weeks, no backups
- #### Grandfather-Father-Son
	- Three sets of backup tapes
	- Son: Daily; Father: Weekly; Grandfather: Monthly;
- #### Towers of Hanoi
	- Three sets of backup tapes (like GFS) that are rotated in a more complex system
	- First tape is used every second day, second is used every fourth, third is used every eighth
- **Snapshot Backup**: primarily used to capture the entire OS image including all apps and data
	- Commonly used with virtualized systems

# 28.10 Disaster Recovery Plan
- Development of an organized and in-depth plan for problems that could affect the access of data or the org's building
- DRP should be written down, policies should be created
- These criteria can include:
	- **Contact info**
	- **Impact Determination**
	- **Recovery Plan**
	- **Business Continuity Plan**
	- **Copies of Agreements**
	- **Disaster Recovery Exercises**
	- **List of Critical Systems and Data**

# 28.11 Business Impact Analysis
- A systematic activity that identifies organizational risks and determines their effect on ongoing, mission critical operations
- Governed by metrics that express system availability
- #### Maximum Tolerable Downtime
	- Longest a business can be inoperable without causing irrevocable business failure
	- Each organization and business process can have its own MTD
	- Sets upper limit on the recovery time that system and asset owners need to resume operations
	- What is our MTD for support services?
- #### Recovery Time Objective
	- How long it takes after an event to get back to normal business
- #### Work Recovery Time
	- How long in addition to RTO for individual systems to perform reintegration and testing of a restored or upgraded system following an event
- #### Recovery Point Objective
	- The longest that an organization can tolerate lost data being unrecoverable
- MTD and RPO help to determine which business functions are critical and prepare accordingly
- Designing disaster recovery and continuity of operations plans requires an understanding of availability and reliability
- Disasters can be internal or external
- **Mean Time Between Failures**: Measures teh average time between failures of a device