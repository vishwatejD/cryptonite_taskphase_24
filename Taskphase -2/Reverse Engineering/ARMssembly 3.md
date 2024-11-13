# ARMssembly 3
What integer does this program print with argument 3634247936?
```
	.arch armv8-a
	.file	"chall_3.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	w0, [x29, 28]
	str	wzr, [x29, 44]
	b	.L2
.L4:
	ldr	w0, [x29, 28]
	and	w0, w0, 1
	cmp	w0, 0
	beq	.L3
	ldr	w0, [x29, 44]
	bl	func2
	str	w0, [x29, 44]
.L3:
	ldr	w0, [x29, 28]
	lsr	w0, w0, 1
	str	w0, [x29, 28]
.L2:
	ldr	w0, [x29, 28]
	cmp	w0, 0
	bne	.L4
	ldr	w0, [x29, 44]
	ldp	x29, x30, [sp], 48
	ret
	.size	func1, .-func1
	.align	2
	.global	func2
	.type	func2, %function
func2:
	sub	sp, sp, #16
	str	w0, [sp, 12]
	ldr	w0, [sp, 12]
	add	w0, w0, 3
	add	sp, sp, 16
	ret
	.size	func2, .-func2
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
**FLAG: picoCTF{00000027}**

## My Approach to solve this challenge:-

After analysis of the code given, I wrote the following code which mimicks the same process as the given code.

```java
import java.util.Scanner;

public class arm3 {
    public static long func2(long value) {
        return value + 3;
    }
    public static long func1(long input) {
        long num = input;
        long counter = 0;  
        while (num != 0) {
            
            if (num %2!= 0) {
                counter = func2(counter);  
            }
            num = num >> 1;  
        }

        
        return counter;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter a number: ");
        long input = scanner.nextLong();
        
        long result = func1(input);
        System.out.println("Result: " + result);
        
    }
}

```
Now, providing the input as 3634247936 gives 39 as result. Thus , the flag is the hex value of 39 which is 0x27.

## Incorrect methods used:-

While writing the java program, I first wrote it using int. When I ran the code with given integer value it gave me Input mismatch exception because the number was too large to be integer. So I changed everything to long which worked fine and gave the flag.
