# Experiment 11: Elliptic Curve Cryptography (ECC)

## AIM:
To implement Elliptic Curve Cryptography (ECC) for secure key generation and encryption/decryption.



## DESIGN STEPS:

### Step 1:
Design the ECC algorithm for key generation, encryption, and decryption.

### Step 2:
Implement ECC using a suitable programming language (C or Python).

### Step 3:
1. Elliptic Curve Cryptography (ECC) is an asymmetric key encryption algorithm that provides security similar to RSA but with much smaller key sizes.
2. ECC operates on points over an elliptic curve, defined by the equation:  
   \[ y^2 = x^3 + ax + b \]
   where `a` and `b` are constants that define the curve, and all operations are performed over a finite field.
3. ECC can be used for secure key exchange (similar to Diffie-Hellman), encryption, and digital signatures.

### Step 4:
Use an appropriate library or implement ECC operations (key generation, encryption, and decryption).



## PROGRAM (Python):

In Python, we can use the `ecies` library for Elliptic Curve Integrated Encryption Scheme (ECIES), which is built on top of ECC.

### Installation:
```bash
pip install eciespy
```

### Program:

```python
from ecies import encrypt, decrypt
from ecies.utils import generate_keypair

# Function to generate ECC key pair
def generate_ecc_keys():
    private_key, public_key = generate_keypair()
    return private_key, public_key

# Function to encrypt the message using ECC
def ecc_encrypt(plaintext, public_key):
    ciphertext = encrypt(public_key, plaintext.encode('utf-8'))
    return ciphertext

# Function to decrypt the message using ECC
def ecc_decrypt(ciphertext, private_key):
    decrypted_text = decrypt(private_key, ciphertext).decode('utf-8')
    return decrypted_text

def main():
    # Generate ECC key pair
    private_key, public_key = generate_ecc_keys()
    
    # Display generated keys
    print(f"Public Key: {public_key.hex()}")
    print(f"Private Key: {private_key.hex()}")

    # Input message from the user
    plaintext = input("Enter the message to encrypt: ")

    # Encrypt the message
    encrypted_message = ecc_encrypt(plaintext, public_key)
    print(f"Encrypted Message (hex): {encrypted_message.hex()}")

    # Decrypt the message
    decrypted_message = ecc_decrypt(encrypted_message, private_key)
    print(f"Decrypted Message: {decrypted_message}")

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Public Key: 0479c3a... (truncated)
Private Key: 3081dc... (truncated)

Enter the message to encrypt: Hello, ECC!
Encrypted Message (hex): b0e9c7b3... (truncated)
Decrypted Message: Hello, ECC!
```



## RESULT:
The implementation of Elliptic Curve Cryptography (ECC) for encryption and decryption was successful, and the plaintext message was securely encrypted and decrypted.
