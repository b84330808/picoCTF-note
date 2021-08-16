## Description
I wrote you another [song](https://jupiter.challenges.picoctf.org/static/b99c57e4274172bf3c93534b6d59632d/lyrics.txt). Put the flag in the picoCTF{} flag format
## Hint

## Approach
1. As you may know, there is a programming language [ROCKSTART](https://codewithrockstar.com/)
2. We can input the lyric to see the output. Unfortunately, it's empty. 
3. After analyzing the lyric, we can see something like `If the ...`, I think it's something like `if(...){}`, so I deleted them.
4. And we can know that `OOO is XXX` is something like `OOO = XXX` and `shout`, `say` are something like `print()`, so we can print all variables to see what will be outputed.
5. I got the output below
```
true
10
170
Keep on rocking!
66
79
78
74
79
86
73
```
6. The `Keep on rocking!` may be the hint to infer it's a starting point. And we can infer that `66` `79` `78` ... is the ASCII code with decimal base.
7. Translate the decimal code into character to get the flag.