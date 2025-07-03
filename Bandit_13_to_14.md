# Bandit Level 13 → Level 14

## Level Goal
The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: `localhost` is a hostname that refers to the machine you are working on.

***

## Commands Used

- `ssh`: Used to log into the next level using the provided private SSH key.

***

## Approach

1.  **Identify the SSH Key:** The level description states that a private SSH key is provided. This key needs to be saved to a file on the local machine.
2.  **Set Permissions:** Ensure the private key file has the correct permissions (e.g., `chmod 600 <key_file>`) to prevent unauthorized access.
3.  **SSH Login:** Use the `ssh` command with the `-i` flag to specify the private key, the username `bandit14`, and the hostname `localhost` (or the appropriate Bandit server address if connecting from outside the wargame environment).
4.  **Retrieve Password:** Once logged in as `bandit14`, read the content of `/etc/bandit_pass/bandit14` to obtain the password for the next level.

***

## Key Concepts

- **SSH Key Authentication**: Understanding how to use a private SSH key for authentication instead of a password.
- **File Permissions (`chmod`)**: The importance of setting correct permissions for sensitive files like private SSH keys.
- **`localhost`**: Understanding that `localhost` refers to the current machine.
