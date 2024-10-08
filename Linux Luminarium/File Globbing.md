# FILE GLOBBING

Globbing lets you reference files without typing them all out, or typing out their full paths

### Resources:-

https://www.gnu.org/software/bash/manual/html_node/Shell-Expansions.html

## Matching with *

> [!TIP]
> When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.
>![image](https://github.com/user-attachments/assets/667ab815-16f8-4874-a8e1-a294581c5d4d)

Given constraints that we need to cd to challenge only using an argument with 4 characters

Thus we use command with `*` globbing as `$ cd /ch*`, this takes us to the /challenge directory where we can run the /challenge/run program to get the flag.

![image](https://github.com/user-attachments/assets/1a0e24f7-0134-43c6-8cbb-553ab6efea34)

## Matching with ?

> [!TIP]
> When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character.
>
> ![image](https://github.com/user-attachments/assets/5704f084-674e-4266-bedd-0a075a72070b)

Given constraints that we need to cd to challenge directory by using ? instead of c and l. We do that and get the flag.

![image](https://github.com/user-attachments/assets/2ac79a85-8ff4-4fd5-b529-651ca50e4892)

## Matching with []

> [!TIP]
> The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:
>
> ![image](https://github.com/user-attachments/assets/c073b49c-522f-40a8-9aa6-a0bd796c11c4)

Taking the conditions given in question into consideration, we first cd to /challenge/files directory, then run the given /challenge/run command along with the argument files_[bash]
This gives us the flag.

![image](https://github.com/user-attachments/assets/1ef78686-931f-4139-a7f1-f9c630236908)

## Matching Paths with []

Using the `/challenge/run` command and providing the path to files along with the globbing yeilds the flag.

`$ /challenge/run /challenge/files/file_[bash]`

![image](https://github.com/user-attachments/assets/0e9cfd1f-07ae-4d6e-aa35-cd543f27b929)

## Mixing Globs

First we cd to /challenge/files directory. Then we can see what all files it contains using the ls command. It shows various files with different names. Since this task expects us to use different globbing methods, we can use the `[]` globbing to specify the first alphabets of the given words and the use `* ` to specify the rest of the word since no other words exist with the same first alphabets. Thus we use the command `$ /challenge/run [cep]*`  to get the flag.

![image](https://github.com/user-attachments/assets/ba2814c7-6e42-42cd-a391-90117a67faf0)

## Exclusionary Globbing

> [!TIP]
> If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed.
>
> ![image](https://github.com/user-attachments/assets/13fc5b42-b316-48e9-bccf-73447421fb76)
>
> The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.



![image](https://github.com/user-attachments/assets/1a567069-3ca1-456f-8669-5908965ebe7c)



