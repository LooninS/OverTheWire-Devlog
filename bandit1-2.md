# Bandit Level 1 → Level 2

## Level Goal
The password for the next level is stored in a file called - located in the home directory
***
## Approach
Let try doing the same thing we did last time:
```bash
cat - 
```
But this doesnt seem to work. Why?

The `-` interpreted as a cmd-line option by the shell, not as a filename, similar to how -p(to specify port) used during ssh. So using `cat -` tells cat that  to read STDIN instead of the filename.

But how do we get it to actully work?

**Using relative path** will tell the shell to treat `-` as a filename instead of option.

```bash 
cat ./-
```
***
