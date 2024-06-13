
# Switching to Root User and Granting Sudo Privileges

### 1. Attempt to Switch to Root User

I tried to switch from the normal user 'teja' to the root user but failed.

![Failed to Switch](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e7690da2-831d-4757-8327-43a5601d9f20)

### 2. Log in as Root

First, log in as the root user:

```sh
su -
```

### 3. Check if the User Exists

If the user doesn't exist, add the user to the sudo group. In RHEL, users in the "wheel" group are granted sudo privileges by default.

To check if the user exists, enter the following command:

```sh
getent passwd teja
```

![Check User Existence](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4deadf6a-8781-4311-9098-f3127013fbb2)

### 4. Add the User to the Sudo Group

If the user exists, add the user "teja" to the "wheel" group:

```sh
usermod -aG wheel teja
```

### 5. Verify the User's Group Membership

Verify that the user "teja" has been added to the correct group:

```sh
groups teja
```

![Verify Group Membership](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/662413db-b8d6-4a7f-969a-400e2e7aa92e)

### 6. Edit the Sudoers File

Edit the sudoers file to ensure the user "teja" has sudo privileges:

```sh
visudo
```

Add the following line to the sudoers file and save it by pressing **esc** followed by **:wq!**:

```sh
teja    ALL=(ALL)       ALL
```

![Edit Sudoers File](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0c7d4003-5bd7-4153-9e9c-2462cbb961a6)

### 7. Set a Password for the User "teja"

Set a password for the user "teja" (example password: Tej@143):

```sh
passwd teja
```

### 8. Switch to the User "teja" and Test Sudo Access

Switch to the user "teja" and test sudo access:

```sh
su - teja
sudo whoami
```

![Test Sudo Access](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/33acc425-c3c1-4fd9-92cf-63480ec26347)

If everything is configured correctly, the output should be `root`, indicating successful sudo access.
