## Pod and Namespaces

1. Run command to create namespace

    ```bash
    kubectl create -f 00-namespace.yml
    ```

2. Get namespaces

    ```bash
    kubectl get namespaces
    ```

3. Create One container pod

    ```bash
    kubectl create -f 01-one-container-pod.yml 
    ```

4. Get pod information in namespace workshop-02

   ```bash
   kubectl get po -n workshop-02 -o wide
   ```
   ```bash
   kubectl describe po one-container-pod -n workshop-02
   ```

5. Create multi container pod and get pod information

   ```bash
   kubectl create -f 02-multi-container-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-02 -o wide
   ```
   ```bash
   kubectl describe po multi-container-pod -n workshop-02
   ```

6. Remove all pod and namespaces
   ```bash
   kubectl delete -f 02-multi-container-pod.yml
   ```
   ```bash
   kubectl delete -f 01-one-container-pod.yml
   ```
   ```bash
   kubectl delete -f 00-namespace.yml
   ```
   ```bash
   kubectl get po --all-namespaces -o wide
   ```