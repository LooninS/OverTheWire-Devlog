# Bandit Level 5 → Level 6
## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable
***
### Approach
The `find` command is used to find files/directories. But since I have no idea how to use it so
```bash
bandit5@bandit:~$ man find
```
So, our file is 1033 byte and non executable. This is rather easy to check using `-size`(to check size) and `-executable`(to check if it's executable) flags. The `!` is the neg operator.
```bash
bandit5@bandit:~$ find . -type f -size 1033c ! -executable
./inhere/maybehere07/.file2
```
Well, that was easy. It seem checking only two parameter were enough. Lets verify it anyway.
```bash
bandit5@bandit:~$ find . -type f -size 1033c ! -executable -exec file {} + | grep "text"
./inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```
Here, `-exec file {} +` runs the `file` command over the output of the `find` command and output the filetypes anf `| grep "text"` "text": filters the output of file to only show entries that contain the word “text”. Now, we know that `./inhere/maybehere07/.file2` is human-readable, 1033 bytes and non-executable. All that's let to done is to `cat` the file
```bash
bandit5@bandit:~$ cat ./inhere/maybehere07/.file2
```
***
<details>
  <summary>Click to reveal spoiler</summary>

  The password is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
</details>

