# Bandit Level 7 → Level 8

## Level Goal

The password for the next level is stored in the file data.txt next to the word millionth

***

## Commands Used

- `cat`: Display file contents
- `grep`: Search for patterns in files

***

## Approach

This one is pretty easy. I solved it using `grep` which I have already used to solve previous levels. 
This is my solution:
```bash
bandit7@bandit:~$ cat data.txt  | grep "millionth"
```
The `cat` command display all the contents of `data.txt`, then `|` operator takes the output of cat command and give it to `grep` command, which displays the lline with the word 'millionth'

***

## Key Concepts

- **Piping (`|`)**: This level reinforces the concept of piping the output of one command as the input to another, a fundamental aspect of shell scripting for data processing.
- **`grep` for Pattern Matching**: The `grep` command is essential for searching and filtering text based on patterns, making it highly useful for extracting specific information from files.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
</details>

