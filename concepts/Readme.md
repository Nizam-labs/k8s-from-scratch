# Kubernetes Core Concepts & Architecture

This section provides a high-level overview of Kubernetes principles and its architecture. Understanding these foundational concepts is crucial before diving into specific Kubernetes objects and workflows.

## What is Kubernetes?

Kubernetes (often abbreviated as K8s) is an open-source platform designed to automate the deployment, scaling, and management of containerized applications. It groups containers that make up an application into logical units for easy management and discovery.

## Key Principles of Kubernetes

- **Declarative Management:** You define the desired state of your applications in configuration files, and Kubernetes works to maintain that state. You don't instruct it on the steps to get there.
- **Self-Healing:** Kubernetes automatically restarts, replaces, and reschedules containers that fail, ensuring application reliability.
- **Scalability:** You can easily scale your application's components up or down to meet demand without requiring changes to your application.
- **Portability:** Kubernetes can run on various cloud platforms, on-premises servers, or even on your local machine, giving you infrastructure flexibility.

## Kubernetes Architecture: The Cluster

A Kubernetes deployment is referred to as a cluster. At a high level, a cluster consists of two main components:

- **Control Plane (Master Node):** The "brain" of the cluster, responsible for management and orchestration.
- **Worker Nodes:** The machines (physical or virtual) that run your containerized applications.

### Control Plane Components

The control plane makes global decisions about the cluster and orchestrates the worker nodes.

- **API Server (kube-apiserver):** The front end of the Kubernetes control plane. It exposes the Kubernetes API and handles all communication between the master and worker nodes.
- **etcd:** A consistent and highly available key-value store that serves as Kubernetes' backing store for all cluster data.
- **Scheduler (kube-scheduler)::** Watches for newly created Pods and assigns them to a worker node based on resource requirements, constraints, and other factors.
- **Controller Manager (kube-controller-manager)::** Runs a set of controller processes that regulate the cluster's state. It includes controllers for ReplicaSets, Deployments, and more.

### Worker Node Components

Worker nodes execute the application workloads assigned to them by the control plane.

- **Kubelet:** An agent that runs on each node in the cluster. It ensures that containers are running in a Pod according to the instructions from the API server.
- **Container Runtime:** The software responsible for running containers. It can be Docker, containerd, CRI-O, or any other Open Container Initiative-compliant runtime.
- **Kube-Proxy (kube-proxy):** A network proxy that runs on each node and maintains network rules to enable communication between Pods and Services.

## How Kubernetes Works

- **Define Desired State:** You describe your application (e.g., "run 3 replicas of my web app") in a YAML manifest file.
- **API Interaction:** You use kubectl to send the manifest to the API Server. The API Server receives the request and stores the desired state in etcd.
- **Scheduling:** The Scheduler sees that new Pods need to be created and assigns them to the best available worker nodes.
- **Execution:** The Kubelet on each worker node receives instructions to create the Pods. It communicates with the Container Runtime to download the image and start the containers.
- **Reconciliation Loop:** The Controller Manager and Kubelets continuously monitor the cluster. If a Pod fails, the Controller Manager detects the change and works to restore the desired state by scheduling a new Pod.