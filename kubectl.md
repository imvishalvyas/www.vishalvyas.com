* Kubectl is a kubernetes command line tool. You can deploy and manage application in kubernetes using kubectl.Using kubectl, you can inspect cluster resources; create, delete, and update components.


### Install Kubectl ubuntu/debian :
```
sudo apt-get update && sudo apt-get install -y apt-transport-https
```
```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```
```
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a  /etc/apt/sources.list.d/kubernetes.list
```
```
sudo apt-get update
```
```
sudo apt-get install -y kubectl
```


### Install kubectl on Centos / Fedora :
```
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
```
```
yum install -y kubectl
```

### Install with snap on Ubuntu : 
```
$sudo snap install kubectl --classic
```
```
$kubectl version
```


### Install kubectl binary using curl : 

Download latest version of kubectl using below command. 
```
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.12.0/bin/linux/amd64/kubectl
```

Give executable permission to binary.
```
$ chmod +x ./kubectl
```

Move that binary to your path. 
```
$ sudo mv ./kubectl /usr/local/bin/kubectl
```
