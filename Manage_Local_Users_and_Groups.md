## User Types:
**1. Super User:** Uid is 0.
**2. System User:** For processes or deamons (uid = 1-999).
**3. Regular User:** For day to day work (uid > 1000).

## Groups Types:
**1. Primary Group** is created itself when a new-user is created. It has the same name as user_name.
**2. Supplementary Group**	Users might also have supplementary group. Additional groups that a user can be part of. Grants access to specific files, directories, or system resources.
**3. System Groups**	Used for system level permissions (eg: sudo, docker, adm).

## To view the users and group details: 
```
cat /etc/passwd
cat /etc/group
```
## Other cmds:
1. To show the info. about current user: ```id```
2. To show the info. about that user: ```id username```
4. To show the owner of that file: ```ls -l```
5. To show the owner of that directory: ```ls -ld```
6. To show process information: ```ps -au```
-a = view all process
-u = view all the user that is associated with a process.

## Switch Accounts:
1. To switch to root:
```
su -
sudo -i
```
3. To switch to userAccount:
```
su - username
```

## Configure Sudo
1. The **/etc/sudoers** file is the main configuration file for the sudo command.
2. By default, the **/etc/sudoers** file also includes the contents of any files in the **/etc/sudoers.d** directory as part of the configuration file.
3. To enable full **sudo** access for user1, you can create the **/etc/sudoers.d/user1** file with the following content:
```
user1 ALL=(ALL) ALL
```
user1: The username this rule applies to.
ALL: The rule applies on all hosts (mostly relevant in multi-host configurations with shared sudoers).
(ALL): user1 can run commands as any user (including root).
ALL: user1 can run all commands.

5. For Group: Create **/etc/sudoers.d/group1** with contents:
```
%group1 ALL=(ALL) ALL
```
7.  

