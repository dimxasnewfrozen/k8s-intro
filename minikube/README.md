# minikube

To setup minikube on your local machine follow the instructions on the minikube site. 
https://minikube.sigs.k8s.io/docs/start/

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