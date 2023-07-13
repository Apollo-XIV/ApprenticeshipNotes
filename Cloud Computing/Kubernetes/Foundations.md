Kuberentes is a Container Orchestration System, designed to make managing lots of micro-services easier by using declarative code. This means that rather than telling the computer step by step what you'd like it to do, you tell it what the end-result should be like and the Kubernetes engine figures out the rest.

# Primitives
At a base level, a Kubernetes cluster[^1] is built up of the following primitives:
## Pods
A pod is the smallest divisible part of a service. A pod typically contains only a single container. This is done to allow parts of the service to scale independently of one another. The exceptions to the rule come in four primary forms:
- ***Sidecar Container.*** A second container that enhances the first, this is typically for the purposes of logging or monitoring, however, other applications exist.
- ***Init Container.*** A container that runs only so that it can initialise the actual container and then - typically - stops running.
- ***Ambassador Container.*** This container acts as a proxy and would stop external entities from accessing the interior container directly. Another way of describing this would be as a proxy container.
- ***Adapter Container.*** This is where another container is used to convert data so that it matches the expected stream. This might be useful when you have multiple different data sources, each in different formats.
When a pod is deployed, it is allocated resources on a [[Foundations#Nodes|Node]] that it can use. Multiple pods can be assigned to a single node. More on nodes can be read [[Foundations#Nodes|here]].

### Phases & States
A when a pod starts it goes through a number of phases that describe how far through the initialisation process they are. After completing initialisation they are tracked through their status that is described using one of three states. The phases are:
- Pending - Pod starts here and waits to be scheduled, image download, etc
- Running - at least one container running
- Succeeded - all containers terminated successfully
- Failed - all containers have terminated, at least one terminated in failure
- Unknown - pod state cannot be obtained, either node communication breakdown or other
And the possible states are:
- Waiting - startup not complete
- Running - executing without issues
- Terminated - ran into issues whilst executing

## Nodes
Nodes are the physical machines that collectively create the cluster. A node can be anything from baremetal servers to VMs running in large cloud datacentres. Each node has a given amount of resources that it can distribute to pods running on them. Much of the benefit of Kubernetes is its ability to dynamically adjust where a pod is located so that load is distributed evenly across nodes, increasing the efficiency of the use of their resources. This is separate from load balancing, which distributes *traffic* among *pods*, instead of *pods* among *nodes*. 









[^1]: A cluster is a group of linked computers that all run the Kubernetes engine and listen to the control plane of the cluster.