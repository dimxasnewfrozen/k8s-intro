# Rollout and Versioning

A rollout creates a revision with your version. 

Updating your pods creates a new revision with a new version.

Allows us to rollback a deployment to a previous version.

### Deployment strategy

**Recreate Strategy:** Destroy all of the pods and spin up new pods with the new version. This causes downtime and is not the default behavior of kubernetes

**Rolling Update:** Take down pods one at a time and spin up a new version. This does not cause downtime and is the default strategy in kubernetes


```bash
# show the status of the deployment
kubectl rollout status deployment/myapp-deployment
```

```bash
# show the history of the deployment
kubectl rollout history deployment/myapp-deployment
```

```bash
# run after making a change to the image version or other property in the definition file
kubectl apply -f deployment.yml
```

```bash
# run the describe deployment command to show the the rollout details
kubectl describe deployment/myapp-deployment
# this should show the StrategyType: RollingUpdate
```

### Rollbacks

```bash
# This will take down the old replicaset and bring back up the old replicaset
kubectl rollout undo deployment/myapp-deployment    
```

## Summary

* Create
  * `kubectl create -f deployment.yml`
* Get
  * `kubectl get deployments`
* Update
  * `kubectl apply -f deployment.yml`
* Status
  * `kubectl rollout status deployment/myapp-deployment`
* Rollback 
  * `kubectl rollout undo deployment/myapp-deployment`