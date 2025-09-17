## User Types:
**1. Super User:** Uid is 0.  
**2. System User:** For processes or deamons (uid = 1-999).  
**3. Regular User:** For day to day work (uid > 1000).  

## Groups Types:
**1. Primary Group** is created itself when a new-user is created. It has the same name as user_name.  
**2. Supplementary Group**	Users might also have supplementary group. Additional groups that a user can be part of. Grants access to specific files, directories, or system resources.  
**3. System Groups**	Used for system level permissions (eg: sudo, docker, adm).  

### To view the users and group details: 
```
cat /etc/passwd
cat /etc/group
```

### Manage local Users: 
1. Create/Add a new users:
```
useradd new_username
```
The **/etc/login.defs** file sets some default options for user accounts, suchas range of valid UID numbers and default password aging rules. The change in this file doesnot affect existing users, it affects only the newly created user accounts.  

```
usermod --help
```

##### Example:   
To add a user (bishal) to the supplementary group (docker):
```
usermod -aG docker bishal
```
To verify the user in the group: 
```
groups bishal
```

2. Set Passwords
```
passwd username
```

3. Delete users:
```
userdel user_name
```
(Above cmd removes the username from **/etc/passwd** but leaves the user's home directory intact.)  

To Completely remove the username from **/etc/passwd** as well as its home directory:
```
userdel -r username
```

### Other cmds:
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
2. To switch to userAccount:
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
**%group1**: The % indicates this is a group, not a user. This rule applies to all users who are members of group1.  
**ALL**: The rule applies on all hosts (mainly relevant in environments using the same sudoers file across multiple systems).  
**(ALL)**: Members of group1 can run commands as any user (including root).  
**ALL**: They can run any command.  



### Manage user passwords

Originally, encrypted passwords were stored in the world-reable **/etc/passwd** file. later, the cryptographically hashed passwords were moved to the **/etc/shadow** file which only the root user can read due to dictionary attacks on encrypted passwords became common.  

An example entry from the **/etc/shadow** file has 9 colon-separated fields:
```
cat /etc/shadow
```
Output:
```
A:B:C:D:E:F:G:H:null
```
where,  
A = username  
B = encrypted Password  
C = last passwd change days
D = min. days since last passwd change before user can change it again.  
E = max. days without a passwd change before it expires.  
F = no. of days to warn the user to change passwd.  
G = no. of days without activity.  
H = expiry days 
null = last field is typically empty & is reserved for future use.  


##### Example:
Command to change the user password aging policy:  
```
chage -m 0 -M 90 -w 7 -I 14 <username>
```
Where,  
**-m 0** → Sets the minimum number of days between password changes to 0, meaning the user can change their password at any time.  
**-M 90** → Sets the maximum number of days the password is valid to 90, requiring the user to change their password every 90 days.  
**-w 7** → Sets the warning period to 7 days, meaning the user will start receiving warnings 7 days before the password expires.  
**-I 14** → Sets the inactive period to 14 days, meaning if the password expires and the user does not change it, the account will be disabled 14 days after expiration.


