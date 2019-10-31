# kubernetes-multiple-scheduler


The Kubernetes scheduler is a policy-rich, topology-aware, workload-specific function that significantly impacts availability, performance, and capacity. The scheduler needs to take into account individual and collective resource requirements, quality of service requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference, deadlines, and so on. Workload-specific requirements will be exposed through the API as necessary.


Kubernetes ships with its default scheduler. Please refer to the architecture discussion about what scheduler does. 

The source code for kubernetes defaule scheduler is - 
https://github.com/kubernetes/kubernetes/tree/master/pkg/scheduler


We will take reference from the official kubernetes documentation to implement a second scheduler which will be a replica of the default scheduler. We will name the new scheduler as - **myscheduler** adn the default scheduler will be named as **default-scheduler**. The original demo is referenced at - https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/

Lets start off by 

* Build kubernetes from source

**Clone the official github repository**

```
git clone https://github.com/kubernetes/kubernetes.git
```

**Install build essentials package for ubuntu**

```
sudo apt-get install build-essential -y
```

**Install GO version 1.12.9**

```
mkdir goinstall
cd goinstall
wget https://dl.google.com/go/go1.12.9.linux-amd64.tar.gz
tar -C /usr/local/ -xzf go1.12.9.linux-amd64.tar.gz
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile
source ~/.profile
echo "export GOPATH=$HOME/go" >> ~/.profile
source ~/.profile

```

**Build Kubernetes** 

```
mkdir -p $GOPATH/src/k8s.io

cd $GOPATH/src/k8s.io

git clone https://github.com/kubernetes/kubernetes

cd kubernetes

make
```






