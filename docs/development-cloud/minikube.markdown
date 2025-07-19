---
layout: page
title: "Minikube Cluster"
permalink: /docs/minikube/
parent: "GC2 Instance Documentation"
nav_order: 11
---

## Minikube In GC2
[Linux]
```bash
# Download and Install Minikube
# Set-Up Minikube Using the docker driver
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```
**Install Kubectl**
[Linux]

Follow these Instruction: [https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

#### Start Minikube Cluster With GPU Access
```bash
# Verify that everything is set up before moving further
sudo apt-get update
curl -O https://raw.githubusercontent.com/rajat709/Cloud-API-Builder/main/meta/minikube-verify.sh && chmod +x minikube-verify.sh && ./minikube-verify.sh; status=$? && rm -f minikube-verify.sh
```
```bash
# Check if bpf_jit_harden is set to 0
sudo sysctl net.core.bpf_jit_harden

# If it’s not 0 run:
echo "net.core.bpf_jit_harden=0" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```
```bash
# Start minikube with gpus access
minikube start --driver docker --container-runtime docker --gpus all
```

Now you're all set! Enjoy your Kubernetes pods with GPU acceleration. 🔥

