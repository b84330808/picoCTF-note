## Description
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to jupiter.challenges.picoctf.org 7480.
## Hint
Remember the flag format is picoCTF{XXXX}
## Approach
1. Access server by `nc jupiter.challenges.picoctf.org 7480`, and get lots of output so that we can find the flag.
2. As mentioned in title, it's plumbing. So he tried to imply using pipe `|`
3. Because we know the flag format, so we can try `nc jupiter.challenges.picoctf.org 7480 | grep pico`