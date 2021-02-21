# bip039-honeyencrypt

## Description
Honey encrypt BIP039 seeds. The program is used to encrypt and decrypt files containing BIP039 seeds with a password derived key. The files are encrypted usoing AES-CBC.
Decryption attempts using the wrong key will always produce a wrong, yet valid BIP039 seed. Thus attempts of breaking the encryption using brute-force or dictionary attacks will be much harder for an attacker, as the resulting plaintext will always seem valid.

## Usage
### Encrypt
`python3 encrypt.py -e -s test_seed.txt -o ciphertext.txt`

### Decrypt
`python3 encrypt.py -d -c ciphertext.txt -o plaintext.txt 

For more information about Honey Encryption:
* https://link.springer.com/chapter/10.1007/978-3-642-55220-5_17







