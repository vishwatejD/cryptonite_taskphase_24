# ARMssembly 4

What integer does this program print with argument 3434881889?

**FLAG: picoCTF{CCBC23D4}**
## My Approach to the challenge:-

Analysis of each function of the code as follows:

func1:

    Takes an integer argument, w0.
    If w0 <= 100, it calls func3.
    If w0 > 100, it increments w0 by 100, then calls func2.
    The result from either func2 or func3 is returned.

func2:

    Takes an integer argument, w0.
    If w0 > 499, it adds 13 to w0 and calls func5.
    If w0 <= 499, it subtracts 86 from w0 and calls func4.
    The result from either func4 or func5 is returned.

func3:

    Takes an integer argument, w0.
    Calls func7 with the same argument and returns the result.

func4:

    Takes an integer argument, w0.
    Sets a local variable to 17 and then calls func1 with 17, saving the result.
    Returns the original w0 value.

func5:

    Takes an integer argument, w0.
    Calls func8, which adds 2 to w0, and returns the result.

func6:

    Contains a loop that runs 899 times.
    Each loop iteration:
        Multiplies w1 by 800 and divides the result by 314.
        Sets the remainder to a memory location.
        Increments a counter by 1.
    Returns the remainder at the end of the loop.

func7:

    Takes an integer argument, w0.
    If w0 > 100, it returns w0 as is.
    If w0 <= 100, it sets w0 to 7 and returns it.

func8:

    Adds 2 to the input w0 and returns the result.

Following these functions, we can map as follows, 
* Given number 3434881889
* It is greater than 100 so it adds 100. 3434881989, then calls func2
* It is greater than 499 so it adds 13,3434882002 , then calls func5
* func5 just calls func8.
* Adds 2, 3434882004
* converting to hex gives CCBC23D4 which is the flag

## Incorrect methods used: 
NONE

## Resources used:

https://www.rapidtables.com/convert/number/decimal-to-hex.html?x=3434882004
