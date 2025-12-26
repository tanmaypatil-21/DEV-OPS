# Devops_QnA


### 1. What is operating system ?
- An operating system is software that manages computer hardware and software resources.**

### 2. Difference between linux and windows ?

| Feature               | Linux                                | Windows                               |
|-----------------------|--------------------------------------|--------------------------------------|
| Interface             | CLI (Command Line Interface)         | GUI (Graphical User Interface)        |
| Usability             | Difficult to use                     | Easy to use                           |
| Source Code           | Open Source                          | Closed Source                         |
| Licensing             | No Licensing Required                | Licensing Required                    |
| Cost                  | Free                                 | Paid                                  |
| Resource Usage        | Lightweight (Consumes Less Resources)| Heavy (Consumes More Resources)       |
| Security              | More Secure                          | Less Secure                           |


### 3. Explain what is open source ?

- Open source refers to software whose source code is made available to the public for free. This means that anyone can view, modify, distribute, and use the software.** 

### 4. Explain linux architecture ?

<img width="1536" height="1024" alt="ChatGPT Image Dec 26, 2025, 07_49_24 PM" src="https://github.com/user-attachments/assets/af57711c-9684-42dc-a04c-06e0bfc4d9b9" />



**1.Hardware Layer:** CPU,memory,storage devices,input/output devices and network interface.

**2.Kernal:** The linux kernal is core component of operating system. It is responsible for managing hardware resources such as CPU scheduling,memory management,device drivers and system calls.

**3.Shell & command-line interface:** linux offers a command line interface (CLI) where users can interact with the operating system by typing commands and communicates with the kernal popular shells include bash & fish.

**4.Application:** users interact with the system through various application games,office software etc.

### 5. What is virtualization ?

- Virtualization is a technology which divides single physical server into multiple logical machines using software called Hypervisor.

### 6. Explain hypervisor and its types ?
 
- Hypervisor is a software that allow for virtualization, which is the process of creating virtual representations of physical hardware.

- There are two types of hypervisor :
1)Baremetal: This type hypervisor runs directly on the physical host and has direct access to its resources.(most cloud providers use this hypervisor)

2)Hosted: This type of hypervisor is an application installed on the host operating system.

### 7. What is shell, its types and how to check current shell ?

- Shell is a program that allow user to interact with linux operating system typing commands.

**There are two types of shell:** 
1)CLI
2)GUI

**check the current shell command:**
````
    echo$SHELL
````

### 8. What is kernel and command to check kernel information ?

- The kernel is the core component of an operating system (OS) that manages system resources and allows software to interact with hardware. It provides basic services like process management, memory management, hardware abstraction, and device management.**

- check kernel information command:**
````
  uname -a
````
- Display the kernel name,version,and more.
````
  uname -r
````
- Display kernel release information.
    
### 9. Command to check os information ?

````
cat /etc/os-release 
````
- Displays information about the operating system, including its name, version, and other details.
   
### 10. Command to check available memory ?

````
free -h
````

- This command shows the amount of free and used memory on your system in a human-readable format (e.g., MB, GB).

### 11. Command to check storage or disk info ?

````
df -h
````

- The df (disk free) command shows disk space usage for all mounted file systems in a human-readable format (e.g., GB, MB).

### 12. Command to check size of file/dir ?

````
du -sh <file_or_directory>
````

- The du (disk usage) command shows the size of a file or directory. The -s option provides the total size of the file or directory, and the -h option makes the output human-readable.

### 13. Explain modes of vim editor ?

**1)Command Mode (esc):** This is the default mode in which you interact with the text. In normal mode, you can navigate through the document, delete or copy text, search for content, and perform other actions using commands.

**2)Insert Mode (i):** In insert mode, you can type and edit the content of the file just like in a regular text editor.

**3)Visual Mode (v):** Visual mode is used to select text. Once text is selected, you can perform operations on the selection, such as copying, cutting, or modifying it.

**4)Execution Mode (:):** Execute various commands that affect the entire file or Vim settings, such as saving the file, quitting, or searching and replacing text.

### 14. Difference adduser and useradd ?

<img width="1536" height="1024" alt="ChatGPT Image Dec 26, 2025, 07_53_24 PM" src="https://github.com/user-attachments/assets/c5f6849c-ca73-4a3f-9d8e-eeefe5075e03" />


### 15. Explain skeleton files ?

- skeleton files are files that are automatically copied to a newly created user's home directory when the user is created.**

- Location of Skeleton Files

- Skeleton files are typically stored in the /etc/skel/ directory. This directory contains files and directories that will be copied into a new user's home directory when the user is created (using commands like adduser or useradd).
````
ls /etc/skel/
````

