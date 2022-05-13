# Secure Sockets Layer (SSL) and Transport Layer Security (TLS)
Secure Sockets Layer (SSL) and Transport Layer Security (TLS) are what provides the encrypted communications for HTTPS and other encrypted connection oriented protocols. This lesson steps through how the handshake process works for TLS and some of the key components.

TSL is just a newer and more secure version of SSL. 
- Privacy and Data Integrity between client & server
- TLS ensures privacy - communications are encrypted: server can make its public key avaialble to any clients so clients can encrypt data that only server can decrypt.
  - Asymmetric and then symmetric architecture
    - Asymmetric encryption allows for trustless encryption: when you don't need to arrange for transfer of keys over a different secure medium => symmatric is easier to perform computationally
- TLS provides Identity Verification
  - To confirm server connected to is correct (ie. netflix.com is netflix.com).
  - 2-way verification: mostly client verifying server using public key cryptography.
  - Server or server/client verification.
- TLS ensures reliable connection
  - Protects against alteration of data in transit
  - If data is altered, protocol can detect

<br>

## SSL/TLS Architecture
**Summary:** We verify the identity of the server that we're communicating with - negotiate an encryption method to use - exchange asymmetric for symmetric encryption keys - initiate secure communications channel => this process happens every time that you communicate with a server using HTTPS.

1. Cipher Suites
- Set of protocols used: key exchange algo, bulk encryption algo, message authenticaon code algo (MAC). 
- Asymmatrical encryption
- Certificate contains server's public key encrypting data which only server can decrypt using its private key.
2. Authentication
- Certificate Authority (CA) to sign the certificate to verify certificate status and DNS
- Making sure client can trust server
3. Key Exchange
- Encrypt and decrypt data at high speed
- Master secret: used over lifetime of the connection to create many session keys ~ these keys are used to decrypt/encrypt data

![SSLandTLS](https://user-images.githubusercontent.com/72099370/168200338-b61eed15-6e09-4b61-8605-1501b5fbfb14.png)
