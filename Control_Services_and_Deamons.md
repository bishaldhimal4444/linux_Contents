# 1. Objectives:
1. **systemd** is a system and serviece manager for linux, responsible for initialization during boot, managing services, and maintaining the system's overall state.
   
2. It runs as PID 1, making it the first process started by the kernel.
   
3. **systemctl** is a command line interface tool to control and iteract with systemd.
   
4. Deamons:
   - are background processes
   - independent of users.
   - many deamons names end with 'd' (eg: sshd, httpd, cron etc)
   - starts automatically during boot.
   - remains active to respond to requests or perform tasks when needed.


# 2. List Service Units:
Lists only the service units with active states:
```
systemctl list-units --type=service
```
List all service units:
```
systemctl list-units --type=service --all
```
Option to see the state of all installed unit files:
```
systemctl list-unit-files --type=service
```

# 3. View Service States:
##### Syntax:```systemctl status <name.type>``` or ```service <name> status``` 
Example:
```
systemctl status sshd
```
or, 
```service sshd status```


# 4. Verify the status of Service;
```
systemctl is-active sshd
```
or,
```
systemctl in-enabled sshd
```

# 5. list Unit Dependecies
    ```
    systemctl list-dependencies sshd
    ```
# 6. Mask and Unmask services:
    ```
    systemctl mask service_name
    ```
    or,
    ```
    systemctl unmask service_name
    ```
# 7. Enable Services to Start or Stop at Boot
    ```
    systemctl enable <unit>
    ```
    or,
    ```
    systemctl enable --now <unit>
    ```
    and
    ```
    systemctl disable <unit>
    ```
    or,
    ```
    systemctl disable --now <unit>
    ```
systemctl enable unit cmd creates a symbolic link from the service unit file, usually in the /usr/lib/systemd/system directory, to the disk location where the systemd command looks for files in the /etc/systemd/system/targetname.target.wants directory.
    
# Control System Services:
Start and Stop services:
```
systemctl status ssh.service
```
or,
```
systemctl start sshd
```
or,
```
systemclt stop sshd
```
Restart and Reload Services:
```
systemctl restart sshd
```
or,
```
systemctl reload sshd
```
or,
```
systemctl reload-or-restart sshd
```
