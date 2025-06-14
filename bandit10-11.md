# Bandit Level 10 → Level 11
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data
### Approach
I'll be using `base64` command to get the password from the encoded text file.
```bash
bandit10@bandit:~$ base64 -d data.txt #-d flag decode the encoded text
```
***

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
</details>

