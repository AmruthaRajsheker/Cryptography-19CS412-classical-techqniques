# Experiment 9: Implement RSA Encryption and Decryption

## AIM:
To implement RSA (Rivest–Shamir–Adleman) encryption and decryption algorithm using standard libraries.



## DESIGN STEPS:

### Step 1:
Design the RSA algorithm for both encryption and decryption.

### Step 2:
Implement the RSA encryption and decryption using a suitable programming language (C or Python).

### Step 3:
1. RSA is an asymmetric encryption algorithm that uses two keys: a public key for encryption and a private key for decryption.
2. The algorithm is based on the mathematical difficulty of factoring large prime numbers.
3. RSA key generation involves the following steps:
   - Generate two large prime numbers, `p` and `q`.
   - Compute `n = p * q` and the totient function `φ(n) = (p-1) * (q-1)`.
   - Choose an encryption key `e` such that `1 < e < φ(n)` and `gcd(e, φ(n)) = 1`.
   - Compute the decryption key `d` such that `(d * e) mod φ(n) = 1`.

### Step 4:
Use an appropriate library to perform RSA encryption and decryption.



## PROGRAM (Python):

To implement RSA in Python, we can use the `pycryptodome` library.

### Installation:
```bash
pip install pycryptodome
```

### Program:

```python
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP
from Crypto.Random import get_random_bytes

# Function to generate RSA keys
def generate_rsa_keys():
    key = RSA.generate(2048)
    private_key = key.export_key()
    public_key = key.publickey().export_key()
    return private_key, public_key

# Function to perform RSA Encryption
def rsa_encrypt(plaintext, public_key):
    rsa_public_key = RSA.import_key(public_key)
    cipher_rsa = PKCS1_OAEP.new(rsa_public_key)
    ciphertext = cipher_rsa.encrypt(plaintext.encode('utf-8'))
    return ciphertext

# Function to perform RSA Decryption
def rsa_decrypt(ciphertext, private_key):
    rsa_private_key = RSA.import_key(private_key)
    cipher_rsa = PKCS1_OAEP.new(rsa_private_key)
    decrypted_message = cipher_rsa.decrypt(ciphertext)
    return decrypted_message.decode('utf-8')

def main():
    # Generate RSA keys
    private_key, public_key = generate_rsa_keys()

    # Display generated keys
    print(f"Public Key: {public_key.decode('utf-8')}")
    print(f"Private Key: {private_key.decode('utf-8')}")

    # Input message from the user
    plaintext = input("Enter the message to encrypt: ")

    # Encrypt the message using the public key
    encrypted_message = rsa_encrypt(plaintext, public_key)
    print(f"Encrypted Message (hex): {encrypted_message.hex()}")

    # Decrypt the message using the private key
    decrypted_message = rsa_decrypt(encrypted_message, private_key)
    print(f"Decrypted Message: {decrypted_message}")

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Public Key: 
--BEGIN PUBLIC KEY--
MIIBIjANBgkq...
--END PUBLIC KEY--

Private Key:
--BEGIN RSA PRIVATE KEY--
MIIEowIBAAKCAQEA...
--END RSA PRIVATE KEY--

Enter the message to encrypt: Hello, RSA!
Encrypted Message (hex): 34f4a... (truncated)
Decrypted Message: Hello, RSA!
```



## RESULT:
The implementation of RSA encryption and decryption was successful.
