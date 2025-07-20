---
layout: page
title: "SSH Access Fortify" 
permalink: /docs/ssh-fortify/
parent: "X-Series Instance Documentation"
nav_order: 3
published: Mar 9, 2025
updated: Mar 10, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">



## Replacing SSH Keys on Your X-Series VMs
This doc will guide you through the process of replacing your existing SSH keys on your Linux VM with a new key pair. This is a common security practice, especially if your default private key is auto-generated or if you simply want to refresh your keys.

{: .highlight }
> If you choose not to rotate your private key and decide to stick with the default `temporary.pem` key, we strongly recommend configuring firewall restrictions and limiting access to a specific set of IP addresses. To configure the firewall, refer to its documentation available [Here](https://dataoorts.document360.io/v1/docs/set-up-firewall-and-security-groups).
>

### Assumptions:
* You have SSH access to your Linux VM using your current SSH key.

* Your username on the Cloud VM is ubuntu. (Default Set for X-Series Instances).

* You are using a Windows machine (but the rsa-key generation steps are broadly applicable to other operating systems).

### Step 1: Generate a New SSH Key Pair on Your Local Machine (Windows Example)
First, you need to create a new SSH key pair on your local computer. This will consist of a private key (which you keep secret) and a public key (which you will upload to your VM).

Open your terminal or command prompt and run the following command to generate a new RSA SSH key in PEM format with the comment “ubuntu”:

```powershell
### PowerShell
ssh-keygen -t rsa -m PEM -C ubuntu
```

Explanation of the command:

* ssh-keygen: The SSH key generation utility.

* -t rsa: Specifies the key type as RSA (a widely used and secure algorithm).

* -m PEM: Specifies the key format as PEM (Privacy Enhanced Mail), the standard format for SSH keys.

* -C ubuntu: This will set the default username to ubuntu (you can choose any username you prefer).

### Prompts during key generation:

1. Enter file/folder/directory in which you want to save the keys, for example: `C:\Users\rjvishwa\Downloads\keys\id_rsa`.

2. Press Enter to accept the default filename id_rsa (private key) and id_rsa.pub (public key) in the current directory (C:\Users\rjvishwa\Downloads\keys in this example). You can also enter a different filename if you wish. (***Note:*** On Linux/Mac the keys will be saved in your home directory typically under ~/.ssh/).

3. After that Enter passphrase (empty for no passphrase) or You will be prompted to enter a passphrase to protect your private key. It is highly recommended to use a strong passphrase. If your private key is compromised, the passphrase provides an extra layer of security. If you don't want a passphrase (less secure, but more convenient), just press Enter twice to leave it blank.

### You will see output similar to this:
```
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\rjvishwa\Downloads\keys\id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\rjvishwa\Downloads\keys\id_rsa
Your public key has been saved in C:\Users\rjvishwa\Downloads\keys\id_rsa.pub
The key fingerprint is:
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx ubuntu
The key's randomart image is:
+---[RSA 3072]----+
|        o        |
|       o .       |
|      . + .      |
|     . o o       |
|    . S + .      |
|   o o *         |
|  . o + E        |
|   + . o         |
|  . . .          |
+----[SHA256]-----+
```

***Key Files Created***: After successful generation, you will have two files in your specified directory (e.g., C:\Users\rjvishwa\Downloads\keys):

* ***id_rsa***: This is your PRIVATE KEY. Keep this file SECRET and SECURE. Do not share it with anyone.

* ***id_rsa.pub***: This is your PUBLIC KEY. You will copy the contents of this file to your cloud ubuntu VM.

### Step 2: View and Copy Your Public Key (id_rsa.pub)
If you're using Linux, you can simply use the `cat` command or open the `id_rsa.pub` file with `nano` to view its contents, and then copy the content. On a Windows machine, you can open the file using any available option, and then copy the public key for later use.

### Step 3: Update the Authorized Keys on Your Ubuntu VM
Backup Existing Authorized Keys, It’s a good practice to keep a backup before making changes.

```bash
cd ~/.ssh
cp ~/.ssh/authorized_keys ~/.ssh/authorized_keys.bak
```
This will create a copy of existing ***authorized_keys*** file as ***authorized_keys.bak*** file in the ***~/.ssh*** directory of the current VM user.

***Edit*** the Authorized Keys File:

```bash
#Open the file with nano editor
nano ~/.ssh/authorized_keys
# When nano editor open delete all keys present
```

{: .important }
> Delete all existing keys in /authorized_keys and paste your new public key content that you copied earlier (id_rsa.pub).

Save and Exit, Press `CTRL+O` to save, then `Enter`, and `CTRL+X` to exit nano.

### Step 4: Test SSH Access with the New Private Key
When connecting to your VM, specify your new private key with the `-i` option:

```
# ssh -i <Path_to_private_key> <username>@<x-series_vm_ip> -p <SSH_Port>
ssh -i C:\Users\rjvishwa\Downloads\keys\id_rsa ubuntu@<YOUR_VM_IP_ADDRESS> -p 22
```
***Verify Successful Login***: If everything is configured correctly, you should be able to log in to your VM without being prompted for a password. You will be logged in using SSH key authentication with your new key pair.

### Step 5: Remove Backup of Old Keys (If Confirmed Working)
If you are confident that your new SSH key access is working correctly, you can remove the backup of your old ***authorized_keys*** file:

```bash
cd ~/.ssh
rm authorized_keys.bak
```
### Important Security Reminders:

* ***Protect Your Private Key***: Your private key (id_rsa) is extremely sensitive. Keep it secure and private. Do not share it with anyone, and do not accidentally upload it to public websites or repositories.

* ***Use a Strong Passphrase***: If you chose to use a passphrase for your private key, remember it and use it whenever you use your private key for SSH.

* ***Firewall Configuration***: If you choose not to replace the default `temporary.pem` key, you should at least configure firewall restrictions to allow access from only a limited set of specific IP addresses.

* ***Regular Key Rotation***: Consider rotating your SSH keys periodically as a security best practice.

{: .note }
> Congratulations! You have successfully replaced the SSH keys on your Cloud X-Series GPU VM, enhancing its security and ensuring you have control over who can access your server via SSH. Always test your SSH access immediately after making changes to your keys.