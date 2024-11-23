### Deployments
deployments are one level above replicaset, you can maintain state, update version live

- replica maintains stable copy of pods
- If a container is deleted, it creates new one automatically
- that means some kind of monitoring features is there which is called as **controller manager** ccm
- 