# DES Implementation in Pure Python
This is my pure python implementation of  DES 64-bit encryption algorithm in ECB and CBC modes. For the sake of simplicity, we divide it into four sections written as modules and ultimately combine them into [one](https://github.com/ybruce61414/Cryptography/blob/master/DES/DES_final.ipynb).

1. Sub-key generation
2. Mangler function
3. Encryption for a single block(64 bits)
4. Decryption for a single block(64 bits)

## ECB mode
**Electronic Code Book**(ECB) is a mode of operation for a block cipher. It requires its input(plaintext) to be an exact multiple of the block size, and each block is encrypted separately. 

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

## Triple DES
Triple DES (3DES) is a symmetric-key block cipher, which applies the DES cipher algorithm three times to each data block. It is based on an encrypt-decrypt-encrypt process and has three 64-bit keys(*k1*,*k2*,*k3*). 

Now, Triple DES comes in three flavors:
1. *k1* = *k3*: 3DES has 128-bit key.
2. *k1* = *k2*: 3DES runs as single DES.
3. *k1*,*k2*,*k3* are distinct: 3DES has 192-bit key.

```python
#simple example of 3DES in ECB & CBC modes

message = 'Test√ cryptography'

#64-bit key(hex form) 
key_1= '0123456789ABCDEF'
key_2= '23456789ABCDEF01'
key_3= '3456789ABCDEF012'

#64-bit initialization vector 
iv = '0123456789ABCDEF'

# ECB mode
a = DES(mode='ecb')
a_ecb_ciphertext = a.encrypt(message,k1,k2,k3)
a_ecb_plaintext = a.decrypt(a_ecb_ciphertext,k1,k2,k3)

# CBC mode
b = DES(mode='cbc')
b_cbc_ciphertext = b.encrypt(message,k1,k2,k3,iv)
b_cbc_plaintext = b.decrypt(b_cbc_ciphertext,k1,k2,k3,iv)

```

Note:
* All plaintext is encoded using UTF-8.
* PKCS5 padding is used for making the input of cipher block be an exact multiple of the block size.

