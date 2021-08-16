## Description
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) `lkmjkemjmkiekeijiiigljlhilihliikiliginliljimiklligljiflhiniiiniiihlhilimlhijil` [new_caesar.py](https://mercury.picoctf.net/static/c9043977604318594ab73d126a01d0b1/new_caesar.py)
## Hint
- How does the cipher work if the alphabet isn't 26 letters?
- Even though the letters are split up, the same paradigms still apply
## Approach
1. After trying the given python code, we can conclude that 1 character will be encrypted into 2 characters and the key length is 1. In fact, you can find more rules if you analyze the code deeply.
2. However, I think the faster way it to print all the encrypted result, and then find its correspond plain text.
For example, input 0-9,a-z,A-Z and to keep their result. Because we know that 2 encrypted characters represents 1, so we can find the flag by doing so.
3. In fact, I didn't know the key, so I just tried it from a, and if it is not correct key, some ASCII character will become out of range. And I found the key is `f` 
4. I write some python code based on the given one:
```
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]
print(ALPHABET)
def b16_encode(plain):
	enc = ""
	for c in plain:
		binary = "{0:08b}".format(ord(c))
		enc += ALPHABET[int(binary[:4], 2)]
		enc += ALPHABET[int(binary[4:], 2)]
	return enc

def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = string.printable 

key = "f"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
	enc += shift(c, key[i % len(key)])

dict = {}
for i in range(0,len(flag)-1):
	dict[enc[i*2:i*2+2]] = flag[i]

cipher = "lkmjkemjmkiekeijiiigljlhilihliikiliginliljimiklligljiflhiniiiniiihlhilimlhijil"
for i in range(0,len(cipher)-1,2):
	print(dict[cipher[i:i+2]], end='')
```