# bip039-honey-encryption

## Description
Honey encryption of BIP39 seeds. 

> Honey encryption is a type of data encryption that "produces a ciphertext, which, when decrypted with an incorrect key as guessed by the attacker, presents a plausible-looking yet incorrect plaintext password or encryption key." 
- https://en.wikipedia.org/wiki/Honey_encryption

The program is used to encrypt and decrypt files containing BIP39 seeds with a password derived key. The files are encrypted using AES-CBC.

Decryption attempts using the wrong key will always produce a wrong, yet valid BIP39 seed. Thus attempts of breaking the encryption using brute-force or dictionary attacks will be much harder for an attacker, as the resulting plaintext will always seem valid.

Read the paper by Juels and Ristenpart for more information about Honey Encryption:
* https://link.springer.com/chapter/10.1007/978-3-642-55220-5_17

## Usage
### Encrypt
The following command will encrypt a seed stored in the file `test_seed.txt`and store the ciphertext in the file `ciphertext.txt`.

`python3 encrypt.py -e -s test_seed.txt -o ciphertext.txt`



### Decrypt
The following command will decrypt a ciphertext stored in the file `ciphertext.txt`and store the plaintext in the file `plaintext.txt`.

`python3 encrypt.py -d -c ciphertext.txt -o plaintext.txt` 
