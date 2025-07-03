# Bandit Level 11 
## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
***
## Commands Used
- `tr` - Translate characters command
- 'A-Za-z' - Source set (all letters)
- 'N-ZA-Mn-za-m' - Target set (ROT13 mapping)
    - A-M 
    - N-Z 
    - Same pattern for lowercase
***
## Approach
```bash
bandit11@bandit:~$ cat data.txt  | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
***
## Key Concepts
How it works: Each letter is shifted 13 positions in the alphabet.
    - A 
    - Since alphabet has 26 letters, ROT13 is its own inverse
    - Numbers and symbols remain unchanged
```markdown
Original: A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
ROT13:    N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
```
***
<details>
  <summary>Click to reveal spoiler</summary>
    The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
</details>
