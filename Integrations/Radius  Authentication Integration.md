# Setting Static IP of RHEL9 OS Server 
![changing Dynamic IP to Static IP](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/8877814b-905b-4687-b39d-f7f8bb36cef6)

```
[ipv4]
method=manual
addresses=192.168.5.140/24
gateway=192.168.5.1
dns=8.8.8.8;8.8.4.4;
```
![Static iP input](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/92b0d6cc-b378-4871-8c8e-2f2a587f357c)

```
sudo nmcli connection reload
sudo nmcli connection down ens160
sudo nmcli connection up ens160
sudo systemctl restart NetworkManager
```
![Excecuted above cmd](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/b6b6b430-ad90-4562-9566-0fb6f69e97b2)

# Setting hostname of RHEL9 OS Server 
Use the hostnamectl command to set the correct hostname:

```
sudo hostnamectl set-hostname RadiusRHEL09
```
Edit the /etc/hostname file:

Open the file with a text editor:

```
sudo vi /etc/hostname
```
Ensure that it contains only RadiusRHEL09:

```RadiusRHEL09```

Save and close the file.

Edit the /etc/hosts file:

Open the /etc/hosts file:

```
sudo vi /etc/hosts
```

Ensure it includes the correct mapping for the hostname:

```
127.0.0.1   localhost RadiusRHEL09
::1         localhost RadiusRHEL09
```

Save and close the file.

Restart the NetworkManager and verify the hostname:

```
sudo systemctl restart NetworkManager
hostnamectl
```

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1015abff-5a35-48b0-8229-d7c8c4ca6333)

# Setting up Radius server and integrating to cyberark

Stop privateark service in primary vault server then update radius secret file via CAVault Manager by excecuting below cmd
```
CAVaultManager SecureSecretFiles /secretType Radius /Secret Tej@143 /SecuredFileName radiussecret.dat
```
![PVault CAVault Manager secret](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1b69763b-885a-426e-9234-7a58cfff8477)

dbparm radius server info updated
```
[Radius]
RadiusServerInfo=192.168.5.140;vault1;radiussecret.dat
```

![dbparm radius server info](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1cb4c077-9161-4bbd-ae76-b6953dff55b6)


