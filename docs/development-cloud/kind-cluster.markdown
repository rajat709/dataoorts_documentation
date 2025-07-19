---
layout: page
title: "KinD Cluster"
permalink: /docs/kind-cluster/
parent: "GC2 Instance Documentation"
nav_order: 10
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">

## KinD In GC2
[Linux]

To Install KinD, You Need To Follow The Instructions Given Here: [https://kind.sigs.k8s.io/docs/user/quick-start/](https://kind.sigs.k8s.io/docs/user/quick-start/)

### Install Kubectl
[Linux]

Follow These Instruction: [https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

Enable GPU Access In KinD Cluster
```bash
# Verify that everything is set up before moving further
sudo apt-get update
curl -O https://raw.githubusercontent.com/rajat709/Cloud-API-Builder/main/meta/kind-verify.sh && chmod +x kind-verify.sh && ./kind-verify.sh; status=$? && rm -f kind-verify.sh
```
```bash
# Create a Kind Cluster --v1.27.3
kind create cluster --name dataoorts --config - <<EOF
apiVersion: kind.x-k8s.io/v1alpha4
kind: Cluster
nodes:
- role: control-plane
  image: kindest/node:v1.27.3@sha256:3966ac761ae0136263ffdb6cfd4db23ef8a83cba8a463690e98317add2c9ba72
  # required for GPU workaround
  extraMounts:
    - hostPath: /dev/null
      containerPath: /var/run/nvidia-container-devices/all
EOF
```
```bash
docker exec -ti dataoorts-control-plane ln -s /sbin/ldconfig /sbin/ldconfig.real
```
```
# In order for K8s to recognize your NVIDIA device, install the K8s NVIDIA GPU operator
helm repo add nvidia https://helm.ngc.nvidia.com/nvidia || true
helm repo update
helm install --wait --generate-name \
     -n gpu-operator --create-namespace \
     nvidia/gpu-operator --set driver.enabled=false
```
```bash
# Now you are all set, test your gpus by running a simple pod
kubectl apply -f - << EOF
apiVersion: v1
kind: Pod
metadata:
  name: cuda-vectoradd
spec:
  restartPolicy: OnFailure
  containers:
  - name: cuda-vectoradd
    image: "nvcr.io/nvidia/k8s/cuda-sample:vectoradd-cuda11.7.1-ubuntu20.04"
    resources:
      limits:
        nvidia.com/gpu: 1
EOF
```
⚡Now you're all set! Enjoy your Kubernetes pods with GPU acceleration.⚡

