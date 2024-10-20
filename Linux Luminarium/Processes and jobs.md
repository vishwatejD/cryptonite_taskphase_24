# Processes and Jobs

## Listing Processes

> The command ps stands for either "process snapshot" or "process status" and is used to display running processes. By default, ps shows only the processes associated with your terminal. You can use the -e option to list all processes and the -f option for a full-format output, which includes arguments. These options can be combined into a single argument like -ef. Additionally, you can use a to display processes for all users, x to include processes not associated with a terminal, and u for a user-friendly output. These can also be combined into a single argument such as aux.



## Backgrounding Processes

To acquire the flag, start the process `/challenge/run` by executing the command. Then, suspend the running process by pressing `Ctrl+Z`. After that, resume the process in the background using the bg command. Finally, execute another instance of `/challenge/run` to obtain the flag.

![Screenshot from 2024-10-14 19-03-55](https://github.com/user-attachments/assets/222b58fa-e3a3-429f-8ff0-06a10fe5bc7a)


## Forgrounding Processes

To acquire the flag, start the process `/challenge/run` by executing the command. Next, suspend the process by pressing `Ctrl+Z`. After that, resume it in the background using the bg command. Finally, bring the process back to the foreground with the fg command to obtain the flag.

![Screenshot from 2024-10-14 19-10-52](https://github.com/user-attachments/assets/a61da48d-da90-4317-9a96-e97bb847c84e)


## Starting Backgrounded processes

Processes can be started from background by appending `&` at the end of the command.

![Screenshot from 2024-10-14 19-19-36](https://github.com/user-attachments/assets/2815a1d0-3ccb-4c7e-ab4d-839e2d79d875)

