# Kubernetes Minikube Cluster Setup
This repository provides the setup for a three-node Kubernetes cluster using Minikube with the Docker driver. Each node is designated for specific purposes, with appropriate labels assigned to enable workload segregation.

## Overview

The Kubernetes cluster consists of three nodes:
- **Node A**: Dedicated to running the main application.
- **Node B**: Dedicated to running the database.
- **Node C**: Dedicated to running dependent services, such as the observability stack or Vault for storing secrets.


# Requirements

- **Docker Desktop** with Kubernetes enabled.
- **Minikube** installed on your system. [Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/)
- **kubectl** command-line tool installed. [kubectl Installation Guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Cluster Configuration

### Nodes and Labels

| **Node Name** | **Purpose**                  | **Label**               |
|---------------|------------------------------|-------------------------|
| Node A        | Runs the main application    | `type=application`      |
| Node B        | Runs the database            | `type=database`         |
| Node C        | Runs dependent services      | `type=dependent_services` |


## Setup Instructions

### Step 1: Start the Kubernetes Cluster
Run the following command to create a three-node cluster using Minikube with Docker as the driver:
```bash
minikube start --nodes=3 --driver=docker

### Step 2: Assign Labels to Nodes

kubectl label nodes <node-name-1> type=application
kubectl label nodes <node-name-2> type=database
kubectl label nodes <node-name-3> type=dependent_services


### **Step 3: Verify Node Labels**

kubectl get nodes --show-labels
