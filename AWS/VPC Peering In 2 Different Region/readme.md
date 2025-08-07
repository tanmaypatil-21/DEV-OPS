# Amazon VPC (Virtual Private Cloud)
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

5. NAT Gateway – Enables private subnets to access the internet securely.9

6. Security Groups – Instance-level firewalls.

7. Network ACLs (NACLs) – Subnet-level firewalls.

8. Endpoints – Private connections to AWS services.

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

