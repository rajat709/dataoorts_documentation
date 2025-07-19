---
layout: page
title: "Configure Firewalls and Security Groups" 
permalink: /docs/set-up-firewall/
parent: "X-Series Instance Documentation"
nav_order: 4
---

## Securing Cloud GPU VM: Allowing Specific IPs and Ports with UFW & iptables
This guide will walk you through securing your Cloud Virtual Machine (VM) by configuring its firewall to accept incoming traffic only from a defined set of IP addresses and on specific ports. This drastically improves your VM's security by blocking unauthorized access attempts. We will be using UFW (Uncomplicated Firewall), a user-friendly front-end for iptables, to manage these firewall rules.

### Prerequisites
* You have an Linux Cloud VM running and are able to access it via SSH.
* You have sudo privileges on the VM.
* You know the specific IP addresses that need to access your VM.
* You know the specific ports that need to be open for necessary services.

### Step 1: Install UFW (Uncomplicated Firewall)
If UFW is not already installed on your Ubuntu VM, you can install it using the following commands:

```bash
sudo apt update
sudo apt install ufw
```

### Step 2: Set Default Firewall Policies
UFW's strength lies in its default deny policy. We will set the default behavior to deny all incoming connections and allow all outgoing connections. This is a fundamental security principle: only explicitly allowed traffic should be permitted.
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

* **sudo ufw default deny incoming**: This command sets the default policy for all incoming connections to deny. This means unless a rule explicitly allows an incoming connection, it will be blocked.
* **sudo ufw default allow outgoing**: This command sets the default policy for all outgoing connections to allow. This generally allows your VM to initiate connections to the outside world (e.g., for software updates, accessing external services), which is usually necessary.

### Step 3: Allow Specific IP Addresses and Ports
Now, we will define rules to allow incoming traffic from specific IP addresses on specific ports. The general syntax for allowing traffic from a specific IP to a specific port using UFW is:
```bash
sudo ufw allow from <ALLOWED_IP> to any port <PORT> [proto <PROTOCOL>] [comment "<DESCRIPTION>"]
```

* **\<ALLOWED_IP\>**: Replace this with the IP address you want to allow. This can be a single IP address (e.g., 203.0.113.5) or an IP range in CIDR notation (e.g., 192.168.1.0/24).
* **\<PORT\>**: Replace this with the port number you want to open (e.g., 22, 80, 443, 3306).
* **[proto \<PROTOCOL\>]**: Optionally specify the protocol, usually tcp or udp. If omitted, UFW usually defaults to tcp for common ports but it's best to be explicit when needed (e.g., for UDP based services).
* **[comment "\<DESCRIPTION\>"]**: Adding a comment helps you remember why a rule was created. This is highly recommended for maintainability.

### Some Common Examples of Allow Rules:

1. Allow SSH (port 22) access from a single IP address 203.0.113.5
```bash
sudo ufw allow from 203.0.113.5 to any port 22 proto tcp comment "Allow SSH from home IP"
```
2. Allow HTTP (port 80) and HTTPS (port 443) access from a specific IP address 203.0.113.5
```bash
sudo ufw allow from 203.0.113.5 to any port 80 proto tcp comment "Allow HTTP from home IP"
sudo ufw allow from 203.0.113.5 to any port 443 proto tcp comment "Allow HTTPS from home IP"
```
3. Allow SSH (port 22) access from a range of IP addresses 198.51.100.0/24 (e.g., your office network)
```bash
sudo ufw allow from 198.51.100.0/24 to any port 22 proto tcp comment "Allow SSH from office network"
```
4. Allow MySQL/MariaDB (port 3306) access from IP 192.0.2.10
```bash
sudo ufw allow from 192.0.2.10 to any port 3306 proto tcp comment "Allow MySQL from DB admin server"
```
5. Allow UDP port 53 (DNS) from a specific IP (though typically DNS queries are outgoing, this is just an example of UDP)
```bash
sudo ufw allow from 203.0.113.5 to any port 53 proto udp comment "Allow UDP DNS from home IP (example)"
```
> Repeat Step 3 for every IP address and port combination that needs to be allowed access to your VM.

