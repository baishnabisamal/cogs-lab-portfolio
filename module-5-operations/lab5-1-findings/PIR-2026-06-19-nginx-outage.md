# Post Incident Review (PIR)

## Incident Summary
A P1 outage occurred when the Nginx gateway service became unavailable, resulting in complete loss of access for users.

## Severity
P1 - Critical

## Detection
Detected by Uptime Kuma when the monitor changed from UP to DOWN.

## Impact
- All users were unable to access the application.
- Gateway service was unavailable.

## Timeline

| Time | Event |
|--------|--------|
| T+0 | Nginx service stopped |
| T+2 | P1 ticket created |
| T+3 | Customer acknowledgement sent |
| T+5 | Uptime Kuma investigation performed |
| T+8 | Prometheus metrics reviewed |
| T+10 | Internal findings documented |
| T+15 | Status update provided |
| T+20 | Nginx service restarted |
| T+22 | Recovery confirmed in monitoring |
| T+25 | Resolution notice sent |
| T+30 | Incident closed |

## Root Cause
Nginx service was unavailable, causing the gateway outage.

## Resolution
The Nginx service was restarted:

```bash
sudo systemctl start nginx
```

Service health was verified through Uptime Kuma and browser access.

## Preventive Actions
- Continue monitoring with Uptime Kuma.
- Use Prometheus metrics during investigations.
- Maintain incident communication process.
- Consider automatic service restart policies.

## Final Status
Resolved.
All services operating normally.
