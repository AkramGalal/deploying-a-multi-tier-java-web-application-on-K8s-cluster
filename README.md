# Deploying a Multi-Tier Java Web Application on Kubernetes
This project demonstrates the deployment of a multi-tier Java application onto a K8s cluster. It covers creating K8s manifests, configuring services, and using deployment strategies to ensure application availability.

## Architecture Overview  
The application consists of the following components:  

| Component      | Type                    | Service        |
|----------------|-------------------------|---------------|
| Database       | Deployment + ReplicaSet | ClusterIP      |
| MemCache       | Deployment + ReplicaSet | ClusterIP      |
| RabbitMQ       | Deployment + ReplicaSet | ClusterIP      |
| Application (Tomcat) | Deployment + ReplicaSet | LoadBalancer  |

## Components Summary  
- 4 Deployments.
- 3 ClusterIP Services.
- 1 LoadBalancer Service.
- 1 Secret.

## Prerequisites  
- A running Kubernetes cluster.
- 9 K8s manifests are included in this repository.
- DockerHub access to pull images.
- All microservice images are available on Docker Hub [Docker Hub Repository](https://hub.docker.com/repository/docker/akramgalal/nodejs/general)

## Deployment Steps
- Clone the repo.
-  Apply all manifests. 
  ```bash
  kubectl -n myapp apply -f .
  ```
- Any deployment can be scaled manually by changing the ReplicaSet
  ```bash
  kubectl scale deployment app-deployment --replicas=5
  ```
- Or scaled automatically using HPA/VPA.

## Deployment Status
- Check the status of myapp namespace.
  
  <img width="1552" height="811" alt="Screenshot 2025-09-21 222637" src="https://github.com/user-attachments/assets/7c0c1c20-4f6e-4b8d-a9e9-a951e45b4550" />

- Access the application using the IP address of any VM of the cluster and the port number of the Loadbalancer service.
  
  <img width="3775" height="1934" alt="Screenshot 2025-09-21 222906" src="https://github.com/user-attachments/assets/7394836a-39a8-4cd2-b89e-1a95fb82c52e" />

