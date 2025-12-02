# aws-vpc-project

Custom Network Setup on AWS.

This project demonstrates how to design and deploy a fully customized Virtual Private Cloud (VPC) architecture on AWS, including public/private subnets, Internet & NAT gateways, EC2

instances, and VPC Peering between two VPCs.

The goal is to understand AWS networking end-to-end and practice real-world cloud architecture design.


Project Overview:

This repository contains all configurations and screenshots for building:

*A custom VPC

*Public + private subnets

*Internet & NAT gateways

*Route tables and security configurations

*EC2 instances inside both subnets

*A second VPC for peering

*VPC Peering connection + route updates for inter-VPC communication.

Architecture Includes:

VPC A (Primary VPC):

* Custom VPC

* Public subnet

* Private subnet

* Internet Gateway

* NAT Gateway

* Route Tables (Public + Private)

* EC2 instances placed inside public and private subnets

🔷 VPC B (Secondary VPC for Peering)

* Custom VPC (e.g., 20.0.0.0/16)

* Subnets

* EC2 instance for connectivity testing.

🔗 VPC Peering:

* Peering connection from VPC A → VPC B

* Route table updates in both VPCs

* Security group updates to allow inter-VPC traffic.


Architecture Diagram:

![vpc_architecture](https://github.com/user-attachments/assets/cb436fd7-5d99-49c6-826d-1f7d239de484)

Services Used:

* Amazon VPC

* Subnets

* Route Tables

* Internet Gateway

* NAT Gateway

* Elastic IP

* EC2

* Security Groups

* Key Pairs

* VPC Peering.
* 

Step-by-Step Workflow:

1️⃣ Create a Custom VPC:

*Choose IPv4 CIDR (example: 10.0.0.0/16)

*Enable DNS hostnames + DNS resolution.



2️⃣ Create Public and Private Subnets:

*2 public subnets (e.g., 10.0.1.0/24, 10.0.2.0/24)

*2 private subnets (e.g., 10.0.3.0/24, 10.0.4.0/24)

*Spread them across multiple availability zones for high availability.

3️⃣ Attach an Internet Gateway:

*Create IGW

*Attach to VPC

*Update public route table to route 0.0.0.0/0 → IGW.

4️⃣ Create NAT Gateway:

*Allocate Elastic IP

*Place NAT Gateway in a public subnet

*Update private route table:
0.0.0.0/0 → NAT Gateway

5️⃣ Launch EC2 Instances:

*Public instance → accessible via SSH

*Private instance → accessible only through public instance.

6️⃣ Configure Security Groups:

*Allow SSH only from specific sources

*Restrict all private subnet access to internal communication only.

Testing the Setup:

* SSH into the public instance using key pair.
  
* From the public instance, SSH into the private instance.
  
* Verify internet access from private instance (via NAT Gateway).

Learning Outcomes:

*Deep understanding of AWS networking.

*Designing VPC architectures manually.

*Hands-on with routing, IGWs, NAT Gateways.

*Working with public vs private subnets.

*Secure deployment of EC2 instances.

*Configuring network-level security.


