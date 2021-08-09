## Description
A one-time pad is unbreakable, but can you manage to recover the flag? (Wrap with picoCTF{}) nc mercury.picoctf.net 58913 [otp.py](https://mercury.picoctf.net/static/e87ba627b72932bdb57b31bbac3c22c5/otp.py)

## Hint
Maybe there's a way to make this a 2x pad.

## Approach
1. By accessing the remote server, we know the encrypted flag is:
`51124f4d194969633e4b52026f4c07513a6f4d05516e1e50536c4954066a1c57`

2. By testing the encrypting mechanism, we can find that 1 character will be encrypted into 1 byte. Therefore, we can know that the encrypted flag was from 32 characters.

3. By analyzing the source code, we can know that the encrypting mechanism is like below:
    1. Take the Xth character of flag, and convert it into its Unicode 
    2. Take the Xth number in key list
    3. Get the XOR of (1) and (2)

4. Therefore, if we send the `\x00\x00\x00\x00\x00...`, we can get the original key.
5. By analyzing the source code, we can know that the length of key is 50,000, and the key will be reused from 50,001.
6. We know that the flag has used 32 keys in the list, so we need to consume the remaining (50000-32) to make it reset the key.
7. After resetting, we can send 32 `\x00` to get the key used to encrypt flag.

8. After getting the key, we can get the flag by XOR the encrypted flag and the key.