Microsoft Azure is a cloud service provider (CSP) that offers a varied and easy-to-use range of services.  Azure offers a range of services across the [[Shared-Responsibility Model]], from managed apps to almost baremetal VMs.

# Azure Subscriptions
To create and use Azure services you need an azure subscription. One Azure account can be made to provide multiple subscriptions for different departments. From each of those subscriptions you can create and distribute resources.

## Azure Free Account
Azure allows free access to the Azure suite in the form of a free account on the following basis:
- Free access to popular Azure products for 12 months
- A credit to use for the first 30 days
- Access to over 25 products that are always free.
The free account provides a gateway for people to explore Azure and decide if it's right for their business.

# Physical Infrastructure
Azure is built around datacenters distributed around the world. These distributed datacenters are grouped into regions or availability zones.
## Regions
Regions describe the physical locations of datacenters and groups physically nearby ones into regions. Through this, Azure can automatically pick which datacenter best suits a user's needs. Certain VM sizes and features are only available in specific regions, so choosing the right one is important.
## Availability Zones
Availability Zones are physically seperate datacenters within a region. Each Zone is made up of one or more datacenters equipped with independent power, cooling, and networking. If one zone goes down, the others should remain operating and functional. Zones within  a region are typically connected with dedicated high-speed fibre connections.
### Using Availability Zones
For users, Availability Zones are a way to ensure resiliency in services. When creating a VM, selecting multiple Availability Zones replicates your environments across into other zones. While this brings an added cost, it makes the process of adding redundancy much simpler. Three types of sercices can be distributed into availability zones:
- **Zonal Services**: You pin the resource to a specific zone
- **Zone-Redundant Services**: The platform automatically duplicates resources across zones
- **Non-Regional Services:** Services are always available from azure geographies and are reilient to zone-wide outages as well as region-wide outages
While Availablility Zones create a high degree of redundancy, it is still possible that an entire region is taken out. To resolve this, there are *Region Pairs*.
## Region Pairs
Region pairs describe two or more regions that are linked and at least 300 miles away from each other, whilst still being in the same geography. This means that in the event of a catastrophic regionwide event, services can be continued. Not every service can be automatically replicated, so it is still important that the user knows what services will be moved and what will have to be done manually. In the case of outages caused by natural disasters, these fall outside of the [[Azure SLAs]], and therefore the user is responisble for their resolution.
## Sovereign Regions
Sovereign Regions are completely isolated datacenters that are seperated from the rest of the Azure network. This is to allow for greater security of the whole datacenter and cloud infrastructure. This is primarily used in governmental and legal instances, and can only be accessed by specific parties.

# Resources & Resource Groups
A resource is a single deployed element in Azure. A resource group is simply a way of grouping and categorising these resources. Resources may only belong to a single resource group, however, a resource group may have many child resources. Moreover, resource groups cannot be nested. Resource groups allow you to apply actions to all children in the group easily. If you delete a resource group, all its children will be killed, for example. Resource groups are not governed or managed in any way by Microsoft, so it is completely up to the user to decide what configuration best suits their needs.

# Subscriptions
Subscriptions, like resource groups, are a way to organise and distribute billing, resource groups, and scale. Each subscription is paid seperately, allowing you to keep track of your expenditure at a larger scale. A subscription is required in order to provision resources. An account may have multiple, however, only one subscription is strictly required. There are two types of subscription boundaries:
- **Billing Boundaries:** This allows you to define different billing types between subscriptions, with each invoiced seperately.
- **Access Control Boundaries:** This allows you to seperate which accounts can access resources by which subscriptions they are granted access to.
## Creating Additional Subscriptions
You may create additional subscriptions for the following reasons:
 - **Managing Environments:** You may choose todo this to have additional developement environments, for increased security, or to seperate data for compliance reasons.
 - **Organisational Structures:** Departments within an organisation may want to divide their subscriptions among teams instead to better allow for cost management.
 - **Billing:** Costs between subscriptions may need to be divided further for better invoicing and cost division.
