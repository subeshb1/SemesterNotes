# Cryptography

Cryptography is the scientific study or art of secret writing or information hiding. It concerns to prevent disclosure of content of information from `interception`, `eavesdropping`, or `modification`.

## Encryption

* It is the process of encoding the data or message so that its meaning is changed.
* Changes the information to some unreadable form.
* It uses some cryptographic algorithm and key.
* The text to be converted is called `plain text`.
* The converted text is called `cipher text`.
* Alternative terms : Encrypt/ Encode/ Encipher

## Decryption

* Process of converting encrypted text to plain text or a readable format i.e. the reverse process of encryption.
* Uses the same algorithm and key.
* Alternative terms: Decrypt/ Decode/ Decipher

## Key

* It is a parameter or piece of information used to determine the output of cryptographic algorithm.
* Determines the transformation of plain text to cipher text and vice-versa.
* The length of the key determines the security of the cipher text.
* Important for both sending and receiving side.

## Cipher

* It's an algorithm to perform encryption or decryption.
* operation of cipher depends upon text.

## Crypto System

* A crypto system is a 5-tuples representation of :

    > (E,D,M,K,C)

where,

* E is set of encryption algorithm/ function.
* D is set of decryption algorithm/ function.
* M is set of plain text.
* K is set of keys.
* C is set of cipher text.

Crypto systems or Cryptographic system are characterized along three independent dimensions : 

1. The type of operations used for transforming plain text to cipher text. All encryption algorithms are based on two general principles: substitution and transposition.
2. The number of keys. If both sender and receiver the same key than it is called `symmetric cipher` else if two different keys are used than it is called `asymmetric cipher`.
3. The way in which the plain text is processed. Block or Stream Cipher.

## Attacks on Crypto Systems

There are two general approaches to attacking a conventional encryption scheme: 

### 1. Brute Force Attack

