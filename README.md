 # kubernetes_practice

### About this Repository
This repositiory contains the study notes, practice code and commands that I gathered while learning and practicing Kubernetes.
<br><br>

## <a name='toc'>Index</a>
- [ ] [Kubernetes components](#k8sComponents)
  * Node and Cluster
  * Control plane components
  * Node components
- [ ] Kubernetes objects
  * POD
  * Replication controller
- [ ] Commands

### Kubernetes Components
### <a name='k8sComponents'>Kubernetes Components</a>
#### Node and Cluster
- Node is a physical or virtual machine where Kubernetes is installed. It can be worker node or master node.
- Kubernetes cluster is set of nodes

#### Control plane components
1. Kube-apiserver<br>
    This is interface via which interaction with K8S can be done. This is kind of frontend for K8S. It can scale horizontally.
   - HTTP API
   - Kubectl cmd line interface
3. Etcd <br> Distributed Key-value DB for K8S backing store for all cluster data
4. Kube-scheduler <br>
   - This component monitors newly created PODs with no assigned node and select node to run the pod.
   - **Decision factors in scheduling**: individual (for pod) and collective resource requirements, hardware/software policy constraints, Data locality
6. Kube-controller-manager <br>
    This runs controller processes. Logically each controller is separate process but compiled into single binary. <br>
    Types:
    + node controller : responds to node related events
    + job controller : manages job object that represents one off tasks. Create pods to run such tasks.
    + endpoint controller
    + service account and token controller : create default accounts and API access tokens for new namespaces.
8. Cloud-controller-manager
   + Embeds cloud-specific logic
   + This lets you link your cluster into your cloud provider's API and separate out the components that interact with that cloud platform from components that only interact with K8S cluster.

#### Node components
1. Kubelet
   - K8S agent that runs on each node
   - makes sure container are running in PODs
3. Kube-proxy
   - Network proxy that runs on each node in cluster
   - implements part of K8S service concept
   - maintains network rules
5. Container runtime
   - Responsible for running containers. Examples: CRI-O, ContainerD (from docker)
   - CRI : Container Runtime Interface <br>
       Interface provided by K8S. Allowed any vendor like docker ( containerd) or rkt to work as container runtime, as long as they adhere to OCI standards.
   - OCI : Open  Container Initiative <br>
       * imagespec : spec on how image should be build
       * runtimespec : spec on how container to be build
         

### Commands
#### 1. Getting list of existing pods. <br><br></b>
> kubectl get pods

#### 2. Creating a new pod with existing image. <br><br></b>
> kubectl run <pod_name> --image=<image_name>
>> Example:  kubectl run nginx --image=nginx

#### 3. Get details of running pod
> kubectl describe pod <pod_name>
>> Example: kubectl describe pod nginx

#### 4. Delete pod from node
> kubectl delete pod <pod_name>
>> Example: delete pod nginx

#### 5. Create Pod from pod definition file
    kubectl create -f <pod_definition_file_name>
    Example: create -f client-pod.yaml
[client-pod.yaml](https://github.com/amolbinwade/kubernetes_practice/blob/master/client-pod.yaml)


  
