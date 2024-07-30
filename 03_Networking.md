## Networking

### 1. VCN Introduction

VCN (Virtual Cloud Network) is a private network that lives in an OCI region, and is used for secure communication.

Main features:
- Highly available
- Scalable
- Secure

#### 1.1 VCN Address Space

- Each VCN has an Address Space (a CIDR block, or IP range).
- OCI default CIDR block is 10.0.0.0/16, but it can be changed on creation.
- The VCN can be broken into Subnets (smaller networks), which can be public or private.

#### 1.2 Communication

![image](https://github.com/user-attachments/assets/4723758a-cfe9-461f-ab7b-6798b9fea75a)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189890)

With internet:
- Internet Gateway: massively scalable, highly available, allows **bidirectional** communication with the internet.
- NAT Gateway: massively scalable, highly available, allows **unidirectional** (outbound) communication to the internet.

Internal:
- Service Gateway: used to access public OCI services (such as Object Storage) without using internet, in a secure manner.

With on-premises:
- Dynamic Routing Gateway: path for private path between a VCN and an on-premises environment.

More detailed picture: 
![image](https://github.com/user-attachments/assets/6284b5be-20bb-44f3-9fdc-cc9caef88e69)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142095)

### 2. VCN Routing

#### 2.1 Route Tables

- Route tables are needed to stablish communication with the internet, on-premises network or peered VCN.
- It consists of a destination CIDR block + a route target.
- Communication inside the VCN, even if between different subnets, does not require route tables.
- More specific routes get higher priority.

#### 2.2 VCN Peering

- VCN peering in the same region uses Local Peering Gateways (LPGs).
- VCN peering between different regions uses Dynamic Routing Gateways (DRGs).

![image](https://github.com/user-attachments/assets/c5be4c1a-6237-42db-b0e7-9d9281b79137)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142175)

- For peering between up to 300 VCNs, there is Dynamic Routing Gateway v2 (DRG-V2).

![image](https://github.com/user-attachments/assets/7091b868-1fed-4f34-b8d3-919b56b79c2c)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142175)


### 3. VCN Security

#### 3.1 Security Lists

- Security Lists are like firewall rules for the subnets.
- The rules can be stateful or stateless.

![image](https://github.com/user-attachments/assets/8eee1b09-9363-4abf-8f61-ba2f05c4cfee)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142146)

#### 3.2 Network Security Group (NSG)

- The difference is that these applies only to a set of virtual network interface cards in a single VCNs
- NSGs can also be the source or destination of a rule

![image](https://github.com/user-attachments/assets/939bb7dd-3229-4f2b-a169-4a0116c4ee56)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142146)


### 4. Load Balancer

Reasons to use a Load Balancer:
- achieve high availability
- achieve high scalability

#### 4.1 Layer 7: HTTP/S Load Balancer

- Scalablity can be configured in two shapes:
  - Flexible shape: you define the minimum and maximum of traffic, between 10 Mbps to 8 Gbps
  - Dynamic shapes: there are pre-defined shapes (micro, small, medium, large) to choose, the load balancer does not require warm up, and it automatically scales
- It can be public or private
- Advanced features, such as (but not limited to):
  - Content-based routing
  - SSL features

![image](https://github.com/user-attachments/assets/9bf85e96-0b5e-441e-8634-2b2765388af5)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142147)

#### 4.2 Layer 3/4: Network Load Balancer

- Understands TCP, UDP and supports ICMP
- It can be public or private
- Much faster than HTTP/S Loadbalancer (it has much lower latency)
- But HTTP/S Loadabalancer has a higher level of intelligence, because it can look/inspect the packets

![image](https://github.com/user-attachments/assets/b3f3ea18-445b-4fb4-aa76-2c6de79ca993)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142147)
