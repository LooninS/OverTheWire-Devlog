# Bandit Level 3 → Level 4

## Level Goal

The password for the next level is stored in a hidden file in the inhere directory.

***

## Commands Used

- `ls`: List directory contents

***

## Approach

```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ ls inhere
```
Hmm, there is nothing there...or the files are just hidden. The files start with `.` are invisible to the normal `ls` 
```bash
bandit3@bandit:~$ ls -a
```
**Fun Fact**: `ls`=list and `cat`=concatenate

***

## Key Concepts

- **Hidden Files**: In Linux, files and directories that start with a dot (`.`) are hidden from normal view. The `ls -a` command can be used to display them.


