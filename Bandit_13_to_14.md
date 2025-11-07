# Bandit Level 13 → Level 14

## Level Goal
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.
***

## Commands Used

- `ssh`: Used to log into the next level using the provided private SSH key.

***

## Approach

It is possible to use a private SSH key for authentication instead of a password. This is useful when you want to log into a server without having to enter a password every time.
````bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
````
Notes: 
- The permission of private key should be `700`
```bash
chmod 700 sshkey.private
```
***

## Key Concepts

- **SSH Key Authentication**: Understanding how to use a private SSH key for authentication instead of a password.
