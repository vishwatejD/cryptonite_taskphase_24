# DIGESTING DOCUMENTATION

### Resources given:- 
 [Online repository of man pages](https://man7.org/linux/man-pages/).

## Learning from documentation

Given documentation of the `/challenge/challenge` program: 
> Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck

Thus , we invoke the command `$ /challenge/challenge --giveflag` to get the flag

![image](https://github.com/user-attachments/assets/210f79df-70fe-477b-bd1a-128ef3f57dca)

## Learning complex usage

Given documentation for `/challenge/challenge` program:

> Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Running the `cd` command shows that the flag is in the `/` directory and the path to flag is `/flag`
 
![image](https://github.com/user-attachments/assets/c4588231-d0fe-4464-903d-7830026f53c3)

As given in description we can use the command `$ /challenge/challenge --printfile /flag ` , which prints the flag in the terminal.

![image](https://github.com/user-attachments/assets/c9bf8caa-74e1-4d11-bd86-932ce9c62b94)

## Reading Manuals

> [!TIP]
> man is short for manual, and will display (if available) the manual of the command you pass as an argument.
> this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command.

Running man command with challenge as specified in question gives a hint that it will print flag when the argument provided with it is `--bnhvgm 313`


![image](https://github.com/user-attachments/assets/53fdc785-0297-4090-ad4a-4ef1615af9ad)

Running the command `$ /challenge/challenge --bnhvgm 313` gives the flag.

![image](https://github.com/user-attachments/assets/d9c0bd9e-36d8-4f44-bbbe-9f052659fe2f)

## Searching Manuals

Invoking the man command on challenge as mentioned in the question gives its manual page. It consists of many arguments but we need to find the argument which gives us the flag.

We can search in a man page using `/ word to be searched` and navigating between results using `n` or `N`.

Thus we search using `/flag ` and we get the following result.

![image](https://github.com/user-attachments/assets/dc1e826a-0b3b-4e6e-a1bb-bc9441cf506c)

We find the argument to be `-- cwmb`

![image](https://github.com/user-attachments/assets/25d039e6-0aab-4624-9831-3f16483ec2b9)

## Searching for manuals

Doing the man man command as specified in the question, reveals the manual page for the man command. Scrolling down reveals a FINDING MANUAL PAGES section where we will see an option called --wildcard. It takes a string as an argument and searches for that string in the other manual pages.

Using that command for searching flag string reveals the actual man page for challenge. Running the command `$ /challenge/challenge --gugumw 365`
gives the flag.

![image](https://github.com/user-attachments/assets/f5cf9142-28e4-40b4-97c0-aa3368ad7233)

![image](https://github.com/user-attachments/assets/2f1833e0-2f1f-4cd8-9dde-a1e468475da6)

![image](https://github.com/user-attachments/assets/a9524c1e-0d91-48ee-ab58-2830a5311e05)

## Helpful programs

Tried challenge --help , which didnt work. Then tried `$ /challenge/challenge --help` it gave the following output.

![image](https://github.com/user-attachments/assets/c0495217-2136-4104-a68f-075626d80286)

Reading it reveals that the `-g` argument takes a value and if it matches the secret value ,prints the flag.
It is also given that the `-p` argument prints the secret value.

Thus we do the following and get the flag.

![image](https://github.com/user-attachments/assets/190db5ef-0d87-40ae-980b-878b40bb408b)

## Help for Builtins

> Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help

Given in question that , `challenge` in this question is a shell builtin, we use the command `$ help challenge` to get information.

![image](https://github.com/user-attachments/assets/d235b92a-d202-45eb-a2c3-f8f3999285df)

> You must be sure to provide the right value to --secret. That value
    is "0gJkwupu".

Thus , we use the command `$ challenge --secret 0gJkwupu` to get the flag.

![image](https://github.com/user-attachments/assets/16c76229-b5e3-49c9-a1c6-740509e18549)



