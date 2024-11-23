# learn-kubernetes

1. visit site http://eksctl.io
2. Kubernetes is open source to manage containerized application
3. Amazon EKS - amazon elastic kubernetes service, cloud based container management service from amazon
3. eksctl - CLI tool for creating and managing cluster on EKS. Amazon's managed kubernetes service for EC2
4. Installing eksctl on workstation
```text
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz
sudo mv /tmp/eksctl /usr/local/bin
```
5. Creating cluster
6. create repo learn-kubernetes | eks-cluster.yml
7. login to workstation | git clone https://github.com/hpatel3747/learn-kubernetes
```text
cd learn-kubernetes
eksctl create cluster -f eks-cluster.yml
```
```text
eksctl update cluster -f eks-cluster.yml
```

8. overview of kubernetes - http://kubernetes.io
9. Concept on kubernetes
```text
greek word kubernetes means helmsman or pilot
in short called as k8s - 8 word from k to s
open source project by google in 2014
bundles and runs applications
```
10. features
- service discovery and loadbalancing - expose service, as well as load balance 
- storage orchestration - mount storage 
- automated rollouts - create/remove containers
- automated bin packing - how much cpu ram each container needs
- self-healing
- scaling
- batch execution is supported
- can be feed from hashi vault

11. similar to VM container has its own filesystem, cpu and memory, considered as lightweight
12. kubernetes architecture
## Kubernetes Arch Components

![Kubernetes Arch Components](https://github.com/hpatel3747/learn-kubernetes/blob/main/kubernetes-arch.jpg)
- control plane, cloud provide api
- Node1 -- container1, container2,..
- Node2
- Node3
- Nodes are in cluster
- API serer is backbone of kubernetes, holds lots of APIs, nodes etc foes thru API calls
- Kubernetes is cloud agnostics
- kubectl is native tool used to talk to api
- GI is kubernetesUI
- k9s is another such utility
13. Install kubectl on workstation
```text
sudo yum install -y kubectl
sudo labauto kubectl
kubectl version
```
POD is smallest deployable unit
POD is logical group of containers
- Creating pod
```text
kubectl run demo --image=nginx
```
```text
kubectl get pods
```
```text
kubectl delete pod demo
```
18. reference for pods
- apiversion
- kind
- metadata
- spec
checkout file 01-pod.yml
20. deploy pod1 
```text
kubectl apply -f 01-pod.yml
```
```text
kubectl get pods
```
20. Install k9s utility on workstation
```text
sudo labauto k9s
```
21. type k9s to open k9s interface, :pod will show all the pods running, :exit to exit
22. delete demo pod
```text
kubectl delete -f 01-pod.yml
```
23. try deploy 02-pod.yml (pod with two container images)
```text
kubectl apply -f 02-pod.yml
```
24. container running in kubernetes is called container run time, which is different than docker container which run containerd
25. ReplicaSet - make sure specified number of identical pods are always running
26. labels are key-value pairs to organize objects, use Selectors to indentify a group of objects after specifiying labels
27. create replicaset
```text
kubectl apply -f 03-rs.yml
```
```text
kubectl get rs
```
to see name and short names of resources
```text
kubectl api-resource
```
show replica with labels
```text
kubectl get rs --show-labels
```
this will bring up only one replica
```text
kubectl scale rs frontend --replicas=1
```
this will bring up 20 replicas
```text
kubectl scale rs frontend --replicas=20
```
this will delete 19 replicas to bring it down to 1 replica
```text
kubectl scale rs frontend --replicas=1
```
show all the replica with certain label
```text
kubectl get rs -l tier=frontend
```
28. If you need to update nginx version, update .yml file and apply, but it will not update version, and so kubernetes came up with concept called deployments
- deployment manages set of pods and application that does not maintain sate
- when we apply new version, it will create new replica with updated version and terminate old one 