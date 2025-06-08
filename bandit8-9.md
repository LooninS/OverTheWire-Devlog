# Bandit Level 8 → Level 9
## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
***
### Approach
I have absolutely no idea how to do it and I dont know any of the commands given in "Commands you may need to solve this level" section. 

Naturally, I asked ChatGPT to tell me a little bit about each of them. It seems that `uniq` is closest to what we need. So, I decided to use `man` it. 

```markdown
UNIQ(1)                                                                             

NAME
       uniq - report or omit repeated lines
```
So I went ahead and did
```bash
bandit8@bandit:~$ uniq -u data.txt #-u or --unique only print unique lines
```
But the result is no different from using `cat data.txt`. What went wrong?

Let use man again
```markdown

DESCRIPTION
       Filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output).
```
It seems it can only filter adjacent matching lines, and therefore data.txt  must be sorted first. Obviously for that we use `sort` command 

```bash
bandit8@bandit:~$ sort data.txt
```
Then I piped the output of `sort` to to `uniq` 
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
```
***
<details>
  <summary>Click to reveal spoiler</summary>

  The password is 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
</details>

