# Microservices in Kubernetes

This is built on top of the previous example in the `Microservices` section.

It takes the concept of running these containers but runs them in a kubernetes cluster.

Steps:
* Deploy pods
* Enable connectivity by creating a ClusterIP service
    * redis (named redis since it's connecting to the hostname redis)
    * db (named db since it's connecting to the hostname db)
        set username and password to "postgres"
* Enable external communication by creating a NodePort service
    * voting-app
    * result-app
    
Deploying 5 pods in total and 4 services (no service for worker pod)

Only use a service type when the pod needs to be exposed for communication.

```bash
# This will show the pods AND the services in a single command
kubectl get pods,svc
```

```bash
# Get the url of the voting service within minkube 
minikube service voting-service --url
```

### pods-and-services (option 1)

These are all of the files used to create individual pods and services

Challenges: 
* doesn't help scale easily if we want to add new instances
* update with a new image: may require downtime

### deployments (option 2)

These are all of the files used to create the pods and services using deployments

Deployments automatically create ReplicaSets
* rolling updates
* rollback
* cause of change

```bash
# if you want to scale a deployment but not update the configuration
kubectl scale deployment voting-app-deploy --replicas=3

# see that it scaled
kubectl get deployments voting-app-deploy
```



