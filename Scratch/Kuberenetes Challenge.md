Rancher Cluster or kubernetes cluster has a 1 master and 2 worker nodes , from which master node is always getting disconnected or getting error kubelet  [stopped posting node status](https://forums.rancher.com/t/kubelet-stopped-posting-node-status/13855 "https://forums.rancher.com/t/kubelet-stopped-posting-node-status/13855") , can u see how we can resolve this and also , how we can add one more node into the cluster so we can have 2 master nodes and 2 worker nodes , you can create your own scenario and workable solution , but start with 1 master and 2 worker and then add one more master node


- 1 master node
- 2 worker nodes
- Master Node repeatedly disconnects
- Receive error "Kubelet stopped posting node status"
- 

# Top Level Analysis
This problem shows the need for high availability in a cluster, demonstrating that should the master node for a cluster have severe issues, its effects could be disastrous for the rest of the cluster. In this case, we need to repair the existing master node and then add a second one to help avoid such issues in the future.

# Issue 1: Kubelet stopped posting node status
The issue as it is presented is ambiguous, at first it could be that the master node has connection issues, or the nodes themselves. The fact it is both of the nodes suggests that either both have failed or it is in fact the master node.



# Issue 2: Add a second master node to cluster
Adding a second node to the cluster largely depends upon the environment; if using something like AWSEKS then adding another node is simple as it handles lots of the configuration for you, simply add another node to the node group in the cluster and it should automatically provision and add the new node to the cluster.

Assuming a more complex solution, a new node can be provisioned by creating a VM and then registering it with the control plane. To do this