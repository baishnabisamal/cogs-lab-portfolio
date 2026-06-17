# Lab 1.3 Findings

## Both VMs configured, WireGuard running — 'wg show' output showing active peer on both sides
<img width="1396" height="277" alt="Screenshot (198)" src="https://github.com/user-attachments/assets/f2261c99-d890-485e-b041-747e4e1c7451" />
<img width="1308" height="300" alt="Screenshot (199)" src="https://github.com/user-attachments/assets/ab1abdae-9b6d-428a-902d-8aaafbec055c" />

## Successful ping from VM2 to 10.0.0.1 (VM1) through the tunnel — screenshot
<img width="1414" height="288" alt="Screenshot (200)" src="https://github.com/user-attachments/assets/bfa0439b-ac69-46a5-b393-c64f130d5b0e" />

## tcpdump screenshot showing encrypted UDP traffic (not readable plaintext)
<img width="1476" height="713" alt="Screenshot (201)" src="https://github.com/user-attachments/assets/bb3592a9-83d5-4b03-859d-db99e1345085" />
<img width="1920" height="544" alt="Screenshot (202)" src="https://github.com/user-attachments/assets/3ba8405a-0404-4d79-981b-31800f1282c6" />

## Map the WireGuard components (client, server, tunnel, keys) to InstaSafe ZTNA components (Agent, Gateway, Controller, certificates)
WireGuard works like ZTNA by using identity-based authentication and encrypted tunnels between a client (agent) and server (gateway)
- VM2 (Client) → ZTNA Agent (user device that connects)
- VM1 (Server) → ZTNA Gateway (controls access)
- WireGuard Tunnel → Secure encrypted ZTNA connection
- Public/Private Keys → Identity-based authentication
- AllowedIPs → Access control rules (what can be accessed)
- Handshake → Successful authentication/session start
- tcpdump UDP traffic → Proof of encrypted communication
