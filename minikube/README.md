# minikube

Minikube combines the worker and master nodes into one bundle as an ISO.

You need to install a hypervisor (hyperv, enable virtualization), docker, kubectl and minikube.exe

To setup minikube on your local machine follow the instructions on the minikube site. 
https://minikube.sigs.k8s.io/docs/start/


```bash
# start up minikube
minikube start
```

```bash
# create a deployment
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
```

```bash
# list the deployment
kubectl get deployment
```

```bash
# expose a service
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```

```bash
# load the service in the browser
minikube service hello-minikube
```

```bash
# delete the service
kubectl delete service hello-minikube
```

## Other helpful commands for interacting with pods

```bash
# name available in dockerhub
kubectl run nginx --image=nginx
```

```bash
# describe the details of a pod
kubectl describe pod nginx
```

```bash
# list more details like where the pod is running
kubectl get pods -o wide
```