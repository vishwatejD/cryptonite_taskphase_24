# COMPREHENDING COMMANDS

## cat: not the pet, but the command!

> [!TIP]
> One of the most critical Linux commands is cat. cat is most often used for reading out files.cat will concatenate (hence the name) multiple files if provided multiple arguments.



Given that the file flag is in the home directory. ls command shows the file. Using cat command on the file flag gives flag.

![image](https://github.com/user-attachments/assets/27b93c20-3cbf-4f4e-b3bc-3b86741fe601)

## catting absolute paths

Given that the flag is present in the root directory.(path given `/flag` )

We can retrieve the flag by the command `$ cat /flag`

![image](https://github.com/user-attachments/assets/fdb8d160-3c11-4f53-b75f-9d8c4803e5ea)

## more catting practice

Given constraints that we cannot move to any directory and we must use absolute path to get to the flag.
Trying the cd command gives the following output and specifies that the flag is present in the `/opt/pwndbg/caps/flag` directory.

Then using the command `$ cat /opt/pwndbg/caps/flag` gives us the flag.

![image](https://github.com/user-attachments/assets/0304be11-0c6d-4d27-9442-ad5845075573)

## grepping for a needle in haystack

> [!TIP]
> Grep is a command used to search for a certain string or sequence from a file or large amount of text.

Given that the flag is present in the file `/challenge/data.txt` we can find the flag from this sequence of text by grepping for pwn.college in the text file.

This can be done by using the command `$ cat /challenge/data.txt | grep pwn.college`

This command first reads the whole file and the grep command searches for the given text sequence in the read text.


![image](https://github.com/user-attachments/assets/13f813b6-02cf-4dd4-a0df-9a28aed18041)

## listing files

> [!TIP]
> ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.

The question says that the name of the run program is changed to something else. We need to use the ls command to find the new name.

Going into the challenge directory and doing the ls command gives the following output.

![image](https://github.com/user-attachments/assets/5add234a-5859-4ab5-a69e-bd6a3544bdfa)

By this we can know the new name of the run program. Now as we are in the same directory of the file we can use explicit relative path to run the file. `$ ./4030-renamed-run-7720`

![image](https://github.com/user-attachments/assets/d5231894-b845-4df5-8e9d-45815842284c)


## touching files

> [!TIP]
> Touch is a command used to create new files. New file can be created by giving the path and name of the file.


We must create new files by using the commands `$ touch /tmp/pwn` and `$ touch /tmp/college`

Then we can use the /challenge/run command to run the program and retrieve the flag.

![image](https://github.com/user-attachments/assets/bf687aeb-5249-45db-b470-fe601b68eef7)

## removing files 

> [!TIP]
> rm command removes the file whose filename provided as an argument

We remove the delete_me file using the ` $ rm delete_me` command which is in the home directory 

Then by running the program using the command `$ /challenge/check` we can retrieve the flag.

![image](https://github.com/user-attachments/assets/245704fc-c278-4b26-b439-ae020a2d4cf5)


## hidden files

To see the hidden files in a directory we need to use the `$ ls -a` 

We find the following flag file in the / directory.

![image](https://github.com/user-attachments/assets/3fd9dfc1-6836-4bb8-a9a8-297a63227d06)

We can now run the cat command over the file to retrieve the flag.


![image](https://github.com/user-attachments/assets/3748600d-3cff-440d-a7b4-609470562e4c)


## An epic filesystem quest

Following the instructions given in each clue gets us to the flag.

![image](https://github.com/user-attachments/assets/2c1eb380-e4c9-4dc5-a906-273ba8f47909)

![image](https://github.com/user-attachments/assets/0121e4f7-3324-42ab-bc49-36960e5173ee)

![image](https://github.com/user-attachments/assets/dee3c86f-9e87-47a6-b666-15c5e43cc68f)


## making directories

A directory can be made using the mkdir command. Thus we make the directory using the command `$ mkdir /tmp/pwn` then we move into that directory by using the command `$ cd /tmp/pwn` then we can now run the command /challenge/run to get the flag.

![image](https://github.com/user-attachments/assets/7479d80f-7a44-4d90-bf1b-c953130dc988)

## finding files
