# 14.1 Workflow Orchestration
- The automation of multiple steps in a deployment process
- #### Example: Adding new VM to load balanced cluster
	- High level: Provision, configuring VM, adding it to cluster, configure load balanced cluster weight distribution
- Orchestration is the automation of the automations
- Rapid elasticity in cloud computing would not be possible without orchestration
- Different types of orchestration including **resource**, **workload**, and **service**
- Third-party orcestration platform is prtection from vendor lock-in
# 14.2 CI/CD
- Continuous Integration/Continuous Delivery and Continuous Deployment
- In the past, to deploy a feature or product, development, testing/integration, staging, and production would be required (very linear)
- **Continuous Integration** mitigates some of the slowness caused by this method
	- A development method where code updates are tested and committed to a development or server/code repo rapidly
	- CI can test and commit updates multiple times per day
	- CI detects and resolves development conflicts early and often
	![[CI.png]]
- **Continuous delivery** is a dev method where app and platform requirements are frequently tested and validated for immediate availability
- **Continuous deployment** is a dev method where app and platform updates are committed to production rapidly
# 14.3 DevSecOps
- **DevOps** is an organizational culture shift that combines software development and systems operations by referring to the practice of integrating the two disciplines within a company
- Operations and developers can build, test, and release software faster and more reliably
- **DevSecOps** is a combination of software development, security operations, and systems operations by integrating each discipline with the others
	- Utilizes a shift-left mindset (shift-left essentially proposes moving testing to the earlier stages of development)
	- Integrate security from the beginning
	- Test during and after development
	- Automate compliance checks
# 14.4 Infrastructure as Code (IAC)
- **IAC** is a provisioning architecture in which deployment of resources is performed by scripted automation and orchestration
	- Allows for the use of scripted approaches to provisioning infrastructure in the cloud
	- Scripts, security templates, and policies are core components
- Robust orchestration can lower overall IT costs, speed up deployments, and increase security
- **Snowflake Systems** are any system that is different in its configs compared to a standard template within an IaC architecture
- Lack of consistency leads to security issues and inefficiencies in support
- **Idempotence** is a property of IaC that an automation or orchestration action always produces the same result, regardless of the component's previous state
- IaC uses carefully developed and tested scripts and orchestration runbooks to generate consistent builds
# 14.5 Machine Learning
- #### Artificial Intelligence
	- The science of creating machines with the ability to develop problem solving and analysis strategies without significant human direction or intervention
- #### Machine Learning
	- A component of AI that enables a machine to develop strategies for solving a task given a labeled dataset where features have been manually identified but without further explicit instructions
	- Machine learning can be prejudiced depending on the dataset
- #### Artificial Neural Network
	- An architecture of input, hidden, and output layers that can perform algorithmic analysis of a a dataset to achieve outcome objectives
- #### Deep Learning
	- A refinement of machine learning that enables a machine to develop strategies for solving a task given a labeled dataset and without further explicit instructions
	- Uses complex classes of nkowledge defined in relation to simpler classes of knowledge to make mroe informed determinations about an environment
	![[ml_vs_dl.png]]