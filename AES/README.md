# AES-128 Implementation in Pure Python
This is my pure python implementation of ASE 128bit encryption algorithm in ECB and CBC modes. For simplicity, we divide it into three sections written as modules and ultimately combine them into [one](https://github.com/ybruce61414/Cryptography/blob/master/AES/AES_final.ipynb).

1. Key expansion
2. Encryption for a single block(128 bits)
3. Decryption for a single block(128 bits)

## ECB mode
Electronic Code Book (ECB) is a mode of operation for a block cipher. It requires its input(plaintext) to be an exact multiple of the block size, and each block is encrypted separately. 

```python
#simple example of encrypting plaintext with ECB mode

message = 'Test??Ã cryptography'
key_32hex = '5468617473206D79204B756E67204675'

a = AES(mode='ecb')
# encrypt message with your key
ciphertext = a.encrypt(plaintext,key_32hex)
# decrypt ciphertext  with the same key
plaintext = a.decrypt(ciphertext,key_32hex)

```

## CBC mode
