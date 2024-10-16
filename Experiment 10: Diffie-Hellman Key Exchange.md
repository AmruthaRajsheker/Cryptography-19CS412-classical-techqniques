# Experiment 10: Diffie-Hellman Key Exchange

## AIM:
To implement the Diffie-Hellman key exchange algorithm to securely exchange cryptographic keys between two parties.



## DESIGN STEPS:

### Step 1:
Design the Diffie-Hellman key exchange algorithm.

### Step 2:
Implement the Diffie-Hellman key exchange using a suitable programming language (C or Python).

### Step 3:
1. Diffie-Hellman is a key exchange protocol that allows two parties to establish a shared secret key over an insecure channel.
2. The algorithm works by generating a shared secret key that both parties can compute independently.
3. The algorithm is based on the difficulty of the discrete logarithm problem in modular arithmetic.

### Step 4:
Use modular exponentiation to compute the shared secret based on the selected prime number and primitive root.



## PROGRAM (Python):

In Python, we can manually implement the key exchange steps using modular arithmetic.

### Program:

```python
import random

# Function to perform Diffie-Hellman Key Exchange
def diffie_hellman(p, g):
    # Step 1: Both parties agree on a large prime number p and a primitive root g

    print(f"Publicly Shared Prime (p): {p}")
    print(f"Publicly Shared Primitive Root (g): {g}")

    # Step 2: Alice chooses a private key a, Bob chooses a private key b
    a = random.randint(1, p - 1)  # Alice's private key
    b = random.randint(1, p - 1)  # Bob's private key

    # Step 3: Alice computes A = g^a mod p, Bob computes B = g^b mod p
    A = pow(g, a, p)  # Alice's public value
    B = pow(g, b, p)  # Bob's public value

    print(f"Alice's Private Key (a): {a}")
    print(f"Alice's Public Value (A): {A}")
    print(f"Bob's Private Key (b): {b}")
    print(f"Bob's Public Value (B): {B}")

    # Step 4: Alice and Bob exchange A and B
    # Step 5: Alice computes the shared secret key: s = B^a mod p
    #         Bob computes the shared secret key: s = A^b mod p
    alice_shared_secret = pow(B, a, p)
    bob_shared_secret = pow(A, b, p)

    print(f"Alice's Shared Secret: {alice_shared_secret}")
    print(f"Bob's Shared Secret: {bob_shared_secret}")

    # Both shared secrets should be equal
    if alice_shared_secret == bob_shared_secret:
        print("Shared secret successfully established.")
    else:
        print("Error in shared secret computation.")

def main():
    # Prime number p and primitive root g (these are usually agreed upon publicly)
    p = 23  # A small prime number for demonstration (use larger primes for real applications)
    g = 5   # A primitive root modulo p

    # Perform Diffie-Hellman key exchange
    diffie_hellman(p, g)

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Publicly Shared Prime (p): 23
Publicly Shared Primitive Root (g): 5
Alice's Private Key (a): 6
Alice's Public Value (A): 8
Bob's Private Key (b): 15
Bob's Public Value (B): 19
Alice's Shared Secret: 2
Bob's Shared Secret: 2
Shared secret successfully established.
```



## RESULT:
The implementation of the Diffie-Hellman key exchange algorithm was successful, and both parties were able to establish a shared secret key securely.
