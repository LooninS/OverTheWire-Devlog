<<<<<<< HEAD
# Bandit Level 5 → Level 6

## Level Goal

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable
=======
# Bandit Level 8 → Level 9

## Level Goal

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
>>>>>>> ccf94c3 (standarizing the filenames)

***

## Commands Used

<<<<<<< HEAD
- `find`: Search for files in a directory hierarchy
- `man`: Display the manual for a command
- `grep`: Print lines that match patterns
- `cat`: Display file contents
=======
- `uniq`: Report or omit repeated lines
- `sort`: Sort lines of text files
>>>>>>> ccf94c3 (standarizing the filenames)

***

## Approach

<<<<<<< HEAD
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
=======
I had absolutely no idea how to tackle this one. The "Commands you may need to solve this level" section listed several tools I'd never used before, so I did what any reasonable person would do: I asked ChatGPT to explain each one.
After reading through the explanations, `uniq` seemed like the most promising candidate for finding unique lines. Time to dive deeper with `man uniq`:
```markdown
UNIQ(1)                                                                             

NAME
       uniq - report or omit repeated lines
```
So, I ran `uniq` on the `data.txt` file
```bash
bandit8@bandit:~$ uniq -u data.txt #-u or --unique only print unique lines
```
But wait... the output looked identical to just running `cat data.txt`. What went wrong?
Back to the manual I went, and there was the crucial detail I'd missed:
```markdown

DESCRIPTION
       Filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output).
```
And there is the issue, the `uniq` only works on lines next to each other. So, I had to use `sort` to sort the lines in the file.

```bash
bandit8@bandit:~$ sort data.txt
```
Then I piped the output of `sort` to `uniq` 
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
>>>>>>> ccf94c3 (standarizing the filenames)
```

***

## Key Concepts

<<<<<<< HEAD
- **File Attribute-Based Searching**: This level demonstrates how to search for files based on their metadata (like size and permissions) rather than their name or content. The `find` command is the primary tool for this.
- **Command Chaining and Filtering**: The solution showcases the power of combining commands. The output of `find` is piped to `grep` to filter the results, and the `-exec` option is used to run `file` on the results of `find`. This is a common and powerful pattern in the shell.
=======
- **`uniq` command behavior**: Understanding that `uniq` only operates on *adjacent* lines is crucial. This highlights the importance of reading man pages carefully.
- **Combining `sort` and `uniq`**: To find truly unique lines in a file, `sort` must be used before `uniq` to bring identical lines together.
- **Piping for sequential processing**: This level further demonstrates the power of piping commands to process data sequentially, where the output of one command becomes the input of the next.
>>>>>>> ccf94c3 (standarizing the filenames)

<details>
  <summary>Click to reveal spoiler</summary>

<<<<<<< HEAD
  The password is HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
=======
  The password is 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
>>>>>>> ccf94c3 (standarizing the filenames)
</details>

