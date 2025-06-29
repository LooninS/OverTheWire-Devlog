# Bandit Level 3 → Level 4
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.
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


