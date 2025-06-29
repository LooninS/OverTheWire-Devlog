# Bandit Level 2 → Level 3
## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory.
***
## Approach
```bash
bandit2@bandit:~$ cat spaces in this filename
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
```
Shell treats each space-separated word as a different argument.
The solution is to use ''. This tells the shell to treat entire string as a single argument
```bash
bandit2@bandit:~$ cat 'spaces in this filename'
```
***
## Key Takeaway 
*Problem*: Spaces in filenames break shell parsing.

*Solution*: Use quotes to group words into single argument.

*Command*: `cat 'filename with spaces'`
***
