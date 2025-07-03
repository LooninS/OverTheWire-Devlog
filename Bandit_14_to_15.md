# Bandit Level 14 → Level 15

## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

***

## Commands Used

- `echo`: Used to output the current password.
- `nc` (netcat): Used to establish a network connection and send data.

***

## Approach

1.  **Obtain Current Password:** Get the password for the current Bandit level (Bandit 14).
2.  **Send Password to Port:** Use `echo` to print the current password and pipe its output to `nc` (netcat). `nc` will then connect to `localhost` on port `30000` and send the password.
3.  **Retrieve Next Password:** The server on port 30000 will respond with the password for the next level (Bandit 15).

Example command:
```bash
echo <current_password> | nc localhost 30000
```

***

## Key Concepts

- **Netcat (`nc`)**: A versatile networking utility used for reading from and writing to network connections.
- **Piping (`|`)**: Used to redirect the output of one command as the input to another command.
- **`localhost`**: Refers to the local machine, meaning the connection is made to the same computer you are currently on.
