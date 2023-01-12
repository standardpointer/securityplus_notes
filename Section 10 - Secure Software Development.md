# 10.1 Secure Software Development
- **Software Development Life Cycle** (SDLC) is an organized process of developing a secure product throughout the lifetime of the project.
	- This is based on a **waterfall model** of information
		- Divides the cycle up into phases (i.e. preparation, requirements, analysis, design, etc.). Visually, these phases have the information step down from one to the next
		- Different organizations may call these phases different things or include/omit different phases entirely.
- ### Planning and Analysis
	- Goals of the project are determined and stakeholder needs are assessed, and all high level knowledge is understood
- #### Software/Systems  Design
	- Application or system is defined, outlined, and diagramed in detail. This primarily focuses upon IO
- #### Implementation
	- Code begins. Some debugging and testing will be held, but no formal stuff yet
- #### Testing
	- This is where the program is put through rigorous, standardized tests.
- #### Integration
	- Testing the e2e service so all portions of the project can communicate effectively and accurately.
		- i.e. if you develop a site which posts quiz questions for students, you need to integrate that quiz app with the server, the database which holds the questions, the network, etc.
- #### Deployment
	- Application or system is moved into production environment, consumers can begin to start using
- #### Maintenance
	- Bug fixes, patches, updates, etc. At this point, your organizational service desk will be focused on monitoring end-user report tickets.
- **Agile Development** occurs when software is developed in more time-sensitive windows or smaller increments to increase the adaptivity of the development process.
- **DevOps**: Software development and IT operations

# 10.2 SDLC Principles
- Developers should always remember the CIA triad (confidentiality, integrity, availability)
	- *Confidentiality* ensures authorized users only can access data
	- *Integrity* ensures that data is not modified or altered without permission
	- *Availability* ensures that data is available to authorized users when needed
- **Threat Modeling** helps prioritize vulnerability identification and patching
	- Additional resources can be delegated more efficiently this way
	- Make sure that threat modeling is conducted early, especially in the requirements or implementation phases
- #### Least Privilege
	-  users and processes should be run using the least amount of privilege necessary to perform a given function
- #### Defense-in-depth
	- Layering of security controls is more effective and secure than relying on a single control
- #### Never trust user input
	- Any input that is received from a user should undergo input validation prior to allowing it to be used by an application
- #### Minimize attack surface
	- Reducing the amount of code used by a program, eliminate unneded functionality, and require authentication prior to running additional plugins
- #### Create secure defaults
	- Default installations should include secure configurations instead of requiring an administrator or user to add in additional security
- #### Authenticity and integrity
	- Applications should be deployed using code signing to ensure the program is not changed inadvertently or maliciously prior to delivery to an end user
- #### Fail Securely
	- Applications should be programmed to properly conduct error handling for exceptions in order to fail securely without crashing
- #### Fix Security Issues
	- If a vulnerability is identified, then it should be quickly and correctly patched to remove that vulnerability
- #### Rely on trusted SDKs
	- A **Software Development Kit** (SDK) allows a programmer to reuse code from other programmers to reduce time and effort 
	- SDKs must come from trusted sources to ensure that no malicious code is being added

# 10.3 Testing Methods
- **Black-box**: occurs when a tester is not provided with any information about the system or program prior to conducting the test
- **White-box**: occurs when a tester is provided full details of a system including the source code, diagrams, and user credentials
- **Gray-hat**: occurs when a tester receives SOME information, and tests as if they don't have full access
	- i.e. user-level credentials for a system, not admin. For networks, you may receive IP addresses, but not system versions
- **Structured Exception Handling** (SEH) provides control over what the application should do when faced with runtime or syntax errors.
	- i.e. for a credit card application site, the user will need to enter their name, DOB, and SSN. You need to check for stuff like invalid DOBs, invalid SSNs, etc.
	- This is when **input validation** should be implemented. If the data matches a certain format/range/whatever, it's fine
- **Static Analysis** occurs when source code is reviewed manually or with automated tools without running the code
- **Dynamic Analysis** occurs when this testing is being conducted while the code is executed.
	- **Fuzzing** involves the injection of randomized data into a software program in an attempt to find system failures, memory leaks, error handling issues, improepr input validation, etc.

# 10.4 Vulnerabilities and Exploits
- #### Backdoors
	- Code placed in computer programs to bypass normal authentication and security mechanisms 
	- This is a bad practice and should not be utilized
	- RATs can act as backdoors
- #### Directory Traversal
	- Accessing unauthorized directories by moving through the directory structure on a remote server
