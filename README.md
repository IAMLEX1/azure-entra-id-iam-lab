# 🔐 Azure Entra ID IAM Lab (ABAC + RBAC + SSO)

## 📌 Project Overview
Implemented an end-to-end Identity and Access Management (IAM) solution using Azure Entra ID, demonstrating automated access control with ABAC, RBAC, and Single Sign-On (SSO) integration with AWS.

## 🧠 Key Concepts Demonstrated
- Identity Lifecycle Management (JML)
- Attribute-Based Access Control (ABAC)
- Role-Based Access Control (RBAC)
- Single Sign-On (SSO)
- Cross-platform identity integration (Azure → AWS)

## 🔄 End-to-End IAM Flow

User → Attribute → Dynamic Group (ABAC) → Group Assignment (RBAC) → AWS SSO Access

## 🔧 Implementation Steps

### 👤 User Creation (Joiner)
- Created user in Azure Entra ID
- Assigned attributes (e.g., department = Finance)

### 🔹 ABAC (Dynamic Group)
- Created dynamic group using rule: user.department -eq "Finance"

- Users automatically added based on attributes

### 👥 RBAC (Group-Based Access)
- Assigned Finance dynamic group to AWS enterprise application
- Access controlled via group membership (not direct user assignment)
- Enforced least privilege through centralized group-based access

### 🔐 SSO Integration (Azure → AWS)
- Configured AWS enterprise application in Azure
- Enabled Single Sign-On (SSO)
- Users access AWS via SSO using Azure Entra ID authentication
- Enabled identity federation between Azure Entra ID and AWS for centralized access management

### 🔄 Identity Lifecycle (JML)

#### 🟢 Joiner
- User created with attributes

---

#### 🟡 Mover
- Updated user attribute (Finance → IT)
- User automatically removed from Finance group and added to IT group

**Attribute Change**

<img src="https://github.com/user-attachments/assets/c248d296-fa50-4c21-b6b9-dd3cf9f2d65b" width="800"/>

**New Group Assignment (IT)**

<img src="https://github.com/user-attachments/assets/bbaa6b60-a01d-43c9-a4b2-e15b704d18c0" width="800"/>


#### 🔴 Leaver
- Disabled user account
- Access revoked across applications

<img src="https://github.com/user-attachments/assets/93fc17be-030f-4b61-90f9-e9316ef77b44" width="800"/> 



- Verified lifecycle events using Azure Entra ID audit logs, confirming automated access changes during Joiner, Mover, and Leaver events

  
## 📸 Screenshots

### 👤 User Creation

<img src="https://github.com/user-attachments/assets/971e8aef-2f80-46a0-bf08-69f73e8e5bd8" width="800" />

### 🔹 ABAC (Dynamic Group)

<img src="https://github.com/user-attachments/assets/fc8188a1-af72-4513-b5b1-fb1984b3e57b" width="800" />

### 🔐 RBAC + SSO (Azure → AWS)
* Assigned Finance group to AWS enterprise application
* Access controlled via group membership (not direct user assignment)
* Enabled Single Sign-On (SSO) for AWS access
  
<img src="https://github.com/user-attachments/assets/975a3494-01c4-487a-aadd-7c6afe4b71b3" width="800" />

- This demonstrates centralized identity federation between Azure Entra ID and AWS, combining ABAC for dynamic access assignment and RBAC for controlled authorization.
  

## 📊 Audit & Monitoring
- Monitored identity lifecycle events using Azure Entra ID audit logs
- Verified user creation, group assignment, attribute updates, and account disable actions - Validated IAM lifecycle operations (Joiner, Mover, Leaver) via audit logs
- The audit logs below capture real-time identity lifecycle events including user creation, group updates, and account disable actions.
<img src="https://github.com/user-attachments/assets/cc86808e-6f80-4a99-83d3-4fde11892444" width="800" />

## 🚀 Outcome

Successfully demonstrated an IAM lifecycle solution where access changes are driven by user attributes, dynamic group membership, and group-based access control across Azure and AWS, with audit visibility into Joiner, Mover, and Leaver events.
