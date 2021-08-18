## Description
I found the flag, but my brother wrote a program to encrypt all his text files. He has a spelling quiz study guide too, but I don't know if that helps.
[public.zip](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/spelling-quiz/public.zip)

## Approach
1. After analyzing the code, we can find the encryption is just to map a character to another one. However, the mapping is random every time.

2. We can use [quipquip] (https://www.quipqiup.com/) to find the mapping. Just paste some words in `study-guide.txt` and it will tell us what the words really.

3. Append the flag too, and then get the flag.