### Step 4: Enable UFW
**Crucial Precaution**: Before enabling UFW, ensure you have created a rule to allow SSH access from your current IP address. If you are accessing your VM via SSH and you enable UFW without allowing your current IP on port 22 (or your custom SSH port), you will likely lose your SSH connection and be locked out.

**If you are unsure, as a safety measure, you can temporarily allow SSH from anywhere before enabling UFW, and then refine the rule afterward:**
```bash
sudo ufw allow ssh comment "Temporary allow SSH from anywhere for initial setup"
```
**After verifying your SSH access is working, you can then enable UFW:**
```bash
sudo ufw enable
```
You will be prompted to confirm enabling the firewall. Type y and press Enter.

> Once UFW is enabled, it will start enforcing the rules you have defined, including the default deny incoming policy.

**If you temporarily allowed SSH from anywhere, now you should replace that rule with a more specific rule to allow SSH only from your known IP(s) and delete the broad "allow ssh" rule.**

For example, to allow SSH only from 203.0.113.5 and remove the temporary rule:
```bash
sudo ufw allow from 203.0.113.5 to any port 22 proto tcp comment "Allow SSH from home IP"
sudo ufw delete allow ssh  # Deletes the rule that allows SSH from anywhere (if you added it)
```
### Step 5: Verify UFW Rules and Status

To check the current status of UFW and review the configured rules, use the command:
```bash
sudo ufw status numbered
```
This command will display the status of UFW (active or inactive) and list all the active rules with numbers assigned to each rule. This numbered list is helpful if you need to delete a specific rule later.

**Example Output:**
```
Status: active

     To                         Action      From
     ----                       ------      ----
[ 1] 22/tcp                     ALLOW IN    203.0.113.5
[ 2] 80/tcp                     ALLOW IN    203.0.113.5
[ 3] 443/tcp                    ALLOW IN    203.0.113.5
[ 4] 22/tcp                     ALLOW IN    198.51.100.0/24
```

This output shows that UFW is active and the following rules are in place:

* Rule 1: Allows TCP traffic on port 22 (SSH) from IP address 203.0.113.5
* Rule 2: Allows TCP traffic on port 80 (HTTP) from IP address 203.0.113.5
* Rule 3: Allows TCP traffic on port 443 (HTTPS) from IP address 203.0.113.5
* Rule 4: Allows TCP traffic on port 22 (SSH) from the IP range 198.51.100.0/24

### Real Case - Firewall Configuration Scenario
Let's say you want to configure your VM with the following requirements:

* Allow SSH access only from IP addresses 203.0.113.5 and 198.51.100.10
* Allow HTTP (port 80) and HTTPS (port 443) access only from IP address 203.0.113.5
* Block all other incoming traffic

**Here are the set of ubuntu commands you would execute:**
```bash
sudo apt update && sudo apt install ufw  # Step 1 (if needed)
sudo ufw default deny incoming          # Step 2
sudo ufw default allow outgoing         # Step 2

#sudo ufw allow from 203.0.113.5 to any port 22
#sudo ufw allow from 203.0.113.5 to any port 80
#sudo ufw allow from 203.0.113.5 to any port 443
#sudo ufw allow from 198.51.100.10 to any port 22

sudo ufw allow from 203.0.113.5 to any port 22 proto tcp comment "Allow SSH from home IP" # Step 3
sudo ufw allow from 198.51.100.10 to any port 22 proto tcp comment "Allow SSH from secondary IP" # Step 3
sudo ufw allow from 203.0.113.5 to any port 80 proto tcp comment "Allow HTTP from home IP" # Step 3
sudo ufw allow from 203.0.113.5 to any port 443 proto tcp comment "Allow HTTPS from home IP" # Step 3

sudo ufw enable                       # Step 4
sudo ufw status numbered              # Step 5 (Verify)
```

