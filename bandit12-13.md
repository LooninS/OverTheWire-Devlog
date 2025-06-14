# Bandit Level 12 → Level 13
## Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
***
### Approach
This level is the longests till now. Let's make a tempoary directory and copy the datafile there, as we dont have the permissions to make new files. 
```bash
bandit12@bandit:~$ mktemp -d
/tmp/tmp.1R5Z6bTAnG
bandit12@bandit:~$ cd /tmp/tmp.1R5Z6bTAnG
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ cp /home/bandit12/data.txt .
```
Now, we know that data.txt contain a hexdump so lets use `xxd` to reverse hexdump to binary.
```bash
bandit12@bandit:~$ xdd -r data.txt > data2
```
Now, let  check whats the filetype
```bash
bandit12@bandit:~$ file data2
data2: gzip compressed data, was "data2.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 585
```
Now, lets do uncompress the file
```bash
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data2 data2.gz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ gzip -d data2.gz
```
Now, lets check the filetype again
```bash
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file data2
data2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data2 data3.bz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ bzip2 -d data3.bz
```
Reapeat this few more times till
```bash
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file daata
daata: ASCII text
```

<details>
  <summary>Click to reveal spoiler</summary>
    The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
</details>
