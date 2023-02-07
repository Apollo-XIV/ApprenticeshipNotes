# [[Cloud Networking Technologies#Types of Storage|Azure Storage]]
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