# Amazon VPC (Virtual Private Cloud)
## 1. Introduction
Amazon Virtual Private Cloud (VPC) allows you to launch AWS resources in a logically isolated network.
It gives you full control over your network environment, including IP address ranges, subnets, route tables, and network gateways.

## 2. Key Features
1. **Custom IP Address Range** – Choose your own IPv4 or IPv6 CIDR block.

2. **Subnets** – Divide the VPC into public and private sections

3. **Route Tables** – Control traffic flow within the VPC and outside

4. **Security Groups & NACLs** – Control inbound and outbound traffic at instance and subnet level.

5. **Internet & NAT Gateways** – Enable internet access for public/private subnets.

6. **VPC Peering** – Connect VPCs privately across regions or accounts.

## 3. Benefits
1. Logical network isolation

2. Enhanced security with multiple layers of control

3. Scalable and flexible network design

3. Integration with other AWS services

## 4. Components of a VPC
1. **VPC** – The main network container.

2. **Subnets** – Logical partitions of the VPC network.

3. **Route Tables** – Define where network traffic is directed.

4. **Internet Gateway (IGW)** – Allows communication between instances in your VPC and the internet.

5. **NAT Gateway** – Enables private subnets to access the internet securely.9

6. **Security Groups** – Instance-level firewalls.

7. **Network ACLs (NACLs)** – Subnet-level firewalls.

8. **Endpoints** – Private connections to AWS services.

# Setup VPC peering Connection between 2 different region
## 1. Objective
This document explains the process of setting up an inter-region VPC peering connection between two VPCs located in different AWS Regions. This setup enables secure, private communication using private IP addresses between resources in different regions without traversing the public internet.

## 2. Flowchart Diagram
<img width="857" height="410" alt="Screenshot 2025-08-07 003339" src="https://github.com/user-attachments/assets/ab36eea0-2f57-4b66-a335-593038e2a4cf" />

## 3. Steps to Set Up Inter-Region VPC Peering

**1. set region for VPC A (us-south-1) and create VPC**
- Go to create VPC
<img width="1914" height="916" alt="Screenshot 2025-08-06 205718" src="https://github.com/user-attachments/assets/17d27a09-5f66-49b7-9419-e11c27679126" />

- Name VPC - mentioned IPV4 CIDR - click Create VPC
<img width="1903" height="925" alt="Screenshot 2025-08-06 205948" src="https://github.com/user-attachments/assets/0b2d6af6-4053-4e56-ab91-7fec04c98b1e" />

- Now Create a Internet Gateway
- Click internet gateway - Create Internate Gateway
-<img width="1895" height="862" alt="Screenshot 2025-08-06 210043" src="https://github.com/user-attachments/assets/3c3c2b26-5b83-4875-a25d-ccce737ac4e4" />

- Name Internet Gateway - click - Create Internet Gateway
<img width="1900" height="866" alt="Screenshot 2025-08-06 210218" src="https://github.com/user-attachments/assets/f533c479-63b8-483a-8749-a6fa1dbef324" />

- Done IGW is created

- Now attach your IGW to your VPC
- Click on attach VPC
 <img width="1899" height="868" alt="Screenshot 2025-08-06 210303" src="https://github.com/user-attachments/assets/0a66e910-6c54-43e5-9b97-a6df533aad8a" />


- Select VPC you create in current region - click attach internet gateway
<img width="1894" height="865" alt="Screenshot 2025-08-06 210328" src="https://github.com/user-attachments/assets/57f99d95-7a82-484c-a553-f5930b96d523" />

- Done internet gateway associated to VPC
<img width="1896" height="862" alt="Screenshot 2025-08-06 210434" src="https://github.com/user-attachments/assets/80b4e2a7-6233-4022-82b7-affbb4c6b30c" />

- Now create subnet
- click subnet - create subnet - select VPC you create in current region
<img width="1871" height="480" alt="Screenshot 2025-08-06 210648" src="https://github.com/user-attachments/assets/1b1e349c-cff0-451f-a105-5fe5f4d8f5db" />

- Name Subnet - select Availability zone - mentioned IPV4 subnet CIDR block - click create subnet
<img width="1904" height="1040" alt="Screenshot 2025-08-06 210712" src="https://github.com/user-attachments/assets/fd9831e3-7d82-4fcb-9c10-5c83b408a817" />

- Done Subnet is Created
- <img width="1897" height="859" alt="Screenshot 2025-08-06 210812" src="https://github.com/user-attachments/assets/e292f217-ad41-4202-bc8b-bc3253f4fdd6" />

