# Kubernetes Learning Path

A structured, hands-on repository for learning Kubernetes, from foundational concepts to advanced cluster management. This guide provides explanations, examples, and hands-on projects to help you master container orchestration.

## Table of Contents
1.  [Introduction to Kubernetes](#1-introduction-to-kubernetes)
2.  [Prerequisites](#2-prerequisites)
3.  [Kubernetes Architecture](#3-kubernetes-architecture)
4.  [kubectl: The Command-Line Tool](#4-kubectl-the-command-line-tool)
5.  [Core Kubernetes Objects](#5-core-kubernetes-objects)
6.  [Configuration and Secrets](#6-configuration-and-secrets)
7.  [Storage in Kubernetes](#7-storage-in-kubernetes)
8.  [Kubernetes Networking](#8-networking-in-kubernetes)
9.  [Cluster Management and Administration](#9-cluster-management-and-administration)
10. [Package Management with Helm](#10-package-management-with-helm)
11. [GitOps with ArgoCD](#11-gitops-with-argocd)
12. [Hands-on Projects](#12-hands-on-projects)

---

## 1. Introduction to Kubernetes
Kubernetes (K8s) is an open-source platform designed to automate deploying, scaling, and managing containerized applications. It groups containers that make up an application into logical units for easy management and discovery.

**Why use Kubernetes?**
*   **Automated rollouts and rollbacks:** Manages and automates the process of deploying updates to your applications.
*   **Self-healing:** Automatically restarts, replaces, and reschedules containers that fail.
*   **Load balancing:** Automatically distributes incoming traffic to ensure even resource utilization.
*   **Service discovery:** Assigns DNS names to services and load balances traffic across them.
*   **Scalability:** Allows you to easily scale your application's components up or down.

## 2. Prerequisites
Before diving into Kubernetes, you should have a solid understanding of these technologies:
*   **Containers:** Basic knowledge of containerization using tools like Docker.
*   **YAML:** Kubernetes configuration files are written in YAML.
*   **Linux fundamentals:** Familiarity with the Linux command line.
*   **Networking basics:** Understanding of core networking concepts (IP addresses, CIDR, DNS).

## 3. Kubernetes Architecture
Kubernetes follows a client-server architecture with a clear separation between the Control Plane and Worker Nodes.

**Control Plane Components:**
*   **API Server (`kube-apiserver`):** The front end of the Kubernetes control plane. It exposes the Kubernetes API.
*   **etcd:** A consistent and highly available key-value store used to store all cluster data.
*   **Scheduler (`kube-scheduler`):** Watches for newly created Pods and assigns them to nodes.
*   **Controller Manager (`kube-controller-manager`):** Runs various controllers that regulate the cluster's state, such as `Deployment` and `ReplicaSet` controllers.

**Worker Node Components:**
*   **Kubelet:** An agent that runs on each node in the cluster. It ensures that containers are running in a Pod.
*   **Container Runtime:** The software responsible for running containers, such as containerd or CRI-O.
*   **Kube-Proxy (`kube-proxy`):** A network proxy that maintains network rules on nodes, enabling communication between Pods and services.

## 4. kubectl: The Command-Line Tool
`kubectl` is the primary command-line tool for interacting with your Kubernetes cluster.

