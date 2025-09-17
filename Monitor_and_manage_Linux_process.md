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
