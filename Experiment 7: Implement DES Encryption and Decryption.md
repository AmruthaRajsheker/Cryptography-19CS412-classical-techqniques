# Experiment 7: Implement DES Encryption and Decryption 

## AIM:
To implement DES (Data Encryption Standard) encryption and decryption algorithm using standard libraries.



## DESIGN STEPS:

### Step 1:
Design the DES algorithm for encryption and decryption.

### Step 2:
Implement the DES encryption and decryption using a suitable programming language (C or Python).

### Step 3:
1. DES is a symmetric key encryption algorithm that encrypts data in 64-bit blocks using a 56-bit key.
2. The encryption process involves multiple rounds of substitution and permutation.
3. Each round uses a different subkey generated from the original key.

### Step 4:
Use an appropriate DES library or write the DES algorithm from scratch for both encryption and decryption.



## PROGRAM (Python):

To implement DES in Python, we can use the `pycryptodome` library, which supports various cryptographic algorithms, including DES.

### Installation:
```bash
pip install pycryptodome
```

### Program:

```python
from Crypto.Cipher import DES
from Crypto.Util.Padding import pad, unpad

# Function to perform DES Encryption
def des_encrypt(plaintext, key):
    des = DES.new(key, DES.MODE_ECB)
    padded_text = pad(plaintext.encode('utf-8'), DES.block_size)
    ciphertext = des.encrypt(padded_text)
    return ciphertext

# Function to perform DES Decryption
def des_decrypt(ciphertext, key):
    des = DES.new(key, DES.MODE_ECB)
    decrypted_text = unpad(des.decrypt(ciphertext), DES.block_size)
    return decrypted_text.decode('utf-8')

def main():
    # DES key must be 8 bytes long
    key = b'8bytekey'
    
    # Input message from the user
    plaintext = input("Enter the message to encrypt: ")
    
    # Encrypt the message
    encrypted_message = des_encrypt(plaintext, key)
    print(f"Encrypted Message: {encrypted_message.hex()}")  # Display in hex format

    # Decrypt the message
    decrypted_message = des_decrypt(encrypted_message, key)
    print(f"Decrypted Message: {decrypted_message}")

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Enter the message to encrypt: Hello, DES!
Encrypted Message: c5f4acb87e5c28da73eb60a2b6769856
Decrypted Message: Hello, DES!
```



## RESULT:
The implementation of DES encryption and decryption was successful.
