## Description
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/3944a59474f9f676942282c50b9c3675/Forensics%20is%20fun.pptm)

## Approach
1. According to the name(hint?), I just open the file with PowerPoint and check the macro, but there is no flag there.
2. After investigating, I knew that pptm can be unzip and try it.
3. After searching, I finally found the file `/slideMasters/hidden` (Yes, it's a hidden file!)
4. The file contains the flag in bash64, so you can get it after decoding.