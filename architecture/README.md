kubernets architecture:
    node or minion: is a machine (virtual/physical) where containers live
    more than 1 node
    cluser is a set of nodes grouped together
    master node: watches over the worker nodes 
    components: api server, etcd, kubelet, container runtime, controller, scheduler
        api server: font end for the user
        etcd: key value store distributed - used to store all data to manage the cluster
        scheduler: distributing work across multiple nodes
        controller: responding when nodes, containers, scheduler goes down (bring up new containers)
        container runtime: software to use the containers (docker)
        kubelet - agent runs on each node in the cluster (containers are runnin on the nodes as expected)
    master: kube-apiserver (talk to kubelet), etcd, controller and manager
    worker: kubelet (talk to api server), container runtime
    kubectl: used to deploy and manage application on the cluster (clusteri info, status of nodes etc) 
        kubectl run hello-minikube -- used to deploy an application on the cluster
        kubectl cluster-info -- used to get information about the cluster
        kubectl get nodes -- list all of the nodes of the cluster
