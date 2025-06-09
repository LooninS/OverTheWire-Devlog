# Bandit Level 10 → Level 11
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data
***
### Approach
The goal is to decode the the base64 encoded text in data.txt, I used the base64 command. 
```bash
bandit10@bandit:~$ man base64
bandit10@bandit:~$ base64 -d data.txt #-d flag decode the base64 txt
```
***
<details>
  <summary>Click to reveal spoiler</summary>
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
</details>
