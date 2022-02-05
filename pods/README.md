# Kubernetes Pods

Pods contain the containers that run your app(s). Pods scale up/down depending on how they are configured in the replicaset (discussed in another section).

## YAML

pods are described using yaml configuration files. See example in this directory.

All pods definition files must have 4 root level properties:

```
apiVersion:
kind:
metaData:
spec:
```

Property table:
```
Kind          | Version
---------------------------
Pod           | v1      
Service       | v1     
Replica Set   | apps/v1       
Deployment    | apps/v1
```

## Running and using the yml definition

```bash
kubectl create -f nginx.yml
```