- #### Arbitrary Code Execution
	- An attacker is able to execute commands on a victim machine
- #### Remote Code Execution
	- An attacker is able to run commands or code from a remote computer
- #### Zero day
	- Exploit or attack that is unknown to the original dev

# 10.5 Buffer Overflows
- **Buffer**: A temporary storage area that a program uses to store data
- Over 85% of data breaches were caused by buffer overflows
- For a phone contact app, the user might need to store local phone numbers and distant (including area code). Since the local phone numbers would require an 8-bit buffer, as opposed to the 10-bit needed for a distant, trying to include the distant would result in an overflow because you're writing into another buffer
- **Stack**: Reserved area of memory where the program saves the return address when a function call instruction is received
	- Placing too much info in the stack or changing the value of the return pointer, an attack can be deployed
	- They can point the stack to a new place in memory where malicious code is stored
- **"Smash the Stack"**: An attacker fills the buffer with a non-operation instruction (NOP) so that the return address may hit the NOP and continue until it finds the malicious code
	- When a series of NOPs are hit, this is a **NOP Slide**
- **Address Space Layout Randomization**: Randomly arranging the different address spaces used by a program or process to prevent buffer overflows

# 10.6 XSS and XSRF
- **Cross-site Scripting (XSS)** occurs when an attacker embeds malicious scripting commands on a trusted website
	- Violates the trust bewteen a web browser and the web server
	- #### Stored/Persistent
		- Attemptes to get data provided by the attacker to be saved on the server by the victim
	- #### Reflected
		- Attempts to have a non-persistent effect activated by a victim clicking a link on the site
	- #### DOM
		- Attempts to exploit the web browser
	- Prevent XSS with input validation and output encoding
- **Cross-site Request Forgery** (XSRF) occurs when an attacker forces a user to execute actions on a web server from which they are already authenticated	
	- i.e. PoisonTap
	- The user will be unable to see the response from the attacker's request commands
	- Prevent XSRF attacks with tokens, encryption, XML file scanning, and cookie verification

# 10.7 SQL Injection
- Structured Query Language (SQL) is a way for webapps to communicate with databases for information
- An SQL injection means inputting an SQL query via the client to a webapp.
- An **injection attack** means adding additional information or code via the same medium 	
- Most common injections are SQL, HTML, XML, and LDAP
- SQL injection is prevented through input validation and using least privilege when accessing a database
# 10.8 	XML Vulnerabilities
- XML data submitted without encryption is vulnerable to spoofing, request forgery, and injection of arbitrary code
- Example XML request below:
![[xml request.png]]
- #### XML Bomb (Billion Laughs Attack)
	- XML encodes entities that expand to exponential size, consuming memory on the host and potentially crashing it
- #### XML Eternal Entity (	XXE)
	- An attack that embeds a request for a local resource
	![[xml xxe.png]]
- XML exploits can be prevented with input validation
# 10.9 Race Conditions
- A software vulnerability when the resulting outcome from execution processes is directly dependent on the order and timing of certain events, and those events fail to execute in the developer's intended order and timing.
	- If you're trying to do something legitimately and a hacker beats you to it, this is what they're exploting
	- Multiple threads are attempting to write a variable or object at the same memory location
- **Dereferencing** occurs when the code attempts to remove the relationship between a pointer an its intended "direction"
- Race conditions are difficult to detect and mitigate
- **DIRTY COW**
	- Exploited the COW (copy-on-write) functionality on Linux memory management systems in ~'06, giving the attacker the ability to change read-only files into write
- Race conditions can also be used against databses and file systems
- **Time of Check to Time of Use** (TOCTTOU) occurs when there is a change between when an app checked a resources and when the app uses this resource
	- Apps should not be develoepd to process things sequentially, if possible	
	- Implementing a locking mechanism to provide app with exclusive access

# 10.10 Design Vulnerabilities
- Vulnerabilites generally arise from the general design of the software code
- #### Insecure Components
	- Any code that is used or invoked outside the main program development process	
	- This includes code reuse, as well as implementing third-party libraries, and SDKs
- #### Insufficient Logging and Monitoring
	- Any program that does not properly record or log detailed enough information for an analyst to perform their job
		- Logging and monitoring must support your use case and answer what, when, who, where, how
- #### Weak and Default Configurations
	- Any program that uses ineffective credentials or configurations, or one in which the defaults have not been changed for security
	- Many apps choose to simly run as root or local admin
	- Permissions may be too permissive on files or directories
	- Utilize scripted installs and baseline configuration templates to secure applications during installation