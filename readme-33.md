### Deployments
deployments are one level above replicaset, you can maintain state, update version live

- replica maintains stable copy of pods
- If a container is deleted, it creates new one automatically
- that means some kind of monitoring features is there which is called as **controller manager** c-m
- C-M (controller manager) monitors, each time a deployment is observed, a replicaset is created to bring up the desired Pods
- **Concept of Stateful application:** means it maintains state, e.g if container is down, application will be down, replicaset will create new replica of the pod and reconnect clients to the app on new container, that's how it maintains the state

#### creating stateful sets (05-statefulset.yml)

