## Description
There is something on my shop network running at `nc mercury.picoctf.net 16524`, but I can't tell what it is. Can you?
## Hint
What language does a CNC machine use?
## Approach
1. After accessing `nc mercury.picoctf.net 16524`, we can get something like this:
```
G17 G21 G40 G90 G64 P0.003 F50
G0Z0.1
G0Z0.1
G0X0.8276Y3.8621
G1Z0.1
G1X0.8276Y-1.9310
```
2. According to the hint, this is [G-code](https://en.wikipedia.org/wiki/G-code).
3. Put the code on the viewer, such as [NC Viewer](https://ncviewer.com/), then we can get the flag.