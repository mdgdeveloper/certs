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
