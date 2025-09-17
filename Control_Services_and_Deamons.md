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
7. View Service States:
8. Verify the status of Service;

# Control System Services:
```
systemctl status ssh.service
systemctl start sshd
systemclt stop sshd

systemctl restart sshd
systemctl reload sshd
systemctl reload-or-restart sshd
```
