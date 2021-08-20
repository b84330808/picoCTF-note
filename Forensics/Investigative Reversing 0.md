## Description
We have recovered a [binary](https://jupiter.challenges.picoctf.org/static/6e007dc305ebb3d94c2ab361ee0127a6/mystery) and an [image](https://jupiter.challenges.picoctf.org/static/6e007dc305ebb3d94c2ab361ee0127a6/mystery.png). See what you can make of it. There should be a flag somewhere.
## Hints
1. Try using some forensics skills on the image
2. This problem requires both forensics and reversing skills
3. A hex editor may be helpful

## Approach
1. Open the `image` with hex editor, we can find the encrypted flag at the end.
```
picoCTK
k5zsid6q_fb51c821}
```

2. Open the `binary` with `Ghidra` and find `main`
```
void main(void)

{
  FILE *__stream;
  FILE *__stream_00;
  size_t sVar1;
  long in_FS_OFFSET;
  int local_54;
  int local_50;
  char local_38 [4];
  char local_34;
  char local_33;
  char local_29;
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  __stream = fopen("flag.txt","r");
  __stream_00 = fopen("mystery.png","a");
  if (__stream == (FILE *)0x0) {
    puts("No flag found, please make sure this is run on the server");
  }
  if (__stream_00 == (FILE *)0x0) {
    puts("mystery.png is missing, please run this on the server");
  }
  sVar1 = fread(local_38,0x1a,1,__stream);
  if ((int)sVar1 < 1) {
                    /* WARNING: Subroutine does not return */
    exit(0);
  }
  puts("at insert");
  fputc((int)local_38[0],__stream_00);
  fputc((int)local_38[1],__stream_00);
  fputc((int)local_38[2],__stream_00);
  fputc((int)local_38[3],__stream_00);
  fputc((int)local_34,__stream_00);
  fputc((int)local_33,__stream_00);
  for (local_54 = 6; local_54 < 0xf; local_54 = local_54 + 1) {
    fputc((int)(char)(local_38[local_54] + '\x05'),__stream_00);
  }
  fputc((int)(char)(local_29 + -3),__stream_00);
  for (local_50 = 0x10; local_50 < 0x1a; local_50 = local_50 + 1) {
    fputc((int)local_38[local_50],__stream_00);
  }
  fclose(__stream_00);
  fclose(__stream);
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return;
}
```

3. The `picoCT` is from the code below:
```
fputc((int)local_38[0],__stream_00);    //p
fputc((int)local_38[1],__stream_00);    //i
fputc((int)local_38[2],__stream_00);    //c
fputc((int)local_38[3],__stream_00);    //o
fputc((int)local_34,__stream_00);       //C
fputc((int)local_33,__stream_00);       //T
```

4. The `K k5zsid6` is from the code below:
``` 
for (local_54 = 6; local_54 < 0xf; local_54 = local_54 + 1) {
  fputc((int)(char)(local_38[local_54] + '\x05'),__stream_00);
}
```
We can find the encrypted text are encrypted by plain text + `\x05`

5. The `q` is from the code below:
```
fputc((int)(char)(local_29 + -3),__stream_00);
```
so decrypte it by adding 3 → `t`

6. The `_fb51c821`  is from the code below:
```  
for (local_50 = 0x10; local_50 < 0x1a; local_50 = local_50 + 1) {
  fputc((int)local_38[local_50],__stream_00);
}
```
So no need to change.

7. Just combine the above result, we can get the flag. 