- Now create a Route Table
- click route table - create route table
<img width="1894" height="869" alt="Screenshot 2025-08-06 210905" src="https://github.com/user-attachments/assets/1c0dcf68-c865-47a9-8132-db7d6949c2ae" />

- Name Route table - select VPC you create current region - click create route table
<img width="1894" height="865" alt="Screenshot 2025-08-06 210955" src="https://github.com/user-attachments/assets/56dbc572-4a72-45f3-8a47-99ce9103e92a" />


- Now we need to Associate our subnet with route table
- Again go to route table - select RT - subnet Associations - click Edit Subnet Association
<img width="1892" height="863" alt="Screenshot 2025-08-06 211120" src="https://github.com/user-attachments/assets/36f553e1-4593-4d56-a9fb-986a011fbf1f" />

- Select Subnet - Save association
<img width="1893" height="866" alt="Screenshot 2025-08-06 211201" src="https://github.com/user-attachments/assets/78224db2-c071-4cb9-bf54-f7d9c7d53c8c" />

- Done this subnet Associated with route table
<img width="1897" height="866" alt="Screenshot 2025-08-06 211306" src="https://github.com/user-attachments/assets/2c3f7281-74ed-4dc7-a2a0-b9a82715bc07" />

- Now we need to update routes
- Go Route table - select routes - edit routes
 <img width="1883" height="815" alt="Screenshot 2025-08-06 211350" src="https://github.com/user-attachments/assets/1a89246b-e6b7-45ae-a8a4-26699a51b27e" />

 - Add routes - select 0.0.0.0/0 - select IGW and select IGW you created -save changes
<img width="1894" height="809" alt="Screenshot 2025-08-06 211452" src="https://github.com/user-attachments/assets/08c7c2ef-f2e0-4c55-9496-3fd332e72726" />

- Done RT is updated
<img width="1893" height="866" alt="Screenshot 2025-08-06 211521" src="https://github.com/user-attachments/assets/c648bb01-0937-40e1-9af2-12df16d86335" />

**Upto now we created VPC,Subnet,Route table & Internet gateway in US-EAST-1 region, so let's create AWS ec2 instance later**

**Now jump on AP-SOUTHEAST-1 Region & let's create VPC,Subnet,Route table, & Internate gateway**

**set region for VPC B (AP-SOUTHEAST-1)**
<img width="1907" height="864" alt="Screenshot 2025-08-09 191441" src="https://github.com/user-attachments/assets/0d5c16a2-61d2-4058-aa7b-edc627adcdf7" />

- Go to create VPC
<img width="1897" height="871" alt="Screenshot 2025-08-09 191508" src="https://github.com/user-attachments/assets/57ec30d2-4a47-4294-8a9e-a7ff971c370f" />

- Name VPC - mentioned IPV4 CIDR - click Create VPC
<img width="1888" height="1034" alt="Screenshot 2025-08-06 212427" src="https://github.com/user-attachments/assets/18901d32-82a2-4425-815a-cbed69008591" />       

- Now create subnet
- create subnet - select VPC you create in current region
<img width="1867" height="471" alt="Screenshot 2025-08-06 212728" src="https://github.com/user-attachments/assets/9d8cc16f-d549-4a9e-92b5-0c8d6c1bb61e" />

- Name Subnet - select Availability zone - mentioned IPV4 subnet CIDR block - click create subnet
<img width="1879" height="1032" alt="Screenshot 2025-08-06 212742" src="https://github.com/user-attachments/assets/e41c7886-3b9f-476b-bfa7-02dd1e9c0404" />
- Done Subnet is created

- Now Create a Internet Gateway
- Click internet gateway - Create Internate Gateway
<img width="1899" height="870" alt="Screenshot 2025-08-06 212814" src="https://github.com/user-attachments/assets/6e06d9d6-69e8-48f8-a8b4-425719f6065f" />

- Name Internet Gateway - click - Create Internet Gateway
<img width="1899" height="861" alt="Screenshot 2025-08-06 212940" src="https://github.com/user-attachments/assets/faf45141-0478-44f7-80a6-060e98bda533" />

- Done IGW is created

- Now attach your IGW to your VPC
- Click on attach VPC
<img width="1896" height="811" alt="Screenshot 2025-08-06 213000" src="https://github.com/user-attachments/assets/1ebfdb4b-d0e4-44e5-bd2d-c5b19ff3321a" />

- Select VPC you create in current region - click attach internet gateway
<img width="1896" height="867" alt="Screenshot 2025-08-06 213025" src="https://github.com/user-attachments/assets/7a8e24dc-59a1-4028-8e82-6ae128e92f56" />

