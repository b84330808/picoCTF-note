## Description
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?
## Hint
How do operating systems know what kind of file it is? (It's not just the ending!
## Approach
1. Analyzing the file by `exifTool`, we can get the information below:
```
ExifTool Version Number         : 12.29
File Name                       : flag.txt
Directory                       : .
File Size                       : 9.8 KiB
File Modification Date/Time     : 2021:08:14 00:20:52+09:00
File Access Date/Time           : 2021:08:14 00:21:22+09:00
File Inode Change Date/Time     : 2021:08:14 00:21:12+09:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 1697
Image Height                    : 608
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
SRGB Rendering                  : Perceptual
Gamma                           : 2.2
Pixels Per Unit X               : 5669
Pixels Per Unit Y               : 5669
Pixel Units                     : meters
Image Size                      : 1697x608
Megapixels                      : 1.0
```
2. Then change the extension to `png` and get the flag. 