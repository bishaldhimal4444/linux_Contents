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


# list Proceses:
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
ps lax
```
or
```
ps -ef
```
