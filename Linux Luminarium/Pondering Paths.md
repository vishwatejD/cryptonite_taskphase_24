# PONDERING PATHS
## The Root

> [!NOTE]
> Points to be noted:-
> 
>the filesystem starts at /
> 
>You can invoke a program by providing its path on the command line.
> 
>Invoking a program doesnt mean opening a file, it means running a program.

Here, we invoke theprogram by using the `$ /pwn` command.




![image](https://github.com/user-attachments/assets/8122455a-db01-480d-a49c-49f886ca55c8)




## Program and absolute paths


Mentioned that the file run is in challenge directory, which in turn is in the root directory.

Tried using cd challenge but didnot work.

The program can be invoked by `$ /challenge/run` command.






![image](https://github.com/user-attachments/assets/feb51648-8c92-4d23-8344-9640d3146f20)



 Also tried doing the following 
 
changing directory to `/` we can do `$ ls` to see all the directories, which includes challenge, doing `$ ls` again shows the run file. Running the run file using `./` gives the following output.

![image](https://github.com/user-attachments/assets/b508167b-4f69-484f-94e4-bbd5b5002f85)



Also tried using the cat command using the path, the found out the location from which the program takes the flag.


![image](https://github.com/user-attachments/assets/646db318-ddca-4038-b271-1d482cfcef3a)


![image](https://github.com/user-attachments/assets/df6ffbca-133a-45ef-978f-3c2da6edf146)




## Position thy self


> [!NOTE]
> Points to be noted:-
> 
>the ~ in the prompt specifies the current directory.


Running the command `$ /challenge/run` gives the directory where the run program is located. Doing cd directory , we can then run the `$ /challenge/run` command to get the flag.




![image](https://github.com/user-attachments/assets/323bd079-80f6-4191-9eea-b8b30111583d)




## Position elsewhere

Running the `$ /challenge/run` command suggests to move to /home directory and then run the file. Doing that and then running the `$ /challenge/run` gives the flag. 





![image](https://github.com/user-attachments/assets/f2a35ecd-4be7-4119-8988-c2600dc7de28)




## Position yet elsewhere

Running the `$ /challenge/run` command suggests to move to `/usr/share/zoneinfo/posix/Asia` directory and then run the file. Doing that and then running the `$ /challenge/run` gives the flag. 

![image](https://github.com/user-attachments/assets/90d46211-81d5-4b51-8b22-091783604c31)


## implicit relative paths, from /


> [!NOTE]
> ![image](https://github.com/user-attachments/assets/2f70e3aa-aad9-45b5-888e-96602f9ea8e3)



Given that the relative path should be from `/` directory. So we first `$ cd /` to jump into the `/` directory. Then we invoke using the relative path `$ challenge/run`

![image](https://github.com/user-attachments/assets/08737311-2c87-449f-8986-e7e71e5eb757)


Also note that other relative paths donot work here since the run program only returns the flag only if our cwd is `/` (as mentioned in the question).






## explicit relative paths , from /


Running the `$ /challenge/run` command suggests us to move to the `/` directory. After moving to the directory we can use the ./challenge/run explicit relative path to invoke the program and get the flag.



![image](https://github.com/user-attachments/assets/c980ee57-e39e-4f1c-9a81-25205819bcdd)



## Implicit relative path


Given in question that we need to invoke the program from the `/challenge ` directory. For that we first move into the required directory using `$ cd /challenge` command.
Then we can run the file using  `$ ./run` command to get the flag.



![image](https://github.com/user-attachments/assets/d3d23149-bf38-467f-9327-59cd03a71ce7)


## Home sweet home


> [!NOTE]
> ![image](https://github.com/user-attachments/assets/129cb8c8-0eec-4293-a2c1-7721ec7fcecc)



The question says that we must provide an argument along with `/challenge/run` which is exactly three characters. This command will write the flag into the file mentioned and will display the flag.
Also given that the file must be present in home directory. So the first two characters of the argument will be `~/` the next character can be any alphabet which will be taken as the file name.




![image](https://github.com/user-attachments/assets/39a912ba-3a6f-46ea-a8b5-91392ff4cbc8)



