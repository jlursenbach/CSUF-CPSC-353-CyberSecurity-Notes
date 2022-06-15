# Chapter 2

# encryption

## Symmetric (Symmetric block encryption) SBE:

- universal technique for making transmitted data confidential
- also conventional or single key encryption

### two requirements

- strong encryption algorithm
- Sender old receiver must have obtained copies of the secret key in a secure fashion and must keep the key secure

### key: string of bits

- common 56, 64, 128 bits
- 256 and 512 bit keys exist too

## attacking symmetric encryption

### attacks rely on:

- nature of algorithm (generally secure)
- general characteristics of plain text
- sample plaintext-ciphertext pairs

### Exploits characteristics of the algorithm

- to deduce plaintext

problem: (how do you distribute the secret key from one party to another)

### 3 famous symmetric algorithms

- DES - 64 bit plain and cypher text 56 bit key
- Tipple DES - 64 bit plain and cypher text 112 or 168 bit key
- AES - 128 bit plain and cypher text, 128, 192, or 256 bit key size

— DES : Data Encryption Standart

— AES: Advanced Encryption Standard

properties of algorithms: 

- E - they must be reversable
- D - Decryption algorithm is the reverse of the encryption

### DES:

until recently most widely used scheme

Strengths:

- 

Weaknesses: 

- can be cracked with brute force
- compromising secret key

### Triple DES

Strengths

- longer key is more effective

Weaknesses

- slow
- same algorithm as DES

### AES

Strength

- 

Weaknesses

### Practical Security Issues

- Electronics Codebook (ECB) is simplest approach to multiple block encryption
    - each block encrypted using the same key
    - cryptanalysts may be able to exploit regularities in plain text
    

Block Cypher

- 

Stream Cypher

- 

### Message Authentication without Confidentiality

Protects against active attacks

## Asymmetric (ABE)

- uses 2 separate keys
    - public key
    - private key
        - public key is made available for others to use
- some form of protocol is needed for distribution

solves problem with sharing secret key but creates new problems

Problem:
can you believe the key public key posted belongs to the person who you think

## Public Key encryption Structure

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled.png)

## Public Key Cryptography

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%201.png)

Plaintext

Encryption algorithm

Public and private Key

Ciphertext

Decryption Key

## Public-Key Cryptography

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%202.png)

## Applications for Public-Key Cryptosystems

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%203.png)

## Requirements for Public-Key Cryptosystems

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%204.png)

## Asymmetric Encryption Algorithms

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%205.png)

Diffie-Hellman key exchange algorithm

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%206.png)

Digital Signatures

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%207.png)

The entire document gets hashed, so if the doc gets changed, the hashes don’t match. 

## Digital Signature Process

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%208.png)

## Public Key Certificate Use

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%209.png)

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2010.png)

## Random Numbers

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2011.png)

## Random Number Requirements

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2012.png)

## Random vs Pseudorandom

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2013.png)

## Practical Application: Encryption of Stored Data

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2014.png)

![20220606_112044.jpg](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/20220606_112044.jpg)

![20220606_112034.jpg](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/20220606_112034.jpg)

Hokeypuck OpenPGP keyserver

- a place to publish your keys

![Untitled](Chapter%202%2017dbce03d2dd4fe291cd8a168b1f0571/Untitled%2015.png)

# RSA

## PGP or GPG

For trust

open source vs proprietary

### Bitlocker

- you don’t know if there’s a back door that microsoft built into bitlocker as it is not open source
- Veracrypt is open source

(“PGP” stands for “Pretty Good Privacy”; “GPG” stands for “Gnu Privacy Guard.” It was the original freeware copyrighted program; GPG is the re-write of PGP. The PGP uses the RSA algorithm and the IDEA encryption algorithm. GPG uses the NIST AES, Advanced Encryption Standard.)

iPhone FBI backdoor riverside 8000 * 20