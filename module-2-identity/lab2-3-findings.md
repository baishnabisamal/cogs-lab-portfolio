# Lab 2.3 Findings

##  TOTP secret generated, QR code created — screenshot of QR PNG
<img width="1920" height="659" alt="Screenshot (244)" src="https://github.com/user-attachments/assets/773f4ea5-a6d4-47dd-a16c-f21fea241996" />

##  Google Authenticator (or equivalent) shows matching OTP — screenshot side by side
<img width="1627" height="414" alt="Screenshot (245)" src="https://github.com/user-attachments/assets/ea27929c-f9c7-4c75-bbf9-305b2222e476" />
<img width="1080" height="1056" alt="WhatsApp Image 2026-06-18 at 14 31 27" src="https://github.com/user-attachments/assets/ad29edd5-3a7f-4c29-b3b2-b17cc038d6e1" />

##  Time-rotation demonstrated — old OTP vs new OTP after 31 seconds
<img width="1080" height="1041" alt="WhatsApp Image 2026-06-18 at 14 31 17" src="https://github.com/user-attachments/assets/ae2121fe-ea12-4b0c-be27-e869bb97b4ca" />
<img width="1374" height="152" alt="Screenshot (245)" src="https://github.com/user-attachments/assets/d81655a2-2e36-49d9-bb9a-00815bb3fcbc" />

##  What causes TOTP failure in an enterprise? List 3 root causes and 1 diagnostic step each.
1. Clock drift between server and user phone
   If the phone time or server time is not perfectly synced, OTP codes will not match.
   Diagnostic: Compare OTP generated on server with the code shown in the authenticator app at the same moment.

2. Wrong or mismatched secret key
   If the secret used to generate OTP on the server is different from the one stored in the user’s authenticator app, codes will always fail.
   Diagnostic: Re-check the provisioning QR/secret stored in the system and confirm it matches what was scanned on the phone.

3. Time window mismatch or strict validation settings
   If the system only accepts OTPs for a very narrow time window (or has strict validation rules), small delays can cause failures.
   Diagnostic: Test OTP acceptance across adjacent 30-second windows or enable a small tolerance window and check if login succeeds.

