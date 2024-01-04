## Create a 4-node K3d cluster and basic node command

1. Run command to create cluster call **mycluster**

    #### MacOS
    ```bash
   k3d cluster create mycluster \
   --api-port 6443 \
   --port 8443:443@loadbalancer  \
   --port 8080:80@loadbalancer \
   --volume $(pwd)/k3dvol:/tmp/k3dvol \
   --volume $(pwd)/server0:/var/data@server:0 \
   --volume $(pwd)/agent0:/var/data@agent:0 \
   --volume $(pwd)/agent1:/var/data@agent:1 \
   --volume $(pwd)/agent2:/var/data@agent:2 \
   --image rancher/k3s:latest \
   --servers 1 --agents 3
    ```

    #### Windows
    ```cmd
    k3d cluster create mycluster --api-port 6443 --port 8443:443@loadbalancer --port 8080:80@loadbalancer --volume %cd%\k3dvol:/tmp/k3dvol --volume %cd%\server0:/var/data@server:0 --volume %cd%\agent0:/var/data@agent:0 --volume %cd%\agent1:/var/data@agent:1 --volume  %cd%\agent2:/var/data@agent:2 --image rancher/k3s:latest --servers 1 --agents 3
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