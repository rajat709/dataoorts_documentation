---
layout: page
title: Access Applications -- Tunnel 
permalink: /docs/access-applications/
---

### Access Applications Running In GC2 Via Tunneling
To access your application running in GC2 on any particular port using a local tunnel to make it publicly accessible, you can use any tunneling service. However, ensure that it is a trusted service since tunneling is a critical process that can introduce many vulnerabilities. We recommend using ngrok or cloudflare, In DMI, we have already installed ngrok and cloudflared services.

#### Ngrok Tunnel
Ngrok Local Tunnel: [https://dashboard.ngrok.com/](https://dashboard.ngrok.com/)

Create Tunnel

```BASH
# Download and Install Ngrok
curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
	| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
	&& echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
	| sudo tee /etc/apt/sources.list.d/ngrok.list \
	&& sudo apt update \
	&& sudo apt install ngrok
```
```Bash
# Run the following command to add your authtoken to the default ngrok.yml, Get your authtoken here:https://dashboard.ngrok.com/get-started/your-authtoken
ngrok config add-authtoken <your-authtoken>
```
```Bash
# Let's suppose your application is running on port 8080, and you want to make that port publicly available
ngrok http http://localhost:8080
```

This command provides a publicly accessible URL that forwards traffic from your local machine’s port 8080. You can also view your tunnel details on Ngrok’s Agents dashboard [https://dashboard.ngrok.com/tunnels/agents](https://dashboard.ngrok.com/tunnels/agents)

Extra: Ngrok offers several third-party plugins that enhance tunnel analysis, improve security, and provide valuable insights for better usability.

#### Cloudflared Tunnel
Cloudflared Tunnel:[ https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/]( https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/)

**Create Tunnel**
```BASH
# Let's suppose your application is running on port 8888, and you want to make that port publicly available
./cloudflared-linux-amd64 --url [http://localhost:8888](http://localhost:8888)
```
**Example Output:**
```BASH
2024-05-31T08:12:59Z INF Thank you for trying Cloudflare Tunnel. Doing so, without a Cloudflare account, is a quick way to experiment and try it out. However, be aware that these account-less Tunnels have no uptime guarantee. If you intend to use Tunnels in production you should use a pre-created named tunnel by following: https://developers.cloudflare.com/cloudflare-one/connections/connect-apps
2024-05-31T08:12:59Z INF Requesting new quick Tunnel on trycloudflare.com...
2024-05-31T08:13:00Z INF +--------------------------------------------------------------------------------------------+
2024-05-31T08:13:00Z INF |  Your quick Tunnel has been created! Visit it at (it may take some time to be reachable):  |
2024-05-31T08:13:00Z INF |  https://metro-impact-lands-ict.trycloudflare.com                                          |
2024-05-31T08:13:00Z INF +--------------------------------------------------------------------------------------------+
2024-05-31T08:13:00Z INF Cannot determine default configuration path. No file [config.yml config.yaml] in [~/.cloudflared ~/.cloudflare-warp ~/cloudflare-warp /etc/cloudflared /usr/local/etc/cloudflared]
2024-05-31T08:13:00Z INF Version 2024.5.0
2024-05-31T08:13:00Z INF GOOS: linux, GOVersion: go1.22.2, GoArch: amd64
2024-05-31T08:13:00Z INF Settings: map[ha-connections:1 protocol:quic url:http://localhost:8888]
2024-05-31T08:13:00Z INF cloudflared will not automatically update when run from the shell. To enable auto-updates, run cloudflared as a service: https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/run-tunnel/as-a-service/
2024-05-31T08:13:00Z INF Generated Connector ID: 332e5631-b7d2-478d-874f-289a9d01f1af
2024-05-31T08:13:00Z INF Initial protocol quic
2024-05-31T08:13:00Z INF ICMP proxy will use 172.28.0.12 as source for IPv4
2024-05-31T08:13:00Z INF ICMP proxy will use :: as source for IPv6
2024-05-31T08:13:00Z INF Starting metrics server on 127.0.0.1:42781/metrics
2024/05/31 08:13:00 failed to sufficiently increase receive buffer size (was: 208 kiB, wanted: 2048 kiB, got: 416 kiB). See https://github.com/quic-go/quic-go/wiki/UDP-Buffer-Sizes for details.
2024-05-31T08:13:00Z INF Registered tunnel connection connIndex=0 connection=b22a9411-f190-41ec-8d40-27933bf07ae2 event=0 ip=198.41.192.7 location=sea01 protocol=quic
```

[http://localhost:8888](http://localhost:8888)---- Public URL ----> [https://metro-impact-lands-ict.trycloudflare.com](https://metro-impact-lands-ict.trycloudflare.com)

You can also forward GC2 ports to your localhost, but to do so, you need to configure the OpenSSH server in your GC2 instance. Below are some useful guides for setting this up:

[SSH GC2 Instance](/docs/ssh-gc2-instances)

[Connect GC2 Locally](/docs/connect-gc2-locally)