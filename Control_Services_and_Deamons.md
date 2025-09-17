1. **systemd** is a system and serviece manager for linux, responsible for initialization during boot, managing services, and maintaining the system's overall state.
2. It runs as PID 1, making it the first process started by the kernel.
3. **systemctl** is a command line interface tool to control and iteract with systemd.
4. Deamons:
   - are background processes
   - independent of users.
   - many deamons names end with 'd' (eg: sshd, httpd, cron etc)
   - starts automatically during boot.
   - remains active to respond to requests or perform tasks when needed.
   - 
6. List Service Units:
   ```
   systemctl list-units --type=service
   systemctl list-units --type=service --all
   systemctl list-unit-files --type=service
   ```
8. View Service States:
   ```
   systemctl status name.type
   systemctl status sshd
   ```
10. Verify the status of Service;
    ```
    systemctl is-active sshd
    systemctl in-enabled sshd
    ```
11. list Unit Dependecies
    ```
    systemctl list-dependencies sshd
    ```
13. Mask and Unmask services:
    ```
    systemctl mask service_name
    systemctl unmask service_name
    ```
14. Enable Services to Start or Stop at Boot
    ```
    systemctl enable <unit>
    systemctl enable --now <unit>
    systemctl disable <unit>
    systemctl disable --now <unit>
    ```
   systemctl enable unit cmd creates a symbolic link from the service unit file, usually in the /usr/lib/systemd/system directory, to the disk location where the systemd command looks for files in the /etc/systemd/system/targetname.target.wants directory.
    
# Control System Services:
```
systemctl status ssh.service
systemctl start sshd
systemclt stop sshd

systemctl restart sshd
systemctl reload sshd
systemctl reload-or-restart sshd
```
