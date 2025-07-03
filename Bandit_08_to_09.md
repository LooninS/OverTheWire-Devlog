# Bandit Level 5 → Level 6

## Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

***

## Commands Used

- `find`: Search for files in a directory hierarchy
- `man`: Display the manual for a command
- `grep`: Print lines that match patterns
- `cat`: Display file contents

***

## Approach

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

## Key Concepts

- **File Attribute-Based Searching**: This level demonstrates how to search for files based on their metadata (like size and permissions) rather than their name or content. The `find` command is the primary tool for this.
- **Command Chaining and Filtering**: The solution showcases the power of combining commands. The output of `find` is piped to `grep` to filter the results, and the `-exec` option is used to run `file` on the results of `find`. This is a common and powerful pattern in the shell.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
</details>

