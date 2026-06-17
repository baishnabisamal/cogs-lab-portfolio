# Lab 2.1 Findings

## OpenLDAP running — ldapsearch returns base directory structure
<img width="1793" height="515" alt="Screenshot (210)" src="https://github.com/user-attachments/assets/0cfee155-37c9-4f0c-a81e-dd10abf09963" />

##  Both users created — ldapsearch returns alice and bob with mail attributes
<img width="1920" height="584" alt="Screenshot (207)" src="https://github.com/user-attachments/assets/587a61f8-c03c-44e3-aa47-1e3d29de441e" />

## ldapwhoami succeeds for alice — bind test passes
<img width="1823" height="488" alt="Screenshot (208)" src="https://github.com/user-attachments/assets/5dd20c1d-6cd4-4c4a-8059-927dca3e5858" />

## Error code 49 screenshot (wrong password bind) + explanation: what does a support engineer do when they see error 49 in an AD sync log?
<img width="1757" height="127" alt="Screenshot (209)" src="https://github.com/user-attachments/assets/e5b7c2a0-9fc2-4806-8ec4-b6b300a67b2f" />

 Error 49 in LDAP or Active Directory indicates invalid credentials. In an AD sync log, it means the bind operation failed because the username (Bind DN) or password is incorrect.
When a support engineer sees error 49, they:
-Check the Bind DN/service account configured for AD sync.
-Verify the password and confirm it has not expired or been changed.
-Test the credentials using ldapwhoami.
-Confirm the account is not locked or disabled in Active Directory.
-Update the credentials in the InstaSafe AD Sync configuration and rerun.

## Map LDAP concepts to InstaSafe AD sync (base DN, bind DN, attributes)
- Base DN:	dc=lab,dc=instasafe,dc=local
- Bind DN:	cn=admin,dc=lab,dc=instasafe,dc=local
- Password:	LabAdmin123
- User Attributes:	uid, cn, mail
