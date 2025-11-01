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

