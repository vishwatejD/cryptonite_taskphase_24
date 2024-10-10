# PRACTICING PIPING 

every process in Linux has three initial, standard channels of communication:

*  **Standard Input** is the channel through which the process takes input. For example, your shell uses Standard Input to read the commands that you input.
*  **Standard Output** is the channel through which processes output normal data, such as the flag when it is printed to you in previous challenges or the output of utilities such as ls.
*  **Standard Error** is the channel through which processes output error details. For example, if you mistype a command, the shell will output, over standard error, that this command does not exist.



## Redirecting output

We use the command `$ echo PWN > COLLEGE` to redirect the stdout PWN to file COLLEGE. We get the flag.

![image](https://github.com/user-attachments/assets/3e48808c-7787-4130-8239-1cf398355247)

## Redirecting more output

Running the commmand `$ /challenge/run > myflag ` overwrites the myflag with the stdout of `/challenge/run` . Now invoking the cat command on the myflag file gives flag.

![image](https://github.com/user-attachments/assets/65e940db-dbb6-486d-999d-cb2932423d8e)


## Appending output

> You can redirect input in append mode using >> instead of >
>
> ![image](https://github.com/user-attachments/assets/26279e98-37c3-44f5-af25-50512302a814)

Running the command `$ /challenge/run >> /home/hacker/the-flag` appends the first half to the file directly to the file and then appends the second half through stdout. If we use the truncated mode instead of append mode the second half will overwrite the first half. thus when we print the file using cat only the second half is printed in the terminal.

![image](https://github.com/user-attachments/assets/f7feb206-06bb-431b-b234-e939c56ccce1)

![image](https://github.com/user-attachments/assets/31f16778-3b18-4dd3-bc1c-21b9b48d92ec)


## Redirecting Errors

> A File Descriptor (FD) is a number the describes a communication channel in Linux. You've already been using them, even though you didn't realize it.
>
> ![image](https://github.com/user-attachments/assets/2bf40d8f-ad1e-4ced-abe5-550c9e72cd69)

We invoke the command `/challenge/run` with the arguments `1> myflag` to specify it to write the stdout in the myflag file and `2> instructions` to specify it to write the stderr in the file instructions.
Now invoking the cat command on myflag gives us the flag.
![image](https://github.com/user-attachments/assets/6368ba3b-2627-4756-bd4a-6d1810a81d4d)

## Redirecting input

Given that we must redirect the file PWN to /challenge/run but first PWN must contain COLLEGE , so we first write COLLEGE to PWN using the following command

`$ echo COLLEGE > PWN`

Now we can redirect the PWN file to the input of /challenge/run using the < operator.

![image](https://github.com/user-attachments/assets/d82711bb-ab26-4502-a6f6-08ce2a965c61)

## Grepping stored results

`$ /challenge/run > /tmp/data.txt` 
We use the above command to redirect the output of /challenge/run program to data.txt file.

Now we use the command `$ cat /tmp/data.txt | grep pwn.college` to read the file data.txt and then grepping for the string pwn.college to get the flag.

We can also use the command `$ grep pwn.college /tmp/data.txt` to grep for the flag.

![image](https://github.com/user-attachments/assets/ffe14489-3344-4d7b-9f09-513a7493f6d4)

## Grepping live Output

We need to grep for flag in the live output of /challenge/run . This can be done by using `|` and grepping for flag in the same command.

`$ /challenge/run | grep pwn.college`

![image](https://github.com/user-attachments/assets/ab97108e-b38e-482c-878b-0dc4fd8fb1c5)

## Grepping errors

> The shell has a `>&` operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors

Here we use the 2>&1 operator. This redirects the stderr to stdout upon which the grep command can be used along with pipe to find the flag.

![image](https://github.com/user-attachments/assets/b1f74187-8196-41f2-a7fb-ef0131c6f00b)

## Duplicating piped data with tee

> The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line.
>
> ![image](https://github.com/user-attachments/assets/d3c97dcc-cba4-4f1d-9b57-a0b089c9c428)
>
> by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file.
>
> ![image](https://github.com/user-attachments/assets/5dcac020-b559-4e47-aa54-7b438ac2e0c6)

Given that we need to intercept the pwn file to know what arguments to be provided to /chaallenge/pwn so that we get the flag.

Thus, we use the following command `$ /challenge/pwn | tee output.txt |/challenge/college`. Now we can view the contents of the file output.txt using cat.

Following the instructions of the file gives us the flag.

`$ /challenge/pwn --secret "cP-MsUHx" |/challenge/college`

![image](https://github.com/user-attachments/assets/d39aa12d-266c-45dc-90cc-0027084b406a)


## Writing to multiple programs

> Linux follows the philosophy that "everything is a file". This is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line (such as tee) and hook it up to the input or output side of a program!

> This is done using what's called Process Substitution. If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe
> ![image](https://github.com/user-attachments/assets/fe15b772-c034-43b9-8814-f6de819925fd)

We use the tee command as follows to write the output generated by the `/challenge/hack` to `/challenge/the` and `/challenge/planet`

`$ /challenge/hack |tee >(/challenge/the) >(/challenge/planet)`

![image](https://github.com/user-attachments/assets/1057a12d-29b7-4f1a-b160-c286334b9832)

## Split piping stderr and stdout

Given that `/challenge/hack` must write its stdout into `/challenge/planet` and stderr channel into `/challenge/the` program. Thus we redirect stdout channel and stderr channel by using named pipes as follows

`$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)`

![image](https://github.com/user-attachments/assets/2ac7d5d2-ffbe-4f51-beb4-e0c8b138bb64)
