<<<<<<< HEAD
# Bandit Level 8 → Level 9

## Level Goal

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

***

## Commands Used

- `uniq`: Report or omit repeated lines
- `sort`: Sort lines of text files

***

## Approach

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
```

***

## Key Concepts

- **`uniq` command behavior**: Understanding that `uniq` only operates on *adjacent* lines is crucial. This highlights the importance of reading man pages carefully.
- **Combining `sort` and `uniq`**: To find truly unique lines in a file, `sort` must be used before `uniq` to bring identical lines together.
- **Piping for sequential processing**: This level further demonstrates the power of piping commands to process data sequentially, where the output of one command becomes the input of the next.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
</details>

=======
# Bandit Level 11 
## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
***
## Commands Used
- `tr` - Translate characters command
- 'A-Za-z' - Source set (all letters)
- 'N-ZA-Mn-za-m' - Target set (ROT13 mapping)
    - A-M 
    - N-Z 
    - Same pattern for lowercase
***
## Approach
```bash
bandit11@bandit:~$ cat data.txt  | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
***
## Key Concepts
How it works: Each letter is shifted 13 positions in the alphabet.
    - A 
    - Since alphabet has 26 letters, ROT13 is its own inverse
    - Numbers and symbols remain unchanged
```markdown
Original: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
ROT13:    N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
```
***
<details>
  <summary>Click to reveal spoiler</summary>
    The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
</details>
>>>>>>> ccf94c3 (standarizing the filenames)
