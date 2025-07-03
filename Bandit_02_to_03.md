# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file data.txt, which contains base64-encoded data.

***

## Commands Used

- `base64`: Built-in Linux utility for base64 operations

***

## Approach

```bash
base64 -d data.txt
```

***

## Key Concepts

- **Base64 Encoding/Decoding**: Understanding Base64 as a common encoding scheme for binary data, often used for transmitting data over mediums that only support text. The `base64` command provides a straightforward way to encode and decode such data.

<details>
  <summary>Click to reveal spoiler</summary>

  The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr 
</details>
