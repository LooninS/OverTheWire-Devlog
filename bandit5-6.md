# Bandit Level 5 → Level 6
## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable
***
### Approach
Started completely blind on the `find` command syntax. Time to RTFM.
```bash
bandit5@bandit:~$ man find
```
After reading the manual, I identified the following parameters:

- `-type f` – find files
- `-size 1033c` – find files that are 1033 bytes in size
- `-executable` – find files that are executable
- `!` – negate the next parameter
Launched the search with minimal parameters:
```bash
bandit5@bandit:~$ find . -type f -size 1033c ! -executable
./inhere/maybehere07/.file2
```
It's seem two parameters were enough to find the file, but let's verify that the file is indeed human-readable.
```bash
bandit5@bandit:~$ find . -type f -size 1033c ! -executable -exec file {} + | grep "text"
./inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```
The `-exec file {} +` runs the `file` command over the output of the `find` command and output the filetypes and `| grep "text"` "text": filters the output of file to only show entries that contain the word “text”. It's clear that the file is human-readable, non-executable, and is exactly 1033 bytes in size.
```bash
bandit5@bandit:~$ cat ./inhere/maybehere07/.file2
```
***
<details>
  <summary>Click to reveal spoiler</summary>

  The password is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
</details>

