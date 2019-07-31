Minikube is a tool that makes it easy to run kubernetes locally. Minikube runs a single node kubernetes cluster inside a Linux VM. we can use it for development and testing purpose. it can not spin up production cluster because it's one node machine with no high availibility. It works on Linux, Windows and Mac machine. You will also need virtulization software installed to run minikube. So here we have use virtual box for virtualisation. 


## Update the system with latest packages.
```
$ apt-get update
```
```
$ apt-get install apt-transport-https
```
```
$ apt-get upgrade
```

## Install Virtual box in ubuntu.

You will also need virtulization software installed to run minikube. So here we have use virtual box for virtualisation. 

```
$ sudo apt install virtualbox virtualbox-ext-pack
```

## Download and install minikube.

We will download minikube binary file and give it to executing permission and put it in to /usr/local/bin/ .

```
$ wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
```
$ chmod +x minikube-linux-amd64
```
```
$ sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```

## Check the minikube version.
```
$ minikube version
```
minikube version: v0.34.1


## Install kubectl on Ubuntu 18.04

we will require kubectl command to deploy and manage app on kubernetes.

```
$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```
```
$ echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
```
$ sudo apt update
```
```
$ sudo apt -y install kubectl
```

## Start the minikube cluster.
```
$ minikube start
```

## To ssh into minikube.
```
$ minikube ssh
```

## To check cluste information.
```
$ kubectl cluster-info
```

## check the cluster nodes.
```
$ kubectl get nodes
```

## access minikube cluster dashboard.
```
$ minikube dashboard --url
```
http://192.168.1.10:30000


## Stop the minikube.
```
$ minikube stop
```

## Delete minikube cluster.
```
$ minikube delete
```

