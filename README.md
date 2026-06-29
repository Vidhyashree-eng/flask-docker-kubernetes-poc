# flask-docker-kubernetes-poc
Python Flask web application and containerized it using Docker.

# Flask Docker Kubernetes POC

A simple end-to-end DevOps POC demonstrating:

- Python Flask application
- Docker containerization
- Kubernetes deployment using Minikube
- NodePort service exposure
- Horizontal pod scaling

---

## Project Architecture

```text
Flask App
   ↓
Docker Image
   ↓
Docker Container
   ↓
Minikube Cluster
   ↓
Deployment
   ↓
Pods
   ↓
NodePort Service
```

---

## Project Structure

```text
flask-docker-kubernetes-poc/

├── app.py
├── requirements.txt
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── screenshots/
```

---

## Run Locally

### Build Docker Image

```bash
docker build -t flask-k8s-app:v1 .
```

### Run Container

```bash
docker run -d -p 5000:5000 --name flask-app flask-k8s-app:v1
```

### Test Application

```bash
curl localhost:5000
```

Output:

```text
Hello from Docker and Kubernetes!
```

---

## Start Minikube

```bash
minikube start --driver=docker
```

Verify:

```bash
kubectl get nodes
```

---

## Load Docker Image

```bash
minikube image load flask-k8s-app:v1
```

---

## Deploy Application

```bash
kubectl apply -f deployment.yaml
```

Verify:

```bash
kubectl get deployments
kubectl get pods
```

---

## Create Service

```bash
kubectl apply -f service.yaml
```

Verify:

```bash
kubectl get svc
```

---

## Access Application

```bash
minikube service flask-service --url
```

---

## Scale Application

```bash
kubectl scale deployment flask-app --replicas=5
```

Verify:

```bash
kubectl get pods
```

---

## Key Learnings

- Docker image creation
- Container lifecycle management
- Kubernetes Deployments
- ReplicaSets and Pods
- Services and NodePorts
- Horizontal scaling

---

## Project Summary

I created a Python Flask web application and containerized it using Docker. I built a custom Docker image and ran it as a container, exposing port 5000. After validating the application locally, I created a Kubernetes cluster using Minikube, loaded the Docker image into the cluster, and deployed the application using a Kubernetes Deployment with two replicas. I exposed the application through a NodePort Service and verified accessibility through the browser. Finally, I demonstrated Kubernetes scalability by increasing the number of pod replicas from 2 to 5 and verified that Kubernetes automatically managed the additional pods.
