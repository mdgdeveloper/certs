# AZ-104 Manage identities and governance in Azure

## Azure Active Directory (Azure AD)
- Internal resources and apps located on your corporate network.
- External resources like Microsoft 365, the Azure portal, and SaaS applications.
- Cloud apps developed for your organization.

### Azure AD features
| Azure AD Feature | Description |
| --- | --- |   
| **Singe sign-on (SSO) access** | For WebApps (both Cloud/On Prem) |
| **Ubiquitous device support** | For Windows, Mac, iOS, Android, and Linux |
| **Secure remote access** | For on-premises apps |
| **Cloud extensibility** | Manage a consistent set of users, pass and devices across environmentrs | 
| **Sensitive data protection** | Protect sensitive data stored in the cloud |
| **Self-service** | Users can reset their passwords, and request access to applications |

### Azure AD Concepts
| **Azure AD concept** | **Description** |
| --- | --- |
| **Tenant** | A dedicated and trusted instance of Azure AD that's automatically created when your organization signs up for a Microsoft cloud service subscription, such as Microsoft Azure, Microsoft Intune, or Microsoft 365. |
| **Directory** | A container for apps, users, groups, and more. |
| **User** | A user account that exists in a tenant. |
| **Group** | A collection of users. |
| **Application** | A cloud app, such as Salesforce, that is registered in a tenant and can be used for authentication. |
| **Service principal** | An identity that is used by a service or app for authentication. |
| **Role** | A collection of permissions that can be assigned to a user, group, service principal, or managed identity at a particular scope. |
| **Role assignment** | The process of binding a role definition to a user, group, service principal, or managed identity at a particular scope. |
| **Role definition** | A collection of permissions that can be used to perform a particular task. |
| **Scope** | The set of resources that a role definition can be assigned to. |

| **Azure AD concept** | **Description** |
| --- | --- |
| **Identity** | Identity authentication is the process of verifying an entity, such as a user, application, or server, using unique credentials like usernames, passwords, secret keys, or certificates, with Azure AD being a popular service that provides this functionality. |
| **Account** | An account is a container for authentication information. It's uniquely identified by a username and password, or by a service principal. | 
| **Azure AD account** | Identity created through Azure AD or another MS Cloud Service (M365) |
| **Azure tenant(directory)** | An instance of Azure AD dedicated to an organization. Each tenant represents a single organization. You can create multiple tenants or instances |
| **Azure subscription** | A logical container used to provision resources in Azure. It holds the details of all your resources like virtual machines (VMs), databases, and more. Each subscription is joined to a single tenant. You can have multiple subscriptions. |


### Differences between Azure AD and AD DS 
- Azure AD is a cloud-based identity and access management service hosted in Microsoft Azure datacenters, whereas AD DS is the on-premises directory service included with Windows Server.

- **Identity solution**: AD DS is a directory service while Azure AD is a **full identity solution**. Azure AD is designed for internet-based applications (HTTP/HTTPS) 

- **Commuinication protocols**: AD DS uses Kerberos, NTLM, LDAP, and DNS, whereas Azure AD uses SAML 2.0, WS-Federation, and OAuth 2.0.

- **Federation services**: Azure AD includes federation services

- **Flat structure**: Azure AD users and groups are created in a flat structure (No OUs or GPOs)

- **Managed service**: You manage only users, groups and policies. Microsoft manages the underlying infrastructure.

### Azure AD editions
- **Free**: Manage user accounts, synchronize with on-premises directories, get single sign-on across Azure, Office 365, and thousands of popular SaaS applications like Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more.
- **Office 365 apps**: Includes all Free edition features, plus group-based access management, self-service password reset for cloud applications, Azure AD Application Proxy, and security reporting.
- **Premium P1**: Includes all Office 365 apps edition features, plus self-service password reset for on-premises applications, advanced security reports, Microsoft Identity Manager (an on-premises identity and access management suite), and Microsoft Cloud App Security.
- **Premium P2**: Includes all Premium P1 edition features, plus Azure Active Directory Identity Protection (detects vulnerabilities and risk events related to user identities), Azure Active Directory Privileged Identity Management (provides time-based and approval-based role activation to mitigate risks), and Azure AD B2C (a consumer identity and access management solution that supports customer and citizen access to web and mobile applications).


### AD Join
- Connection options
    - Register
    - Join: Extension of registering a device. 
- Combine using MDM (Mobile Device Management) like Intune.

## Role-Based Acces Contrl (RBAC)
- **Security principal**: Object which represents something that requests access to resource (users, groups, managed identity, service principal)
- **Role definition**: Set of permissions
- **Scope**: Boundary of requested level of access
- **Assignment**: Attaches a role definition to a security princpial in an specific scope

### Interesting things to know about RBAC

* The purpose of a role assignment is to control access.
* The scope limits which permissions defined for a role are available for the assigned requestor.
* Access is revoked by removing a role assignment.
* A resource inherits role assignments from its parent resource.
* The effective permissions for a requestor are a combination of the permissions for the requestor's assigned roles, and the permissions for the roles assigned to the requested resources.

## User Accounts in Azure AD
### Permissions and roles
User assigned - inherit permissions from that role. 

### Administrator roles 
Allow users elevated access to control who is allowed to do what. 

Powershell:
```powershell 
New-AzureADUser
```

Azure CLI: 
```powershell
az ad user create
```

### Member users
- Native member of Azure AD 
- Set of default permissions
- Considered internal 

### Guest users 
- Restricted Azure AD org permissions
- Considered external

### Add user accounts
- Azure CLI:
```powershell
# Create a new user
az ad user create
```

- Azure Powershell:
```powershell
# Create a new user
New-AzureADUser
```

Example on how to bulk invite guest users
```powershell
$invitations = import-csv c:\path\invitations.csv

$messageInfo = New-Object Microsoft.Open.MSGraph.Model.InvitedUserMessageInfo

$messageInfo.customizedMessageBody = "Hello. You are invited to join Contoso. Please click the link below to join."

foreach($email in $invitations)
{
    New-AzureADMSInvitation `
    -InvitedUserEmailAddress $email `
    -InvitedUserDisplayName $email.Name `
    -InviteRedirectUrl https://myapps.microsoft.com `
    -InvitedUserMessageInfo $messageInfo `
    -SendInvitationMessage $true
}

```

### Remove user accounts
```powershell
# Rmove user
Remove-AzADUser -ObjectId <objectID>
```

### Access management
- Azure AD Roles: Azure AD-related resources like users, groups, billing, licensing, application registration, etc.
- Role-based access control (RBAC): Azure resources like VMs, storage, databases, etc.

### Azure AD Access
- Direct assignment
- Group assignment
- Rule-based assignment 


## Azure RBAC 
Azure role-based access control (Azure RBAC) is an authorization system built on Azure Resource Manager that provides fine-grained access management for resources in Azure. 

### How it works
1. Security principal (WHO)
2. Role definition (WHAT)
    - Owner
    - Contributor
    - Reader
    - User Access Administrator
3. Scope (WHERE)
4. Role assignment (HOW)

### Azure RBAC is an allow model
When you're assigned a role, Azure RBAC allows you to perform certain actions, such as read, write, or delete

Azure RBAC ```NotActions``` is computed by subtracting the actions in the role definition from the ```Actions```.

