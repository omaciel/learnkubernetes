### Repository for Kubernetes Learning
Inspired on the repository [k8s in 1-hour](https://gitlab.com/nanuchi/k8s-in-1-hour).

<br />

| :memo:        | Check other branches in this repository for other examples.       |
|---------------|:------------------------|

#### K8s manifest files 
* nginx-deployment.yaml
* nginx-service.yaml

#### K8s commands

##### start Minikube and check status
    minikube start 
    minikube status

##### get minikube node's ip address
    minikube ip

##### create a basic nginx container
    kubectl apply -f nginx-deployment.yaml
    kubectl apply -f nginx-service.yaml


<br />

##### expose the pod for local access

    minikube service nginx-service
    |-----------|---------------|-------------|---------------------------|
    | NAMESPACE |     NAME      | TARGET PORT |            URL            |
    |-----------|---------------|-------------|---------------------------|
    | default   | nginx-service | http/80     | http://192.168.49.2:31549 |
    |-----------|---------------|-------------|---------------------------|
    🏃  Starting tunnel for service nginx-service.
    |-----------|---------------|-------------|------------------------|
    | NAMESPACE |     NAME      | TARGET PORT |          URL           |
    |-----------|---------------|-------------|------------------------|
    | default   | nginx-service |             | http://127.0.0.1:54390 |
    |-----------|---------------|-------------|------------------------|
    🎉  Opening service default/nginx-service in default browser...
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

#### Links
* Nginx image on Docker Hub: https://hub.docker.com/_/nginx
* k8s official documentation: https://kubernetes.io/docs/home/
* Docker official documentation: https://docs.docker.com/reference/
