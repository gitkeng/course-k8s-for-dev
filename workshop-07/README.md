## Multi-Container and Init Containers
1. Create workshop namespace and create sidecar pod

   ```bash
   kubectl apply -f 00-namespace.yml
   ```
   ```bash
   kubectl apply -f 01-sidecar-pod.yml
   ```
   ```bash
   kubectl get po -n workshop-07
   ```
   ```bash
   kubectl logs -f po/sidecar-pod -c sidecar -n workshop-07
   ```   
2. create initial-pod

   ```bash
   kubectl apply -f 02-initial-container.yml
   ```
   ```bash
   kubectl get po -n workshop-07 -w
   ```
3. Remove all Pod and namespace

   ```bash
   kubectl delete -f 00-namespace.yml
   ```
   ```bash
   kubectl get po -A
   ```