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

