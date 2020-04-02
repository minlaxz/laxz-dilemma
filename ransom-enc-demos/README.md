AES-ENCRYPTIONS
===

### AES with PASSWORD:

#### ENCRYPTION AND DECRYPTION USING PASSWORD:
+ #### encrypt __FILE__ using PASSWORD:
	- `$ openssl aes-256-cbc -salt -pbkdf2 -in inkyung.zip -out inkyung.zip.aes`

+ #### encrypt __STRING__ using PASSWORD:
	- `$ echo "a_string" | openssl enc -e -aes-256-cbc -a -salt -pbkdf2`

+ #### decrypt __FILE__ using PASSWORD:
	- `$ openssl aes-256-cbc -d -salt -pbkdf2 -in inkyug.zip.aes -out inkyung.zip`

+ #### decrypt __STRING__ using PASSWORD:
	+ `$ echo "U2FsdGVkX193eRmMTDQhV0x5fB2aHUDxt80jPi9noks=" | openssl enc -e -aes-256-cbc -a -d -salt -pbkdf2 `

---

### AES with key-file:

#### ENCRYPTION AND DECRYPTION USING KEY-FILE:

+ #### CREATE SYMMETRIC KEY: 
	+ `$ openssl rand 256 > symme.key`

+ #### encrypt __FILE__ using KEY-FILE: 
	+ `$ openssl enc -aes-256-cbc -salt -pbkdf2 -in secret.png -out secret.png.enc -k symme.key`

+ #### encrypt __STRING__ usingKEY-FILE:
	+ `$ echo "hi, there." | openssl enc -e -aes-256-cbc -a -salt -pbkdf2 -k symme.key`

+ #### decrypt __FILE__ using KEY-FILE:   
	+ `$ openssl enc -aes-256-cbc -salt -pbkdf2 -d  secret.png.enc -out secret.png -k symme.key`

+ #### decrypt __STRING__ using KEY-FILE:
	+ `$ echo "CIPHER-TEXT" | openssl enc -e -aes-256-cbc -a -salt -pbkdf2 -d -k symme.key`

#### CHECK:

+ `$ sha256sum secret.png`

	+ > 37f6a93e896f501333151687cc136bc0241e032ce1d0048915a989807093181b  secret.png

+ `$ sha256sum secret.png.enc`

	+ > 7c3f55bc6ae0b4609337287a679c3c7090cdad1cebc6f87ddf53bab7ff03504e  secret.png.enc

---

### Reference for AES-Password Encryption
+ [REF:](https://codingbee.net/centos/openssl-demo-encrypting-decrypting-files-using-both-symmetric-and-asymmetric-encryption)

--- --- --- --- --- --- --- --- --------- --- --- --- --- --- --- --- --- --- ---
---


RSA ENCRYPTIONS
===

#### CREATE RSA KEYs with PEM OUTPUT:
+ Private Key:
	+ `$ openssl genrsa -aes256 -out private.pem 4096`
+ Public Key:
	+ `$ openssl rsa -in private.pem -outform PEM -pubout -out public.pem`

---

> ###  ENCRYPT using PUBLIC.key (`pem`) and DECRYPT using PRIVATE.key

>> #### ENCRYPT *FILE* :
+ `$ openssl rsautl -encrypt -inkey public_key.pem -pubin -in PlainTextFile.txt -out EncryptedData.encrypted`

>> #### DECRYPT _FILE_ :
+ `$ openssl rsautl -decrypt -inkey private_key.pem -in EncryptedData.encrypted -out DecryptedData.txt`

>> #### ENCRYPT _STRING_:
+ `$ echo "hi." | openssl rsautl -encrypt -inkey public.pem -pubin | openssl enc -base64`

>>#### DECRYPT _STRING_:
+ `$ echo "hi." | openssl rsautl -encrypt -inkey public.pem -pubin | openssl enc -base64`

---

> ###  ENCRYPT using PRIVATE.key (`pem`) and DECRYPT using PUBLIC.key

>> #### ENCRYPT _FILE_:
+ `$ openssl rsautl -encrypt -inkey private_key.pem -in PlainTextFile.txt -out EncryptedData.encrypted`

>> #### DECRYPT _FILE_:
+ `$ openssl rsautl -decrypt -inkey public_key.pem -pubin -in EncryptedData.encrypted -out DecryptedData.txt`   

--- --- --- --- --- --- --- ---
---

### creating a Certificate Signing Request (CSR) file and getting it signed by a Certificate Authority.
+ `$ md5sum public_key.pem | openssl rsautl -inkey private_key.pem -sign > checksum.signed`  
+ `$ openssl rsautl -inkey public_key.pem -pubin -in checksum.signed`
+ `$ md5sum public_key.pem`


---

[REF:](https://www.czeskis.com/random/openssl-encrypt-file.html)


==noted by  ```minlaxz```/`*_*`\==

---
