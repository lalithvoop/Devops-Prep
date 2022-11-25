## Intro:

**Kubernetes** is a orchestration tool used to manage containers, VMs and servers. 

Any server in which a kubernetes is installed is called a **Node**. Set of nodes come together to form a **Cluster**. Multiple nodes help in sharing the load.   

A Kubernetes cluster consists of 2 planes - **control plane (brain of the cluster) and data plane (worker nodes)**. 
  - Control plane AKA Master node: orchestrates the cluster
  - Data plane : contains of the child/worker nodes
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Architecture :atom:

![alt text](https://d33wubrfki0l68.cloudfront.net/2475489eaf20163ec0f54ddc1d92aa8d4c87c96b/e7c81/images/docs/components-of-kubernetes.svg)

The architecture of kubernetes consists of the following components: ACCES- Master node; KCP- Child node;

**Master node:**
1. API Server: All the internal and external components of the Kubernetes cluster communicate with each other using the API Server. A manifest file is given to API server takes in the file using POST method. It is subjected to Authentication and Authorization.

2. Etcd: contains the configuration and their status in key-value pairs. multiple replicas (3-5) of this has to be maintained for high availability. Etcd prefers consistency over availability. If this is down, apps will still work but no updates will happen. It will store the desired state of the cluster.

3. Contoller manager: Controller of the controllers like endpoint controller, node controller etc. This is main controller which keeps a track of all the control loops.

4. Cloud controller manager: found only if cluster is on public cloud based provider. Comes into picture when we are using cloud components like external load balancer, storage accounts, etc.

5. Scheduler: runs complex logics in the backend and assigns points to the nodes. Points to nodes are assigned based on params like RAM availability, ports open, etc. Based on the points, Scheduler selects which task to assign to which node. If no node is sufficient task is left in pending state.

**Child node:**
1. Kubelet: Kubelet keeps a watch at the API server for work assignment. If node cannot perform the task, it replies to API server. Thereafter, it is the responsibility of control panel to decide what to do with the assigned task. 

2. Container runtime: Container runtime like docker is installed for running and maintaining the container.

3. Kube-proxy: deals with IP configuration of the node. Makes sure each node has a different IP and IPv Rules are in place. Responsible for cluster networking.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Kubernetes DNS:** :desktop_computer:

Kubernetes DNS is present in every cluster which holds a static IP address. Each pod/node is aware about where to find this service. 

Helps in telling other nodes/pods about IP address and associate name.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------
