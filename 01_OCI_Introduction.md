## OCI Introduction

### 1. OCI Overview

7 major categories of services:

![image](https://github.com/user-attachments/assets/88ad8258-4bde-42d5-bc84-80213392c0f6)

### 2. OCI Architecture

Region:
- localized geographic area
- comprised by one or more Availability Domains (AD)

Availability Domains (AD):
- Fault tolerant set of data centers within a region
- Each data center connected to others by low latency, high bandwith network

Fault Domains (FD):
- grouping of hardware and infrastructure within an AD
- provide antiaffinity
- logical datacenters

As of March 2023: 
- 41 regions (9 more planned)
- 12 Azure Interconnect Regions
- Dedicated region Cloud@Customer: differentiated hybrid cloud offering

#### 2.1 Choosing a region:
- Location: closest to users -> low latence and highest performance
- Data Residency & Compliance
- Service Availability -> some services are available only in specific regions

#### 2.2 Availability Domains (AD)

- Isolated from each other
- Fault tolerant
- Unlikely to fail simultaneously -> Physical infrastructure is not shared

![image](https://github.com/user-attachments/assets/5338697a-b1d3-4343-8d31-f89671a10d55)

#### 2.3 Fault Domains (FD)

- Each AD has 3 FDs
- Logical data center within an AD
- Resources placed in differente FDs will not share single points of hardware failure
- Change procedures in a region happen at most in ONE fault domain each time, so availability problems caused by changed procedures are isolated at FD level
- At instance launch time you can control the FD placement of compute or database instances

 ![image](https://github.com/user-attachments/assets/0d3b1051-f266-46d3-8958-4d490d00c84c)

#### 2.4 In summary, use ADs and FDs to avoid single points of failure

- Design your architecture to deploy instances that perform the same tasks...
- in different FDs inside one AD...
- and in different ADs for multiple regions

![image](https://github.com/user-attachments/assets/10df987e-8dd6-4a10-99b1-c9d4f63063c3)

![image](https://github.com/user-attachments/assets/6e3f5882-e763-4065-a09a-6b90b8273246)


### 3. OCI Distributed Cloud

Distributed cloud offers exceptional flexibility and choice. Oracle offers:

- Public cloud with 41+ global rgions, including:
  - Commercial
  - US Government
  - UK Government
  - US National Security Regions
  - EU Sovereign
- Hybrid cloud, including:
  - Oracle Exatada Cloud@Customer
  - Oracle Roving Edge Infrastructure
  - OCI Observability and Management
  - Oracle Database
- Dedicated cloud (a type of Hybrid cloud), when it runs in customer data centers, including:
  - OCI Dedicated Region
  - Oracle Alloy
- Multicloud, when Oracle products work with other providers, including:
  - Oracle Database Service for Azure
  - Oracle Interconnect for Azure
  - Oracle MySQL Heatwave on AWS

#### 3.1 Hybrid Cloud Services

![image](https://github.com/user-attachments/assets/3fc08ae0-3085-4d88-a085-967364d0670e)

#### 3.2 Dedicated Region Cloud@Customer

![image](https://github.com/user-attachments/assets/8145d378-cad1-4868-8a95-fe97e6cc8462)

#### 3.3 Multicloud: OCI-Azure Interconnect

![image](https://github.com/user-attachments/assets/15ab48f1-445f-4bb3-8576-89430d2875b7)

#### 3.4 Multicloud: Oracle Database Service for Azure

![image](https://github.com/user-attachments/assets/0518b986-800f-4608-85cc-9ac5603b5dca)
