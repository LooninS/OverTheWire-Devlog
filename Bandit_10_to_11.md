# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file data.txt, which contains base64-encoded data.

***

## Commands Used

- `cat`: Display file contents
- `grep`: Search for patterns in files
- `base64`: Built-in Linux utility for base64 operations

***

## Approach

This one is pretty easy. I solved it using `grep` which I have already used to solve previous levels. 
This is my solution:
```bash
bandit7@bandit:~$ cat data.txt  | grep "millionth"
```
The `cat` command display all the contents of `data.txt`, then `|` operator takes the output of cat command and give it to `grep` command, which displays the lline with the word 'millionth'
=======
```bash
base64 -d data.txt
```
***

## Key Concepts

- **Piping (`|`)**: This level reinforces the concept of piping the output of one command as the input to another, a fundamental aspect of shell scripting for data processing.
- **`grep` for Pattern Matching**: The `grep` command is essential for searching and filtering text based on patterns, making it highly useful for extracting specific information from files.
- **Base64 Encoding/Decoding**: Understanding Base64 as a common encoding scheme for binary data, often used for transmitting data over mediums that only support text. The `base64` command provides a straightforward way to encode and decode such data.
***
