# Bandit Level 2 → Level 3

## Level Goal

The password for the next level is stored in a file called spaces in this filename located in the home directory.

***

## Commands Used

- `base64`: Built-in Linux utility for base64 operations
=======
- `cat`: Display file contents

***

## Approach

```bash
base64 -d data.txt
=======
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

## Key Concepts

- **Base64 Encoding/Decoding**: Understanding Base64 as a common encoding scheme for binary data, often used for transmitting data over mediums that only support text. The `base64` command provides a straightforward way to encode and decode such data.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
</details>
=======
- **Shell Argument Parsing**: The shell interprets spaces as delimiters for arguments. To treat a string with spaces as a single argument, it must be enclosed in quotes (e.g., `'filename with spaces'`).
>>>>>>> ccf94c3 (standarizing the filenames)
