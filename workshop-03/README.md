## kubectl

1. List K8s Resources

    ```bash
    kubectl api-resources
    ```

2. Create namespace and echo-pod

    ```bash
    kubectl apply -f 00-echo-pod.yml
    ```

3. Get pod information

    ```bash
    kubectl get po -A
    ```
    ```bash
    kubectl get po -o wide -A
    ```
    ```bash
    kubectl get po -o json -A
    ```   
    ```bash
    kubectl get po -o yaml -A
    ```    
    ```bash
    kubectl describe po/echo-pod -n workshop-03
    ```
    ```bash
    kubectl get po -A -o wide --sort-by .spec.nodeName
    ```   
    ```bash
    kubectl get po -n kube-system -o wide --sort-by .metadata.name
    ``` 
    ```bash
    kubectl get po -A -o wide --selector app=echo-pod-app
    ```
          
4. Execute command in pod

   ```bash
   kubectl exec -it po/echo-pod -n workshop-03 -c netshoot -- curl "localhost?query=helloWorld!"
   ```
   ```bash
   kubectl exec -it po/echo-pod -n workshop-03 -c netshoot -- bash
   ```
   ```bash
   exit 
   ```

5. Remove all Pod and namespace

   ```bash
   kubectl delete -f 00-echo-pod.yml
   ```