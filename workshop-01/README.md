## Create a 4-node K3d cluster and basic node command

1. Run command to create cluster call **mycluster**

    #### MacOS
    ```bash
    k3d cluster create mycluster \
    --servers 1 \
    --agents 3 \
    --image rancher/k3s:latest
    ```

    #### Windows
    ```cmd
    k3d cluster create mycluster --servers 1 --agents 3 --image rancher/k3s:latest
    ```
   
   Tip: You can break up long lines in windows with the caret `^` as long as you remember that the caret and the newline following it are completely removed


2. Run the following command to confirm your kubectl context has been updated to work with the new cluster. You’ll need kubectl installed for this to work.
   ```bash
    kubectl get no -o wide
   ```

3. Get node information
   ```bash
   kubectl describe no k3d-mycluster-server-0
   ```