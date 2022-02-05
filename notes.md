containers:
    docker
        web server, database, messaging, orchestration
        the matrix from hell: different components requiring different dependency versions
        compatibility issues
        os/library/depdencies
        new developers requiring lots of setup and configuration time running many commands
    completely isolated environments
        like a vm but share the same OS kernal
    high level tool
    common linux kernal: same for centos, ubuntu etc
    difference with virtual machine: each vm has it's own OS using a hypervisor and completely isolated. docker can run the containers (lightweight) using the same OS kernal
    docker run ansible - run an instance of ansible on the docker host
    docker run nodejs x 3 -- have load balancer in front
    docker image: package template plan -- can create multiple containers


container orchestration:
    docker swarm, kubernetes, mesos
    orchestration: multiple docker hosts each with their own container(s) (web app, database, messaging)
    aws, gcp, azure
    declarative object configuration files


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


setting up kubernetes
    developers: minikube
    cloud: aws, gcp, azure
    kodekloud.com

    minikube: combines the worker and master nodes into one bundle as an ISO
        need a hypyervisor (hyperv), kubectl, minikube.exe
        https://minikube.sigs.k8s.io/docs/start/
        install docker for windows

minikube:
    https://minikube.sigs.k8s.io/docs/start/
    create a deployment: kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
    list the deployment: kubectl get deployment 
    expose as a service: kubectl expose deployment hello-minikube --type=NodePort --port=8080
    load the service in the browser: minikube service hello-minikube
    delete the service: kubectl delete service hello-minikube

pod demo:
    minikube start
    kubectl run nginx --image=nginx (name available in dockerhub)
    kubectl describe pod nginx (describes the pod)
    kubectl get pods -o wide (where the pod is running)

yaml files:
    configuration data
    key: value (Fruit: Apple)
    array/lists:
        Fruits:
            - Orange
            - Apple
    Dictionary/Map:
        Banana:
            Calories: 105
    
    Key Value/Dictionary/Lists:
        Fruits:
            -   Banana:
                    Calories: 105
            -   Grape:
                    Calories: 10

    dictionary: unordered
    list: ordered
    # (hash) are comments

pod yaml:
    required 4 root level properties:
        apiVersion:
        kind:
        metaData:
        spec:

controllers:
    replication controllers: 
        helps run multiple instances of a single pod, 
        share load, 
        keep the number of pods running, 
        spans across multiple nodes
        somewhat outdated
    replica sets:
        new way of setting up replication

