# bip039-honey-encryption

## Description
Honey encryption of BIP39 seeds. 

> We introduce honey encryption(HE), a simple, general approach to encrypting messages using low min-entropy keys such as passwords. HE is designed to produce a ciphertext which, when decrypted with any of a number of incorrect keys, yields plausible-looking but bogus plaintexts called honey messages. A key benefit of HE is that it provides security in cases where too little entropy  is available to withstand brute-force attacks that try every key;  in this sense,  HE  provides  security  beyond  conventional  brute-force  bounds. 
> 
> <cite>*"Honey Encryption: Security Beyond the Brute-Force Bound", A. Juels and T. Ristenpart, https://link.springer.com/chapter/10.1007/978-3-642-55220-5_17*</cite>

The program is used to encrypt and decrypt files containing BIP39 seeds of all possible sizes with a password derived key. The keys are derived from user chosen passwords using salted Argon2id. The files are encrypted using AES-CBC.

Decryption attempts using the wrong key will always produce a wrong, yet plausible looking BIP39 seed. Thus attempts of breaking the encryption using brute-force or dictionary attacks will be much harder for an attacker, as the resulting plaintext will always seem valid.

## Usage
### Encrypt
The following command will encrypt a seed stored in the file `test_seed.txt`and store the ciphertext in the file `ciphertext.txt`.

`python3 encrypt.py -e -s test_seed.txt -o ciphertext.txt`



### Decrypt
The following command will decrypt a ciphertext stored in the file `ciphertext.txt`and store the plaintext in the file `plaintext.txt`.

`python3 encrypt.py -d -c ciphertext.txt -o plaintext.txt` 


## Demo
Encrypting the seed in `test_seed.txt` with password `s3cret` results in the following ciphertext (`ciphertext.txt`):
```
$ python3 encrypt.py -e -s test_seed.txt -o ciphertext.txt
Password:
Password:
Ciphertext written to ciphertext.txt
$ cat ciphertext.txt
{"salt": "KwUQUC0RIsP3PCAfB1CYRA==", "iv": "wFTCSnfW39twIkSKD/WPbg==", "ciphertext": "tnYx74rCWAD1cbVtxpHNb8kRuVR0jmGbP/9SCVbudI+kKkFjYbDQo356VW6YBkRaYrjjwk/5Q5J2a/ccvzecRSsLNACT55LenUuPEv7C9eJe+ZV8qDoLURIt37rrlDmUiGjq+aHZsIzAMuQY3M0Ze4GzWLJeX9jX4Rgu1of/Se54FzyzwZ5FsN9eRvx96PI6YG4d3r9HPDvq3+sE2WvMtjJk/bzyklLxRclToN9eLovNxVqki/UphBrq8B4Sc19P"}
```

Decrypting the ciphertext in `ciphertext.txt`with the wrong password `Passw0rd`results in the following plausible looking plaintext seed:
```
$ python3 encrypt.py -d -c ciphertext.txt -o plaintext.txt
Password:
Plaintext written to plaintext.txt
$ cat plaintext.txt
truly
season
tape
sausage
believe
feed
answer
glory
share
pelican
track
expect
```

Decrypting the ciphertext in `ciphertext.txt`with the correct password `s3cret`results in the following actual plaintext seed, identical to the seed in `test_seed.txt`:
```
$ python3 encrypt.py -d -c ciphertext.txt -o plaintext.txt
Password:
Plaintext written to plaintext.txt
$ cat plaintext.txt
acid
actress
census
already
wood
swamp
zero
salute
joke
jar
gravity
face
```
