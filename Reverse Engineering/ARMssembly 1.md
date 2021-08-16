## Description
For what argument does this program print `win` with variables `68`, `2` and `3`? File: [chall_1.S](https://mercury.picoctf.net/static/d6c56d724795c006b319c6aa6a09140e/chall_1.S) Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

## Approach
1. Instead of reading the ARM assembly code, I chose compile it and analyzed it with `GhidraRun`
2. Compile the assembly code:
```
> sudo apt install gcc make gcc-aarch64-linux-gnu binutils-aarch64-linux-gnu
> aarch64-linux-gnu-as chall_1.S -o chall_1
```
3. With `GhidraRun`, we can get the code below:
```
int main(undefined8 param_1,long param_2){
  int iVar1;
  iVar1 = atoi(*(char **)(param_2 + 8));

  iVar1 = func(iVar1);
  if (iVar1 == 0) {
    iVar1 = puts("You win!");
  }
  else {
    iVar1 = puts("You Lose :(");
  }
  return iVar1;
}

int func(int param_1){
  return 0x5a - param_1;
}
```
4. According to the above code, we can know if we input the argument that can make  `0x5a - argument == 0`, then we can win. 