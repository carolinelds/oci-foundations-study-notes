## Identity and Access Management

### 1. IAM Introduction

Allows user to be assigned one or more pre-determined roles, and each role comes with a set of permissions.

Also known as:
- Fine-grained Access Control
- Role Based Access Control

Key aspects:
- AuthN (authentication): who are you?
- AuthZ (authorization): what permissions do you have?

#### 1.1 Identity Domain

User population (users and groups) and associated configurations and security settings.

![image](https://github.com/user-attachments/assets/2889b995-0521-4046-9761-227484ba9567)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/165501)

#### 1.2 OCID

Each OCI resource have a unique Oracle-assigned identifier -> Oracle Cloud ID (OCID).

Format: ocid1.\<resource type\>.\<realm\>.[region][.future use].\<unique id\>
- ocid1: type of resource
- resource type: compute instance | block storage | etc
- realm: set of regions that share same characteristics (commercial | government | etc)

![image](https://github.com/user-attachments/assets/7a84a293-14cc-428a-bf60-666d90349a48)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/165501)

#### 1.3 Compartment

Collection of related resources. Use to isolate and control access.

![image](https://github.com/user-attachments/assets/a257e191-0909-4149-a5e9-96a3409c68f0)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142151)

Root Compartment can hold all the cloud resources, but the best practice is to create dedicated compartments to isolate resources:

- each resource belongs to a single compartment
- groups + policies => control access to Compartments
- resources can interact with other resources in other compartments
- resources can be moved from one compartment to another
- comparment is a global construct => resources from MULTIPLE regions can be in the SAME compartment

![image](https://github.com/user-attachments/assets/75f46533-df67-4ba4-b19a-9bb9b0544bff)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142151)

- comparments can be nested: up to 6 levels of nesting allowed
- you can set quotas and budgets on compartments

![image](https://github.com/user-attachments/assets/cc1613c8-d9ea-4baf-af84-51534aeffc2c)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/142151)

### 2. AuthN and AuthZ

#### 2.1 Principals

IAM entities that are allowed to interact with OCI resources.
Examples:
- IAM Users
- Resource Principals

#### 2.2 Groups

Collection of users who have the same type of access to resources.

#### 2.3 AuthN (authentication)

IAM authentication
- check IAM entity

API Signing Key
- using OCI API + SDK/CLI
- uses RSA key pair (PEM)

Auth Tokens:
- Oracle-generated token strings
- Authenticate third party APIs

#### 2.4 AuthZ (authorization)

AuthZ in OCI -> IAM policies

Policies are human readable statements to define granular permissions.
- Everything is denied by default
- Policy Attachment: to a compartment or the tenancy:

![image](https://github.com/user-attachments/assets/d04dbfe2-4051-441c-8f73-5f600851b5c6)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189910)

- General syntax:

![image](https://github.com/user-attachments/assets/cc6719f1-0c0d-4876-b408-ee8d47291ed7)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189910)

#### 2.5 IAM big picture

![image](https://github.com/user-attachments/assets/a31fdbcb-006d-4dbf-967d-ca218f2b21c0)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/189886)

Some notes:
- Policies can be assigned to groups, not to users
- When you create an IAM Domain, you associate it to a Compartment (e.g. Sandbox, Development, Root, etc)
- When you create an IAM Domain, it automatically comes with 2 default groups:
  - All_Domain_Users
  - Domain_Administrators
- Then you are able to create groups inside an IAM Domain
- And when you create a user you can assign it to a group or not
- And then you can create policies and assign them to groups, giving permissions to specific Compartments or to a Tenancy

#### 2.6 Tenancy Setup

![image](https://github.com/user-attachments/assets/f84d0e6a-db1b-45ec-961f-9890625a6252)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/165492)

Best practices:
- Don't use the Tenancy Administrator Account for day-to-day operations: create an administrator group inside the OCI account instead
- Create dedicated compartments to isolate resources: e.g. in the above picture, you could create more compartments inside the sandbox-compartment to isolate even more; and don't use the root compartment
- Enforce the use of Multi-Factor Autentication (MFA): something you know (e.g. password) + something you have (e.g. TOTP token from a device)

Examples of policies to provide for an OCI-admin-group so that it can act as a proxy for Tenancy Administrator (i.e. be used in day-to-day operations):

![image](https://github.com/user-attachments/assets/1a9c90b4-2535-43f5-be7e-0fe1d7da52ca)
Source: [Oracle University](https://mylearn.oracle.com/ou/course/oracle-cloud-infrastructure-foundations/139383/165492)




 





