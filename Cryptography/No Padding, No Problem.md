## Description
Oracles can be your best friend, they will decrypt anything, except the flag's ciphertext. How will you break it? Connect with nc mercury.picoctf.net 2671.
## Hint
What can you do with a different pair of ciphertext and plaintext? What if it is not so different after all...
## Approach
1. Our goal it to find a number that can become the real ciphertext by some calcultation.
2. Fortunately, if we multiply a ciphertext by another one, we can get the original one! Like the calculation below:
- `C1 ＝ M1^e`
- `C1 × C2 ＝ M1^e ×  M2^e ＝ (M1 × M2)^e`
For example, if we replace C2 with 2, we can get:
- `C1 × 2^e ＝ M1^e ×  2^e ＝ (M1 × 2)^e`
3. If we input `C1 × 2^e`, Oracles can decrypt it for us, the output is `(M1 × 2)`. So the last step is divide `(M1 × 2)` by `2` to get `M1`, which is the flag. (after translating into hex and then into ASCII)