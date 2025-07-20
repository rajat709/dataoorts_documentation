---
layout: page
title: Get Started With X-Series GPU Instances
permalink: /docs/get-started-x-series-gpu-instances/
parent: "X-Series Instance Documentation"
nav_order: 1
published: Mar 9, 2025
updated: Mar 9, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


## Launch X-Series Instance
Here are steps to launch your first x-series instance:

step 1: Visit [Here](https://cloud.dataoorts.com/) or Register your account and verify your email and make sure x-series instance starts with “x_“ or “x-“.

step 2: Add sufficient credit amount to start your x-series instance.

step 3: Select the instance type you want to spin up, For more specifications about GPU models, visit [Here](https://dataoorts.com/pricing).

step 4: Select your DMI (learn more about DMI: [Here](https://dataoorts.com/dmi)) and **Launch Instance**.

step 5: To access your instance, Default **temporary.pem** SSH key is automatically generated for instance access. However, since this key is provided by default, you should update your instance's SSH credentials with your own key. Instructions for changing the key is [Here](https://dataoorts.document360.io/v1/docs/ssh-fortify).

{: .highlight }
> Note: While the instance is launching or terminating, do not close or refresh the browser. It will take a while to process everything.

<details class="fancy-details">
<summary>
Super-DDRA Cluster for Hosting X-Series Instance Nodes
</summary>
<div class="fancy-details-content">
All X-Series instances are hosted in a secure cloud environment within Tier 3 and Tier 4 data centers. The DDRA Cluster for X-Series consists of a globally distributed hybrid GPU infrastructure, integrating our own GPU racks in data centers alongside major cloud and GPU providers.
</div>
</details>

{: .warning-title }
> Report Issue/Bug
>
> If you encounter any bugs or issues on our cloud platform, we sincerely appreciate your efforts and time in notifying us. Please feel free to reach out to us
> at [help@dataoorts.com](help@dataoorts.com).
>
