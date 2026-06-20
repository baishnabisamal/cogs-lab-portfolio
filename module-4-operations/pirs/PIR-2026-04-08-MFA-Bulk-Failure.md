
# Post-Incident Report (PIR)

**Incident ID:** INC-2026-0408-001
**Date:** 2026-04-08
**Severity:** P2
**Status:** Resolved
**Author:** Baishnabi Samal 
**Reviewed By:** [L2 Lead Name]

---

## Incident Summary

On 2026-04-08 at 09:15 IST, a mid-size financial institution reported that 25 users in their finance department were unable to receive SMS OTP for InstaSafe login. Email OTP worked correctly. Investigation revealed that the Kaleyra SMS sender ID used for OTP delivery had been flagged by TRAI due to a DND violation by another sender sharing the same SMS route, causing all outbound messages from that sender ID to be blocked at carrier level from 08:45 IST. The issue was resolved at 11:45 IST by switching to a backup sender ID, resulting in a total downtime of 2 hours and 30 minutes for affected users.

---

## Timeline

| Time (IST) | Event |
|------------|-------|
| 08:45 | Kaleyra sender ID blocked at carrier level (silent failure — no alert triggered) |
| 09:15 | Customer reported MFA failure for 25 users via Zoho Desk ticket |
| 09:18 | Ticket #1001 created — priority set to P2 |
| 09:20 | First response sent to customer acknowledging the issue |
| 09:35 | Checked Kaleyra dashboard — REJECTED status codes confirmed for all 25 numbers |
| 09:40 | Test OTP sent to personal number on same carrier — also failed |
| 10:30 | Escalated to L2 with full investigation findings |
| 10:45 | L2 engaged Kaleyra support to identify sender ID status |
| 11:20 | Kaleyra confirmed: sender ID flagged due to shared route DND violation |
| 11:35 | L2 initiated switch to backup sender ID |
| 11:40 | Backup sender ID activated |
| 11:42 | Test OTP sent to 3 affected numbers — all delivered successfully |
| 11:45 | Customer requested all 25 users to retry — all confirmed successful |
| 11:50 | Ticket #1001 resolved and closed |

---

## Root Cause

The Kaleyra SMS sender ID assigned to InstaSafe OTP delivery shared an SMS routing path with another sender that had violated TRAI DND regulations. TRAI flagged the route and the carrier blocked all messages from that sender ID at 08:45 IST. InstaSafe had no monitoring alert configured for Kaleyra sender ID health status, so the failure was only detected when a customer reported it 30 minutes after it began.

---

## Impact Assessment

- **Users affected:** 25 (finance department, single tenant)
- **Duration:** 2 hours 30 minutes (08:45 IST to 11:45 IST)
- **Business impact:** Finance department users unable to authenticate into business applications during morning work hours. No data loss. No security breach.
- **Customer sentiment:** Frustrated by delay in detection. Satisfied with resolution.

---

## Resolution Steps

1. Identified REJECTED status codes in Kaleyra dashboard for all affected numbers
2. Escalated to L2 with full diagnostic findings at 10:30 IST
3. L2 engaged Kaleyra support and confirmed sender ID block cause
4. Switched OTP delivery to pre-configured backup sender ID
5. Verified delivery with test OTPs before informing customer
6. Customer confirmed all 25 users able to log in successfully

---

## Prevention Actions

- [ ] Configure Kaleyra sender ID health monitoring alert in Site24x7 — **Owner: L2 Lead** — **Due: 2026-04-15**
- [ ] Pre-configure backup sender ID for all production tenants and document switchover procedure — **Owner: L3 Infrastructure** — **Due: 2026-04-22**
- [ ] Add SMS OTP delivery rate check to daily health dashboard — **Owner: L2 Lead** — **Due: 2026-04-15**

---

## Open Items

- [ ] Write KB article: "SMS OTP not delivered — Kaleyra sender ID block troubleshooting steps" — **Owner: Baishnabi Samal** — **Due: 2026-04-10**
- [ ] Customer follow-up call to confirm no recurrence — **Owner: Account Manager** — **Due: 2026-04-09**
