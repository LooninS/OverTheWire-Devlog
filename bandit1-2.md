# Bandit Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory
***
## Approach
Naturally, I went with the method I used previously.
```bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat -
```
Why does it not work the file is right there, I even checked it with `ls`.
For many commands, `command -` means "read from STDIN" and when the terminal see `-` is thinks, "Ah, it's a option. not a filename"
So, how did I actually get it to work? There are lots of ways I found these:

1. Using `./` will explicitly tell the shell, "this is a path" 
    ```bash 
    cat ./-
    ```
2. Using `--` can also work like so
    ```bash
    cat -- -
    ```
