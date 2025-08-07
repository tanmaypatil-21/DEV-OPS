# Amazon VPC (Virtual Private Cloud) Documentation
## 1. Introduction
Amazon Virtual Private Cloud (VPC) allows you to launch AWS resources in a logically isolated network.
It gives you full control over your network environment, including IP address ranges, subnets, route tables, and network gateways.

## 2. Key Features
1. Custom IP Address Range – Choose your own IPv4 or IPv6 CIDR block.

2. Subnets – Divide the VPC into public and private sections

3. Route Tables – Control traffic flow within the VPC and outside

4. Security Groups & NACLs – Control inbound and outbound traffic at instance and subnet level.

5. Internet & NAT Gateways – Enable internet access for public/private subnets.

6. VPC Peering – Connect VPCs privately across regions or accounts.

## 3. Benefits
1. Logical network isolation

2. Enhanced security with multiple layers of control

3. Scalable and flexible network design

3. Integration with other AWS services

## 4. Components of a VPC
1. VPC – The main network container.

2. Subnets – Logical partitions of the VPC network.

3. Route Tables – Define where network traffic is directed.

4. Internet Gateway (IGW) – Allows communication between instances in your VPC and the internet.

5. NAT Gateway – Enables private subnets to access the internet securely.

6. Security Groups – Instance-level firewalls.

7. Network ACLs (NACLs) – Subnet-level firewalls.

8. Endpoints – Private connections to AWS services.

