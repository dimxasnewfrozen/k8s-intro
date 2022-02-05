# Containers:
    When you have a web server, database, messaging and orchestration on separate systems (EC2 instances) it's difficult to have these component communicate with eachother. Each component has its own dependency version, os, libraries and you run into compatibility issues.

    It's also difficult for developers to get a local environment set up.

### Difference between Virtual Machines and Docker Containers
* VM: has it's own operating system, using a hypervisor and is completely isolated. 
* Container: shares the same OS kernal (centos, ubuntu, etc) on the docker host, much more lightweight. 

### Docker Image

A packaged template plan for creating the container

### Basic Docker Usage

Run an instance of ansible on the docker host.

```bash
$ docker run ansible
```