### 16. Explain fields of passwd file ?

**Username:**	User’s login name (unique identifier)

**Password:**	Encrypted password or placeholder

**UID:**	User’s unique numeric identifier

**GID:** 	User’s primary group ID (numeric identifier)

**Comment:**	Full name or other user-related information	

**Home Directory:**	Path to the user’s home directory

**Login Shell:**	User's default shell (the command run upon login)

### 17. How to check user belongs to which group ?
````
cat /etc/group
````
### 18. Explain file types in linux ?

**1.Regular file:** A regular file is the most common type of file in Linux. It can contain text, binary data, images, or program code.

**2.Directory Files:** A directory is a special type of file that holds references to other files and directories. Directories organize files in a hierarchical structure.

**3.Symbolic (Soft) Link:** A symbolic link (symlink) is a file that points to another file or directory. It acts as a shortcut to another file or location.

### 19. Difference Hard Link vs Soft Link ?

**Softlink:** 

1)A separate file that contains a path.

2)A path to the target file.

3)If the target file is deleted,the softlink becomes a "dangling link" and is unusable.

**Hardlink:**

1)A reference to the inode

2)Same inode as the target file.

3)Even if the orignal file is deleted,the hardlink remains,and the data us not lost.**

### 20. How to change ownership of file/dir ?
````
chown username <file_name or dir_name>
````
### 21. How to set permissions using symbolic and numeric modes ?

**1. Symbolic Mode:**
In symbolic mode, permissions are specified using letters for users and operations to modify permissions.

Syntax of Symbolic Mode:
````
chmod [who][operation][permission] file
````
who: Defines the user(s) whose permissions are being changed. It can be:
- u: User (owner)
- g: Group
- o: Others (everyone else)
- a: All (user, group, and others)

operation: Defines the operation you want to perform:
- +: Add permission
- -: Remove permission
- =: Set exactly the specified permission, removing all others

permission: Defines the type of permission:
- r: Read
- w: Write
- x: Execute

Examples of Symbolic Mode:
Add execute permission for the owner:
````
chmod u+x file.txt
````
**2. Numeric (Octal) Mode:**
In numeric mode, permissions are represented as a three-digit octal number where each digit represents the permissions for the owner, group, and others. Each permission is assigned a number:
- Read (r) = 4
- Write (w) = 2
- Execute (x) = 1

The number is a sum of the values for the permissions:
- No permissions = 0
- Read-only = 4
- Write-only = 2
- Execute-only = 1
- Read + Write = 6 (4 + 2)
- Read + Execute = 5 (4 + 1)
- Write + Execute = 3 (2 + 1)
- Read + Write + Execute = 7 (4 + 2 + 1)
Syntax of Numeric Mode:
````
chmod [permissions] file
````
Examples of Numeric Mode:
Set permissions for owner as read/write, group as read, and others as read:
````
chmod 644 file.txt
````
![image](https://github.com/user-attachments/assets/884242f1-ae78-4304-b1f5-dc1135bf124d)

### 22. What is umask ?

- umask is a command and a file permission mask that determins the defauit permission for newly created files and directories.

### 23. Default permissions for root user for file/dir ?

**root:**

1.File: 644(Full Permission:666)

2.Directory: 755(Full Permission:777)

### 24. Default permissions for local user for file/dir ?

**Local:**

1.File: 664(Full Permission:666)

2.Directory: 775(Full Permisson:777)

### 25. Explain crontab fields?

**Minute (0-59):** This field specifies the minute(s) when the job will run.

**Hour (0-23):** This field specifies the hour(s) when the job will run.

**Day of the Month (1-31):** This field specifies the day of the month when the job will run.

**Month (1-12):** This field specifies the month(s) when the job will run.

**Day of the Week (0-7):** This field specifies the day(s) of the week when the job will run.**

### 26. Explain top command ?

- The top command is used to display real-time information about the running processes on a system. It provides a dynamic, real-time view of system performance, including CPU usage, memory usage, and process details.

### 27. Expalin ps command ?

- The ps (process status) command is used to display information about the currently running processes on the system. It provides a snapshot of active processes, showing details like process IDs, CPU usage, memory usage, and more.

### 28. Explain grep command ?

- grep (Global Regular Expression Print)
grep is used to serach for text patterns within files used to filter lines containing specific text in files.

<grep "search_text" filename>

### 29. How to archieve and compress files also extract them ?

### 30. Explain osi model ?

**1)Physical Layer:** Transmits raw bit stream over the physical medium.

