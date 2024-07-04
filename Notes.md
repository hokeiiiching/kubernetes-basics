## What is Kubernetes? What is its purpose?
- Open source container tool
- Containers: Executable units of software in which application code is packaged with its libraries and dependencies so that it can be ran on different servers
- Helps manage containerised applications in different deployed environments (physical machine, virtual machine, cloud environments)

### Kubernetes Architecture
- **Cluster**: 1 Master node, connected to other worker nodes. Each node contains a kubelet.
- **Master node**: Several important K8 processes, incl: API server (entrypoint to K8 cluster, talks to API, UI, CLI) && controller manager
(keeps track of whats happening in the cluster - if a container died || something needs to be repaired) && scheduler (ensures pod placement, depending on workload and server resources) && etcd (current state of kubernetes cluster, configuration data)
- **Virtual Network**: Creates one unified machine using all of the nodes together
- **Worker nodes**: Hundreds of containers; bigger, higher workload
- **Master node**: Handful of master processes but much more important
- **Pods**: Smallest unit in Kubernetes; abstraction over pods, usually contains 1 application
Each pod gets its own internal IP address that it uses to communicate with other pods
- **Pods are ephemeral**: If they die (crash, node ran out of resources), a new one is recreated with a new IP address
- **Server**: Static IP address so that if a pode dies, endpoint can remain the same as lifecycle of pod and service is not connected
- **Database URL**: Stored in built in application. If change: Rebuild app -> Push to repo -> Pull to pod (troublesome)
- **ConfigMap**: External configuration of application; store non-configuration data, like db-url
- **Secret**: Similar to ConfigMap, but used to store secret data. Base-64; third party encryption tools.
- **Volumes**: Attach a physical storage device to database so that data is persistent through resets (Storage: Local machine || Remote, outside of K8 cluster)
- Create replicas of everything, in case app dies. Also acts as load balancer
- You create **deployments**(blueprints) that specify how many pods
- DBs have state (its data) hence cannot be replicated
- **StatefulSets**: MongoDB, MySQL, elastic. Created for controlling replicated DBs (When it writes to storage, when it waits)

### Kubernetes Configuration
- **Declarative**
- Desired State == Actual State ??? (Checked by controller manager)
- 3 Parts
1) **Metadata**: Name, etc
2) **Specifications**: API version, deployment vs service?
3) **Statuses**: # of replicas, etc.
- Master Process -> Cluster Brain -> Control Plane -> **etcd** holds the current status of any K8 component

### Cluster Set
- Multiple Master and worker nodes
- **Minikube**: One master node and one worker node; docker is pre-installed
- **Kubectl**: API server enables interaction with cluster