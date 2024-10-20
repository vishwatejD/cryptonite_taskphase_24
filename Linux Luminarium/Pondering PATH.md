# Pondering PATH

## The PATH variable

There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.
In this challenge we empty out the path variable, then invoke the /challenge/run command. Since we emptied out the path the run file cannot invoke rm command. Thus we get the flag.

![image](https://github.com/user-attachments/assets/9625d85d-2076-4c28-8c25-25f1d3d43c7b)


## Setting PATH

We can add paths of other directories to the PATH variable so that we can execute commands without invoking them along with their path.

Here, we assign the required directory to the PATH variable, thus /challenge/run can invoke win command using bare name.

![image](https://github.com/user-attachments/assets/630420d3-8d2c-427e-a390-0b5cef819f4f)

## Adding Commands

Here, /challenge/run runs as root and invokes the win command. Thus, we can just place the path of home directory in the PATH variable. But rewriting the PATH variable breaks the access to the cat command. Thus, we have to append the path to home directory in PATH , not overwrite it.

First, I tried appending the :/home/hacker to PATH using redirection operator >>. But , that does nothing. In this form, PATH is interpreted as a file, not the environment variable. Since PATH is not a file, the command does nothing.

Thus we need to edit PATH using assignment only as follows. 

`PATH=$PATH:/home/hacker`

Now invoking the /challenge/run gives us the flag.

> NOTE: Remember changing `win`'s permissions to executable to execute it using bare name. 


![image](https://github.com/user-attachments/assets/ba9118ef-8558-474c-bacf-244933afaeca)

## Hijacking Commands

First i tried the following,

![image](https://github.com/user-attachments/assets/489ef7c2-634c-4400-af46-114cdce51d74)

Through this we can understand that the shell is using the original rm command even though I made a new rm command. After a bit of searching I found out the the PATH is scanned from left to right. Once it encounters the command it executes it. THus we need to append the home directory before the directory in which the original rm command is present.

 we restart the challenge and assign `PATH=/home/hacker:$PATH`.

 ![image](https://github.com/user-attachments/assets/f801a781-e222-4b23-bd94-ddc546f1fd4a)

Now executing the /challenge/run gives us the flag.
