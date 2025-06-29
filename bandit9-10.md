
# Bandit Level 9 → Level 10
## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
***
### Approach
The mention of strings in the level ;made me think of `strings` command. Obviously, the next step is to RTFM

```markdown
strings - print the sequences of printable characters in files
```

Sounds like a good candidate for the job. I ran `strings` on the `data.txt` file.
```bash
bandit9@bandit:~$ strings data.txt
l0@P(
,k=?
tIsrQ
k`Dl5
....
```
The output was a bit overwhelming, so I decided to pipe the output to `grep` to filter out the lines that contained the password.
```bash
bandit9@bandit:~$ strings data.txt | grep '==='
```
## Learning Points
- The `strings` command is a powerful tool for finding strings in files
- The `grep` command is a powerful tool for filtering lines in files
***

<details>
  <summary>Click to reveal spoiler</summary>

  The password is FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey 
</details>

