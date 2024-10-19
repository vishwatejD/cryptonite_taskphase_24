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

When you enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow.

Separated by :s, the first field of each line is the username and the second is the password. A value of * or ! functionally means that password login for the account is disabled, a blank field means that there is no password.

![image](https://github.com/user-attachments/assets/ad8a541c-a918-442c-93e7-758c1fb6548c)

```
As with the /etc/passwd, each field in the shadow file is also separated with “:” colon characters as follows:
    Username : A valid account name, which exist on the system.
    Password : Your encrypted password is in hash format. The password should be minimum 15-20 characters long including special characters, digits, lower case alphabetic and more. Usually password format is set to $id$salt$hashed, The $id is the algorithm prefix used On GNU/Linux as follows
        `$1$` is MD5
        `$2a$` is Blowfish
        `$2y$` is Blowfish
        `$5$` is SHA-256
        `$6$` is SHA-512
        `$y$` is yescrypt
    Last password change (lastchanged) : The date of the last password change, expressed as the number of days since Jan 1, 1970 (Unix time). The value 0 has a special meaning, which is that the user should change her password the next time she will log in the system. An empty field means that password aging features are disabled.
    Minimum : The minimum number of days required between password changes i.e. the number of days left before the user is allowed to change her password again. An empty field and value 0 mean that there are no minimum password age.
    Maximum : The maximum number of days the password is valid, after that user is forced to change her password again.
    Warn : The number of days before password is to expire that user is warned that his/her password must be changed
    Inactive : The number of days after password expires that account is disabled.
    Expire : The date of expiration of the account, expressed as the number of days since Jan 1, 1970.

```

When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user.


> **John the Ripper** is an Open Source password security auditing and password recovery tool available for many operating systems.

we first crack the password using john the ripper tool and use the password to su to zardus. Here we run the `/challenge/run` command to get the flag.
![image](https://github.com/user-attachments/assets/62a598a9-e70f-4553-a293-789bf6e4dc01)

## 

