## K8s Storage
1. Create workshop namespace and volume pod

   ```bash
   kubectl apply -f 00-namespace.yml
   ```
   ```bash
   kubectl apply -f 01-volume-pod.yml
   ```
   ```bash
   kubectl get po -o wide -n workshop-11
   ```

   Goto worker node and check data in file "volume-pod.log"

   ```bash
   kubectl delete -f 01-volume-pod.yml
   ```

2. Share data pod

   ```bash
   kubectl apply -f 02-share-data-pod.yml
   ```
   ```bash
   kubectl get po -o wide -n workshop-11
   ```
   ```bash
   kubectl logs -f po/shared-data-pod -c busybox2 -n workshop-11
   ```
   
   Exit from logs (Ctrl+C)

3. Local Storage class,Persistent Volume and Persistent Volume Claim

   ```bash
   kubectl apply -f 03-localdisk-sc.yml
   ```
   ```bash
   kubectl get sc 
   ```
   ```bash
   kubectl apply -f 04-host-pv.yml
   ```
   ```bash
   kubectl get pv
   ```
   ```bash
   kubectl apply -f 05-host-pvc.yml
   ```
   ```bash
   kubectl get pv
   ```   
   ```bash
   kubectl get pvc -n workshop-11
   ```     
   ```bash
   kubectl apply -f 06-pv-deployment.yml
   ```
   ```bash
   kubectl get po -o wide -n workshop-11
   ```
   Goto worker node and check data in file "pv-deploy.log"

4. All cluster Persistent volume

   check k3d cluster storage class
   ```bash
   kubectl get sc 
   ```
   ```bash
   kubectl apply -f 07-k3d-pv.yml
   ```
   ```bash
   kubectl get pv
   ```
   ```bash
   kubectl apply -f 08-k3d-pvc.yml
   ```
   ```bash
   kubectl get pv
   ```   
   ```bash
   kubectl get pvc -n workshop-11
   ```
   ```bash
   kubectl apply -f 09-k3d-pv-deployment.yml
   ```
   ```bash
   kubectl get po -o wide -n workshop-11
   ```
   Goto k3dvol folder and check data in file "k3d-pv-deploy.log"

5. Remove all

   ```bash
   kubectl delete -f 00-namespace.yml
   ```
   ```bash
   kubectl get po -A
   ```
   ```bash
   kubectl delete -f 04-host-pv.yml
   ```
   ```bash
   kubectl delete -f 07-k3d-pv.yml
   ```   
   ```bash
   kubectl get pv 
   ```    
   ```bash
   kubectl delete -f 03-localdisk-sc.yml
   ``` 
   ```bash
   kubectl get sc 
   ```   
  