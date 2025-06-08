# Bandit Level 6 → Level 7
## Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size
***

### Approach
I will be taking a similar approach to last one by using the `find` command. The given file can lie anywhere on the server is 33 bytes in size, owned by user `bandit7` and group `bandit6`. Therefore, let do this in this root directory.
```bash
bandit6@bandit:/$ find . -size 33c -group bandit6 -user bandit7
```
But, now I get this output
```shell
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
I could just go through this manually or just remove all output containing an error. I will chose the latter.
```bash
bandit6@bandit:/$ find . -size 33c -group bandit6 -user bandit7 2> /dev/null
```
In  bash, 2 is used for STDERR(Standard Error), 1 is for STDOUT(Standard Output) and 0 is for STDIN(Standard Input) and `/dev/null` is basically a null device ie it doesnt exist. So, `2> /dev/null` is redirecting the STDERR to a null device. Finally, we get this output.
```bash
./var/lib/dpkg/info/bandit7.password
```
***
<details>
  <summary>Click to reveal spoiler</summary>

  The password is morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
</details>


