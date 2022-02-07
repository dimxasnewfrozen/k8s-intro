# Deploying on the cloud

### Self hosted vs Hosted/Managed

Self hosted:
* you provision vms, configure them and update them
* kubernetes on aws using kobs or kubeone

Hosted/Managed
* kubernetes-as-a-service
* provider provisions vms
* provider installs k8s
* Example GKE or EKS

### GKE

* Basically just walk through the form of creating a kubernetes cluster.
* connect to the cloud shell in the browser
* git clone the repo
* cd into the folder and trigger the kubectl create commands
* replace NodePort with LoadBalancer. This will ensure GKE creates a load balancer service(s)

### EKS

**Pre-requisites**
* Create EKS cluster role

https://docs.aws.amazon.com/eks/latest/userguide/service_IAM_role.html#create-service-role

* Create EKS node role

https://docs.aws.amazon.com/eks/latest/userguide/service_IAM_role.html#create-service-role

* VPC
* EC2 key pair which can be used to ssh to worker nodes

Setup
* Create a new cluster in the dashboard using the EKS cluster role
* Leave the rest as the defaults for now
* Create a new node group in the "Compute" section of the EKS cluster page
