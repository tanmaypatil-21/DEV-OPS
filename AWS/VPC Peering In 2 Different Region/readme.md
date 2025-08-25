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

**$$\color{red}\textbf** 1. set region for VPC A (US-EAST-1) and create VPC$$**
<img width="1902" height="861" alt="Screenshot 2025-08-09 191417" src="https://github.com/user-attachments/assets/a03899cc-2b69-471d-9768-c97f9c57dce6" />

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

- Done this IGW is Attached
<img width="1898" height="858" alt="Screenshot 2025-08-06 213054" src="https://github.com/user-attachments/assets/cefee309-140c-4afc-b726-c100645ea9b5" />

- Now create a Route Table
- click route table - create route table
<img width="1895" height="867" alt="Screenshot 2025-08-06 213113" src="https://github.com/user-attachments/assets/30dd9a9f-90d4-4c52-8edf-06d17ef40f68" />

- Name Route table - select VPC you create current region - click create route table
<img width="1897" height="864" alt="Screenshot 2025-08-06 213218" src="https://github.com/user-attachments/assets/cc606137-c45d-4d2d-9bea-324848ba6978" />

- Now we need to Associate our subnet with route table
- Again go to route table - select RT - subnet Associations - click Edit Subnet Association
<img width="1889" height="860" alt="Screenshot 2025-08-06 213337" src="https://github.com/user-attachments/assets/0180be72-33f7-4c9e-bea4-58c7b70f3577" />

- Select Subnet - Save association
<img width="1898" height="865" alt="Screenshot 2025-08-06 213410" src="https://github.com/user-attachments/assets/045894b3-8463-45cc-8d55-b2255fae6d1a" />

- Done this subnet Associated with route table
<img width="1885" height="858" alt="Screenshot 2025-08-06 213440" src="https://github.com/user-attachments/assets/e775bb7f-8a1b-4856-919b-0ac7bf2e0d85" />

- Now we need to update routes
- Go Route table - select routes - edit routes
<img width="1899" height="867" alt="Screenshot 2025-08-06 213502" src="https://github.com/user-attachments/assets/e303f2ce-79c7-4b90-b0bf-82c084fe0fb8" />

- Add routes - select 0.0.0.0/0 - select IGW and select IGW you created -save changes
<img width="1894" height="854" alt="Screenshot 2025-08-06 213543" src="https://github.com/user-attachments/assets/852adedc-29d5-4a0d-9293-bbefb3b36e60" />

- Done RT is updated
<img width="1893" height="867" alt="Screenshot 2025-08-06 213600" src="https://github.com/user-attachments/assets/10fd719a-d8f5-4cbf-a888-d949ec4de120" />

**Now we created EC2 instance in both of inter region VPC**

- Now first we create instance in **US-EAST-1**
 
- Go to EC2 - click launch instace
<img width="1884" height="868" alt="Screenshot 2025-08-06 213934" src="https://github.com/user-attachments/assets/f21d93c2-e4ed-4cdd-bfa1-fd334c86b664" />

- Name instance - select OS 
<img width="1913" height="964" alt="Screenshot 2025-08-06 214713" src="https://github.com/user-attachments/assets/e6dfb930-5172-469b-9ed8-cb971277e5a8" />

- select instace type (t3 micro) - create new key pair
<img width="1919" height="623" alt="Screenshot 2025-08-06 214727" src="https://github.com/user-attachments/assets/f91e2613-1573-4c1a-b85a-687d1fee031a" />

- Now edit Network setting
- select VPC you create - select subnet or automatic apply - auto assign public id (eneble) - name security group - description
<img width="1226" height="822" alt="Screenshot 2025-08-06 214753" src="https://github.com/user-attachments/assets/134de9cc-8d4b-4c6c-99d4-ffa8492d7af1" />

- Change security inbound rules
- click add security group rule 2 and add this - default storage - click launch instace
<img width="1906" height="1079" alt="Screenshot 2025-08-06 214815" src="https://github.com/user-attachments/assets/91ad7da4-ba75-4693-9ef2-c0f8ca92e736" />

- Now we create instance in **AP-SOUTHEAST-1**

- Go to EC2 - click launch instace
<img width="1889" height="869" alt="Screenshot 2025-08-06 214903" src="https://github.com/user-attachments/assets/a6fdac7c-b818-4c22-89b2-018551f987e0" />

- Name instance - select OS
<img width="1904" height="1034" alt="Screenshot 2025-08-06 215551" src="https://github.com/user-attachments/assets/f3a6cbaf-296d-4643-8a46-5cd60a8d1c96" />

- select instace type (t3 micro) - create new key pair
<img width="1919" height="682" alt="Screenshot 2025-08-06 215606" src="https://github.com/user-attachments/assets/c34a7cfb-174c-4453-b19a-dbe526d966a3" />

