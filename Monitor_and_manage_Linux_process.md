# Process States and Lifecycle:
- running: R    
- sleeping:  
   S : task_interruptible  
   D : task_uninterruptible  
   K : task_killable  
   I : task_report_idle  
- stopped: T  
- Zombie:  
   Z : exit_zombie  
   X : exit_dead


# list Processes:
```
ps aux
```
ps — process status command, shows active processes.  
a — show processes for all users, not just the current user  
u — show the user/owner of the process along with other details in a user-oriented format.  
x — show processes that don’t have a controlling terminal (background or daemon processes).  

or
```
ps -aux
```
or
```
ps -ef
```  
ps aux	Correct BSD-style full process list	Widely used on Linux  
ps -aux	Not recommended, may behave unexpectedly	May treat x as username filter  
ps -ef	POSIX-style full process list	Alternative, standard on many Unix systems  

or
```
ps lax
```

# Top vs. ps cmd:
- top cmd is used for interactive and real-time process monitoring.
- ps is a snapshot tool that displays a static list of currently running processes at a single point in time.

# Control Jobs:
- Run jobs in the backgroud:
```
sleep 5 &
```
- Runs the job in the foreground:
```
sleep 5
```
- Bring background job to foreground:
  ```
  fg %1
  ```
  where '1' is the job number  
- Suspends the current foreground job & places it in background:
   ```
   ctrl + Z
   ```
- Start running the suspended process:
  ```
  bg %1
  ```
  
- Stop the job:
  ```
  kill %1
  ```
  or
  ```
  kill job_number
  ```

