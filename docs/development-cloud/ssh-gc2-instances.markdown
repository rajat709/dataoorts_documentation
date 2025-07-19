---
layout: page
title: SSH GC2 Instances
permalink: /docs/ssh-gc2-instances/
---

### Access GC2 Instance — SSH
You can access our GC2 instance either directly through a browser or from your local machine.
Ways to Access the GC2 Instance:
Web Based Jupyter Terminal (Depreciated)

SSH

#### Web Based Terminal - Jupyter (Depreciated)
We provide direct access to a web terminal (Jupyter-based). You don't need to set up anything. Just choose your instance type and DMI, and launch the instance. You will find a button for ‘‘Web-SSH’’ for web-based terminal access.

#### SSH
To use SSH, you need to manually set up an SSH server on the GC2 instance. You can choose either password-based or key-based authentication. Below is a quick tutorial on how to set up an SSH connection.  

```BASH
BASH
# Update everything
sudo apt-get update
```

```BASH
BASH
# The openssh-server is pre-installed, but you should reinstall it if any updates are available
sudo apt install -y openssh-server
```

```BASH
BASH
# Check status of ssh-server
sudo service --status-all
# If SSH shows a negative sign, it means the SSH server is not activated yet. You need to activate it
```

Before activating OpenSSH, if you want to use key-based authentication, you need to upload your public key. For this example, we will use password-based authentication, so we first set the password for the user. By default, the user is root, but you can add as many users as you want with the privileges you wish to assign. Here, we will proceed with the root user.

```BASH
BASH
# set up password for root user
sudo passwd root
```

```BASH
BASH
# Permit Root Login
sudo nano /etc/ssh/sshd_config
# This will open the 'ssh_config' file. You need to add the line 'PermitRootLogin Yes'
```

```
CUSTOM
# Add line
PermitRootLogin Yes
# After that Press <ctrl + O> to save the modification and after that <ctrl + X> to close the nano editor
```

```BASH
BASH
# Now you need to start the OpenSSH service if it is not already running
sudo service ssh start
# After this, check if the SSH service has a plus sign indicating that it is active and running
sudo service --status-all
```

Now you are set to SSH to your GC2 instances from anywhere using SSH.

```BASH
BASH
# SSH into your GC2 instance
ssh <user>@<Node-Public-IP> -p <Node-port Forwording to your Instance port 22>
# If you are using key-based authentication, you will be logged in directly as <user>
# If you are using password-based authentication, you need to type your password for <user>
```

```BASH
BASH
# Let's take an example!
# user is 'root'
# node public-ip is '16.25.96.84'
# forwarded node port mapped with your instance port 22 is '7852'
ssh root@16.25.96.84 -p 7852
# Now enter your 'root' user password that you set earlier, and you are all set
# These configurations are one-time; you don't need to do this again
```

If you are comfortable with your local development environment, there is a way to connect your GC2 instance with your local machine. This allows you to leverage the comfort of your local development setup while benefiting from the performance acceleration provided by Dataoorts GC2 instances. [Set-Up Guide](/docs/connect-gc2-locally/)