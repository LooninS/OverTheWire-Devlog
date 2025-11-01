# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
>>>>>>> ccf94c3 (standarizing the filenames)

***

## Commands Used

<<<<<<< HEAD
- `find`: Search for files in a directory hierarchy
- `cat`: Display file contents
=======
- `strings`: Print the sequences of printable characters in files
- `grep`: Search for patterns in files
>>>>>>> ccf94c3 (standarizing the filenames)

***

## Approach

<<<<<<< HEAD
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
=======
The mention of strings in the level made me think of `strings` command. Obviously, the next step is to RTFM

```markdown
strings - print the sequences of printable characters in files
```

Sounds like a good candidate for the job. I ran `strings` on the `data.txt` file.
```bash
bandit9@bandit:~$ strings data.txt
l0@P(
,k=?
tIsrQ
k`Dl5
....
```
The output was a bit overwhelming, so I decided to pipe the output to `grep` to filter out the lines that contained the password.
```bash
bandit9@bandit:~$ strings data.txt | grep '==='
>>>>>>> ccf94c3 (standarizing the filenames)
```

***

## Key Concepts

<<<<<<< HEAD
- **File Ownership and Permissions**: This level highlights the importance of file ownership (`user` and `group`) and how it can be used as a search criterion.
- **Redirecting Output**: The `2> /dev/null` command is a useful technique for redirecting error messages (stderr) to `/dev/null`, effectively silencing them and making the output of a command cleaner.
=======
- **Extracting Human-Readable Strings**: The `strings` command is invaluable for extracting human-readable text from binary files or files with mixed content, which is often a crucial step in analyzing unknown data.
- **Filtering Output with `grep`**: Combining `strings` with `grep` allows for efficient filtering of potentially large outputs, helping to pinpoint relevant information based on specific patterns.
>>>>>>> ccf94c3 (standarizing the filenames)

<details>
  <summary>Click to reveal spoiler</summary>

<<<<<<< HEAD
  The password is morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
</details>


=======
  The password is FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey 
</details>

>>>>>>> ccf94c3 (standarizing the filenames)
