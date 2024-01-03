## Deployments
1. Create workshop namespace and first deployment

   ```bash
   kubectl apply -f 00-namespace.yml
   ```
   ```bash
   kubectl apply -f 01-my-deployment.yml
   ```
   ```bash
   kubectl get po -n workshop-09
   ```
   ```bash
   kubectl delete po/<my-deployment pod name> -n workshop-09 
   ```
   ```bash
   kubectl get po -n workshop-09
   ```  
   ```bash
   kubectl get deploy -n workshop-09
   ```   
   
2. Scaling Applications

   Modify 01-my-deployment.yml and change replicas to 6

   ```bash
   kubectl apply -f 01-my-deployment.yml
   ```
   ```bash
   kubectl get po -n workshop-09
   ```
   ```bash
   kubectl edit deploy/my-deployment -n workshop-09
   ```
   Find and change replicas to 4
   ```bash
   kubectl get po -n workshop-09
   ```
   ```bash
   kubectl scale deploy/my-deployment --replicas=2 -n workshop-09
   ```
   ```bash
   kubectl get po -n workshop-09
   ```
   ```bash
   kubectl get deploy -n workshop-09
   ```  
   
3. Rolling Updates with Deployments

   ```bash
   kubectl edit deploy/my-deployment -n workshop-09
   ```
   Change nginx image to nginx:1.12
   ```bash
   kubectl rollout status deploy/my-deployment -n workshop-09
   ```
   ```bash
   kubectl get po -n workshop-09
   ```
   ```bash
   kubectl get deploy -n workshop-09
   ```     
   ```bash
   kubectl set image deploy/my-deployment nginx=nginx:broken --record -n workshop-09
   ```
   ```bash
   kubectl rollout status deploy/my-deployment -n workshop-09
   ```
   ```bash
   kubectl get po -n workshop-09
   ```     
   ```bash
   kubectl get deploy -n workshop-09
   ```             
   ```bash
   kubectl rollout history deploy/my-deployment -n workshop-09
   ```
   ```bash
   kubectl rollout undo deploy/my-deployment --to-revision=1 -n workshop-09
   ```   
   ```bash
   kubectl rollout status deploy/my-deployment -n workshop-09
   ```
   ```bash
   kubectl rollout history deploy/my-deployment -n workshop-09
   ```   

4. Remove all

   ```bash
   kubectl delete -f 00-namespace.yml
   ```
   ```bash
   kubectl get po -A
   ```