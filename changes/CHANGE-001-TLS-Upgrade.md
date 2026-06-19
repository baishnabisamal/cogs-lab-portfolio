# Change ID: CHANGE-001

## Type

Normal Change

## Description

Update Nginx TLS configuration to prefer TLS 1.3.

## Justification

TLS 1.3 provides improved security and performance and aligns with current best practices.

## Execution Steps

1. Backup current nginx config.
2. Update ssl_protocols line.
3. Validate configuration using nginx -t.
4. Reload nginx.
5. Verify TLS 1.3 connectivity.

## Rollback Trigger

Rollback if TLS verification fails or the site becomes unreachable.

## Rollback Steps

1. Restore previous configuration.
2. Validate using nginx -t.
3. Reload nginx.

## Rollback Time

2 minutes

## Maintenance Window

Immediate (Lab environment – no customer impact)
