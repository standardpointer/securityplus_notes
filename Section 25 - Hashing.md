# 25.1 Hashing
- One-way cryptographic function which takes an input and produces a unique message digest
- Acts like a fingerprint for the hashed file
- Hash is always the same length, regardless of the plaintext length
- **Message Digest 5 (MD5)**: creates a fixed-length 128-bit hash value unique to the input file
- **Collision**: occurs when two different files create the same hash digest
- **Secure Hash Algorithm 1 (SHA1)**: creates a fixed-length 160-bit hash value unique to the input
- **SHA-2**: family of algorithms that includes SHA-224, SHA-256, SHA-348, and SHA-512
	- Each of these algorithms produces a hash digest between 224-bits and 512-bits (hence the names)
- **SHA-3**: similar to SHA-2, but uses 120 rounds of computations to create its hash digests.
- **RACE Integrity Primitive Evaluation Message Digest (RIPEMD)**: open-source hash algorithm that creates a unique 160-bit, 256-bit, or 320-bit digest for each input file
- **Hash-based Message Authentication Code (HMAC)**: uses a hash algorithm to create a level of assurance as to the integrity and authenticity of a given message or file
	- HMAC-MD5, HMAC-SHA1, HMAC-SHA256
- Digital signatures prevent collisions from being used to spoof the integrity of a message
	- Use either DSA, RSA, ECDSA, or SHA
- **Code signing**: Uses digital signatures to provide an assurance that the software code has not been modified after it was submitted by the dev
- **LANMAN (LM Hash)**: Original version of password hashing used by Windows that uses DES and is limited to 14 chars
- **NT LAN Manager Hash (NTLM Hash)**: replacement to LM Hash that uses RC4 and was released in 1993 (Windows NT 3.1)

# 25.2 Hashing Attacks
- #### Pass the Hash
	- Allows an attacker to authenticate to a remote server or service by using the underlying NTLM or LM hash instead of requiring the associated plaintext password
	- Re-use the hash of the user account, known as a reply hash
	- Difficult to defend against
	- **Mimikatz**: tool used to automate the harvesting of hash and conduct the PtH attack
	- To mitigate these attacks, use a trusted OS, patch/update regularly, and use MFA
- #### Birthday Attack
	- Used by an attacker to find two different messages that have an identical hash digest, causing a collision
	- Name derived from the birthday paradox: If you have a random group of people together, there's a strong chance that at least two of them have the same birthday
		- 99% chance of finding a matching birthday in a 57 person group, 50% for 23 people

# 25.3 Increasing Hash Security
- **Key stretching**: used to mitigate a weaker key by increasing the time needed to crack it (at least 128-bits long)
- WPA, WPA2, PGP, bcrypt, and other algorithms use key stretching
- **Salting**: Adding random data into a one-way cryptographic hash to help protect against password cracking techniques
- **Nonce**: number only used once
- Limiting login attempts