## Azure Management Groups
The last piece of management is Management Groups. These allow you to divide resource groups into different projects or applications being developed into different groups to allow for easier management of projects and development.
![[Pasted image 20230203151118.png]]
Unlike [[Microsoft Azure#Resources & Resource Groups|Resource Groups]], management groups can be nested up to 6 times, allowing for a high degree of organisation.

# ExpressRoute
This lets you connect your on-premises networks into the microsoft cloud via a dedicated line with the aid of a connectivity provider. This is called an ExpressRoute Circuit. Crucially, expressroute circuits do not go over the internet and offer a faster, more reliable, and more secure connection.
## Features
- Connectivity to microsoft cloud services across all regions in the geopolitical region
- Global connectivity to microsoft services across all regions with the ExpressRoute Global Reach
- Dynamic Routing between your network and microsoft via border gateway protocol
- Builtpin Redundancy in every peering location for higher [[Cloud Predictability#Reliability|Reliability]] .
## Connectivity Models
ExpressRoute can connect a network to the microsoft cloud via one of four models:
- CloudExchange Colocation
- Point-to-Point Ethernet Connection
- Any-to-Any Connection
- Directly from ExpressRoute Sites
## Security Considerations
While data over ExpressRoute doesnt travel over the public internet, some data is still transmitted via it such as DNS queries, certificate revocation list checking, and Azure Content Delivery Network requests.

# Azure DNS
This is a service that provides standard domain name resolution via azure infrastructure. This simply means you can manage DNS settings via the same portal as all other azure resources.
## Benefits
- Reliability and Performance
- Security
- Ease of Use
- Customisable Virtual Networks
- Alias Records

# Azure Storage
This provides a unique namespace to access your azure storage data thats accessible from anywhere in the world via HTTP or HTTPS. 
## Redundancy Options
- Locally Redundant Storage
- Geo-Redundant Storage
- Read-Access Geo-Redundant Storage
- Zone-Redundant Storage
- Geo-Zone-Redundant Storage
- Read-Access Geo-Zone-Redundant Storage
### Locally Redundant Storage
This is where data is replicated three times within a single datacenter in the primary region. This provides at least 11 nines of durability over a given year.

This is the cheapest form of redundancy and is similarly the least effective.
### Zone-Redundant Storage
This replicates all azure storage data synchronously across three azure availability zones in the primary region. This offers at least 12 nines of durability.
### Geo-Redundant Storage
Geo Redundant Storage asynchronously replicates a Locally Redundant setup in a seperate region of the region pair. This includes all the backups. This offers at least 16 nines of durability.
### Geo-Zone-Redundant Storage
This is zone redundant storage with a locally redundant storage setup in a seperate region pair. 
## Storage Services
- **Blobs:** A massively scalable object store for text and binary data. Also includes support for big data analytics through Data Lake Storage Gen2
- **Files:** Managed file shares for cloud or on-premises deployments
- **Queues:** A messaging store for reliable messaging between application components
- **Disks:** Block-Level storage volumes for Azure VMs
## Storage Account Endpoints
The end of a storage account's namespace is dependent upon its type
| Storage Service        | Endpoint                                         |
| ---------------------- | ------------------------------------------------ |
| Blob Storage           | "\<storage-account-name>.blob.core.windows.net"  |
| Data Lake Storage Gen2 | "\<storage-account-name>.dfs.core.windows.net"   |
| Azure Files            | "\<storage-account-name>.file.core.windows.net"  |
| Queue Storage          | "\<storage-account-name>.queue.core.windows.net" |
| Table Storage          | "\<storage-account-name>.table.core.windows.net"                                                 |

## Account Types
| Type                        | Supported services                                                                        | Redundancy Options                   | Usage                                                                                                                                                                                                                                        |
| --------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard general-purpose v2 | Blob Storage (including Data Lake Storage), Queue Storage, Table Storage, and Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS | Standard storage account type for blobs, file shares, queues, and tables. Recommended for most scenarios using Azure Storage. If you want support for network file system (NFS) in Azure Files, use the premium file shares account type.    |
| Premium block blobs         | Blob Storage (including Data Lake Storage)                                                | LRS, ZRS                             | Premium storage account type for block blobs and append blobs. Recommended for scenarios with high transaction rates or that use smaller objects or require consistently low storage latency.                                                |
| Premium file shares         | Azure Files                                                                               | LRS, ZRS                             | Premium storage account type for file shares only. Recommended for enterprise or high-performance scale applications. Use this account type if you want a storage account that supports both Server Message Block (SMB) and NFS file shares. |
| Premium page blobs          | Page blobs only                                                                           | LRS                                  | Premium storage account type for page blobs only.                                                                                                                                                                                            |                                                                                                                                                                                                                                        |

## Redundancy
Azure Storage always involves some degree of redundancy so that it is protected no matter the circumstances. Redundancy is always a balance between costs and risk. Factors to consider when choosing a redundancy option include:
- How data is replicated in the region
- Whether your data is replicated to a second region taht is geographically distant to ther primary region
- Whether your application requires read access to the replicated data in the secondary region if the primary region becomes unavailable.

# Azure Active Directory
Azure AD is a cloud based identity and login system. It functions as a cloud based counterpart for Microsoft's on-prem ActiveDirectory. Azure AD has a host of features, including but not limited to Authentication, Single Sign on, Application Management, and Device management.





--- 
#cloud #azure