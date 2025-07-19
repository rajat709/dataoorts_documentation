---
layout: page
title: "GC2: Docker"
permalink: /docs/gc2-docker/
parent: "GC2 Instance Documentation"
nav_order: 8
published: May 30,2024
updated: May 30, 2024
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


## Using Docker In GC2 Instance
We have now added Docker as one of the primary setups for the GC2 instance for all DMI. Hence, you have the latest version of Docker running. If you want to install a specific version of Docker, please follow the instructions given on the official Docker site,[(https://docs.docker.com/engine/install/ubuntu/)](https://docs.docker.com/engine/install/ubuntu/).

**Bonus**: We have also installed and configured the latest version of the **NVIDIA Container Toolkit** with Docker for your convenience. Now you can run GPU-accessible containers by adding two flags: --gpus and --runtime=nvidia
You can also install a specific version of the NVIDIA Container Toolkit from the official site: [(https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).

