## Description
Not all ancient ciphers were so bad... The flag is not in standard format. `nc mercury.picoctf.net 19354`

## Approach
1. The main function of encryption is `encrypt_string`, and there is also a function `encrypt_pair` in it.

2. It looks like that 2 characters in plaintext will be taken as argument into `encrypt_pair` at one time.

3. However, the function `encrypt_pair` is a little complicated, so I decided to input all possible plaintext to get corresponded cipher.

4. I write the the python code below, it can be appended to the original code. 
```
chars = "abcdefghijklmnopqrstuvwxyz0123456789"
matrix = generate_square("n5vgru7ehz1klja8s9340m2wcxbd6pqfitoy")
dict = {}
for c1 in chars:
	for c2 in chars:
		pair = c1+c2
		enc_pair =  encrypt_pair(pair,matrix)
		dict[enc_pair] = pair
cipher = "dbc8bf9bae7152d35d3c200c46a0fa30"
plaintext =""
for i in range(0,len(cipher)-1,2):
	plaintext += dict[cipher[i]+cipher[i+1]]
print(plaintext)
```

5. Then we can get the plaintext of cipher, paste it into the server to get the flag.