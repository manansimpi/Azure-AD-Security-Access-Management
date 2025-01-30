# Azure-AD-Security-Access-Management(Part 1)
## Objective
   - Enhance the security and management of identities in Azure Active Directory (Azure AD) by implementing a structured approach to access control, risk-based authentication, privileged identity management, and continuous monitoring. This project aims to establish a robust identity protection framework that minimizes security risks, enforces least privilege access, and ensures compliance with best practices for securing cloud environments.

## Requirements
To successfully implement this project, the following prerequisites and resources are required:

1. Azure Environment :
An active Azure subscription with administrative access
A configured Azure Active Directory (Azure AD) tenant
2. Licensing & Features :
Azure AD Premium P2 license (required for Identity Protection and Privileged Identity Management)
Microsoft Entra ID (formerly Azure AD) for access control and authentication
3. User & Role Setup :
At least one Global Administrator for configuring security policies
Users assigned to various roles (e.g., Security Administrator, Compliance Administrator)
Groups configured for role-based access control (RBAC)
4. Security Policies & Controls :
Multi-factor authentication (MFA) enabled for users
Conditional Access policies configured for device compliance and risk-based sign-ins
Risk-based policies for detecting risky sign-ins and users
5. Privileged Access Management :
Privileged Identity Management (PIM) enabled for just-in-time (JIT) access
Approval workflows and MFA enforcement for role activation
6. Monitoring & Incident Response :
Azure AD logs enabled for tracking identity activities
Alerts configured for suspicious sign-ins and privilege escalations
Automated workflows for incident response and risk mitigation


## Phase 1: Initial Setup and Configuration of Azure AD

### Objective

- Establish a secure Azure Active Directory (Azure AD) environment for managing identities and access in the cloud.

### Implementation Details

1. Azure AD Tenant Creation

Logged into the Microsoft Entra Adim Center portal and navigated to the Overview Section then to Manage Tenants.

Created a new Azure AD tenant and configured basic settings.

