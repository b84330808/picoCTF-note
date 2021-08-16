## Description
We found this [file](https://mercury.picoctf.net/static/09a86202e72dbdb5bf4d1b5d2c6a5b86/tunn3l_v1s10n). Recover the flag.
## Hint
Weird that it won't display right...
## Approach
1. Aftering analyzing the file with `exiftool`, we can know this is a `bmp` file, but we can not open it any photo viewer because it is broken.
2. By checking the [header of `bmp`](https://www.file-recovery.com/bmp-signature-format.htm) and open the file with hex editor, we can find the information below:
```
offset:14 size:4  - size of BITMAPINFOHEADER structure, must be 40
```
So try to correct the file:
`0x1001~0x000E ->  0x00 0x00 0x00 0x28`

3. Try to open the photo. However, there is no flag in this photo.
4. I found there is one weird thing that why the size of this file is so big, but the photo looks like so simple and small?
5. So I tried to edit the height of the photo.
```
offset:22 size:4 - image height in pixels
``` 
6. I tried to edit the hex of 0x17 from `01` to `02`, to `03`...and found the flag! (It seems if you set the value too big, it will be seen as broken file, too.)