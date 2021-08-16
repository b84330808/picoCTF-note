## Description
What does asm1(0x6fa) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/b41e08fc19ceb9d0466ebd68d36c5630/test.S)
## Hint
assembly [conditions](assembly conditions)
## Approach
1. I added some comment below:
* `DWORD PTR [ebp+0x8]` is the parameter `0x6fa` in the description.
```
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x3a2    ; compare 0x6fa and 0x3a2
	<+10>:	jg     0x512 <asm1+37>              ; if greater then jump to +37
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x358
	<+19>:	jne    0x50a <asm1+29>
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0x12
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8]
	<+32>:	sub    eax,0x12
	<+35>:	jmp    0x529 <asm1+60>
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x6fa    ; compare  0x6fa and 0x6fa
	<+44>:	jne    0x523 <asm1+54>              ; if not equal, jump to +54 (it's equal,though)
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]      ; eax = 0x6fa
	<+49>:	sub    eax,0x12                     ; eax -= 0x12  , so eax is 0x6e8
	<+52>:	jmp    0x529 <asm1+60>              ; jump to +60
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]      
	<+57>:	add    eax,0x12
	<+60>:	pop    ebp
	<+61>:	ret    
```
2. So we can get flag `0x6e8`