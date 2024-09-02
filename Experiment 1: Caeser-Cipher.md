# Experiment 1: Caeser Cipher

## AIM:
To encrypt and decrypt the given message by using Ceaser Cipher encryption algorithm.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

1.	In Ceaser Cipher each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
2.	For example, with a left shift of 3, D would be replaced by A, E would become B, and so on.
3.	The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the   
    scheme, A = 0, B = 1, Z = 25.
4.	Encryption of a letter x by a shift n can be described mathematically as,
                       En(x) = (x + n) mod26
5.	Decryption is performed similarly,
                       Dn (x)=(x - n) mod26

## PROGRAM:
```C
#include <stdio.h>
#include <stdlib.h>

void caesarEncrypt(char *text, int key) 
{
 for (int i = 0; text[i] != '\0'; i++) 
 {
 char c = text[i];
 if (c >= 'A' && c <= 'Z') 
 {
 text[i] = ((c - 'A' + key) % 26 + 26) % 26 + 'A';
 }
 else if (c >= 'a' && c <= 'z') 
 {
 text[i] = ((c - 'a' + key) % 26 + 26) % 26 + 'a';
 }
 }
}
void caesarDecrypt(char *text, int key) 
{
 caesarEncrypt(text, -key);
}
int main() 
{
 char message[100]; 
 int key;
 printf("Enter the message to encrypt: ");
 fgets(message, sizeof(message), stdin); 
 printf("Enter the Caesar Cipher key (an integer): ");
 scanf("%d", &key); 
 caesarEncrypt(message, key);
 printf("Encrypted Message: %s", message);
 caesarDecrypt(message, key);
 printf("Decrypted Message: %s", message);
 return 0;
}
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/18fb42b0-1a7e-4e65-8aff-01cc2ff90b19)

## RESULT:
The program is executed successfully
