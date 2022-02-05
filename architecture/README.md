# Kubernetes Architecture:

* A node or minion is a machine (virtual or physical) where the containers live
* There can be many nodes
* A Kubernetes cluster is a set of nodes grouped together
* A Master Node
  * watches over all of the worker nodes
  * includes kube-apiserver (talk to kubelet), etcd, controller and manager
* Worker Node
  * includes kubelet (talk to api server), container runtime
  
## Kubernetes Components
* API Server: front end for the user
* etcd: a key/value distributed database used to store all data to manage cluster
* scheduler: distributing work across multiple nodes
* controller: responds to node status messages. If scheduler goes down it brings up new containers
* container runtime: software to use containers (docker)
* kubelet: agent runs on each node in the cluster. Containers are running on the nodes as expected.
  
## kubectl

used to deploy and manage application on the cluster (clusteri info, status of nodes etc) 

```bash
# used to deploy an application on the cluster
kubectl run hello-minikube
```

```bash
# used to get information about the cluster
kubectl cluster-info
```

```bash
# list all of the nodes of the cluster
kubectl get nodes
```