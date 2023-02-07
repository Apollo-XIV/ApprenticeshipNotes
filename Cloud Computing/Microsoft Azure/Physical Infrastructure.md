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