# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several  ‘=’  characters.

***

## Commands Used

- `find`: Search for files in a directory hierarchy
- `cat`: Display file contents
- `strings`: Print the sequences of printable characters in files
- `grep`: Search for patterns in files

***

## Approach

Lets look at "Commands you may need to solve this level". There is a mention of `string` command. Obviously, the next step is to RTFM.

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

***

## Key Concepts
- **Filtering Output with `grep`**: Combining `strings` with `grep` allows for efficient filtering of potentially large outputs, helping to pinpoint relevant information based on specific patterns.
