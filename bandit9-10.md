
# Bandit Level 9 → Level 10
## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
***
### Approach
The goal has something to do with strings, so i decided to do `man strings`. 

```markdown
strings - print the sequences of printable characters in files
```

After that I did this 
```bash
bandit9@bandit:~$ strings data.txt
```
And got this output
```bash
l0@P(
,k=?
tIsrQ
k`Dl5
....
```
The strings are preceded by bunch of '==='. Naturally, I use `grep`.
```bash
bandit9@bandit:~$ strings data.txt | grep '==='
```
***

<details>
  <summary>Click to reveal spoiler</summary>

  The password is FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey 
</details>

