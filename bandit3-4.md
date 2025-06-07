# Bandit Level 3 → Level 4
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.
***
### Approach
Hidden files are files that often start with a period(.) and hidden in most fileviewer. So, lets use the `ls`(it list the content of a directory) command as such:
```bash
bandit3@bandit:~$ ls inhere
```
But don't get any output. Does that mean there are no files in 'inhere' directory?
No, if we were to use the -a(for all) flag, we get the following:
```bash
bandit3@bandit:~$ ls -a inhere
.  ..  ...Hiding-From-You
```
Now, let just cat the file. Did you know, `cat` stands for concatenate and `ls` stand for list?
```bash
bandit3@bandit:~$ cat inhere/...Hiding-From-You
```
***

