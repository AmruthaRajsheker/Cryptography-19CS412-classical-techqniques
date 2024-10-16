# Experiment 8: Implement AES Encryption and Decryption

## AIM:
To implement AES (Advanced Encryption Standard) encryption and decryption using a standard library.



## DESIGN STEPS:

### Step 1:
Design the AES algorithm for encryption and decryption.

### Step 2:
Implement the AES encryption and decryption using a suitable programming language (C or Python).

### Step 3:
1. AES is a symmetric key encryption algorithm that encrypts data in blocks of 128 bits, with key sizes of 128, 192, or 256 bits.
2. It involves multiple rounds of substitution, permutation, mixing, and key expansion depending on the key size.
3. AES encryption operates in different modes such as ECB (Electronic Codebook) and CBC (Cipher Block Chaining).

### Step 4:
Use an appropriate AES library to perform encryption and decryption.



## PROGRAM (Python):

To implement AES in Python, we can use the `pycryptodome` library, which supports various cryptographic algorithms including AES.

### Installation:
```bash
pip install pycryptodome
```

### Program:

```python
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
from Crypto.Random import get_random_bytes

# Function to perform AES Encryption
def aes_encrypt(plaintext, key):
    cipher = AES.new(key, AES.MODE_CBC)  # Using CBC mode
    iv = cipher.iv  # Initialization vector
    padded_text = pad(plaintext.encode('utf-8'), AES.block_size)
    ciphertext = cipher.encrypt(padded_text)
    return iv + ciphertext  # Prepend IV to ciphertext

# Function to perform AES Decryption
def aes_decrypt(ciphertext, key):
    iv = ciphertext[:AES.block_size]  # Extract the IV
    cipher = AES.new(key, AES.MODE_CBC, iv)
    decrypted_text = unpad(cipher.decrypt(ciphertext[AES.block_size:]), AES.block_size)
    return decrypted_text.decode('utf-8')

def main():
    # AES key must be 16 bytes (128 bits), 24 bytes (192 bits), or 32 bytes (256 bits) long
    key = get_random_bytes(16)  # Generate a 128-bit key
    
    # Input message from the user
    plaintext = input("Enter the message to encrypt: ")
    
    # Encrypt the message
    encrypted_message = aes_encrypt(plaintext, key)
    print(f"Encrypted Message (hex): {encrypted_message.hex()}")  # Display in hex format

    # Decrypt the message
    decrypted_message = aes_decrypt(encrypted_message, key)
    print(f"Decrypted Message: {decrypted_message}")

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Enter the message to encrypt: Hello, AES!
Encrypted Message (hex): b6d6d9bc8234d07a5a8bbbd5a290305d2b55f0f6e344ee2064345dd3432cd2fb
Decrypted Message: Hello, AES!
```



## RESULT:
The implementation of AES encryption and decryption was successful.
