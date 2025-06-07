# Bandit Level 0 → Level 1
## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
***
## Approach
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220 #login to the level
```
In each of the level we have to find the file containing password to next level. The name of given file in this level is readme. 
Let use cat to view the contents of the readme file.
```bash
cat readme
```
***

