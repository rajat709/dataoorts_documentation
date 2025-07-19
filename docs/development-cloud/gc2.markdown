---
layout: page
title: Get Started With GC2 GPU Instance
permalink: /docs/gc2/
parent: "GC2 Instance Documentation"
nav_order: 1
published: Mar 9, 2025
updated: Feb 24, 205
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">

## Launch GC2 Instance

### Here are steps to launch your first gc2 instance:

step 1: Visit [https://cloud.dataoorts.com/](https://cloud.dataoorts.com/) Register your account and verify your email.

step 2: Add sufficient credit amount to start your GC2 instance.

step 3: Select the instance type you want to spin up. The first object is the GPU model, the second object is the total GPU memory, and the third object is the total number of GPUs in the instance. For example, 'H100-80-1' means one Nvidia H100 GPU. For more specifications about GPU models, visit [https://dataoorts.com/pricing/](https://dataoorts.com/pricing/).

step 4: Select your DMI (learn more about DMI: [https://dataoorts.com/dmi/](https://dataoorts.com/dmi/)) and Launch Instance.

step 5: To access your instance, we provide a Jupyter-based web SSH session. fyi, You can add your preferred method for accessing the instance.

{: .highlight }
> Note: While the instance is launching or terminating, do not close or refresh the browser. It will take a while to process everything.

<details class="fancy-details">
<summary>DDRA Cluster for Hosting GC2 Instances Nodes</summary>
<div class="fancy-details-content">
All GC2 instances are hosted within Dataoorts' globally distributed DDRA Cluster. As community-based instances, GC2 leverages decentralized GPUs worldwide, ensuring robust isolation and a secure operating environment.
</div>
</details>

<br>

{: .warning}
> Report Issue/Bug
>
>If you encounter any bugs or issues on our cloud platform, we sincerely appreciate your efforts and time in notifying us. Please feel free to reach out to us at [help@dataoorts.com](help@dataoorts.com)