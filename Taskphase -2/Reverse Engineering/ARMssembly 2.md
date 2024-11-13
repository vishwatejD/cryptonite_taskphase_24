# ARMssembly 2
What integer does this program print with argument 1748687564? 

```
	.arch armv8-a
	.file	"chall_2.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	sub	sp, sp, #32
	str	w0, [sp, 12]
	str	wzr, [sp, 24]
	str	wzr, [sp, 28]
	b	.L2
.L3:
	ldr	w0, [sp, 24]
	add	w0, w0, 3
	str	w0, [sp, 24]
	ldr	w0, [sp, 28]
	add	w0, w0, 1
	str	w0, [sp, 28]
.L2:
	ldr	w1, [sp, 28]
	ldr	w0, [sp, 12]
	cmp	w1, w0
	bcc	.L3
	ldr	w0, [sp, 24]
	add	sp, sp, 32
	ret
	.size	func1, .-func1
	.section	.rodata
	.align	3
.LC0:
	.string	"Result: %ld\n"
	.text
	.align	2
	.global	main
	.type	main, %function
main:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	w0, [x29, 28]
	str	x1, [x29, 16]
	ldr	x0, [x29, 16]
	add	x0, x0, 8
	ldr	x0, [x0]
	bl	atoi
	bl	func1
	str	w0, [x29, 44]
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	ldr	w1, [x29, 44]
	bl	printf
	nop
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits
```
**FLAG: picoCTF{38b09064}**

## My Approach to solve the challenge

Analysis of the code reveals the following
1. This stores the input value at stackpointer 12. It also has zero pointers at sp 24 and 28. This , function runs in a loop until the value of counter at 28 is equal to input value. Every time the loop runs the value at sp24 is incremented by 3. So by the time the loop terminates, the value would be 3 times the input value.

2. Converting it to hex value gives us the flag. 

![image](https://github.com/user-attachments/assets/5769a257-73b6-4234-9501-d6d6631b0f5d)

## Learning outcomes

 the bcc instruction stands for Branch if Carry Clear. It is a conditional branch instruction that causes the program to jump to a specified label if the Carry flag (C flag) in the Program Status Register (CPSR) is clear (i.e., if the result of a previous operation did not generate a carry-out).

## Incorrect methods used:-

I was using all the 9 digits as the flag, I forgot that the flag had to be 32 bits means 8 digits. Then I tried only the 8 digits not considering the MSB, the flag was correct.
