***Virtual Private Network***

A VPN is an encrypted network channel that allows you to act as though you were a device on a remote network. This allows you to connect two trusted networks over an untrusted one (such as the internet).
# VPN Gateways
A VPN Gateway is a type of virtual network gateway. VPN Gateways allow you to access a network as part of a subnet. They allow you to:
- Connect On-Premises datacenters to virtual networks through a site-to-site connection
- Connect Individual Devices to Virtual Networks through a point-to-site connection
- Connect virtual networks to other virtual networks through a network-to-network connection
VPN Gateways can either be policy based or route based. This describes the method of encryption and detecting whether traffic is valid.
- **Policy-based:** Specifies packet IPs statically. This method evaluates every data packet against a set list of IPs, and if matching the list i s send through a different tunnel
- **Route-based:** IPSec tunnels are modeled as network interfaces or virtual tunnels. IP Routing can then be used to direct traffic through the correct gateway. These are the preferred method of connecting on-prem devices as theyre more resilient to changes like the addition of subnets.

A route based gateway is appropriate if:
- Connecting Virtual Networks
- Point-to-Site connections
- Multi-site connections
- Coexistence with an Azure ExpressRoute gateway

# [[Cloud Availability|High Availability]]
When dealing with important data, you want to be able to ensure that your information is highly available and your connection is fault tolerant. 
## Active/Standby
This is a default VPN configuration with gateways deployed in two instances, one active vand one standby. This means that when something unexpected or planned happens the standby interface can take over and allow work to continue. Connection may be interrupted during this failover, but generally connection can be restored after a few seconds.
## Active/Active
With the introduction of support for BGP (Border Gateway Protocol) you can also deploy VPN gateways in an active/active configuration. With this, each gateway has a unique public IP address. This creates seperate tunnels for each IP address to the device on-premises. To increase availability you can install an additional VPN device on-premises.
## [[Microsoft Azure#ExpressRoute|ExpressRoute]] Failover
A VPN can be configured as a failover for an ExpressRoute Gateway. This means that should the secure connection fail over the dedicated network, an alternate path via a secure VPN over the internet can be used instead.
## Zone-Redundant Gateways
Availability zones and VPNs can be configured in a zone-resilient configuration. This brings resiliency, scalability, and higher availability to virtual network gateways. This means that your connection to your cloud environment is not dependent upon a single zone, but instead distributed across all of them.