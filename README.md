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

🔶 VPC A (Primary VPC):

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

1️⃣ Build VPC A (Main VPC):

*CIDR: 10.0.0.0/16

*Create  public +  private subnets

*Attach Internet Gateway

*Create NAT Gateway

*Configure Route Tables

*Launch EC2 instances.

2️⃣ Build VPC B (Peering VPC):

*CIDR: 20.0.0.0/16

*Create subnets

*Launch one EC2 instance

*Configure its security group.

<img width="1366" height="662" alt="vpc" src="https://github.com/user-attachments/assets/2077418a-10c9-47db-a918-0b2907ccddb8" />


<img width="1366" height="662" alt="subnet" src="https://github.com/user-attachments/assets/2053b209-86ca-41b8-853b-cade0b8882c4" />


<img width="1366" height="662" alt="vpc_ec2" src="https://github.com/user-attachments/assets/8595e294-66e8-4509-939e-abbb93193458" />


<img width="1366" height="662" alt="vpc_testmap1" src="https://github.com/user-attachments/assets/310d6d0c-bffd-41bb-b287-56551fb2e305" />


<img width="1366" height="662" alt="prod_map1" src="https://github.com/user-attachments/assets/85102dec-7fec-42e4-a608-be6b947caf1a" />


<img width="1366" height="662" alt="igw" src="https://github.com/user-attachments/assets/9cc45d2c-3842-4c7a-895b-113c1e8a777c" />


3️⃣ Create VPC Peering Connection:

Steps:

1) Go to VPC Dashboard → Peering Connections

2) Create a new peering connection

3) Select:

*Requester VPC: VPC A

*Accepter VPC: VPC B

4) Accept the peering request

5) Verify connection status → Active.

<img width="1366" height="662" alt="vpc_peering" src="https://github.com/user-attachments/assets/e94543e8-4923-445e-bf69-562196a2d461" />


4️⃣ Update Route Tables for Peering:

1) In VPC A Route Tables:

Add route →

*Destination: 20.0.0.0/16

*Target: PeeringConnectionID

2) In VPC B Route Tables:

Add route →

*Destination: 10.0.0.0/16

*Target: PeeringConnectionID

<img width="1366" height="662" alt="routetables" src="https://github.com/user-attachments/assets/0028a1b0-ce71-4600-a5c1-bcd50f2d5772" />


5️⃣ Update Security Groups:

Allow inter-VPC communication:

* In VPC A EC2 SG → Allow inbound traffic from 20.0.0.0/16

* In VPC B EC2 SG → Allow inbound traffic from 10.0.0.0/16


<img width="1366" height="662" alt="ec2rules" src="https://github.com/user-attachments/assets/69256b2d-a211-4ec1-9be2-1c9bfa10b96e" />

<img width="1366" height="662" alt="ec2rulesprod" src="https://github.com/user-attachments/assets/5d827883-b844-4715-8ea0-1417ac4206c8" />


6️⃣ Test VPC Peering:

* SSH into EC2 instance in VPC A
  
* Ping the VPC B EC2 private IP
  
* SSH from VPC A instance → VPC B instance (if allowed)
  
* Validate successful inter-VPC communication.


<img width="1366" height="662" alt="testping" src="https://github.com/user-attachments/assets/2edc5995-199a-4d90-a963-1af1b5b00ef6" />

<img width="1366" height="662" alt="prodping" src="https://github.com/user-attachments/assets/1703f7ca-5227-45da-9a05-57570015dd4f" />


Learning Outcomes:

By completing this project, I learned:

*VPC design in AWS

*Public vs private subnets

*Internet and NAT gateway configuration

*Route table management

*Security group architecture

*EC2 networking basics

*Cross-VPC connectivity using peering

*CIDR segmentation and IP planning

This project significantly strengthened my understanding of AWS networking fundamentals.
