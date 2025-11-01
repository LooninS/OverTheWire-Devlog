# Bandit Level 11 -> 12
## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
***
## Commands Used
- `tr` - It is unix utility for text manipulation used to translate, delete, orr squeeze the characters from STDIN.T
-  In this level we are using only translation i.e replacing each character in a specified set('A-Za-z')  with a corresponding character in another set('N-ZA-Mn-za-m').
***
## Approach
```bash
bandit11@bandit:~$ cat data.txt  | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
***
## Key Concepts
- Learned about how `tr` command works
How ROT13 works: Each letter is shifted 13 positions in the alphabet.
    - Since alphabet has 26 letters, ROT13 is its own inverse
    - Numbers and symbols remain unchanged
```markdown
Original: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
ROT13:    N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
```
***
