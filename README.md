# **ReadMe: Kubernetes and Kind Cluster Setup**

## **Table of Contents**
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Command Summary](#command-summary)
4. [Explanation of Steps](#explanation-of-steps)

## **Overview**
This document outlines the steps and commands executed to set up and manage a Kubernetes cluster using `kind` (Kubernetes in Docker). It includes cluster creation, namespace management, and checking installed tools.

## **Prerequisites**
Before running the commands, ensure the following tools are installed on your system:
- `Docker`
- `kubectl`
- `kind` (Kubernetes in Docker)

## **Command Summary**
Below is a chronological list of commands executed:

```bash
# Delete a directory named NewFolder
sudo rm -r NewFolder/

# Edit and create scripts
vim kube_ctl.sh
vim install_kub.sh

# Install `kind` tool
[ $(uname -m) = x86_64 ] && \
  curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64 \
  chmod +x ./kind && \
  sudo cp ./kind /usr/local/bin/kind

# Directory management
mkdir kube_install
cd kube_install/
vim kube.sh
chmod 777 kube.sh
./kube.sh

# Check versions
kubectl version
docker --version
kind --version

# Create and configure a `kind` cluster
mkdir kind_cluster
cd kind_cluster/
vim config.yml
kind create cluster --name=e-commerce-webiste --config=config.yml

# Kubernetes namespace and pod management
kubectl get nodes
kubectl get ns
kubectl get ns kube-system
kubectl get pods -n kube-system
kubectl create ns website
kubectl delete ns website
```

## **Explanation of Steps**

### Step 1: Removing and Managing Files/Directories
- **Command:** `sudo rm -r NewFolder/`
  - Deletes an existing directory `NewFolder`.
- **Command:** `mkdir kube_install`
  - Creates a directory named `kube_install` for scripts.

### Step 2: Script Creation
- **Commands:**
  - `vim kube_ctl.sh`, `vim install_kub.sh`, `vim kube.sh`
    - Open the `vim` editor to create or modify scripts for Kubernetes setup and management.

### Step 3: Install Kind Tool
- **Command:**
  ```bash
  [ $(uname -m) = x86_64 ] && \
  curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64 \
  chmod +x ./kind && \
  sudo cp ./kind /usr/local/bin/kind
  ```
  - Downloads the `kind` binary, makes it executable, and copies it to `/usr/local/bin` for system-wide access.

### Step 4: Cluster Creation
- **Commands:**
  - `vim config.yml`
    - Create a configuration file for the cluster.
  - `kind create cluster --name=e-commerce-webiste --config=config.yml`
    - Creates a Kubernetes cluster using the configuration.

### Step 5: Kubernetes Management
- **Commands:**
  - `kubectl get nodes`: Lists all nodes in the cluster.
  - `kubectl get ns`: Lists all namespaces.
  - `kubectl get pods -n kube-system`: Lists all pods in the `kube-system` namespace.
  - `kubectl create ns website`: Creates a new namespace called `website`.
  - `kubectl delete ns website`: Deletes the `website` namespace.

### Step 6: Version Checks
- **Commands:**
  - `kubectl version`: Displays the Kubernetes client and server version.
  - `docker --version`: Displays the installed Docker version.
  - `kind --version`: Displays the installed Kind version.

---

This README provides a structured outline of the commands for setting up a Kubernetes environment using Kind. Customize the configuration and scripts as needed for specific project requirements.
