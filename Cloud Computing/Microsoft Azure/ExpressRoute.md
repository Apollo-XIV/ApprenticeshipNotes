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