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
12. kubernetes architecture (https://kubernetes.io/docs/concepts/overview/components/)
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
14. POD is smallest deployable unit
15. POD is logical group of containers
16. creating pod
```text
kubectl run demo --image=nginx
```
```text
kubectl get pods
```
```text
kubectl delete pod demo
```
17. reference for pods
- apiversion
- kind
- metadata
- spec