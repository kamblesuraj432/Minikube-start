# Minikube-start
# Minikube Installation for Ubuntu OS Guide

## Pre-requisites

* Ubuntu OS
* sudo privileges
* Internet access
* t2.medium instance type or higher

Run the following commands on the server nodes to prepare them for minikube.

```bash
# using 'sudo su' is not a good practice.
sudo apt update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install docker.io -y

sudo systemctl enable docker.service # enable and start in single command.
sudo usermod -aG docker $USER && newgrp docker

# Adding minikube.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube


# Start minikube.
minikube start --driver=docker

sudo apt update 
```
## Verify  minikube Connection

On server:

```bash
kubectl get pods -A
```

# Minikube Installation for Amazon-Linux OS Guide

## Pre-requisites

* Amazon-Linux OS
* sudo privileges
* Internet access
* t2.medium instance type or higher

Run the following commands on the server nodes to prepare them for minikube.

```bash
# using 'sudo su' is not a good practice.
sudo yum update
sudo yum install docker -y
sudo service docker start

sudo systemctl enable docker.service # enable and start in single command.
sudo usermod -aG docker $USER && newgrp docker

# Adding minikube.
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube


# Start minikube.
minikube start --driver=docker

```
## Minikube Server

1. Initialize the Kubectl to the server node.

    ```bash
    sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    
    ```


2. Set up local kubectl config file:

    ```bash
    sudo chmod +x kubectl
    sudo mkdir -p ~/.local/bin
    sudo mv ./kubectl ~/.local/bin/kubectl
    ```

## Verify  minikube Connection

On server:

```bash
kubectl get pods -A
```
