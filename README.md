# Kubernetes-Email-Storage-with-MongoDB-Node.js-Web-UI
 
 This project demonstrates how to deploy a full-stack email storage application using Kubernetes, Docker, and MongoDB. The application consists of a Node.js Web UI for interacting with a MongoDB database that stores email addresses. The project uses Kubernetes to manage the deployment, scaling, and data persistence of the containers.
 

# Features:-

Node.js Web UI that provides a simple interface to add and view emails.
MongoDB as the database to store email addresses.
Persistent Storage using Kubernetes PersistentVolumes (PV) and PersistentVolumeClaims (PVC) to ensure that email data persists across pod restarts and Minikube shutdowns.
Two Deployment Strategies:-

* Single Pod Deployment:- Running both Node.js and MongoDB containers in the same pod.
* Separate Pods: Running Node.js and MongoDB containers in separate pods, offering more flexibility and scalability.

# Technologies Used:-
Kubernetes for container orchestration, managing Pods, Deployments, Services, and storage.
Docker for creating and running containerized applications (Node.js Web UI and MongoDB).
Minikube for running a local Kubernetes cluster.
MongoDB as the database to store email addresses.
Node.js (Express.js) for the backend API to manage email-related operations.

# Kubernetes YAML Files:-
This project uses the following Kubernetes resources to deploy and configure the application:

1. PersistentVolume (PV) & PersistentVolumeClaim (PVC).

* PersistentVolume (PV): This defines the physical storage (in this case, a hostPath) that will be used to store MongoDB's data. It ensures data is stored persistently on the local file system, even if pods are restarted.
* PersistentVolumeClaim (PVC): This is used to claim the storage defined in the PersistentVolume. It allows Kubernetes to allocate and manage the storage for the MongoDB container.

2. ConfigMap
* ConfigMap: This stores MongoDB connection details (like host and port) and makes them available as environment variables to the Node.js container. This configuration allows the Node.js app to dynamically connect to MongoDB.

3. MongoDB Deployment
* MongoDB Deployment: This YAML file defines the deployment of the MongoDB container, including its image (mongo:latest), ports, and the volume for persistent storage. It ensures MongoDB is available as a service within the Kubernetes cluster.

4. MongoDB Service
* MongoDB Service: The service defines how to access the MongoDB container. In this case, it's exposed internally within the Kubernetes cluster using the ClusterIP type. This makes it accessible for communication between containers within the cluster.

5. Node.js Web UI Deployment
* Node.js Web UI Deployment: This YAML file defines the deployment of the Node.js application. It includes the image (admin726/node-mongo-db:03), the number of replicas (2), and environment variables to connect to the MongoDB database. The deployment ensures the Node.js application runs as intended in Kubernetes.

6. Node.js Web UI Service
* Node.js Service: This service exposes the Node.js Web UI container. It is defined with the LoadBalancer type, which allows the service to be accessed externally. The Node.js Web UI interacts with MongoDB through the ClusterIP service defined earlier.


# How to Run Locally:

1. Clone this repository:

* git clone https://github.com/yourusername/kubernetes-email-storage.git
* cd kubernetes-email-storage

2. Start Minikube:

* minikube start

3. Apply Kubernetes Configuration:

* kubectl apply -f kubernetes/

4. Access the Node.js Web UI:

* kubectl get svc service-node-app

# Project Summary

This project demonstrates how to deploy a full-stack email storage application using Kubernetes, Docker, and MongoDB. It features a Node.js Web UI that allows users to submit and retrieve emails stored in a MongoDB database. The deployment supports persistent storage, ensuring data remains intact across restarts using PersistentVolumes (PV) and PersistentVolumeClaims (PVC). The project explores two deployment strategies: running both containers in the same pod and in separate pods, providing insights into different Kubernetes architectures. This setup is ideal for learning container orchestration, database persistence, and cloud-native application deployment. 🚀

