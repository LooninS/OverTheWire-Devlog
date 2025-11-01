# Bandit Level 7 → Level 8

## Level Goal

The password for the next level is stored in the file data.txt next to the word millionth

***

## Commands Used

 HEAD
- `ls`: List directory contents
- `file`: Determine file type
- `cat`: Display file contents
- `cat`: Display file contents
- `grep`: Search for patterns in files

***

## Approach

```bash
bandit4@bandit:~$ ls inhere
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07	-file08  -file09
```
There are 10 files in the directory, but only one is human-readable i.e a text file.
I have the option to use a brute force approach to find the password by `cat`ing each file one-by-one, but that is not very efficient.
It's much more efficient to use `file` command to check the type of the file and then use `cat` to view the contents.
```bash
bandit4@bandit:~$ file inhere/-file00
inhere/-file00: PGP Secret Sub-key -
```
Now, let's preform the same operation on all the files in the directory. The `*` wildcard will match all the files in the directory.
```bash
bandit4@bandit:~$ file inhere/*
inhere/-file00: PGP Secret Sub-key -
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
```
Now, let's use `cat` to view the contents of the human-readable file.
```bash
bandit4@bandit:~$ cat inhere/-file07
```

This one is pretty easy. I solved it using `grep` which I have already used to solve previous levels. 
This is my solution:
```bash
bandit7@bandit:~$ cat data.txt  | grep "millionth"
```
The `cat` command display all the contents of `data.txt`, then `|` operator takes the output of cat command and give it to `grep` command, which displays the lline with the word 'millionth'

***

## Key Concepts

- **File Type Identification**: The `file` command is a powerful utility to determine the type of a file, which is more reliable than just relying on file extensions.
- **Wildcards**: The `*` wildcard can be used to match all files in a directory, which is useful for running commands on multiple files at once.
- **Piping (`|`)**: This level reinforces the concept of piping the output of one command as the input to another, a fundamental aspect of shell scripting for data processing.
- **`grep` for Pattern Matching**: The `grep` command is essential for searching and filtering text based on patterns, making it highly useful for extracting specific information from files.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
</details>

>>>>>>> ccf94c3 (standarizing the filenames)
