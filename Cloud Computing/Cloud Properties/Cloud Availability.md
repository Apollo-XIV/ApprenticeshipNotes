Two of the largest considerations for cloud deployments are availability and scalability. Availability describes the uptime of the service, and scalability describes its ability to handle high volumes of traffic.

# High Availability
High availability is incredibly important as you need to ensure you have critical services when you need them. Availability needs to be ensured, in spite of any events or occurrances that may occur. In an on-prem model, this could be incredibly difficult without high redundancy, however, in the cloud this becomes far more achievable.

Availability with a cloud provider is best predicted using their SLAs (Service Level Agreements)

[[Azure SLAs]]

Most services offer a range of availabilities (measured in percentages) at different price points, so determining exactly how much unavailability your service can afford is important as part of any optimisation strategy.

# Scalability
Scalability is another major benefit of cloud resources. Scalability allows you to request more or less resources according to you and your business' needs. Peaks in traffic are easier to handle by requesting more resources, and quiet periods where services go unused are cheaper.

Scalability is typically divided into two varieties: vertical and horizontal.
## Vertical Scalability
Vertical Scalability is the process of increasing or decreasing the capabilities of existing resources. With vertical scalability, if you realised you needed more processing power you could provision more CPUs or RAM to the machine, boosting your power. Conversely, if you realised you did not need all of the resources you were paying for, you could choose to scale back your VM and instead *decrease* the amount of CPUs and RAM you're using.
## Horizontal Scalability
When dealing with peaks in traffic, your deploted resources can be scaled out, both automatically and manually. This means adding more VMs or containers to your pool. Similarly, you could also shrink your array of devices, reducing cost and waste.


--- 
#cloud #azure 