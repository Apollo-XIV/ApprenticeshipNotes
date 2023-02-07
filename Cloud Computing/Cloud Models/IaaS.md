Infrastructure as a Service provides the greatest amount of flexibility in cloud service management. In an IaaS model the CSP only provides the physical hardware and connectivity to the VM, and all on-board services and software are completely managed by the end user. In IaaS you are essentially renting only the hardware in the datacenter and nothing else.

As described in the [[Shared-Responsibility Model]], IaaS leaves the user with the greatest amount of responsibility, with the CSP only being responsible for the physical hosts, the network, and the datacenter.

Examples of where IaaS may be in place are as follows:
- **Lift and Shift Migration:** You're standing up cloud resources similar to your on-prem datacenter, and hten simply moving ht esthings running on-prem to running on the IaaS infrastructure.
- **Testing and Development**: You have established configurations for development and test environments that you need to rapidly replicate. You can stand up or shut down the different environments rapidly with IaaS structure, while maintaining complete control.

# Azure Virtual Machines
Azure VMs are the IaaS-like service provided by azure. They give you total control over the operating system, the ability to run custom software, and allow you to use custom hosting configurations. You may even use a system image to rapidly provision VMs.

## Scaling VMs in Azure
VMs in Azure allow you to rapidly provision new machines either manually or automatically.
### Scale Sets
Scale sets are a way to govern and load-balance a host of identitcal VMs. Azure allows you to do load balancing automatically and in minutes, as well as updating each to the same settings immediately. You can set the number of VMs to scale with demand, or with a defined schedule. 
### Availability Sets
Availability Sets ensure that an error in one machine does not cascade to the others, destroying your cluster. To do this, VMs are grouped in two ways:
- **Update Domain:** This allows you to update VMs in stages, staggering updates to ensure no downtime and that if an update is bad it does not destroy the entire cluster.
- **Fault Domain:** Fault domains group VMs by their common powersource and switch. Splitting VMs across fault domains mean that individual component failures do not take out entire resource groups. By default, resources in Azure are split across 3 fault domains.
Availability Sets require no additional cost in Azure, meaning it is cheaper and easier to have reliable services.



---
#cloud #azure 