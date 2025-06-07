# Bandit Level 2 → Level 3
==========================
## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory.
***
### Approach
If we were to simply use cat command as such
```bash
bandit2@bandit:~$ cat spaces in this filename
```
We get following error
```bash
cat: spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename: No such file or directory
```
This happens because the shell interprets each word separated by spaces as a separate argument. So it's trying to read four different files: spaces, in, this, and filename, none of which exist. To treat it as a single file we can use quotes.

```bash
bandit2@bandit:~$ cat 'spaces in this filename'
```
And we get the password to next level.
***

