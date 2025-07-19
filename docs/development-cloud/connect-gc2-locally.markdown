---
layout: page
title: Connect GC2 Locally
permalink: /docs/connect-gc2-locally/
parent: "GC2 Instance Documentation"
nav_order: 4
---

## Run GC2 Instance Locally

{: .important-title }
> Note 📝
> 
> To run a GC2 instance locally, you need to set up the OpenSSH server manually on your GC2 instance. Here is the guide: [SSH-GC2](https://dataoorts.document360.io/docs/ssh-gc2-instances)
>

You can use local port forwarding for many applications to turn your local machine into an interface powered by a remote GC2 instance. This setup allows you to enjoy the comfort of your local environment while leveraging the acceleration of GPU compute. You can use several major services locally with the hardware acceleration of GC2, including:

* Google Colab
* Deepnote
* Jupyter
* VS Code
* PyCharm
* RStudio
* Matlab
* TensorFlow
* PyTorch
* Apache Spark
* AutoML tools
* Unity 3D
* GROMOS
* LAMMPS
* NAMD
* AMBER
* And many more…

```bash
# Forward the port <abcd> from your local machine to port <wxyz> on your remote GC2 machine
# ssh -L <abcd>:localhost:<wxyz> user@node_ip -p <node port forwarded to port 22 on GC2>
ssh -L <abcd>:localhost:<wxyz> user@node_ip -p <node port forwarded to port 22 on GC2>
```

```bash
# You can also forward multiple ports
# ports to forward: <abcd> --> <wxyz> & <ghij> --> <pqrs>
ssh -L <abcd>:localhost:<wxyz> -L <ghij>:localhost:<pqrs> user@node_ip -p <node port forwarded to port 22 on GC2>
```

```bash
# Let's take an example
# forward localhost port from: 7788
# to remote GC2 instance port: 9988
# GC2 instance user: root
# GC2 instance node_ip: 24.56.84.12
# node port forwarded to port 22 on GC2: 24697
ssh -L 7788:localhost:9988 root@24.56.84.12 -p 24697
```