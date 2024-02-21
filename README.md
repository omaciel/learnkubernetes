### Repository for Kubernetes Learning
Inspired on the repository [k8s in 1-hour](https://gitlab.com/nanuchi/k8s-in-1-hour)

#### K8s manifest files 
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
