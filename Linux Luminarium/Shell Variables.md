# Shell Variables

## Printing variables

We us the command `echo $FLAG` to print the flag.

![image](https://github.com/user-attachments/assets/63369fa7-acf3-4dbc-902f-4da5afd9edba)

## Setting variables

We use the command `PWN=COLLEGE` to assign the value college to pwn variable. This gives us the flag.

![image](https://github.com/user-attachments/assets/aa37f769-5321-4278-9eb2-bad0585f004a)

## Multi-Word variables

We use the command `PWN="COLLEGE YEAH"` to assign the string college yeah to variable PWN thus we get the flag.

![image](https://github.com/user-attachments/assets/7d1ff68e-4aac-49ec-814e-f16783fcde22)


## Exporting variables

> We can open a minimal shell implementation within the current shell using the command `sh` .
> We can also export variables to this shell implementation using the export command.

First we set the value of variable PWN to COLLEGE and set teh value of variable COLLEGE to PWN. Now we export the variable PWN to the shell by using the command `export PWN`.
Then we can open a shell implementation and execute the command `/challenge/run` to get the flag.

![image](https://github.com/user-attachments/assets/3deeadc9-b836-4d9c-8bf0-3f631fd7b6c4)

## Printing exported variables

> `echo` is one one the way to print variables.
> `env` is another way to print exported variables. Invoking this command prints all the exported variables.

Invoking the env command prints all the exported variables along with their values in the terminal. One of them is the flag.

![image](https://github.com/user-attachments/assets/f19307d9-3ebb-40ae-80c8-c26590096f7c)


## Storing command output

> We can also store the output of a command into a variable by assigning the command along with $() to a variable.
> for example:
>
> ![image](https://github.com/user-attachments/assets/13ef884a-e8ed-4266-8d22-70ea20276f33)

Here, We assign the variable PWN with the command /challenge/run by using the following command:

`PWN=$(/challenge/run)`

Now we can read the contents of the variable by using the `echo "$PWN"` command.

![image](https://github.com/user-attachments/assets/bada8897-7fc9-4a17-851d-e6aac9795589)

## Reading input

> The read function is a builtin which takes the input from user over the stdin channel. We can also specify prompts for better readability using the argument `-p` along  with read command.
>
>![image](https://github.com/user-attachments/assets/3f71a91a-358b-46c7-9837-fb48bd842982)
> ![image](https://github.com/user-attachments/assets/91249dab-6554-4e35-94c9-2e8f7b1f8e46)

We can use the command `read -p "input:-" PWN` to take the input and give COLLEGE as input when asked. This gives us the flag.

![image](https://github.com/user-attachments/assets/219c2269-05cc-4dbd-8e0f-251a7348469c)

## Reading Files
> We can also read a file or output of command into a variable by using the `read` command.
> For example:-
>
> ![image](https://github.com/user-attachments/assets/cc10edde-66b1-4f6f-afa3-ab8d73590fb3)

We use the command `read PWN < /challenge/read_me` to read the  `/challenge/read_me ` file into the stdin of PWN variable using read command. Thus we get the flag.

![image](https://github.com/user-attachments/assets/c04c7477-1cfe-4326-9020-10342055cfa6)