**2)Data Link Layer:** Defines the formate of data on the network.

**3)Network Layer:** Decides which physical path the data will take.

**4)Transport Layer:** Transmits data using transmission protocols using TCP and UDP.

**5)Session Layer:** Maintains connections and is responsible for controlling ports and sessions.

**6)Presentation Layer:** Ensure that data is in a usable formate and is where data encryption occurs.

**7)Application Layer:** Human-computer interaction layer,where application can access the network service.

### 31. Difference TCP and UDP ?

<img width="1024" height="1536" alt="ChatGPT Image Dec 26, 2025, 07_57_57 PM" src="https://github.com/user-attachments/assets/a0ed58a6-4bd3-486b-8fdf-a18a3aadc675" />


### 32. Basic networking commands ?
**1.ifconfig:**  Displays or configures network interfaces.

**2.ip:** A powerful tool for managing network interfaces, routing, and IP addresses.

**3.ping:** Tests if you can connect to another device (e.g., a website).

**4.curl:** Downloads data from the internet (HTTP/HTTPS).

**5.wget:** Downloads files from the internet.

### 33. Explain ip clases ?

**1.Class A**
 
IP Range: 1.0.0.0 to 126.255.255.255

First Octet: 1 to 126

Purpose: Used for large networks (e.g., multinational companies).

Number of Networks: 128 (2^7)

Number of Hosts per Network: Over 16 million (2^24 - 2 for network and broadcast)

Class A addresses are used for very large organizations because they allow for a very large number of hosts on each network.

**2.Class B**

IP Range: 128.0.0.0 to 191.255.255.255

First Octet: 128 to 191

Purpose: Used for medium-sized networks (e.g., universities, large offices).

Number of Networks: 16,384 (2^14)

Number of Hosts per Network: 65,534 (2^16 - 2 for network and broadcast)

Class B addresses are used by medium-sized networks, with a good balance between the number of networks and hosts.

**3.Class C**

IP Range: 192.0.0.0 to 223.255.255.255

First Octet: 192 to 223

Purpose: Used for small networks (e.g., small businesses, home networks).

Number of Networks: 2,097,152 (2^21)

Number of Hosts per Network: 254 (2^8 - 2 for network and broadcast)

Class C addresses are the most common, often used in small networks, like home or office networks, because of the limited number of hosts per network.

**4.Class D (Multicast)**

IP Range: 224.0.0.0 to 239.255.255.255

First Octet: 224 to 239

Purpose: Reserved for multicast addresses, used for one-to-many communication (e.g., video conferencing, streaming).

Number of Networks: N/A (These are special addresses, not for typical networking use)

Class D addresses are used for multicasting, where one source sends data to multiple recipients, such as in streaming or group communications.

**5.Class E (Reserved for Future Use)**

IP Range: 240.0.0.0 to 255.255.255.255

First Octet: 240 to 255

Purpose: Reserved for experimental or future use by IETF (Internet Engineering Task Force). Not used for public addressing.

Class E addresses are reserved for future research and development purposes, and they are not typically used in actual networks.

**Example Range: Common private IP address ranges for IPv4 include:**

10.0.0.0 to 10.255.255.255 (Class A)

172.16.0.0 to 172.31.255.255 (Class B)

192.168.0.0 to 192.168.255.255 (Class C)


### 34. Difference public and private ip addresses ?


**Key Differences:**

- Public IP: Can be accessed from anywhere on the internet (like a home address for a building).

- Private IP: Can only be used inside your home or office network (like an apartment number within a building).

--- 

## AWS Cloud: 
##  1. what is cloud computing ?
- Cloud computing refers to the delivery of computing services over the internet ("the cloud"). These services include storage, servers, databases, networking, software, analytics, and intelligence. Cloud computing enables users to access and use resources on-demand without having to own and manage physical infrastructure.

##  2. explain cloud service models ?
- Cloud service models define the types of services provided to users based on their requirements. These models are often referred to as IaaS, PaaS, and SaaS.
### 1. Infrastructure as a Service (IaaS)
- What it provides:
Virtualized computing resources like servers, storage, and networks.
Users manage operating systems, applications, and data.**

- Use case:
Building virtual machines for hosting custom applications.
Examples: Amazon EC2, Google Compute Engine, Microsoft Azure Virtual Machines.

- Key Features:
High scalability.
Pay-as-you-go pricing.
Suitable for developers and system administrators.

### 2. Platform as a Service (PaaS)
- What it provides:
A platform for developers to build, deploy, and manage applications.
Includes tools for coding, testing, and deploying applications.

