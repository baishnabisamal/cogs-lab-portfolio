# Lab 1.1 Findings
## My VM Details
- Provider: AWS
- Region: eu-north-1
- OS: Ubuntu 26.04 LTS

## Experiment Results
### Ping to 8.8.8.8
- Average RTT: 4.558ms
- TTL value observed: 118
- What does TTL tell us about the path?:  TTL tells us the number of hopes a packet has travelled across the network, helps identify the sender's operating system based on default TTL values, indicates the approximate distance to the destination, and prevents infinite routing loops by causing routers to drop packets when the counter reacher zero.

### Traceroute to google.com
- Number of hops: 6
- Any * * * hops? At which hop number?: yes, observed at 2.

### DNS Comparison
- Result from default DNS: 
Server: 127.0.0.53
Address: 127.0.0.53#53
Non-authoritative answer:
Name: google.com
Address: 142.251.38.110
Name: google.com
Address: 2a00:1450:400f:80f::200e
- Result from 1.1.1.1: 
Server: 1.1.1.1
Address: 1.1.1.1#53
Non-authoritative answer:
Name: google.com
Address: 142.251.143.142
Name: google.com
Address: 2a00:1450:400f:806::200e
- Are they different? Why might they differ?: Yes. the address differs because default DNS and 1.1.1.1 use different server infrastuctures and locations. Each DNS provider resolves domains to their nearest or preffered server, so default DNS routes to one IP while 1.1.1.1 rounts to another

### google.com TLS Certificate
- Issuer: C=US, O=Google Trust Services, CN=WR2
- Expiry date: Aug 17 08:36:18 2026 GMT
- TLS version used: TLSv1.3

### Screenshots:
<img width="1015" height="739" alt="Screenshot (172)" src="https://github.com/user-attachments/assets/968aeb2f-f48c-4573-8fc3-23bba8c2a76b" />

<img width="1285" height="597" alt="Screenshot (173)" src="https://github.com/user-attachments/assets/f97c807b-74b0-4e32-ace0-0fdf3994d8d2" />

<img width="1484" height="699" alt="Screenshot (174)" src="https://github.com/user-attachments/assets/9d59e31b-caeb-4589-b99e-672ee35b48a6" />

<img width="818" height="724" alt="Screenshot (175)" src="https://github.com/user-attachments/assets/14c3ec74-aaa3-4e1e-98b9-b94b69e036ab" />

<img width="1704" height="908" alt="Screenshot (176)" src="https://github.com/user-attachments/assets/4a483e9c-bd8f-423d-a00a-b81ace907d1b" />








