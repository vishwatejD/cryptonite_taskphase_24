# Processes and Jobs

## Listing Processes

> The command `ps` stands for either "process snapshot" or "process status" and is used to display running processes. By default, `ps` shows only the processes associated with your terminal. You can use the `-e` option to list all processes and the `-f` option for a full-format output, which includes arguments. These options can be combined into a single argument like `-ef`. Additionally, you can use `a` to display processes for all users, `x` to include processes not associated with a terminal, and `u` for a user-friendly output. These can also be combined into a single argument such as `aux`.

To obtain the flag, we need to list the currently running processes using the ps -ef command and identify the renamed version of `/challenge/run`. This will reveal the new file name, which in this case is `/challenge/11666-run-26230`. To retrieve the flag, we then execute the command: `/challenge/11666-run-26230`.

## Killing Proccesses

> `kill` command will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

To obtain the flag, we need to locate the dont_run process as instructed. First, we run the ps -e command to list all processes. Among them, the process labeled with sleep is the one we're looking for, with a PID of 74. We then terminate this process using the command kill 74. After that, we can execute /challenge/run to get the flag.

## Interrupting the processes

> we use `Ctrl-C` key to interrupt and exit a running process

To obtain the flag, we need to run the process `/challenge/run` by executing the command $ `/challenge/run`, and then interrupt it by pressing `Ctrl + C`. This will reveal the flag.

## Suspending processes

> we use `Ctrl-Z` key to suspend a running process
> Another alternative, is using the process `kill -2 PID`. 

To obtain the flag, we need to suspend the `/challenge/run` process by executing the command $ `/challenge/run`, then suspending it with `Ctrl + Z`. After that, we need to run $ `/challenge/run` again to get the flag.

## Resuming Processes

> we use `fg` command to resume a suspended process in foreground
> 
> We can also foreground specific process by using the job id along with the fg command as `fg%jobnumber`.

here to aquire flag we need to suspend the process `/challenge/run` by running it using $ `/challenge/run` command and then we need to suspend it using `Ctrl-Z` key and the we need to resume it using $ fg command to get the flag.

## Backgrounding Processes

To acquire the flag, start the process `/challenge/run` by executing the command. Then, suspend the running process by pressing `Ctrl+Z`. After that, resume the process in the background using the bg command. Finally, execute another instance of `/challenge/run` to obtain the flag.

![Screenshot from 2024-10-14 19-03-55](https://github.com/user-attachments/assets/222b58fa-e3a3-429f-8ff0-06a10fe5bc7a)


## Foregrounding Processes

To acquire the flag, start the process `/challenge/run` by executing the command. Next, suspend the process by pressing `Ctrl+Z`. After that, resume it in the background using the bg command. Finally, bring the process back to the foreground with the fg command to obtain the flag.

![Screenshot from 2024-10-14 19-10-52](https://github.com/user-attachments/assets/a61da48d-da90-4317-9a96-e97bb847c84e)


## Starting Backgrounded processes

Processes can be started from background by appending `&` at the end of the command.

![Screenshot from 2024-10-14 19-19-36](https://github.com/user-attachments/assets/2815a1d0-3ccb-4c7e-ab4d-839e2d79d875)

## Process exit codes

> we use `echo $?` command to see the exit codes of the error programs. You can access the exit code of the most recently-terminated command using the special `?` variable (don't forget to prepend it with `$` to read its value.

> NOTE: commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

To obtain the flag, we first need to run the $ `/challenge/get-code` command, which will exit without running. Then, we find the exit code using the $ `echo $?` command. This exit code is used as an argument for the `/challenge/submit-code` command. Finally, we run $ `/challenge/submit-code 65` to get the flag.