- Use case:
Developing web and mobile applications without worrying about managing the infrastructure.
Examples: Google App Engine, Microsoft Azure App Service, Heroku.

- Key Features:
Simplified development.
Reduces the time-to-market.
Managed runtime environment and middleware.

### 3. Software as a Service (SaaS)
- What it provides:
Complete software applications accessible via the internet.
End-users do not manage the underlying infrastructure or platform.

- Use case:
Collaborative tools for businesses, such as email or CRM software.
Examples: Google Workspace (Docs, Sheets), Microsoft Office 365, Salesforce.

- Key Features:
Ready-to-use applications.
Subscription-based pricing.
Accessible from any internet-connected device.


## 3. explain deployment models in cloud ?
- Cloud deployment models define how cloud services are hosted, managed, and accessed. The choice of deployment model depends on the specific requirements of an organization, such as control, security, and scalability.
### 1. Public Cloud
- A public cloud is owned and operated by third-party cloud providers, and services are delivered over the internet to multiple organizations (multi-tenant model).

- Characteristics:
Shared resources.
Highly scalable and cost-effective.
Managed by the cloud provider.

- Advantages:
No upfront costs; pay-as-you-go model.
Easy scalability and availability.
Minimal maintenance by users.

- Disadvantages:
Limited control over infrastructure.
May raise security and compliance concerns.

- Examples:
Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP).

### 2. Private Cloud
- A private cloud is dedicated to a single organization, offering greater control and security. It can be hosted on-premises or by a third-party provider.

- Characteristics:
Exclusive use by one organization.
Customizable according to specific needs.
Higher level of security and compliance.

- Advantages:
Enhanced control over data and infrastructure.
Better compliance with industry regulations.
Improved security for sensitive data.

- Disadvantages:
Higher costs compared to public cloud.
Requires in-house expertise for maintenance.

- Examples:
VMware vSphere, OpenStack, Azure Stack.

### 3. Hybrid Cloud
- A hybrid cloud combines public and private clouds, allowing data and applications to be shared between them. This model is ideal for organizations requiring a mix of flexibility and control.

- Characteristics:
Integration of public and private clouds.
Workloads can move between environments as needed.
Suitable for dynamic and scalable applications.

- Advantages:
Balances cost-effectiveness with control.
Ensures business continuity and disaster recovery.
Allows sensitive workloads to remain private.

- Disadvantages:
Complex to implement and manage.
May involve compatibility issues between environments.

- Examples:
AWS Outposts, Microsoft Azure Arc.

### 4. Community Cloud
- A community cloud is shared among organizations with similar goals, such as government agencies, healthcare providers, or educational institutions.

- Characteristics:
Shared infrastructure and costs.
Focused on common interests or compliance needs.
Can be managed internally or by a third party.

- Advantages:
Cost-effective for similar organizations.
Shared responsibility for maintenance and security.
Meets specific compliance or regulatory needs.

- Disadvantages:
Limited scalability compared to public clouds.
Dependency on shared governance and resources.

- Examples:
Government-hosted clouds, healthcare consortium clouds

## 4. explain IAM service ?
### What is IAM?

- IAM stands for Identity and Access Management. It is a framework of policies and technologies used to ensure that the right individuals and entities in an organization have appropriate access to resources.
IAM services are crucial in cloud environments, allowing organizations to manage who can access what resources and under what conditions.

### Key Features of IAM Services :
#### Authentication-
- Verifies the identity of users, devices, or services trying to access resources.
Methods include passwords, multi-factor authentication (MFA), and single sign-on (SSO).

#### Authorization-
- Determines what actions authenticated entities are allowed to perform on resources.
Access is granted based on roles, policies, or attributes.

#### Granular Permissions
- Fine-tuned control over resources.
Permissions can be set for specific actions (e.g., read, write, delete) on specific resources.

#### Role-Based Access Control (RBAC)
- Access is granted based on roles assigned to users (e.g., admin, developer, viewer).

#### Policy Management
- Use of policies to define access rules. Policies can be attached to users, groups, or roles.

#### Audit and Compliance
- Logs all access and activities for auditing purposes.
Ensures compliance with security and regulatory requirements.

#### Federated Access
- Allows external identity providers (e.g., Google, Microsoft Azure AD) to authenticate users.

### Why is IAM Important?
 **Security:** Prevents unauthorized access and protects sensitive data,
**Scalability:** Easily manage access for a growing number of users and resources.
**Compliance:** Helps organizations meet industry standards and regulatory requirements.
**Efficiency:** Streamlines access management processes.

