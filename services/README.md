# Services

Services enable the front end application for example to be accessible to users.

Allows connection between frontend and backend pods.

Services allow loose coupling between microservices.

A service is an object just like pods.

uses labels and selectors to link the service to the pods

### External Communication Example:

How to make a frontend application available to end users? 
* The node has an ip address of 192.168.1.2 for example. 
* User on the same network has an ip of 192.16.1.10
* Internal network in the container has an ip of 10.244.0.0
* Pod within the node has an internal ip of 10.244.0.1
  
Options: 
* can ssh into 192.168.1.2 and access the internal pod network or curl the webapp (not ideal)

### Types of services

node-port service: listen to a port on the node to forward requests to the pods.

clusterip: a service creates a virtual ip to front end server to BE servers. 

load balancer: distribute load between services

### Node-port

3 Ports involved.

1) the port on the pod called the *target port* (80)
2) the port on the service itself called the *port* (80)
3) the port on the node itself called the *node port* (30008)
   1) these ports range from 30000-32767

see nodeport.yml file for an example

```bash
kubectl create -f nodeport.yml
kubectl get services
```

When a request is made the service finds a pod with the label to forward to. It uses a random algorithm in selecting the pod. 

If the pods are distributed between different nodes, creating the service automatically spans across all nodes in the cluster. 

### Note:
When running this in minikube, you won't be able to access the service directly since it's running inside of minikube.

```bash
# get the locally accessible url. This will route minikube to the service node and pod. 
minikube service --url myapp-service
```

### ClusterIP

Multiple pods for each: frontend, backend, database

The frontend needs to communicate to backend, backened needs to communicate to database.

Connectivity between services? pods all have an ip address. Not static, cannot rely on IP.

A ClusterIP services manages the communication between services. 

### Load Balancer

Multiple nodes in the cluster have their own IP. You can access any of the IPs in the cluster. 

Users need a single IP or URL to access your application. 

You'd generally use a new VM with nginx to handle the load balancing.

But using a cloud provider you can utilize their native load balancer.

