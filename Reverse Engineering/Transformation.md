## Description
I wonder what this really is...

`灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥ㄴㅡて㝽`
```
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
```
## Approach
The code below seems python code. 
```
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
```
so we just test it in python environment, but I got:
```
NameError: name 'flag' is not defined
```
Then, I add variable `flag="pico"` into my code.
```
flag="pico"
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])`
```
Then I got `'灩捯'`. These are the first two characters of hints given, so we can infer that `灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥ㄴㅡて㝽` are the answer to submit.

Let's break the python code down:
```
for i in range(0, len(flag), 2):
    r1 = ord(flag[i]) << 8
    r2 = ord(flag[i + 1])
    r3 = r1 + r2
    result = chr(r3)
```
ord(): Returns the number representing the unicode code of a specified character
chr(): Returns a string representing a character whose Unicode code point is an integer

For example: if the flag is `pi`

1. `p` will be converted into `112(0x70)` and  shifted 8 bit left to become `28672(0x7000)`
2. `i` will be converted into  `105(0x69)`
3. Then we add two number and get `28777(0x7069)` and its unicode is `灩`

So we can reverse the character `灩` like this:
1. Shift `28777(0x7069)` 8 bit right to get `112(0x70)` and chr() it
2. Take the last 8 bit of `28777(0x7069)` to get `105(0x69)` and chr() it

Like the codes below
```
result =""
chars = ['灩','捯','䍔','䙻','ㄶ','形','楴','獟','楮','獴','㌴','摟','潦','弸','彥','ㄴ','ㅡ','て','㝽']
for i in range(0,len(chars)):
    ch = ord(chars[i])
    r1 = chr(ch>>8)
    r2 = chr(ch&0b11111111)
    result+=(r1+r2)

print(result)
```


