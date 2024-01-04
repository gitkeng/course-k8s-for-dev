## Example deployment of Wordpress

1. create "mysql-data" folder under "k3dvol" and change owner and permission for store mysql

    for unix based system
    ```bash
    cd k3dvol
    mkdir mysql-data
    sudo chown -R 1000:1000 mysql-data
    sudo chmod -R 777 .mysql-data
    ```
    for windows
    ```bash
    cd k3dvol
    mkdir mysql-data
    ```

2. deploy all yaml files in "bonus-02-wordpress" folder

    ```bash
    kubectl apply -f .
    ```
    ```bash
    kubectl get po -n wordpress-ns -o wide
    ```

3. Set host name in /etc/hosts (unix based system), c:\windows\system32\drivers\etc\hosts (windows)

    ```
    127.0.0.1    wp.k8.local
    ```

4. Open browser and go to http://wp.k8.local:8080