# UNTANGLING USERS

All the users within a linux system are listed in the /etc/passwd file. We can see them by using the `cat /etc/passwd` command.

![image](https://github.com/user-attachments/assets/67625b6d-d413-4527-bb6a-7d2e8582f895)

Each line contains, separated by :s, the username, an x as a placeholder for where the password used to be , the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.

Some are service accounts to support various installed software, and some are "utility" accounts

NOTE:- the nobody user is used to ensure that, e.g., a program runs without any special privileges

## Becoming root with su

> su (switch user command) is a setuid binary. Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell. Before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password

We run the su command, when it prompts for password, we give hack-the-planet as the password. It then opens a root shell where we can invoke the `cat /flag` command which gives us the flag.

 ![image](https://github.com/user-attachments/assets/f7021b03-cf2b-46aa-bf15-dd373dd3aea5)

## Other users with su

With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root.

![image](https://github.com/user-attachments/assets/218f06d7-d642-4341-b391-7fdf1c2fcd29)

![image](https://github.com/user-attachments/assets/7dd63b6b-9459-4300-8208-7f09faa67a39)

## Cracking passwords

