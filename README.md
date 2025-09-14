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
- All microservice images are available on Docker Hub [Docker Hub Repository](https://hub.docker.com/repository/docker/akramgalal/node.js/general)

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
<img width="2423" height="788" alt="Screenshot 2025-09-14 214907" src="https://github.com/user-attachments/assets/03b5f1a3-7811-45c3-ad7b-a183dfacedbe" />
