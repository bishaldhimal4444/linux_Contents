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
