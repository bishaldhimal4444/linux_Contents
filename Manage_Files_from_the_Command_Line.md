# Linux File System Hierarchy / Linux Directories:  
**/boot:**	Files to start the boot process.    
***/root:***	Home directory of super or root.  
	
**/home:**	Home directory, where regular users stores their data and files.  
**/etc:**	System-specific configuration files.  
**/var:**	Files that dynamically  change, such as db, cache directories, log files, website content.  
**/tmp:**	Files that are not accessed, changed, or modified for 10 days are deleted from this directory automatically.  
	
**/run:**	Includes data’s about process ID files and lock files.  
**/usr:**	Includes files, read-only program data, installed software and shared libraries.  
**/dev:**	Special device files that the system uses to access hardware.  


# Linux Important Sub-directories:
**/etc/passwd:** To view all users.  
**/etc/sudoers:**	Main configuration file for the sudo command.  
**/etc/sudoers.d/user1:**	To enable full sudo access for user1: [ user1 ALL=(ALL) ALL ]  
**/etc/sudoers.d/group1:**	To enable full sudo access for group1 users: [ %group1 ALL=(ALL) ALL ]  
**/etc/login.defs:**	Sets some default options for user accounts, such as range of valid uid numbers, and default password aging rules. The change in this file does not affect existing users, it only affects the newly created user accounts.

## Absolute Path vs. Relative Path
**Absolute Path:** Always refers to the same location and starts from the root. It's longer but unambiguous.  
**Relative Path:** Depends on your current location in the file system and is shorter but context-sensitive.


### Joining cmd's:
```
mkdir dir1; cd dir1
mkdir folder{1,2,3}
echo file{1..3}.txt
var_name=value; echo $var_name
```
