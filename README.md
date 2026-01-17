Deploying MongoDB and Mongo Express on Kubernetes

This project demonstrates deploying a stateful backend (MongoDB) and a web-based database UI (Mongo Express) on a Kubernetes cluster, using best practices such as Secrets, ConfigMaps, internal and external Services.

Components Overview :-

-MongoDB Pod – Database running inside the cluster
-MongoDB Internal Service (ClusterIP) – Internal access for Mongo Express and Node.js app
-Secret – Stores MongoDB credentials securely
-ConfigMap – Stores non‑sensitive configuration values
-Mongo Express Deployment – Web UI for MongoDB
-Mongo Express External Service – Exposes Mongo Express to the browser

Prerequisites :-

a)Kubernetes cluster (Minikube / Kind / EKS / GKE / AKS)
b)kubectl configured

Steps to Deploy the Application:-

Step 1: Create Secrets

     kubectl apply -f mongo-secret.yaml

Stores MongoDB username and password securely.

Step 2: Deploy MongoDB Pod

    kubectl apply -f mongo-deployment.yaml

MongoDB runs inside the cluster with credentials injected from Secrets.

Step 3: Create ConfigMap

    kubectl apply -f mongo-configmap.yaml

Stores MongoDB service name and database configuration.

Step 5: Deploy Mongo Express

    kubectl apply -f mongo-express-deployment.yaml

Mongo Express connects to MongoDB using Secrets and ConfigMap values.

Accessing Mongo Express

For Minikube:

    minikube service mongo-express-service

Or access via browser:

    http://<NODE_IP>:<NODE_PORT>
