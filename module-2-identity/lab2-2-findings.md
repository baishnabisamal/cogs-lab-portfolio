# Lab 2.2 Findings
## Keycloak running — login to admin console works, screenshot of realm dashboard
<img width="1920" height="946" alt="Screenshot (219)" src="https://github.com/user-attachments/assets/95d668e3-4620-44b6-94f7-d721c8897155" />
<img width="1920" height="961" alt="Screenshot (233)" src="https://github.com/user-attachments/assets/a976ac80-4310-4f93-9665-16f48ad1ff91" />

##  SAML client configured — screenshot of client settings showing SAML type
<img width="1920" height="903" alt="Screenshot (222)" src="https://github.com/user-attachments/assets/17757b4b-3df9-42fc-9a48-3b74171be5bd" />
<img width="1920" height="968" alt="Screenshot (234)" src="https://github.com/user-attachments/assets/a70ec2a6-ed0d-4b3a-8867-813353e3659e" />

##  Attribute mapper configured for email and groups — shown in screenshots
In Keycloak, Attribute Mappers translate user profile data into SAML assertions sent to the SP. Under Clients → InstaSafe SP Simulation → Client Scopes → Mappers, each mapper defines what user property (like email, groups) maps to a SAML Attribute Name. Without correct mappers, the SP receives no user data even after successful authentication, causing attribute errors.
<img width="1920" height="894" alt="Screenshot (236)" src="https://github.com/user-attachments/assets/1fac0d68-1d15-4ae7-927e-2edd6ccb7144" />

## Screenshot: Keycloak IdP metadata XML downloaded
<img width="1920" height="601" alt="Screenshot (223)" src="https://github.com/user-attachments/assets/10bf72fa-d656-4c0d-a22a-0d6d4fcb1ea5" />
<img width="1920" height="962" alt="Screenshot (232)" src="https://github.com/user-attachments/assets/a68bde92-a65b-4d19-9353-c922cd12b3f7" />

##  If a customer reports SSO users get Attribute Error, what in this Keycloak config would you check first?'
If a customer reports SSO users are getting an Attribute Error, the first thing to check in Keycloak is the Attribute Mapper configuration. Navigate to Clients → InstaSafe SP Simulation → Client Scopes → Mappers and verify that mappers for email and groups exist with the correct SAML Attribute Names. Next, check Client Scopes → Assigned Default Scopes to ensure the scopes are actually attached to the client. Finally, go to Users → testuser → Attributes to confirm the user has actual values populated. Missing mappers or empty user attributes are the most common causes of Attribute Errors in SAML SSO flows.
