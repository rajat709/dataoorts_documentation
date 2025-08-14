---
layout: page
title: "FAQs: X-Series Instance" 
permalink: /docs/x-series-instance-faqs/
parent: "X-Series Instance Documentation"
nav_order: 3
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


## X-Series Instance — F.A.Qs
<br>
<details class="fancy-details">
<summary>What is DDRA ?</summary>
<div class="fancy-details-content">
Learn about DDRA [Here](/why-and-how-dataoorts-gpu-cloud).
</div>
</details>


<details class="fancy-details">
<summary>Is it necessary to secure my SSH access after launching the VM ?</summary>
<div class="fancy-details-content">
Yes, it is highly recommended to secure your SSH access. You should either reset the SSH key or configure firewall rules to allow access only from authorized IPs. By default, a temporary.pem key is generated for instance access, but for enhanced security, you should replace it with your own SSH key. Detailed instructions on updating your SSH key can be found in our documentation [Here](https://dataoorts.document360.io/v1/docs/ssh-fortify).
</div>
</details>


<details class="fancy-details">
<summary>What should I do if I configured my X-Series instance firewall and security group rules to my remote IP, but my IP has changed or is lost ?</summary>
<div class="fancy-details-content">
If you have restricted access to your X-Series instance using specific IP addresses and those IPs have changed, you will no longer be able to access your instance. However, there’s no need to worry—we're here to help! Simply email us at [help@dataoorts.com](help@dataoorts.com) with your VM ID, and we will reset the firewall rules to their default settings. This will restore your access without any data loss.
</div>
</details>

<details class="fancy-details">
<summary>Where My X-Series Instance Hosted ?</summary>
<div class="fancy-details-content">
All X-Series instances are hosted in a secure cloud environment within Tier 3 and Tier 4 data centers. The DDRA Cluster for X-Series consists of a globally distributed hybrid GPU infrastructure, integrating our own GPU racks in data centers alongside major cloud and GPU providers.
</div>
</details>

<details class="fancy-details">
<summary>
Does X-Series Instance Work on DDRA ?
</summary>
<div class="fancy-details-content">
Yes, All X-Series Instance Works on Super-DDRA Secured Cluster.
</div>
</details>

<details class="fancy-details">
<summary>
What are RAMs and CPUs in Particular Instance ?
</summary>
<div class="fancy-details-content">
RAMs and CPUs and all other resources are allocated dynamically using DDRA Technology.
</div>
</details>

<details class="fancy-details">
<summary>Is there any hidden charge ?</summary>
<div class="fancy-details-content">
No, what you see in the dashboard is it.
</div>
</details>

<details class="fancy-details">
<summary>
Does X-Series Instance is VM-Based ?
</summary>
<div class="fancy-details-content">
Yes, X-Series Instance is Complete VM with KVM Hypervisor Enabled, You Get Complete Access to Machine.
</div>
</details>

<details class="fancy-details">
<summary>Can I use X-Series for Gaming ?</summary>
<div class="fancy-details-content">
Yes, You can use all instances for gaming, video rendering and all other ethical works that required GPU compute.
</div>
</details>

<details class="fancy-details">
<summary>Can I mine Crypto In GC2 Instance ?</summary>
<div class="fancy-details-content">
No, we strictly prohibit any mining activity or any illegal activity.
</div>
</details>

<details class="fancy-details">
<summary>What if my balance goes down below the threshold point ?</summary>
<div class="fancy-details-content">
If your balance goes below $2.50, all running instances and pods are automatically scheduled for termination. So please maintain the minimum balance of $2.50 or above.
</div>
</details>



<details class="fancy-details">
<summary>Can we pause the instance rather than terminating it ?</summary>
<div class="fancy-details-content">
Currently, we are working on persistent storage for GC2 instances. We assure you that this will be supported very soon.
</div>
</details>


<details class="fancy-details">
<summary>What is DMI ?</summary>
<div class="fancy-details-content">
Learn about DMI [Here](/dmi).
</div>
</details>
