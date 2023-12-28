## Restart Policy
1. Create workshop namespace and create Always policy pod

   ```bash
   kubectl apply -f 00-namespace.yml
   ```
   ```bash
   kubectl apply -f 01-always-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-06 -w
   ```
2. create OnFailure pod

   ```bash
   kubectl apply -f 02-onfailure-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-06 -w
   ```
   ```bash
   kubectl apply -f 03-onfailure-pod-with-err.yml
   ```
   ```bash
   kubectl get po -n workshop-06 -w
   ```
3. create Never pod

   ```bash
   kubectl apply -f 04-never-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-06 -w
   ```

4. Remove all Pod and namespace

   ```bash
   kubectl delete ns/workshop-06
   ```
   ```bash
   kubectl get po -A
   ```