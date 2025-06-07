# Bandit Level 4 → Level 5
## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
***
### Approach
Let check the files inside of inhere directory.
```bash
bandit4@bandit:~$ ls inhere
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07	-file08  -file09
```
We can simply `cat` eaach file one-by-one but that's a brute force solution. So, what else can we do? 
We also know that the file is human-readable i.e. a text file. We can use the `file` command to check the filetype of each file.
```bash
bandit4@bandit:~$ file inhere/-file00
inhere/-file00: PGP Secret Sub-key -
```
We can also perform the operation recursively.
```bash
bandit4@bandit:~$ file inhere/*
inhere/-file00: PGP Secret Sub-key -
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
```
Use `cat` with the either the relative path or full path.
```bash
bandit4@bandit:~$ cat inhere/-file07
```
