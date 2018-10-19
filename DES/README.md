# DES Implementation in Pure Python
This is my pure python implementation of  DES 64-bit encryption algorithm in ECB and CBC modes. For simplicity, we divide it into four sections written as modules and ultimately combine them into [one](https://github.com/ybruce61414/Cryptography/blob/master/DES/DES_final.ipynb).

1. Sub-key generation
2. Mangler function
3. Encryption for a single block(64 bits)
4. Decryption for a single block(64 bits)

The usage of our implementation is straightforward, and it looks like this:

```python
#simple example of encrypting plaintext with ECB mode

message = 'Test√ cryptography'
#64-bit key(hex form)
key_16hex = '0123456789ABCDEF'

a = DES(mode='ecb')
# encrypt message with the key
ciphertext = a.encrypt(message,key_16hex)
# decrypt ciphertext  with the same key
plaintext = a.decrypt(ciphertext,key_16hex)

```

## CBC mode
**Cipher Block Chaining**(CBC) is a mode of operation for a block cipher. Each block of plaintext is XORed with the previous ciphertext block before being encrypted, and an **initialization vector** must be used in the first block.

```python
#simple example of encrypting plaintext with CBC mode

message = 'Test√ cryptography'
#64-bit key(hex form) 
key_16hex = '0123456789ABCDEF'
#64-bit initialization vector 
iv = '0123456789ABCDEF'

b = DES(mode='cbc')
# encrypt message with the key
ciphertext = b.encrypt(message,key_16hex,iv)
# decrypt ciphertext  with the same key
plaintext = b.decrypt(ciphertext,key_16hex,iv)

```
Note:
* All plaintext is encoded using UTF-8.
* PKCS5 padding is used for making the input of cipher block be an exact multiple of the block size.

