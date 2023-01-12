# 24.1 Cryptography
- The practice and study of writing and solving codes in order to hide the true meaning of info
- **Encryption**: the process of converting ordinary information (plaintext) into an unintelligible form (ciphertext)
	- Protects data at rest, in transit, and in use
	- **Data at rest**: inactive data that is archived such as data residing on a hard drive
	- **Data in transit**: is crossing the network or residing in memory
	- **Data in use**: undergoing constant change
- **Cipher**: an algorithm which performs encryption or decryption
	- In a ROT13 cipher, adding 13 letters is considered the encryption, and subtracting 13 is the decryption
- Encryption strength derives from the KEY, not the complexity of the algorithm
	- A **key** is an essential piece of info that determines the output of a cipher
# 24.2 Symmetric vs. Asymmetric
- **Symmetric (Private Key)**: both the sender and the receiver must know the same secret using a privately held key
	- A slightly flawed analogy is using your house key
	- Confidentiality can be assured with symmetric encryption.
	- Non-repudiation can't be assured
	- Key distribution can be challenging. If you wanted to share something with five pals, you need five pairs of keys
	- Algorithms include DES, 3DES, IDEA, AES, Blowfish, Twofish, RC4/5/6
- **Asymmetric (Public Key)**: Different keys are used to encrypt and decrypt the data
	- Algorithms include Diffie-Hellman, RSA, and ECC
- Symmetric is 100-1000x faster than asymmetric, but asymmetric is more convenient for key distribution
- **Hybrid approach**: involves asymmetric encryption to securely transfer a private key that can be used with symmetric encryption on the bulk of that data transfer
- **Stream cipher**: utilizes a keystream geenrator to encrypt data bit by bit using a mathematical XOR function to create ciphertext
	- Great for encrypting audio/video streams
	- Tend to be symmetric
- **Block cipher**: breaks the input into fixed-length blocks of data and performs the encryption on each block
	- i.e. a 1KB piece of data could be divided into 16 blocks of 64 bytes. 
	- Easier to implement and less susceptible to security issues
# 24.3 Symmetric Algorithms
- #### Data Encryption Standard (DES)
	- Breaks the input into 64-bit blocks and uses transposition and substitution to create ciphertext using an effective key strength of only 56-bits.
	- Used to be the standard for encryption
- #### Triple DES (3DES)
	- Uses three separate symmetric keys to encrypt, decrypt, then encrypt the plaintext into ciphertext.
- #### International data Encryption Algorithm (IDEA)
	- Symmetric block cipher which uses 64-bit blocks to encrypt plaintext into ciphertext
	- Used in the Pretty Good Privacy Suite
- #### Advanced Encryption Standard
	- Symmetric block cipher that uses 128, 192, or 256-bit blocks and a matching encryption key size to encrypt plaintext into ciphertext
	- Encryption used by the federal government
- #### Blowfish
	- Symmetric block cipher that uses 32-bit to 448-bit encryption keys to encrypt 64 bits of data in blocks at a time
- #### Twofish
	- Symmetric block cipher that replaced blowfish and uses 128-bit blocks and a 128/192/256-bit encryption key 
- #### Rivest Ciphers
	- RC1, RC2 were considered insecure, RC3 was cracked before public release
	- **RC4**: symmetric stream cipher using a variable key size from 40-bits to 2048-bits that is used in SSL and WEP
	- **RC5**: symmetric block cipher uses key sizes up to 2048-bits
	- **RC6**: based on RC5 and was introduced as a replacement for DES before AES came along

# 24.4 Public Key Cryptography
- Provides confidentiality, integrity, authentication, and non-repudiation
- Data should be encrypted using the receiver's public key. This makes asymmetric cryptography one-way.
- **Digital signature**: a hash digest of a message encrypted with the sender's private key to let the recipient know that the data was created and sent by the person claiming to have done so

# 24.5 Asymmetric Algorithms
- #### Diffie-Hellman
	- Used to conduct key exchanges and secure key distribution over an unsecure network
	- Used for the establishment of a VPN tunnel using IPSec
	- Susceptible to MiTM attacksm so use a password/digital certificate to create stronger security
- #### RSA
	- Named after its creators (Rivest, Shamir, Aldeman)
	- Relies on the mathematical difficulty of factoring large prime numbers
	- 1024-bit to 4096-bit key sizes
	- Most MFA one-time verification codes are RSA
- #### ECC
	- Based upon the algebraic structure of elliptic curves over finite fields to define keys
	- 256-bit key is just as secure as RSA with 2048-bit key
	- Used in a lot of mobile-based cryptography because of their lower power consumption
	- Variations include ECDH, ECDHE, ECDSA

# 24.6 Pretty Good Privacy
- An encryption program used for signing, encrypting, and decrypting emails
- This has expanded to include files, and even entire storage drives
- Uses the IDEA algorithm
- Uses a symmetric cipher to encrypt the bulk of the data and an asymmetric cipher (RSA) to create the digital signatures
- Symmetric functions use 128-bit or higher keys and the asymmetric functions use 512-2048-bit key sizes
- PGP became open source eventually
	- **GNU Privacy Guard (GPG)**: a newer version of the PGP suite that uses AES for its symmetric encryption functions
		- Cross-platform availability

# 24.7 Key Management
- Refers to how an organization will generate, exchange, store, and use encryption keys
- As mentioned, encryption strength relies on the key
- Keys must be securely stored
- Periodically change your keys, similar to passwords

# 24.8 One-Time Pad
- A strea mcipher that encrypts plaintext informatio nwit ha secret random key that is the same length as the plaintext input
- There is no such thing as truly random numbers in computers
- **Pseudo-random number generator (PRNG)**: simulated random number stream generated by a computer that is used in cryptography, video games, and more 
	- One-time pads are not commonly used because of this
	- Moreover, since the length of the key is equal to the length of the plaintext, it's inefficient to do this

# 24.9 Cryptography Considerations

