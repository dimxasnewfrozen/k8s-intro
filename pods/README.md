pod demo:
    minikube start
    kubectl run nginx --image=nginx (name available in dockerhub)
    kubectl describe pod nginx (describes the pod)
    kubectl get pods -o wide (where the pod is running)

pod yaml:
    required 4 root level properties:
        apiVersion:
        kind:
        metaData:
        spec:
