## Scheduling and DaemonSets
1. Create workshop namespace and label nodes

   ```bash
   kubectl apply -f 00-namespace.yml
   ```
   ```bash
   kubectl get no
   ```
   ```bash
   kubectl label no/k3d-mycluster-agent-0 worker-type=frontend 
   ```
   ```bash
   kubectl label no/k3d-mycluster-agent-1 worker-type=service
   ```   
   ```bash
   kubectl label no/k3d-mycluster-agent-2 worker-type=database
   ``` 
   ```bash
   kubectl describe no/k3d-mycluster-agent-0 
   ```
   ```bash
   kubectl describe no/k3d-mycluster-agent-1
   ```   
   ```bash
   kubectl describe no/k3d-mycluster-agent-2
   ``` 

2. create node selector and node name pods

   ```bash
   kubectl apply -f 01-nodeselector-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-08 -o wide
   ```
   ```bash
   kubectl apply -f 02-nodename-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-08 -o wide
   ```   

3. create daemonset pod

   ```bash
   kubectl apply -f 03-daemonset-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-08 -o wide
   ```

4. Remove all label, Pod and namespace

   ```bash
   kubectl label no/k3d-mycluster-agent-0 worker-type-
   ```
   ```bash
   kubectl label no/k3d-mycluster-agent-1 worker-type-
   ```   
   ```bash
   kubectl label no/k3d-mycluster-agent-2 worker-type-
   ```
   ```bash
   kubectl delete -f 00-namespace.yml
   ```
   ```bash
   kubectl get po -A
   ```