Kubernetes cluster is being represented as a plenty of nodes

There are 2 types of nodes:
- Worker node 
- Master node (Control Plane)

## Worker node
On each there is [[Kubelet process]] running on it
The applications containers are running on worker nodes
Higher workload than master nodes and more resources(hundreds of containers may run on worker nodes)

## Master node
Purpose of this node is to organize, manage and control worker nodes.
The most important part of the kubernetes cluster. It is a good practise to have at least 2 masters inside a k8s cluster in case of master node collapsing(which will make the whole k8s cluster unavailable)

it has 4 main processes: 
- API server - entrypoint to k8s cluster (UI, API, CLI of cluster)
- Controller Manager - keeps track of whats happening in the cluster (whether something should be repaired or redeployed)
- Scheduler  - ensures [[Pod]]s placement(decides on which node new [[Pod]] should be scheduled based on available resources of worker nodes)
- etcd - key value storage - basically holds an anytime the current of the kubernetes cluster(has all configuration data and status data of each node and each container)

The etcd are usually have snapshots, so it is possible to recover the whole cluster state
So, basically, k8s cluster controller manager checks the status of each component in etcd and compares it with the desired state state of each component configuration that is present in [[Deployment]]  

![[Screenshot 2024-10-12 at 14.37.59.png]]
# Virtual network

Virtual network - organizes communication between each node and turn the whole k8s cluster into one unified machine.

![[Screenshot 2024-09-29 at 23.20.23.png]]

# Main k8s components
## Main Components
- [[Pod]]
- [[Service]]
- [[Ingress]]
- [[ConfigMap]]
- [[Secret]]
- [[Volume]]
- [[Deployment]]
- [[StatefulSet]]
- [[DaemonSet]]




