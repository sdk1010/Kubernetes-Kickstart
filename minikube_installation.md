# Minikube Installation Guide for Ubuntu

This guide provides step-by-step instructions for installing Minikube on Ubuntu. 

Minikube allows you to run a single-node Kubernetes cluster locally for development and testing purposes.

## Pre-requisites

Ubuntu OS

sudo privileges

Internet access

Virtualization support enabled (Check with egrep -c '(vmx|svm)' /proc/cpuinfo, 0=disabled 1=enabled)

## Step 1: Update System Packages

Update your package lists to make sure you are getting the latest version and dependencies.

```
sudo apt update -y
```

![Screenshot (77)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/6028614b-c9f9-4c43-a408-23588ea14a26)

## Step 2: Install Required Packages

Install some basic required packages.

```
sudo apt install -y curl wget apt-transport-https
```

![Screenshot (76)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/3fd5b331-cb62-4b47-b8b0-be76f7f7bd88)

## Step 3: Install Docker

Minikube can run a Kubernetes cluster either in a VM or locally via Docker. 

This guide demonstrates the Docker method.

```
sudo apt install docker.io -y
```

![Screenshot (75)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/658ada89-fa17-4110-8b2c-b9118a239163)

Start and enable Docker.

```
sudo systemctl enable docker --now
```

Add current user to docker group (To use docker without root)

```
sudo usermod -aG docker $USER && newgrp docker
```
![Screenshot (74)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/2dc07c86-b7ef-4d3c-a044-e0d1b0b5a2ec)


## Step 4: Install Minikube

First, download the Minikube binary using curl:

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

Make it executable and move it into your path:

```
chmod +x minikube
sudo mv minikube /usr/local/bin/
```

![Screenshot (73)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/9b29d27d-4f37-4e9a-846e-6629e5803208)

## Step 5: Install kubectl

Download kubectl, which is a Kubernetes command-line tool.

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Check above image ⬆️ Make it executable and move it into your path:

```
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

![Screenshot (72)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/f4014a54-931b-4a12-9fc1-9dca6b8937ce)

## Step 6: Start Minikube

Now, you can start Minikube with the following command:

```
minikube start --driver=docker
```

This command will start a single-node Kubernetes cluster inside a Docker container.

## Step 7: Check Cluster Status

Check the cluster status with:

```
minikube status
```

You can also use kubectl to interact with your cluster:

```
kubectl get nodes
```

![Screenshot (71)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/344910bd-7fbd-4c6b-aca6-7b530e83c5de)

You can login to Minikube cluster using SSH:

```
minikube ssh
```

![Screenshot (70)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/16088cfd-75d1-4a0a-9108-0aca7d630e52)

You can get Minikube profile list to view all profiles:

```
minikube profile list
```
![Screenshot (82)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/5e0e5954-646b-4dcb-9eed-f5ebe71fe6a3)

## Step 8: Stop Minikube

When you are done, you can stop the Minikube cluster with:

```
minikube stop
```
![Screenshot (80)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/6630a643-f503-4ec0-9934-f1128045ea3a)

Optional: Delete Minikube Cluster

If you wish to delete the Minikube cluster entirely, you can do so with:

```
minikube delete
```
![Screenshot (81)](https://github.com/sdk1010/Kubernetes-Kickstart/assets/145788176/216012f6-175e-4e7f-b970-e371e009fe7a)

That's it! You've successfully installed Minikube on Ubuntu, and you can now start deploying Kubernetes applications for development and testing.
