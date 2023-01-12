# 26.1 PKI
- A system of harware, software, policies, procedures, and people that is base on asymmetric encryption
- Using PKI to create a secure SSL/TLS tunnel:
	- The end-user's web browser will reach out to a trusted third party certificate authority and requests the server's public key
	- Your browser chooses a random shared secret 
	- Use Public Key Encryption (asymmetric) to send this.
	- Once received, the server will use its private key to decrypt the PKE
	- Since only you and the server know the shared secret, a symmetric SSL or TLS tunnel can be created using AES

# 26.2 Digital Certificates
- Digitally-signed electronic documents that bind a public key with a user's ID
- **X.509**: standard PKI for digital certs and contains the owner/users information and the cert authority's information
- **Wildcard certificates**: allow all of the subdomains to use teh same public key certificate and have it displayed as valid
	- Easier to manage
	- However, if the cert needs to be revoked, it'll affect all subdomain servers
- **Subject Alternative Name (SAN)**: allows a cert owner to specify additional domains and IP addresses to be supported
- **Single-sided certificates**: only require the server to be validated
- **Double-sided certificates**: require both the server and the user to be validated
- The certificate itself must be encoded. There are a few methods under the X.609 standard:
	- **Basic Encoding Rules (BER)**: original ruleset governing the encoding of data structs for certs where several different encoding types can be used
	- **Canonical Encoding Rules (CER)**: A restricted version of BER that only allows the use of one encoding type
	- **Distinguished Encoding Rules (DER)**: restricted version of BER which allows one encoding type and has more restrictive rules for length, character strings, and how elements of a digital cert are stored in X.509
- File types associated with these certs:
	- **Privacy-enhanced Electronic Mail (PEM)**
	- **Public Key Cryptographic System #12 (PKCS#12):
	- **Personal Information Exchange (PIX)**
# 26.3 Certificate Authorities
- Entity that issues certs to a user
- **Registration Authority**: used to verify info about a user prior to requesting that a cert authroity issue the certificate
- Veriign, Digisign, and many others act as Root CA
	- They also maintain a public copy of that user's public key
- **Certificate Revocation List  (CRL)**: an online list of digital certs that the certificate authority has revoked
- **Online Certificate Status Protocol (OSCP)**: a protocol that allows you to determine the revocation status of a digital certificate using its serial number
	- **OSCP Stapling**: allows the certificate holder to get teh OCSP record from the server at regular intervals and include it as part of the SSL/TLS handshake
- **Public Key Pinning**: allows an HTTPS website to resist impersonation attacks by presenting a set of trusted public keys to the user's web browser as part of the HTTP header.
- **Key Escrow**: occurs when a secure copy of a user's private key is held in case the user accidentally loses their key
- **Key Recovery Agent**: a specialied type of software that allows the restoration of a lost or corrupted key to be performed
- All of a CA's certificates must be revoked if it's compromised!

# 26.4 Web of Trust
- A decentralized trust model that addresses issues associated with the public authentication of public keys within a CA-based PKI system
- It's a p2p model
- Certificates are created as self-signed certificates
- Pretty Good Privacy (PGP) is a web of trust