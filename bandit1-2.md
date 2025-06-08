# Bandit Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory
***
## Approach
Naturally, I went with the method I used previously.
```bash
cat - 
```
But this doesnt seem to work. Why?

The `-` interpreted as a cmd-line option by the shell, not as a filename, similar to how -p(to specify port) used during ssh. So using `cat -` tells cat that  to read STDIN instead of the filename.

So, how did I actually get it to work?

**Using relative path** will tell the shell to treat `-` as a filename instead of option.

```bash 
cat ./-
```
***
