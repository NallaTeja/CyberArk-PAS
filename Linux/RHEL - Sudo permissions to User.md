Tried to switch from normal user 'teja' to root user, got failed. 

![failed to switch](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e7690da2-831d-4757-8327-43a5601d9f20)

Log in as a Root 
```
su -
```

if the user doen't exist then add the User to the Sudo Group. Here users in the "wheel" group are granted sudo privileges by default.

```
usermod -aG wheel teja
```

To check if the user exists or not enter below command

```
getent passwd teja
```

![getent passwd teja](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4deadf6a-8781-4311-9098-f3127013fbb2)

Verify the User's Group Membership

```
groups Teja
```

![groups Teja](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/662413db-b8d6-4a7f-969a-400e2e7aa92e)


Edit the Sudoers File & add user 'teja'. 
```
visudo
```
Add below line in the sudoer file. save the file by pressing **esc** & **:wq!**
```
teja    ALL=(ALL)       ALL
```
![sudo permission](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/0c7d4003-5bd7-4153-9e9c-2462cbb961a6)

Set a password for the user "teja": (password: Tej@143)
```
passwd Teja
```

Exit from root user. now try to switch from normal user to root user.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/4ff513ef-c4d7-4513-a093-20ca61fb1d95)

Switch to the user "Teja" and test sudo access:
```
su - teja
sudo whoami
```
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/33acc425-c3c1-4fd9-92cf-63480ec26347)
