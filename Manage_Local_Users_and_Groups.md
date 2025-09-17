# User Types:
```
1. Super User: Uid is 0.
2. System User: For processes or deamons (uid = 1-999).
3. Regular User: For day to day work (uid > 1000).
```
# Groups Types:
1. Primary Group is created itself when a new-user is created. It has the same name as user_name.
2. Supplementary Group	Users might also have supplementary group. Additional groups that a user can be part of. Grants access to specific files, directories, or system resources.
3. System Groups	Used for system level permissions (eg: sudo, docker, adm).

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

