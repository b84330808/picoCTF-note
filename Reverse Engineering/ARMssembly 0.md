## Description
What integer does this program print with arguments 4134207980 and 950176538? File: [chall.S](https://mercury.picoctf.net/static/da36e19990a2cede1dff10f9f33fe4b4/chall.S) Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

## Approach
1. Instead of reading the ARM assembly code, I chose compile it and analyzed it with `GhidraRun`
2. Compile the assembly code:
```
> sudo apt install gcc make gcc-aarch64-linux-gnu binutils-aarch64-linux-gnu
> aarch64-linux-gnu-as chall.S -o chall
```
3. With `GhidraRun`, we can get the code below:
```
undefined8 main(undefined8 param_1,long param_2){
  int iVar1;
  int iVar2;
  ulong uVar3;
  
  iVar1 = atoi(*(char **)(param_2 + 8));
  iVar2 = atoi(*(char **)(param_2 + 0x10));
  uVar3 = func1(iVar1,iVar2);
  printf("Result: %ld\n",uVar3 & 0xffffffff);
  return 0;
}

uint func1(uint param_1,uint param_2){
  if (param_2 < param_1) {
    param_2 = param_1;
  }
  return param_2;
}
```
4. We can find this is just a function to output the bigger parameter.
5. Choose the bigger parameter and translate it with hex base.