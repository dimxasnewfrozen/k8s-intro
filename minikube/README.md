minikube:
    https://minikube.sigs.k8s.io/docs/start/
    create a deployment: kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4
    list the deployment: kubectl get deployment 
    expose as a service: kubectl expose deployment hello-minikube --type=NodePort --port=8080
    load the service in the browser: minikube service hello-minikube
    delete the service: kubectl delete service hello-minikube
