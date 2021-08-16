## Description
In RSA d is a lot bigger than e, why don't we use d to encrypt instead of e? Connect with `nc jupiter.challenges.picoctf.org 19566`.
## Hint
What is e generally?
## Approach
1. According to the description. we can guess maybe `d` is small, so we can try Wiener's attack at first and get the `d`.
2. Decode `c` with `d` and then we can get the flag.