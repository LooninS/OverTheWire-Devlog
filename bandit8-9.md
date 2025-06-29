# Bandit Level 8 → Level 9
## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
***
### Approach
I had absolutely no idea how to tackle this one. The "Commands you may need to solve this level" section listed several tools I'd never used before, so I did what any reasonable person would do: I asked ChatGPT to explain each one.
After reading through the explanations, `uniq` seemed like the most promising candidate for finding unique lines. Time to dive deeper with `man uniq`:
```markdown
UNIQ(1)                                                                             

NAME
       uniq - report or omit repeated lines
```
So, I ran `uniq` on the `data.txt` file
```bash
bandit8@bandit:~$ uniq -u data.txt #-u or --unique only print unique lines
```
But wait... the output looked identical to just running `cat data.txt`. What went wrong?
Back to the manual I went, and there was the crucial detail I'd missed:
```markdown

DESCRIPTION
       Filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output).
```
And there is the issue, the `uniq` only works on lines next to each other. So, I had to use `sort` to sort the lines in the file.

```bash
bandit8@bandit:~$ sort data.txt
```
Then I piped the output of `sort` to `uniq` 
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
```
***
<details>
  <summary>Click to reveal spoiler</summary>

  The password is 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
</details>

