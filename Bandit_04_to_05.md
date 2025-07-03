<<<<<<< HEAD
# Bandit Level 12 → Level 13
## Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
***
## Commands Used

**File Analysis**

- `file filename` - Determines file type
- `xxd -r filename` - Reverse hexdump to binary

**Compression Tools**

- `gzip -d filename.gz` - Decompress gzip files
- `bzip2 -d filename.bz2` - Decompress bzip2 files
- `tar -xf filename.tar` - Extract tar archives

**File Management**

- `mv oldname newname` - Rename files
- `cp source destination` - Copy files
- `mktemp -d` - Create temporary directory
***
## Key Concepts
- **File Decompression:** This level involves multiple layers of compression. The key is to use the `file` command to identify the compression type (gzip, bzip2, tar) and then use the appropriate tool (`gzip -d`, `bzip2 -d`, `tar -xf`) to decompress it.
- **Hexdump:** The initial file is a hexdump. `xxd -r` is used to revert the hexdump back to its binary representation.
- **Temporary Directories:** Using `/tmp` with `mktemp -d` is a standard practice for creating a temporary workspace.
***
## Approach
Since I don't have write permissions in the home directory, I need to work in /tmp and copy the file to /tmp:
```bash
bandit12@bandit:~$ mktemp -d
/tmp/tmp.1R5Z6bTAnG
bandit12@bandit:~$ cd /tmp/tmp.1R5Z6bTAnG
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ cp /home/bandit12/data.txt .
```
The file is a hexdump, so I need to reverse it back to binary format
```bash
bandit12@bandit:~$ xxd -r data.txt > data2
```
Now I start the process of identifying and decompressing the file
```bash
bandit12@bandit:~$ file data2
data2: gzip compressed data, was "data2.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 585
```
Now, lets do uncompress the file
```bash
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data2 data2.gz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ gzip -d data2.gz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file data2
data2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data2 data3.bz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ bzip2 -d data3.bz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file data2
data2: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data2 data3.bz2
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ bzip2 -d data3.bz2
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file data3
data3: gzip compressed data, was "data4.bin", last modified: Thu Apr 10 14:22:57 2025, max compression, from Unix, original size modulo 2^32 20

bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ mv data3 data4.gz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ gzip -d data4.gz
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file data4
data4: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ tar -xf data4
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ ls
data4  data5.bin
```
Repeat these steps few more times till
```bash
bandit12@bandit:/tmp/tmp.1R5Z6bTAnG$ file daata
daata: ASCII text
```
***
<details>
  <summary>Click to reveal spoiler</summary>
    The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
</details>
=======
# Bandit Level 4 → Level 5

## Level Goal

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

***

## Commands Used

- `ls`: List directory contents
- `file`: Determine file type
- `cat`: Display file contents

***

## Approach

```bash
bandit4@bandit:~$ ls inhere
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07	-file08  -file09
```
There are 10 files in the directory, but only one is human-readable i.e a text file.
I have the option to use a brute force approach to find the password by `cat`ing each file one-by-one, but that is not very efficient.
It's much more efficient to use `file` command to check the type of the file and then use `cat` to view the contents.
```bash
bandit4@bandit:~$ file inhere/-file00
inhere/-file00: PGP Secret Sub-key -
```
Now, let's preform the same operation on all the files in the directory. The `*` wildcard will match all the files in the directory.
```bash
bandit4@bandit:~$ file inhere/*
inhere/-file00: PGP Secret Sub-key -
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
```
Now, let's use `cat` to view the contents of the human-readable file.
```bash
bandit4@bandit:~$ cat inhere/-file07
```

***

## Key Concepts

- **File Type Identification**: The `file` command is a powerful utility to determine the type of a file, which is more reliable than just relying on file extensions.
- **Wildcards**: The `*` wildcard can be used to match all files in a directory, which is useful for running commands on multiple files at once.
>>>>>>> ccf94c3 (standarizing the filenames)