### Important Notes and Best Practices:
* **Lockout Prevention is Paramount**: Always be extremely cautious when enabling and configuring firewalls. Ensure you have a way to access your VM even if you misconfigure the firewall (e.g., through a cloud provider's console access). Test your rules incrementally. Add one rule at a time and verify connectivity before adding more.
* **IP Ranges (CIDR Notation)**: Use CIDR notation (e.g., 192.168.1.0/24) when you need to allow access from a range of IP addresses, such as a network.
* **Deleting Rules**: If you need to remove a rule, use the sudo ufw delete <RULE_NUMBER> command. You can get the rule number from the output of sudo ufw status numbered. For example, to delete rule number 1, use: sudo ufw delete 1. You can also delete rules by specifying the rule itself, e.g., sudo ufw delete allow from 203.0.113.5 to any port 22 proto tcp.
* **Rule Order**: UFW rules are generally processed in order. The first rule that matches the incoming traffic will be applied. While UFW tries to optimize rule order, it's generally a good practice to place more specific rules before broader ones.
* **Testing Your Configuration**: After enabling UFW and setting up your rules, thoroughly test your setup. Try accessing your VM from the allowed IP addresses on the allowed ports. Also, try to access it from a disallowed IP address or on a disallowed port to confirm that the firewall is blocking as expected.
* **Comments are as Your Friends**: Always use comments (comment "<DESCRIPTION>") when adding rules. This makes it much easier to understand and manage your firewall rules in the future.
* **Persistence**: UFW rules are persistent by default. They will be automatically loaded when your VM reboots. You don't need to take extra steps to save them.
* **Advanced Scenarios (Optional)**: For very large sets of IP addresses, consider using ipset with iptables directly, as mentioned in the more advanced section below. However, for most common use cases, UFW is sufficient and easier to manage.

### Advanced Topic: Using 'ipset' for Very Large IP Sets (Optional)
If you need to manage firewall rules for a very large number of IP addresses (thousands or more), using ipset directly with iptables can be more efficient than adding individual UFW/iptables rules. ipset allows you to create named sets of IPs and then match against these sets in your iptables rules.

> Note: Using ipset directly requires a deeper understanding of iptables and is generally only necessary for very specific, high-scale scenarios. For most users, UFW is sufficient.

If you choose to explore ipset, you would follow steps similar to these (this is a brief overview and not a complete tutorial):

1. Install ipset: sudo apt install ipset
2. Create an ipset: sudo ipset create ALLOWED_IPS hash:ip (creates a set named ALLOWED_IPS of type hash:ip).
3. Add IPs to the set: sudo ipset add ALLOWED_IPS 203.0.113.5, sudo ipset add ALLOWED_IPS 198.51.100.10, etc.
4. Create iptables rules that use the ipset:

```bash
sudo iptables -A INPUT -m set --match-set ALLOWED_IPS src -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -m set --match-set ALLOWED_IPS src -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -m set --match-set ALLOWED_IPS src -p tcp --dport 443 -j ACCEPT
sudo iptables -A INPUT -j DROP  # Default drop rule (similar to UFW's default deny incoming)
```
5. Make iptables rules persistent (using iptables-persistent package if needed).

### Alternative: Using 'iptables' Directly (Advanced Users)
While UFW simplifies firewall management, you can also configure iptables directly for more granular control. However, this method is more complex and error-prone for beginners. If you are comfortable with iptables, you can achieve the same results by directly manipulating iptables rules, setting **default policies**, and creating ACCEPT rules for specific source IPs and destination ports. Remember to save your iptables rules to persist after a reboot if you use iptables directly.

### Conclusion
By following this guide, you have successfully configured your Cloud GPU VM firewalls & Security Groups to allow incoming traffic only from specific IP addresses and on designated ports using UFW. This significantly enhances the security of your VM by limiting exposure to unauthorized access attempts. Remember to always test your firewall rules and maintain a record of your configuration for future management. Always prioritize security best practices and keep your system updated.

