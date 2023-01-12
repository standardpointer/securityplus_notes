# 8.1 Virtualization
 - Creation of a virtual resource
	 - Servers, desktops, file systems, drives, networks, etc.
- A **virtual machine** is a container for an emulated computer that runs an entire operating system
	- This includes all hardware virtualization needed for the guest OS
- **System Virtual Machine**: Complete platform designed to replace an entire computer and includes a full desktop/server operating system
- **Processor Virtual Machine**: Designed to only run a specific process or application, like a web browser or simple web server
- Virtualization has been on the rise for the past few years to reduce costs for physical equipment in data centers

# 8.2 Hypervisors
- Manages the distribution of the physical resources of a host machine (server) to the virtual machines being run (guests)
	- CPU, memory, drive space
- **Type I**: "bare-metal", runs natively on the installed machine.
	- i.e. Microsoft's Hyper-V, Citrix's XenServer, VMWare's ESXi, vSphere
- **Type II**: runs from within a normal operating system
	- VirtualBox, VMWare
- **"Type III"**: Containerization; a single OS kernel is shared across multiple VMs, but each machine receives its own user space for programs and data
	- Allows for rapid and efficient deployment of distributed applications
	- i.e. Docker, Parallels Virtuozzo, OpenVZ

# 8.3 Threat to VMs
- VMs are separated and segmented by default
- **VM Escape**: An attack that allows an attacker to break out of a normally isolated VM by interacting directly with the hypervisor
- **Elasticity**: allows for scaling up and down to meet user demands
- **Data remnants**: Contents of a VM that exist as deleted files on a cloud-based server after deprovisioning of a machine
- Privilege escalation can also be conducted upon VMs
- **Live migration** occurs when a VM is moved from one physical server to another over the network
- Important to note: containerization can be dangerous because if someone exploits the container, any VM shared by it will be affected

# 8.4 Securing VMs
- Uses many similar techniques for that of a physical server
- Update, patch, etc. VMs as needed. Make this a habit. Ensure that you're using proper patch management.
- Limit connectivity between the VM and the host
- Remove any unnecessary virtual hardware from VMs
	- By removing something as trivial as a virtual CD drive, you're reducing the attack surface
- **Virtualization Sprawl** occurs when virtual machines are created/deployed without much oversight from sysAdmins