# Elliptic Curve Integrated Encryption Scheme (ECIES)

## What is a Elliptic Curve Integrated Encryption Scheme
Elliptic Curve Integrated Encryption Scheme, or ECIES, is a hybrid encryption system proposed by Victor Shoup in 2001. ECIES combines a Key Encapsulation Mechanism (KEM) with a Data Encapsulation Mechanism (DEM). The system independently derives a bulk encryption key and a MAC key from a common secret. Data is first encrypted under a symmetric cipher, and then the cipher text is MAC'd under an authentication scheme. Finally, the common secret is encrypted under the public part of a public/private key pair.

## Why would I want to use ECC?
The small key sizes make ECC very appealing for devices with limited storage or processing power, which are becoming increasingly common in the IoT. A 256 bit ECC key is equivalent to RSA 3072 bit keys (which are 50% longer than the 2048 bit keys commonly used today). In terms of more traditional web server use cases, the smaller key sizes can offer speedier SSL handshakes (which can translate to faster page load times) and stronger security.


## Install python ECIES
I was unable to use eciepy if i used pip install, and I therefor decided to download the zip file. Once you have the zip file simple move the **ecies** folder that is inside the first folder over to the same directory as your python file. Then you can simple run a simple starter code to make sure that everything works correctly
 ```
from ecies.utils import generate_eth_key, generate_key
from ecies import encrypt, decrypt
import binascii

privKey = generate_eth_key()
print(privKey)
privKeyHex = privKey.to_hex()
pubKeyHex = privKey.public_key.to_hex()
print("Encryption public key:", pubKeyHex)
print("Decryption private key:", privKeyHex)

plaintext = b'Some plaintext for encryption'
print("Plaintext:", plaintext)

encrypted = encrypt(pubKeyHex, plaintext)
print("Encrypted:", binascii.hexlify(encrypted))

decrypted = decrypt(privKeyHex, encrypted)
print("Decrypted:", decrypted)
 ```
 
 - https://pypi.org/project/eciespy/
 
 ## Flow diagram 
 ![alt text](https://github.com/gudbrandsc/ECIES-project/blob/master/1_A3yiRaX7xBPBsovR_NyuVQ.png "Logo Title Text 1")