![Screenshot 2025-01-28 235043](https://github.com/user-attachments/assets/adb81046-4ce7-4db1-bfa4-0c6ea828729c)


Verified domain settings and linked the tenant to an existing subscription.

2. User and Group Setup

Creating new users that can be assigned to relevant groups so that we can delegate roles to the entire group makes it easier but I haven't since this would be considered a small project.



![1 1](https://github.com/user-attachments/assets/9bd4916a-c758-4023-a5ac-a6f898521230)

<br><br>

![Screenshot 2025-01-29 000033](https://github.com/user-attachments/assets/c7216db0-9cd4-4ca1-a3fc-a010d0aa9572)

<br><br>

3. Assigned built-in roles(Reader, Contributor, Owner) to groups for better role delegation.  

![Screenshot 2025-01-28 130253](https://github.com/user-attachments/assets/1c401285-c604-4f52-8cd6-dd16e06dc5e8)

<br><br>

![Screenshot 2025-01-28 130229](https://github.com/user-attachments/assets/0cb4fa62-e794-429a-b7fa-4d385d9d6cd9)

<br><br>

![Screenshot 2025-01-28 221250](https://github.com/user-attachments/assets/1757830c-886b-4316-96ed-1a97f0efae8f)

<br><br>

![Screenshot 2025-01-28 223258](https://github.com/user-attachments/assets/dd8926dc-0442-404a-8f6f-7f8ea3c8488b)

<br><br>


4. Configuring RBAC for Secure Access

- Navigated to Azure Subscription > IAM (Identity & Access Management).

- Created custom roles where necessary for specific access control.

![Started Creating Custom Role](https://github.com/user-attachments/assets/73fb44a3-21f0-46b0-874d-703c3ddd720b)

<br><br>

![Screenshot 2025-01-28 223854](https://github.com/user-attachments/assets/dbeae0eb-eb9f-4cbd-8dda-f9a666d916aa)

<br><br>


- Since Roles are made up of a combination of Permissions we are adding all the permissions required for this Role.
  
![Screenshot 2025-01-28 223923](https://github.com/user-attachments/assets/ffb2b33c-0477-41ce-b572-5a36bca54370)


<br><br>

![Screenshot 2025-01-28 224144](https://github.com/user-attachments/assets/72f7bc1f-2088-4fa6-b7f3-b0405fb8edb8)


<br><br>

![Screenshot 2025-01-28 224451](https://github.com/user-attachments/assets/1b48ec10-7824-4811-b463-ca3ea4ab53e3)

<br><br>

![Screenshot 2025-01-28 224513](https://github.com/user-attachments/assets/1c182c4c-0adb-4dbb-8e96-000e17db13a6)

<br><br>

- The Subscription wherein we want this role.

![Screenshot 2025-01-28 224547](https://github.com/user-attachments/assets/185102d1-6841-4076-b76e-ddf09841a86e)

<br><br>

- Auto-generated Role in JSON Format based upon our requirements.

![Screenshot 2025-01-28 224612](https://github.com/user-attachments/assets/e73eb4d6-a4bb-4ad8-bf90-8dda18386331)

<br><br>

5. Assigning this role to the required User.

- Again navigated to Azure Subscription > IAM (Identity & Access Management).

![T1](https://github.com/user-attachments/assets/64f215dc-3aa0-4a64-9771-661ae582a362)

<br><br>

![Screenshot 2025-01-28 230314](https://github.com/user-attachments/assets/37fa7dcb-2523-4d7f-9971-9aa667dbffae)

<br><br>

![Screenshot 2025-01-28 230650](https://github.com/user-attachments/assets/e40e88e2-4503-4e25-b0d8-1202f2eed535)

<br><br>

![Screenshot 2025-01-28 230714](https://github.com/user-attachments/assets/6e4eab14-b0cb-4859-bf57-ba769c6e113b)

<br><br>

![Screenshot 2025-01-28 232134](https://github.com/user-attachments/assets/541658dd-b5c8-461f-b629-921f0158b4ee)



## Verification & Testing

### Tested user access and role assignments by logging in with different user accounts.

- Logging from **NewUser** with the Global Administrator role and trying to create a new temporary Test User.

![Screenshot 2025-01-29 210337](https://github.com/user-attachments/assets/81c6eb1e-9711-4058-ae81-7ef6f7e53031)

<br><br>

![Screenshot 2025-01-29 212627](https://github.com/user-attachments/assets/f9353c7f-0538-41f8-8d34-401083aaed08)

<br><br>

### Ensured that users with limited roles cannot perform restricted tasks.

- Tried to do the same from User1(U1) with Global Reader but failed.
  
![Screenshot 2025-01-29 213225](https://github.com/user-attachments/assets/65d9c4de-c672-4a27-91be-738d3d4e8131)







### Validating if RBAC policies were enforced properly.

- But first, let's give Reader Access to U1(User1) so that it can access the resource of that resource group. In our case, we need to test if we can Start and Stop the Virtual Machine so we need access to the Resource group and the VM running.

![Screenshot 2025-01-29 221049](https://github.com/user-attachments/assets/2c2712f0-6009-49a5-9c78-b0e7c411fbfe)

<br><br>

![Screenshot 2025-01-29 221110](https://github.com/user-attachments/assets/fb8a638f-ffbf-4fda-9338-0d26de8b02ba)

<br><br>

![Screenshot 2025-01-29 221211](https://github.com/user-attachments/assets/1cec3795-3cc7-4bb5-ac18-57f73eff9949)

<br><br>

![Screenshot 2025-01-29 221211](https://github.com/user-attachments/assets/b15ac0ba-07a2-4a1a-9355-ca38b5108d58)

<br><br>

- So now the Subscription and the VM runnning is visible from the User1(U1) user and testing to Stop and Start it.

![Screenshot 2025-01-29 222039](https://github.com/user-attachments/assets/d67e8b6d-5c16-4c8a-940a-e018d5dafc14)

<br><br>

![Screenshot 2025-01-29 222055](https://github.com/user-attachments/assets/7cc6ea92-4ee0-4cae-bcc2-b70b954a0509)

<br><br>

![Screenshot 2025-01-29 222444](https://github.com/user-attachments/assets/8728f6ac-91f1-4139-b27b-5cae64dbf933)

- Now trying to delete the VM which obviously fails since we just have provided the permissions to Start and Stop the Vm.

![Screenshot 2025-01-29 222604](https://github.com/user-attachments/assets/2d603e37-8fc7-47ac-a8ca-32a58a202641)




