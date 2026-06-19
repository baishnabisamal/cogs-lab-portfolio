CHANGE-001 Rollback Summary

A bad configuration was intentionally introduced.

nginx -t failed due to an unknown directive.

Rollback steps:
- Restored lab-tls.backup
- Verified configuration with nginx -t
- Reloaded nginx
- Confirmed service availability

Rollback completed successfully.
