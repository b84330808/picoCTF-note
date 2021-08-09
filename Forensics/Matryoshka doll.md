## Description
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg)
## Hint
Wait, you can hide files inside files? But how do you find them?
## Approach
1. Check the file with `Exiftool`, but we can not get information about flag.
2. Try to unzip the file and you will get another files. Repeat it four times and you can get the flag. (like the title of this problem!)