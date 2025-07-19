---
layout: page
title: "GC2: Kubernetes"
permalink: /docs/gc2-kubernetes/
parent: "GC2 Instance Documentation"
nav_order: 9
published: May 30, 2024
updated: May 31, 2024
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">



## Get Started With K8s In GC2 Instance
Setting up a Kubernetes cluster on a GC2 instance has been tested with KinD, Minikube, and Rancher K3s. Before setting up your Kubernetes environment, ensure you select Docker as the driver and configure it to use the GPU devices you want to make visible in your pods.

1. [Setting Up Kubernetes via KinD](https://dataoorts.document360.io/docs/kind-cluster)

2. [Setting Up Kubernetes via Minikube](https://dataoorts.document360.io/docs/minikube)

3. [Installing Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)