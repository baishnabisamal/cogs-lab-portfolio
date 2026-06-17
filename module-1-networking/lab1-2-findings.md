# Lab 1.2 Findings

## Nginx serving HTTP and HTTPS — screenshots of both curl responses
<img width="1564" height="636" alt="Screenshot (178)" src="https://github.com/user-attachments/assets/34de2ba4-efb7-421f-9a18-43a1047bbcf1" />
<img width="969" height="213" alt="Screenshot (179)" src="https://github.com/user-attachments/assets/8ae4736c-8738-44d2-a993-bcc28efbe2c0" />

## Firewall rules configured correctly — nmap output showing ports 80 and 443 open
<img width="1082" height="261" alt="Screenshot (180)" src="https://github.com/user-attachments/assets/7a1d3c59-1500-4365-8c01-69d381a83a3c" />

## Certificate details documented: 
#### -Subject: C = IN, ST = Karnataka, L = Bangalore, O = InstaSafe Lab, CN = 16.171.197.113
#### -Issuer: C = IN, ST = Karnataka, L = Bangalore, O = InstaSafe Lab, CN = 16.171.197.113
Same as the Subject, meaning the certificate is self-signed. It was created and signed by InstaSafe Lab rather than by a trusted Certificate Authority (CA).
#### -Key algorithm: rsaEncryption 
The certificate uses the RSA public-key cryptographic algorithm for authentication and secure key exchange
#### -Expiry date: Jun 17 07:08:01 2027 GMT
The certificate remains valid until this date and time. After expiration, clients such as curl or web browsers will reject it unless a new certificate is installed.

## Why does curl without -k fail? What would need to change to make it succeed?
#### curl without the -k option fails because it verifies the server’s SSL/TLS certificate to ensure a secure and trusted connection. If the certificate is self-signed, expired, has a hostname mismatch, or lacks a complete certificate chain, the verification fails and the connection is rejected. The -k option bypasses these security checks. To make the command succeed without -k, the server must present a valid certificate issued by a trusted certificate authority, provide the full certificate chain, and use a hostname that matches the certificate. The client system must also trust the issuing certificate authority.


## Screenshot: openssl s_client output showing certificate details
<img width="1080" height="748" alt="Screenshot (181)" src="https://github.com/user-attachments/assets/39b27623-0cba-4e1d-a6f1-630fc7a78f18" />
<img width="1062" height="758" alt="Screenshot (182)" src="https://github.com/user-attachments/assets/9597f64c-442a-46ee-88be-c742d26a30e6" />
<img width="1423" height="755" alt="Screenshot (183)" src="https://github.com/user-attachments/assets/53d537f5-37f1-4cbf-b3c2-d5764a63049c" />
<img width="1438" height="744" alt="Screenshot (184)" src="https://github.com/user-attachments/assets/badb9095-7368-4db0-8764-dd6e1eb4ae6b" />
<img width="1438" height="744" alt="Screenshot (184)" src="https://github.com/user-attachments/assets/88787291-5c84-4383-a528-777aedded4d3" />
<img width="1438" height="744" alt="Screenshot (184)" src="https://github.com/user-attachments/assets/88800860-ea03-4e3c-a25b-32ad5a162a13" />
<img width="920" height="746" alt="Screenshot (188)" src="https://github.com/user-attachments/assets/a25324ca-d797-4902-9288-cd60365cf850" />
<img width="1403" height="730" alt="Screenshot (189)" src="https://github.com/user-attachments/assets/fa0de067-1fce-418c-897d-29a26c7b0df0" />




