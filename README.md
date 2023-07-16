# kubernetes_practice

### About this Repository
This repositiory contains the study notes, practice code and commands that I gathered while learning and practicing Kubernetes.
<br><br>

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


  
