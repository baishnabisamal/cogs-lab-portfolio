# Capstone Lab Architecture

## Capstone architecture running — screenshot 

### Curl Proof
<img width="1449" height="726" alt="Screenshot (344)" src="https://github.com/user-attachments/assets/1b185bd2-1527-48d3-9a16-86e6607347fd" />
<img width="1455" height="707" alt="Screenshot (345)" src="https://github.com/user-attachments/assets/ea5fd74e-ad6c-47b1-bfdf-79def0907dd9" />
<img width="1463" height="709" alt="Screenshot (346)" src="https://github.com/user-attachments/assets/0d206c89-4a31-4d79-8302-85e318abcca5" />

### Wireguard Handshake
<img width="1782" height="296" alt="Screenshot (349)" src="https://github.com/user-attachments/assets/e617888d-913c-4b3f-b41d-81b620a4334e" />

### Uptime Kuma Dashboard
<img width="1861" height="920" alt="Screenshot (361)" src="https://github.com/user-attachments/assets/2b51bd01-644c-41ca-b49f-34e0a6719266" />


### Ping from laptop
<img width="1263" height="351" alt="Screenshot (347)" src="https://github.com/user-attachments/assets/00710434-dbcd-43d5-9b10-4994c907bf7c" />

## Architecture diagram 
<img width="1119" height="762" alt="architecture" src="https://github.com/user-attachments/assets/1f2f6afa-e816-460d-b08e-8d3e9e0d1bef" />

## How does this mini-ZTNA map to the real InstaSafe product?What is missing compared to a production deployment?

### What I built and what I learned

When I started this capstone, Zero Trust was just a term I had read about. By the end of it, I had actually built one — two AWS servers, a VPN tunnel, a reverse proxy, an identity provider, and a monitoring stack all working together. It is not a perfect ZTNA, but it is real enough that I can now look at an InstaSafe support ticket and picture exactly what is happening under the hood.

The part that clicked for me first was WireGuard. Before this lab, I thought of VPNs as something you just install and it works. Building it from scratch — generating key pairs, writing the config file, watching the handshake appear in `wg show` — made me understand why a "VPN not connecting" ticket is almost always a key mismatch or a firewall blocking UDP 51820. Those two things cover a lot about tunnel failures. I would not have known that without debugging my own setup for an hour.

The WireGuard tunnel in this lab is doing the same job as the InstaSafe Agent on a user's laptop. The Agent creates an encrypted connection to the Gateway, exactly like my laptop's WireGuard client connects to VM2. Every packet between my laptop and VM2 is encrypted with ChaCha20 — nobody on the network between us can read it. That is the whole point of Zero Trust: do not trust the network, encrypt everything regardless.

Nginx surprised me. I thought a reverse proxy was complicated but the config is just a few lines — listen on port 80, if the path is `/app` forward to VM1 port 8080. What made it real was seeing it actually work: typing `curl http://10.0.0.1/app` on my laptop and getting Keycloak HTML back, knowing that request had just travelled through an encrypted tunnel, been decrypted by VM2, forwarded across the AWS private network, hit Keycloak on VM1, and come all the way back. That whole journey in under 200ms. In InstaSafe, the Gateway does this same routing — but it also checks access policies before forwarding. That is the big difference.

Keycloak was the most challenging piece. On a t2.micro with 1GB of RAM it takes almost 90 seconds to start, and it crashed twice before I added the 2GB swap file. That experience alone taught me something useful: when a customer says "Keycloak is down" or "SSO stopped working after a restart," the first thing I would check now is memory. Identity providers are heavy. They need resources.

Uptime Kuma monitoring the stack made the whole thing feel like a real system. When I stopped Nginx and watched the monitor go red, then restarted it and watched it go green — that is exactly what a Site24x7 alert looks like on a real shift.

### What is missing

The biggest gap is that there is no authentication before the tunnel comes up. In InstaSafe, you have to log in before the Agent connects. In my setup, anyone with the WireGuard private key can connect — no username, no password, no MFA. That is a fundamental difference.

There is also no access policy engine. My Nginx proxy forwards every request to Keycloak without checking who is asking. A real Gateway would verify the user's identity, group membership, device health, and time of day before allowing the request through. Without that, it is just a proxy, not Zero Trust.

Device posture checking is completely absent too. InstaSafe checks whether your laptop has antivirus running, whether the OS is patched, whether the disk is encrypted. My WireGuard server does not care about any of that — it only checks the cryptographic key.

Finally, there is no management plane. Every change I made required SSHing into a VM and editing a config file manually. InstaSafe has a Controller that pushes policy updates to all Gateways centrally, handles key rotation automatically, and gives admins a dashboard. Building that from scratch would take months.

But despite all of that, this capstone gave me something no amount of reading could: I now understand what I am looking at when a support ticket comes in. "Gateway unreachable" means WireGuard or firewall. "SSO failure" means Keycloak or LDAP. "Users can't reach the app" means Nginx or the backend. 
