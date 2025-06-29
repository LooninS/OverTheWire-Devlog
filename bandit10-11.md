# Bandit Level 10 → Level 11
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data
### Approach
```bash
bandit10@bandit:~$ base64 -d data.txt #-d flag decode the encoded text
```
- `base64` - Built-in Linux utility for base64 operations
- `-d` flag - Decode mode (default is encode)
- `data.txt` - Input file
***
## How This Work?
- **Base64 encoding**: It is a method to encode data using 64 character(A-Z, a-z, 0-9, +, /). It often end with `==` or `=`
***

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
</details>

