# Bandit Level 0 → Level 1

## Level Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

***

## Commands Used

- `ssh`: Secure Shell for remote login
- `ls`: List directory contents
- `pwd`: Print working directory
- `cat`: Display file contents
- `exit`: Exit current shell session

***

## Approach

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```
In each level, we have to find the file containing the password for the next level. The name of the file in this level is `readme`. Let's use `cat` to view the contents of the `readme` file.
```bash
cat readme
```
`cat` is a shell command for writing the content of a file or input stream to STDOUT.

***

## Key Concepts

- **SSH Connection**: Always use port 2220 for Bandit challenges
- **File Reading**: Multiple ways exist to read the contents of a file in Linux
- **Password Format**: Bandit passwords are typically 32-character alphanumeric strings
- **Home Directory**: The ~ symbol represents the user's home directory
