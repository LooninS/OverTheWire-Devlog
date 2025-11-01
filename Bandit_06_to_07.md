# Bandit Level 6 → Level 7

## Level Goal

The password for the next level is stored somewhere on the server and has all of the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

***

## Commands Used

- `ls`: List directory contents
- `find`: Search for files in a directory hierarchy
- `cat`: Display file contents

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
=======
This is a fun one, instead of searching just one directory, I will have to search the entire file system. There is a minor problem though, I don't have the permissions to search the entire file system. So, when I use `find` command with the required parameters, I am flooded with permission denied errors.
```bash
bandit6@bandit:/$ find . -size 33c -group bandit6 -user bandit7
find: ‘./root’: Permission denied
find: ‘./proc/tty/driver’: Permission denied
find: ‘./proc/1799527/task/1799527/fd/6’: No such file or directory
find: ‘./proc/1799527/task/1799527/fdinfo/6’: No such file or directory
find: ‘./proc/1799527/fd/5’: No such file or directory
find: ‘./proc/1799527/fdinfo/5’: No such file or directory
find: ‘./boot/lost+found’: Permission denied
find: ‘./boot/efi’: Permission denied
find: ‘./etc/polkit-1/rules.d’: Permission denied
find: ‘./etc/sudoers.d’: Permission denied
find: ‘./etc/xinetd.d’: Permission denied
find: ‘./etc/credstore’: Permission denied
...
```
Rather than dealing with all this noise, I decided to suppress the error output entirely. In bash, 2 is the error stream, 1 is the standard output stream and 0 is the standard error stream 1. `> /dev/null`
```bash
bandit6@bandit:/$ find . -size 33c -group bandit6 -user bandit7 2> /dev/null
./var/lib/dpkg/info/bandit7.password
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
```

***

## Key Concepts

- **Hidden Files**: In Linux, files and directories that start with a dot (`.`) are hidden from normal view. The `ls -a` command can be used to display them.
=======
- **File Ownership and Permissions**: This level highlights the importance of file ownership (`user` and `group`) and how it can be used as a search criterion.
- **Redirecting Output**: The `2> /dev/null` command is a useful technique for redirecting error messages (stderr) to `/dev/null`, effectively silencing them and making the output of a command cleaner.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
</details>