### Key Components of IAM Services
**Users:** ndividual identities that need access (e.g., employees, contractors).
**Groups:** Collections of users with similar permissions.
**Roles:** A set of permissions assigned to a user or group (e.g., Admin Role).
**Policies:** Rules that define what actions are allowed or denied.
**Resources:** The cloud assets (e.g., files, servers, databases) being accessed.

### Popular IAM Services
**AWS IAM (Identity and Access Management)**
 - Allows secure access control to AWS services and resources.
Features include roles, policies, and MFA.

#### Google Cloud IAM
- Manages access to Google Cloud resources with fine-grained permissions.

#### Azure Active Directory (Azure AD)
- Provides identity management and access control for Microsoft Azure.

#### Okta
- A third-party identity and access management platform offering SSO and MFA.

#### Auth0
- Specializes in identity management for developers to build authentication into applications.

### Real-World Use Cases
#### Role Assignment:
- Grant developers access to deploy code but restrict them from modifying production environments.

#### MFA Enforcement:
- Require employees to authenticate with both a password and a mobile device.

#### Temporary Access:
- Grant contractors access to a project for a limited time and automatically revoke it afterward.

#### Auditing:
- Monitor and log who accessed critical resources and when.

**IAM is a cornerstone of secure and efficient cloud operations, ensuring that only the right users and services have access to the necessary resources while maintaining strong governance.**

## 5. explain policies in IAM ?
### Types of IAM Policies :

#### Managed Policies :
- Predefined policies created and managed by the cloud provider or your organization.
#### Two types:
**1. AWS-Managed Policies (or similar in other clouds):** Generic, ready-to-use policies provided by the provider.
**2. Customer-Managed Policies:** Custom policies created and managed by users.

#### Inline Policies
- Policies that are embedded directly within a user, group, or role.
Used for highly specific use cases.

#### Service Control Policies (SCPs)
- Used in multi-account environments to set guardrails on what actions can be performed across accounts.

#### Identity-Based Policies
- Attached to users, groups, or roles to define their access to resources.

#### Resource-Based Policies
- Attached directly to a resource (e.g., an S3 bucket in AWS).
Useful for granting cross-account access.

## 6. explain roles in IAM ?
### Roles in IAM (Identity and Access Management)
- A role in IAM is a set of permissions that define what actions an entity (a user, service, or application) can perform on resources. Unlike users, roles are not associated with a specific identity by default. Instead, roles are assumed by trusted entities when needed, enabling temporary and secure access to resources.

### Types of IAM Roles
#### Service Roles
- Used by AWS services (or equivalent in other clouds) to perform actions on behalf of the user.
Example: An Amazon EC2 instance using a role to access S3.

#### Cross-Account Roles
- Allows users or services in one account to access resources in another account.
Example: Account A granting Account B access to its S3 bucket.

#### Application Roles
- Used by applications to securely access resources without embedding credentials in the code.
Example: A serverless application accessing a database using a role.

#### Identity Provider Roles (Federated Roles)
- Used for integrating external identity providers (e.g., Google, Okta) for authentication.
Example: Employees using corporate SSO to assume roles in AWS.

## 7. diff roles and policies ?

## 8. explain ec2 service ?

9. explain instance types and perchasing options?
10. diff ami and snapshot ?
11. explain ebs volume types ?
12. explain concept of loadbalancing ?
13. diff ALB and NLB ?
14. explain autoscaling ?
15. explain s3 service and its advantages ?
16. diff s3 efs and ebs ?
17. explain s3 storage classes ?
18. what is lifecycle policy in s3 ?
19. explain vpc service ?
20. diff public and private subnet ?
21. explain nat ?
22. explain peering connection ?
23. diff nacl and sg ?
24. what is domain name ?
25. what is hosted zone ?
26. explain records in rt53 ?
27. explain routing policies ?
28. explain concept of ssl ?
29. explain CDN ?
30. what is edge location ?
31. explain OAC/OAI in cloudfront ?
32. what is latency?
--- 
### Devops: 
1. what is devops ?
2. explain sdlc ?
3. diff cvcs and dvcs ?
4. git basic commands ?
5. diff git pull and fetch ?
6. diff git merge and rebase ?
7. git cherry pick 
8. explain branching strategy ?
10. diff container and vm ?
11. explain docker volume and network ?
12. concept of compose and sworm ?
13. explain k8s architecture
14. dif rs and rc 
15. diff rs and deployment
16. diff deployment  vs statefulset 
17. explain deployment types of servises 
18. explain cicd 
19. where is jenkins home directory located 
20. dif freestyle and pipeline project 
21. explain IAC 
22. tf modules 
23. tfstate
24. rmote backend
