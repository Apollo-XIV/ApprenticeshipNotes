# Features
Software Defined Storage describes a storage architecture that seperates the management software from teh storage hardware. SDS resides between the data request. Essentially, SDS abstracts away the hardware involved in storage, allowing for a simpler interface with easier use of more complex features. The following might be among settings you can customise:
- Compression
- Data Deduplication
- Scalability
- Thick and Thin Storage Provisioning
- Data Replication

## Compression
Data compression takes data of a given format and reformat/performs computation upon it to either lossfully or losslessly reduce its size. This can be done through many methods but typically for storage youd only choose lossless options. Decompression takes time, so is not as suitable if a high read speed is required.

## Deduplication
Data deduplication looks for repeated chunks of data and removes extras. This helps make sure that storage space is being used efficiently.

## Thin vs Thick Provisioning
Thin provisioning is where you might reserve a max storage and then dynamically provision it as you use it. This means you will only be charged for exactly how much storage you use. Thick provisioning involves reserving a given amount of storage which you are then charged for, regardless of whether or not you use it all.

## Replication
 Data can be replicated in multiple ways:
 - SAN replication
 - VM replication
 - CDN
 - Distributed File System Replication
 - AZ Replication

# Billing
Billing for cloud storage falls under three top level categories: **Hot Access, Cold Access, and Archive.**

Choosing the right level of access speed can lead to a significant reduction in cost with minimal impact on the business and function of your resources. This is dependent, however, on choosing the most appropriate option. Improper choice will lead to poor or degraded performance with possibly higher bills.

# Storage Types
Cloud storage is formatted in multiple ways, but the primary ones are **Block storage**, **Object Storage**, **Buckets**, and **File storage**

File storage is where data is stored as discrete files, whereas block storage offers a single contiguous block of data. Block storage might be used for VM storage, or other applications where large chunks of unstructured data is needed.

# Multitenancy
Data privacy is a major concern nowadays, as such seperation between tenants in the cloud is of crucial importance. 
