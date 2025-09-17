# Interpret linux File System Permissions
**read(r):** 4  
**write(w):** 2  
**execute(x):**	1  

# Manage File System Permissions from the command line:
```
chmod <who/what/which> <file/directory>
```
**Who** =	User(u), group(g), other(o), and all(a).  
**What** =	Add(+), remove(-), and set exactly(=).  
**Which** = 	Read(r), write(w), execute(x) and special execute (X).  

#### Example:
1. remove r&w permissions for group and other:
```
chmod go-rw document.txt
```
or
```
chmod 600 document.txt
```

2. add r&w permissions for user and group:
```
chmod ug+rw document.txt
```
or
```
chmod 660 document.txt
```

## Change File and Directory User or Group Ownership:
1. To grant ownership of the **app.conf** file to the **student**:
```
chown student app.conf
```
2. To change the group ownership of the **Picture** directory to **admin**:
```
chown :admin Picture
```
3. To change the ownership of the **Picture** directory to the **visitor** user and group to **guests**:
```
chown visitor:guests Picture
```

# Manage Default Permissions and File Access:
1.	Default File Permissions:  
  a.	On creation, a file is assigned initial permissions.	  
  b.	Two factors affect these initial permissions:  
    i.	First is: whether you are creating a file or directory.	  
    ii.	Second is: the current umask (user file-creation mask)  
  c.	If you create a directory, then its initial octal permisisons are 0777 (drwx rwx rwx)  
  d.	If you create a regular file, then its initial octal permissions are 0666 (-rw -rw -rw).  

2.	Umask:	  
  a.	Umask cmd dispalys the umask value of current shell. 
  b.	To change the umask value: umask <vlaue>  
##### Example: umask  
##### Output: 0022  
Cmd:
```
mkdir dir1 ; ls -ld dir1
```
Output: drwxr- xr -x.    2    user    user   0 Jan 7   11:35   dir1  
Here, umask value is 0022, which clears write(w) permissions for group(g) and other(o). So, when the user creates the new directory(dir1), it doesnot include the write(w) permissions for group(g) and other(o).   

4.	Setting Special Permissions:  
  a.	Symbolic:  
    i.	Setuid = u+s (executes files as the user that owns the file)  
    ii.	Setgid = g+s (executes files as the group that owns the file)  
    iii.	Sticky = o+t (users with write access to the directory can remove only files that they own)  
  b.	Octal:  
    i.	Setuid = 4 (u + s)  
    ii.	Setgid = 2 (g + s)  
    iii.	Sticky = 1 (o + t)

##### Example: chmod 2777 read.txt  

