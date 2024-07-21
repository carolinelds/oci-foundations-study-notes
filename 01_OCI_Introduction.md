## OCI Introduction

### 1. OCI Overview

7 major categories of services:

![image](https://github.com/user-attachments/assets/88ad8258-4bde-42d5-bc84-80213392c0f6)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/221326)

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

As of July 2024: 
- 48 regions (commercial, government and sovereign regions)
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
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189909)

#### 2.3 Fault Domains (FD)

- Each AD has 3 FDs
- Logical data center within an AD
- Resources placed in differente FDs will not share single points of hardware failure
- Change procedures in a region happen at most in ONE fault domain each time, so availability problems caused by changed procedures are isolated at FD level
- At instance launch time you can control the FD placement of compute or database instances

![image](https://github.com/user-attachments/assets/fcaf37df-e4c8-4e11-8ff8-9b72dc887acc)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189909)

#### 2.4 In summary, use ADs and FDs to avoid single points of failure

- Design your architecture to deploy instances that perform the same tasks...
- in different FDs inside one AD...
- and in different ADs for multiple regions

![image](https://github.com/user-attachments/assets/10df987e-8dd6-4a10-99b1-c9d4f63063c3)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189909)

![image](https://github.com/user-attachments/assets/6e3f5882-e763-4065-a09a-6b90b8273246)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189909)

### 3. OCI Distributed Cloud

Distributed cloud offers exceptional flexibility and choice. Oracle offers:

- Public cloud with 48 global rgions, including:
  - Commercial
  - US Government
  - UK Government
  - US National Security Regions
  - EU Sovereign
- Hybrid cloud, including:
  - Oracle Cloud@Customer
  - Oracle Roving Edge Infrastructure
- Dedicated cloud (a type of Hybrid cloud), when it runs in customer data centers, including:
  - OCI Dedicated Region
- Multicloud, when Oracle products work with other providers, including:
  - Oracle Database@Azure
  - Oracle Interconnect for Azure
  - Oracle MySQL Heatwave on AWS

#### 3.1 Multicloud: Oracle Database@Azure

![image](https://github.com/user-attachments/assets/4ce76c71-cde5-451c-9553-9f581ed31b87)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/221635)

#### 3.2 Hybrid Cloud Services

![image](https://github.com/user-attachments/assets/7d8bfc22-0c63-4f0f-9e26-d4fc08ea31ce)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/221635)

#### 3.3 Dedicated Region Cloud@Customer

Follows a shared responsibility model with the customer. Generally used due to data residency & compliance requirements, and to reduce latency.

![image](https://github.com/user-attachments/assets/8145d378-cad1-4868-8a95-fe97e6cc8462)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/221635)
