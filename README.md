# Padding-Oracle-Attack-Implementation
A practical implementation of the padding oracle attack against CBC (Cipher Block Chaining) mode encryption, demonstrating how seemingly minor information leakage can lead to complete plaintext recovery.

## Overview
This project implements a padding oracle attack that exploits CBC mode encryption when an oracle reveals whether decrypted ciphertext has valid PKCS#7 padding. The attack can decrypt arbitrary ciphertext without knowing the encryption key.
How It Works
The padding oracle attack leverages the mathematical properties of CBC mode decryption:

CBC Vulnerability: In CBC mode, each ciphertext block affects the plaintext of the next block
Padding Oracle: A service that indicates whether decrypted data has valid padding
Byte-by-byte Recovery: By manipulating ciphertext and observing padding validity, we can deduce plaintext bytes

## Attack Process

Block Isolation: Split ciphertext into 16-byte blocks
Padding Manipulation: Craft malicious ciphertext to create known padding patterns
Oracle Queries: Use padding validation responses to deduce intermediate values
Plaintext Recovery: XOR intermediate values with original ciphertext to recover plaintext

## Key Features

Complete Implementation: Full padding oracle attack from scratch
Block-by-block Processing: Handles arbitrary length messages
Padding Validation: Robust PKCS#7 padding verification
Error Handling: Deals with edge cases and false positives
Test Suite: Comprehensive testing with various message lengths

## Technical Details
Core Algorithm
The attack exploits the relationship: Plaintext[i] = Ciphertext[i-1] ⊕ Intermediate[i]
By controlling Ciphertext[i-1] and observing padding validity, we can determine Intermediate[i] and recover the original plaintext.