- Now edit Network setting
- select VPC you create - select subnet or automatic apply - auto assign public id (eneble) - name security group - description
<img width="1238" height="839" alt="Screenshot 2025-08-06 215619" src="https://github.com/user-attachments/assets/5e8cd916-2083-4b81-9a57-aeccc438cc37" />

- Change security inbound rules
- click add security group rule 2 and add this - default storage - click launch instace
<img width="1227" height="947" alt="Screenshot 2025-08-06 215637" src="https://github.com/user-attachments/assets/082bcbb5-c2e7-4eb0-9767-2af35dfe06fb" />

**Now get peering connection in both servers**

- Go to first **US-EAST-1** region
- Click peering connection - Create peering connection
<img width="1894" height="856" alt="Screenshot 2025-08-06 220713" src="https://github.com/user-attachments/assets/602779d7-364a-48ef-a596-2b0fac3d31fd" />

- Name peer connection - select requster vpc id create in another region - my account
<img width="1890" height="857" alt="Screenshot 2025-08-06 221148" src="https://github.com/user-attachments/assets/d5432951-b553-4eea-8520-d0bb70be89de" />

- Select another region (you create peer in another region so select this)
- we need accpeter vpc id so jump to anoter region **AP-SOUTHEAST-1** - select vpc and in details copy vpc id and paste accepter block - click create peering connection
<img width="1896" height="869" alt="Screenshot 2025-08-06 221157" src="https://github.com/user-attachments/assets/a6a8aeb3-84ee-4d70-a762-e58063bb4fc8" />

- Vpc peering connection is done requst sent
<img width="1896" height="854" alt="Screenshot 2025-08-06 221220" src="https://github.com/user-attachments/assets/9234a9c5-742e-48b4-8240-1856ddf460aa" />
  
- Now jump to anoter region and accept this requst **AP-SOUTHEAST-1**
- show pending acceptance - go to actions - accept requst - done 
<img width="1892" height="862" alt="Screenshot 2025-08-06 221306" src="https://github.com/user-attachments/assets/703e97d2-1845-46cf-a743-c5c9fe822438" />

- Now once update a route table go to **US-EAST-1** region
- Go to route table - select routes - routes - edit routes
<img width="1895" height="868" alt="Screenshot 2025-08-06 221540" src="https://github.com/user-attachments/assets/08cbebb1-d64a-424a-a917-fe42da8eda4f" />

- Add rule - need **AP-SOUTHEAST-1** vpc IPv4 CIDR no. copy - paste into route rule in **US-EAST-1** - select peering connection - slect pcx connection - save changes
<img width="1898" height="869" alt="Screenshot 2025-08-06 221807" src="https://github.com/user-attachments/assets/944bc014-4708-42a4-b531-470e82a7b556" />

- Done successfully update peering in **US-EAST-1**
<img width="1896" height="862" alt="Screenshot 2025-08-06 221825" src="https://github.com/user-attachments/assets/d2941259-8a01-4c51-b9fa-9638c7ab2eda" />

- Same thing do in **AP-SOUTHEAST-1** region
- copy IPV4 CIDR no. of **US-EAST-1** - go routes table - select routes - edit routes
<img width="1893" height="870" alt="Screenshot 2025-08-06 221903" src="https://github.com/user-attachments/assets/9229be61-637a-4b19-8cce-c22e8838ba3f" />

- Add rule - paste IPVR CIDR no. of **AP-SOUTHEAST-1**  - select peering connection - slect pcx connection - save changes
<img width="1904" height="868" alt="Screenshot 2025-08-06 222004" src="https://github.com/user-attachments/assets/7993d931-3b23-4138-8bcd-db078903b151" />

- Done successfully update peering in **AP-SOUTHEAST-1**
<img width="1901" height="877" alt="Screenshot 2025-08-06 222019" src="https://github.com/user-attachments/assets/2235ac1f-4afa-4c02-965e-484d5f688b02" />

**Now all setup is done chek peering connection , so you can use terminus or mobaxtrem to connect your instance**
- Connect both instance in terminus and use command **PING**
- Now  here copy 1st **AP-SOUTHEAST-1** servers public ip address - paste into **US-EAST-1** terminus - like (ping <ip-address>)
- And
- 2nd copy  **US-EAST-1** servers public ip address - paste into **AP-SOUTHEAST-1** terminus - like (ping <ip-address>)

- Done peering connection
- **US-EAST-1**
<img width="1919" height="1008" alt="Screenshot 2025-08-06 222743" src="https://github.com/user-attachments/assets/327cb287-29df-4d0f-acc0-2e0e5c66f6a8" />

-  **AP-SOUTHEAST-1**
 <img width="1919" height="1011" alt="Screenshot 2025-08-06 222751" src="https://github.com/user-attachments/assets/28de8011-8f57-4beb-a8d4-c6a61fff1590" />

# Conclusions:
Inter-region VPC peering provides a secure and efficient way to connect VPCs across AWS regions using private IP addresses. With proper routing and security group setup, this enables low-latency, high-throughput communication between applications in different geographic locations without exposing data to the internet.
