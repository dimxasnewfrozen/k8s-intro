# Networking

A node has an ip address. For example 192.168.1.99. 

This is the ip address to ssh and access the node.

Each pod in the node contains its own internal IP address. 10.244.1.0 for example. 

When kubernetes is configured it creates an internal private network with the IP of 10.244.0.0. All of the pods are attached to it.

When a cluster is set up, it does not automatically set up any networking for multiple nodes to communicate with eachother. This can result in IP conflicts with the internal networks in the node. 

Kubernetes expects us to configure the network to meet this criteria:
* All containers/pods can communicate with each other without NAT
* All nodes can communicate with the containers and vice- versa without NAT

Some solutions exist to handle this:
* cisco
* flannel
* cilium
* vmware nsx
* weave net
* and others

