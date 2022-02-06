# Deployments

Higher in the Kubernetes heirarcher than ReplicaSets. 

Deployments are definitions on how you want to deploy your app.

YAML file is identical to the ReplicaSet in the other section but the `Kind` is replaced with `Deployment`

```bash
# creates a new kubernetes object of kind: Deployment
kubectl create -f deployment_definition.yml
```

```bash
# lists the current deployments
kubectl get deployments
```

```bash
# the deployment created a replicaset for the deployment
kubectl get replicaset
```

```bash
# the deployment also created the pods defined in the replicaset which is defined in the deployment
kubectl get pods
```

```bash
kubectl describe deployment myapp-deployment
```

```bash
# to list all of the kubernetes objects at once
kubectl get all
```