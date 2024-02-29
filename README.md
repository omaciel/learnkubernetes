### Repository for Kubernetes Learning
Inspired on the repository [k8s in 1-hour](https://gitlab.com/nanuchi/k8s-in-1-hour)

#### K8s manifest files 
* deploy-mariadb.yaml
* mariadb-config.yaml
* mariadb-secret.yaml
* mariadb.yaml

#### K8s commands

##### start Minikube and check status
    minikube start 
    minikube status

##### get minikube node's ip address
    minikube ip

##### create a basic MariaDB container
    kubectl apply -f mariadb-config.yaml
    kubectl apply -f mariadb-secret.yaml
    kubectl apply -f mariadb.yaml

<br />

or replace the last step with the following for a deployment with 2 replicas

<br />

    kubectl apply -f deploy-mariadb.yaml

<br />

##### query the pods database
    kubectl get pods
    kubectl exec -it mariadb-deployment-f58d85f49-nvd8l -- mariadb -uroot -pmy-secret-pw -e "show databases"

<br />

> :memo: **Note** 

Replace `mariadb-deployment-f58d85f49-nvd8l` with a valid pod name.

##### expose the pod for local access

    kubectl apply -f mariadb-service.yaml
    minikube service mariadb-deployment
    |-----------|--------------------|-------------|---------------------------|
    | NAMESPACE |        NAME        | TARGET PORT |            URL            |
    |-----------|--------------------|-------------|---------------------------|
    | default   | mariadb-deployment |        3306 | http://192.168.49.2:30963 |
    |-----------|--------------------|-------------|---------------------------|
    🏃  Starting tunnel for service mariadb-deployment.
    |-----------|--------------------|-------------|------------------------|
    | NAMESPACE |        NAME        | TARGET PORT |          URL           |
    |-----------|--------------------|-------------|------------------------|
    | default   | mariadb-deployment |             | http://127.0.0.1:50417 |
    |-----------|--------------------|-------------|------------------------|
    🎉  Opening service default/mariadb-deployment in default browser...
    ❗  Because you are using a Docker driver on darwin, the terminal needs to be open to run it.


##### get basic info about k8s components
    kubectl get node
    kubectl get pod
    kubectl get svc
    kubectl get all

##### get extended info about components
    kubectl get pod -o wide
    kubectl get node -o wide

##### get detailed info about a specific component
    kubectl describe svc {svc-name}
    kubectl describe pod {pod-name}

##### get application logs
    kubectl logs {pod-name}
    
##### stop your Minikube cluster
    minikube stop

<br />

> :memo: **Secrets** 

For this example, user names and passwords were `base64` enconded as follows:
    
    mariadb-user: ZXhhbexample-userXBsZS11c2Vy # example-user
    mariadb-password: bXlfY29vbF9zZWNyZXQ=     # my_cool_secret
    mariadb-root-password: bXktc2VjcmV0LXB3    # my-secret-pw

    echo -n example-user | base64
    echo -n my_cool_secret | base64
    echo -n my-secret-pw | base64

<br />

#### Links
* MariaDB image on Docker Hub: https://hub.docker.com/_/mariadb
* k8s official documentation: https://kubernetes.io/docs/home/
* Docker official documentation: https://docs.docker.com/reference/
