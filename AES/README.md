# AES-128 Implementation in Pure Python
This is my pure python implementation of AES 128-bit encryption algorithm in ECB and CBC modes. For simplicity, we divide it into three sections written as modules and ultimately combine them into [one](https://github.com/ybruce61414/Cryptography/blob/master/AES/AES_final.ipynb).

1. Key expansion
2. Encryption for a single block(128 bits)
3. Decryption for a single block(128 bits)

## ECB mode
**Electronic Code Book**(ECB) is a mode of operation for a block cipher. It requires its input(plaintext) to be an exact multiple of the block size, and each block is encrypted separately. 

The usage of our implementation is straightforward, and it looks like this:

```python
#simple example of encrypting plaintext with ECB mode

message = 'Test√ cryptography'
#128-bit key(hex form)
key_32hex = '5468617473206D79204B756E67204675'

a = AES(mode='ecb')
# encrypt message with the key
ciphertext = a.encrypt(message,key_32hex)
# decrypt ciphertext  with the same key
plaintext = a.decrypt(ciphertext,key_32hex)

```

## CBC mode
**Cipher Block Chaining**(CBC) is a mode of operation for a block cipher. Each block of plaintext is XORed with the previous ciphertext block before being encrypted, and an **initialization vector** must be used in the first block.

```python
#simple example of encrypting plaintext with CBC mode

message = 'Test√ cryptography'
#128-bit key(hex form) 
key_32hex = '5468617473206D79204B756E67204675'
#128-bit initialization vector 
iv = '3468617473206D79204B756E67204675'

b = AES(mode='cbc')
# encrypt message with the key
ciphertext = b.encrypt(message,key_32hex,iv)
# decrypt ciphertext  with the same key
plaintext = b.decrypt(ciphertext,key_32hex,iv)

```
Note:
* All plaintext is encoded using UTF-8.
* PKCS7 padding is used for making the input of cipher block be an exact multiple of the block size.




