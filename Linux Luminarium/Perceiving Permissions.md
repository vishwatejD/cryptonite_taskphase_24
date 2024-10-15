# PERCEIVING PERMISSIONS
> In Linux, files have different permissions or file modes. You can check out a permissions of a file or directory using `ls -l`.
> File Type Indicators:

    - (dash): Regular file
        This indicates a normal file (text file, binary, etc.).
        Example: -rw-r--r-- for file1.txt.

    d: Directory
        This indicates a directory.
        Example: drwxr-xr-x for directory1.

    l: Symbolic Link (symlink)
        This indicates that the file is a symbolic link pointing to another file.
        Example: lrwxrwxrwx for link -> /some/file.

    c: Character Device
        This is a special file for character-oriented devices (like terminals or keyboards).
        Example: crw-rw----.

    b: Block Device
        This indicates a block device file (like hard drives).
        Example: brw-rw----.

    p: Named Pipe (FIFO)
        This indicates a FIFO special file or named pipe.
        Example: prw-r--r--.

    s: Socket
        This indicates a socket file, which is used for inter-process communication.
        Example: srwxr-xr-x.


> The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting the permissions that the user who owns the file (termed the "owner") has to the file, 3 characters denoting the permissions that the group that owns the file (termed the "group") has to the file, and 3 characters denoting the permissions that all other access (e.g., by other users and other groups) has to the file.

## Changing file ownership

> NOTE that `$` in front of all commands means that we are not root and regular user, doesnt have all permissions. When it is `#` it means we are root and have all administrative priviliges.
> chown [username] [file] command can be used to change the owner of the file. But it requires us to be the root to perform this action.

Given that we must change the user of the flag file which is in the root directory. We first cd into root directory then we do `ls -l`.
We can see that the user and group of flag have been set to root and root. We thus use the command `chown hacker flag` to change the user of flag to hacker. Now we can use the command cat flag to get the flag.
![image](https://github.com/user-attachments/assets/febfb366-f749-470f-a0de-29a3b81d678d)

## Groups and files
> With the `id` command we can know which groups we are part of. For example:-
>
> ![image](https://github.com/user-attachments/assets/2fee852d-d397-4e77-a615-204614a78b63)
> A group can have mutliple users in it and a user can be part of multiple groups.
>
> We can change the group the file is part of using chgrp command. Unless we have the write permissions on the file and be part of the new group, invoking this command requires root access.

We can find the flag in the / directory. So we run the command `chgrp hacker flag` after `cd` into root directory. This changes the group that the file flag is part of from root to hacker. Now running the cat command gives us the flag. 

![image](https://github.com/user-attachments/assets/5b15a17c-a34a-4b9c-bafe-f1778dc4bcf1)

## Fun with group names

Given in question that the group the user hacker is changed to some random name. We can know that either by doing `id` or `ls -l` when we are in home directory.

Thus running the chgrp command according to the new group name gives us access to the flag file. Now we can cat the file to get the flag.

![image](https://github.com/user-attachments/assets/bc271cb5-c0c7-475c-866c-94bafb10d739)

## Changing permissions

> `chmod` command is used to change the file permissions. This can be done in two ways either adding or subtracting permission to user, group or others. The other way is to overwrite all the permissions using 3 digit numeric bits where first digit stands for user, second digit stands for group and the third for others. Each digit can have a maximum weight of 7 of which
> * 4 for read
> * 2 for write
> * 1 for executable permissions
>
> ![image](https://github.com/user-attachments/assets/c2d1d368-53b2-44d9-86c6-7dedcbc8fe59)


![image](https://github.com/user-attachments/assets/33e86cc3-f4ac-481f-b212-ce38f29eb74a)

## Executable files

Running `ls -l` command on the `/challenge/run` file gives the following.

![image](https://github.com/user-attachments/assets/e8824074-3388-471c-bb97-58a253c75409)

We can see that the file is in hacker user and hacker group, thus we have to give executable permissions to the user. So we use the command `chmod 544 /challenge/run` or `chmod u+x /challenge/run` to change the file permissions. Now we can use the command /challenge/run to get the flag. (5 = 4 for read + 1 for executable)

![image](https://github.com/user-attachments/assets/f26898cd-4633-439e-b223-d1149c7d2a5b)

## Permission Tweaking practice

![image](https://github.com/user-attachments/assets/14764b4e-b9d8-4b84-9b9a-c43c500e8fc4)

`/challenge/run` gives us the initial instructions.

Now we change the file permissions as per the instructions.  

![image](https://github.com/user-attachments/assets/87cd83b0-780c-4b04-a292-98f3976be506)

After the eight rounds we are given the authority to chmod the flag file . Now we add the readable permission to flag and then run cat command to get the flag.

## Permissions setting practice

`/challenge/run` gives the initial instructions. 
Now we can set the permissions according to instructions by using `chmod`.

Following the instructions we write the following commands.

```
chmod 551 /challenge/pwn
chmod 036 /challenge/pwn
chmod 664 /challenge/pwn
chmod 733 /challenge/pwn
chmod 142 /challenge/pwn
chmod 342 /challenge/pwn
chmod 746 /challenge/pwn
chmod 111 /challenge/pwn

```

In the last step we are given the authority to chmod the flag file. changing it to readable and running the cat command on it gives the flag.

## The SUID bit

> There are many cases in which non-root users need elevated access to do certain system tasks. The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do. The "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.
> 
> The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (**as long as they have executable permissions**), the program will execute as the owner user.
> 
> As the **owner of a file**, you can set a file's SUID bit by using chmod:
`chmod u+s [program] `

In this task we are given the authority to add the suid bit to the `/challenge/getroot` program. We add the suid bit by using the command `chmod u+s /challenge/getroot`. 

Now we can execute the command /challenge/getroot. This spawns a shell with root privileges where we can `cat /flag` to get the flag.

![image](https://github.com/user-attachments/assets/4ac33464-1404-4ff7-877a-712f138e05e8)

![image](https://github.com/user-attachments/assets/23e45667-34be-4648-9983-573e91ac32fd)

