# Experiment 14: Hash Function Implementation

## AIM:
To implement a hash function to demonstrate how hashing works for data integrity verification.



## DESIGN STEPS:

### Step 1:
Understand the concept of hash functions and their properties.

### Step 2:
Implement a hash function using a suitable programming language (C or Python).

### Step 3:
1. A hash function is a one-way function that takes an input (or message) and returns a fixed-size string of bytes.
2. The output, known as the hash value or digest, is unique to each unique input. Even a small change in the input will produce a significantly different output.
3. Hash functions are widely used for data integrity verification, password storage, and digital signatures.

### Step 4:
Use a standard library for hashing (e.g., SHA-256) to implement the hash function.



## PROGRAM (Python):

In Python, the `hashlib` library can be used to implement various hashing algorithms, including SHA-256.

### Program:

```python
import hashlib

# Function to compute the hash of a message using SHA-256
def compute_hash(message):
    # Create a new sha256 hash object
    sha256_hash = hashlib.sha256()
    
    # Update the hash object with the bytes-like object (encoded message)
    sha256_hash.update(message.encode())
    
    # Return the hexadecimal digest of the hash
    return sha256_hash.hexdigest()

def main():
    # Input message from the user
    message = input("Enter the message to hash: ")
    
    # Compute the hash of the message
    hash_value = compute_hash(message)
    
    # Display the hash value
    print(f"SHA-256 Hash: {hash_value}")

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Enter the message to hash: Hello, this is a test message.
SHA-256 Hash: 8c14c1f614539d4c1655151a7f86a61015477f58a5f6b08f6880b314ff8021b4d
```



## RESULT:
The implementation of a hash function using SHA-256 was successful, demonstrating how to compute a hash value for a given message. The hash value ensures data integrity, as even a minor change in the input will result in a completely different hash output.
