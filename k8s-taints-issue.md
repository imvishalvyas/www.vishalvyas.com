# 1 node(s) had taints that the pod didn't tolerate.

By default pods doesn't schedule on master node of kubernetes. Pods always run on worker node but sometime you want to run pods on single node master cluster. then you can use this to run pods on master node kubernetes aws. But it' not best prectice for kubernetes. 

`Error :`  `1 node(s) had taints that the pod didn't tolerate`
have you faced your pod in pending state while deploying new pod and not running ? the problem is your pod not able to schedule on worker node. there are many resons. Nodes not ready, pod not ready or unsuffciant resources it's because taint.


`Solution :`
you can remove taint using below command. it will deploy your pod direct on master node instead of your worker.

```
kubectl taint nodes --all node-role.kubernetes.io/master-
```
