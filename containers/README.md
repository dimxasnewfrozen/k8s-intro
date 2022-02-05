containers:
    docker
        web server, database, messaging, orchestration
        the matrix from hell: different components requiring different dependency versions
        compatibility issues
        os/library/depdencies
        new developers requiring lots of setup and configuration time running many commands
    completely isolated environments
        like a vm but share the same OS kernal
    high level tool
    common linux kernal: same for centos, ubuntu etc
    difference with virtual machine: each vm has it's own OS using a hypervisor and completely isolated. docker can run the containers (lightweight) using the same OS kernal
    docker run ansible - run an instance of ansible on the docker host
    docker run nodejs x 3 -- have load balancer in front
    docker image: package template plan -- can create multiple containers

