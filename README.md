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
in shor called as k8s - 8 word from k to s
open source project by google in 2014
bundles and runs applications
```

