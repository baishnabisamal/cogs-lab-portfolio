# Lab 3.1 Findings

## All 3 monitors created and showing green — screenshot of dashboard
<img width="1920" height="906" alt="Screenshot (249)" src="https://github.com/user-attachments/assets/93288681-db88-48f0-8d23-f905ff2cb8b1" />

## Failure triggered and captured — screenshot of red monitor with incident timeline
<img width="1920" height="903" alt="Screenshot (251)" src="https://github.com/user-attachments/assets/9a4d2274-7386-4069-9c71-18556ef8167c" />
<img width="1920" height="888" alt="Screenshot (252)" src="https://github.com/user-attachments/assets/c8eda669-eb36-4470-be15-49fc4df6308d" />

##  Recovery captured — screenshot showing transition back to green
<img width="1920" height="906" alt="Screenshot (254)" src="https://github.com/user-attachments/assets/a3225a5b-2180-4f5f-9c75-b7ee167aa862" />
<img width="1920" height="894" alt="Screenshot (253)" src="https://github.com/user-attachments/assets/d4342daf-c732-4166-ae07-2d9449108fb9" />

##  Map Uptime Kuma monitor types to Site24x7 monitor types. Which type would you use to monitor an InstaSafe Gateway?
Uptime Kuma monitor types map closely to Site24x7 in terms of service checks.
An HTTP(S) Monitor in Uptime Kuma corresponds to Site24x7 Web URL monitoring and is used for checking application availability.
A TCP Port Monitor maps to Site24x7 Port/Service monitoring, validating services like SSH or custom gateways.
A Ping Monitor is equivalent to Site24x7 Network or ICMP monitoring for basic reachability.
For an InstaSafe Gateway, the best choice is a **TCP Port Monitor (or HTTPS Monitor if it exposes a web interface)** because gateways primarily validate service availability on specific ports and secure connectivity rather than simple webpage loading.
