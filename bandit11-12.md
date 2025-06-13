# Bandit Level 11 → Level 12
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data
***
### Approach
The goal is to decode the the ROT13 encoded text `data.txt`. In ROT13, each letter is moved by 13 places i.e A becomes N and B becomes O. 
I'll using `tr` command to translate the encoded text to decoded text. The `tr` command translate/delete the text based on the 
```bash
bandit11@bandit:~$ cat data.txt  | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
'A-Za-z' specifies the set of characters to be translated. 
'N-ZA-Mn-za-m' specifies the corresponding characters to which the characters in the first set will be translated.
***
<details>
  <summary>Click to reveal spoiler</summary>
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
</details>
