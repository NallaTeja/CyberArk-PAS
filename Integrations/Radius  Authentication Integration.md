Reference link: 
```
https://docs.secureauth.com/2104/en/pam-radius-installation-and-configuration-guide.html
```

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
Login as root user
```
su root
```
Enter password
```
Tej@143
```
Enable the epel 

```
sudo yum install epel-release
```
![Enable epel](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/ce7535bb-c5f8-4958-8943-8c5330658115)

if you get "No match for argument" execute below cmd
```
sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```
![rpm](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6ac19e47-b02f-478e-a04b-2843cb72e10b)

clean up the caches
```
sudo yum clean all
```
Go to yum.repos.d 
```
cd /etc/yum.repos.d/
```
open the list you can see below output.

```
ls -la
```

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/df6dddb5-79fe-4c73-8514-1c6a8445e05b)


sudo yum check
sudo yum update
```
yum install pam_radius
```
```
[root@localhost yum.repos.d]# yum install pam_radius
Updating Subscription Management repositories.
Last metadata expiration check: 0:01:14 ago on Wed 12 Jun 2024 11:53:34 AM IST.
Dependencies resolved.
============================================================================================================================================================================
 Package                                    Architecture                           Version                                       Repository                            Size
============================================================================================================================================================================
Installing:
 pam_radius                                 x86_64                                 1.4.0-4.el7                                   epel                                  29 k

Transaction Summary
============================================================================================================================================================================
Install  1 Package

Total download size: 29 k
Installed size: 60 k
Is this ok [y/N]: y
Downloading Packages:
pam_radius-1.4.0-4.el7.x86_64.rpm                                                                                                            76 kB/s |  29 kB     00:00    
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                        14 kB/s |  29 kB     00:02     
Extra Packages for Enterprise Linux 7 - x86_64                                                                                              1.6 MB/s | 1.6 kB     00:00    
Importing GPG key 0x352C64E5:
 Userid     : "Fedora EPEL (7) <epel@fedoraproject.org>"
 Fingerprint: 91E9 7D7C 4A5E 96F1 7F3E 888F 6A2F AEA2 352C 64E5
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
Is this ok [y/N]: y
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                                                                                    1/1 
  Installing       : pam_radius-1.4.0-4.el7.x86_64                                                                                                                      1/1 
  Running scriptlet: pam_radius-1.4.0-4.el7.x86_64                                                                                                                      1/1 
  Verifying        : pam_radius-1.4.0-4.el7.x86_64                                                                                                                      1/1 
Installed products updated.

Installed:
  pam_radius-1.4.0-4.el7.x86_64
```

Edit the `pam_radius.conf` file

```
vi /etc/pam_radius.conf
```

```
# server[:port] shared_secret      timeout (s)
127.0.0.1       secret             1
other-server    other-secret       3
```

Update the sshd file

```
vi /etc/pam.d/sshd
```
```
#%PAM-1.0
auth       sufficient      pam_radius_auth.so
```
create a directory `raddb`
```
mkdir /etc/raddb
```

Edit the `Clients.conf` file

```
vi /etc/raddb/clients.conf
```

```
client vault1 {
    ipaddr = 192.168.5.129
    secret = Tej@143
    require_message_authenticator = no
}

```

yum install -y freeradius-utils

vi /etc/pam_radius.conf
```
192.168.122.36  testing123       3
```
useradd bob

Stop privateark service in primary vault server then update radius secret file via CAVault Manager by excecuting below cmd
```
CAVaultManager SecureSecretFiles /secretType Radius /Secret Tej@143 /SecuredFileName radiussecret.dat
```
![PVault CAVault Manager secret](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1b69763b-885a-426e-9234-7a58cfff8477)

In dbparm.ini file radius server info is updated.

```
[Radius]
RadiusServersInfo=192.168.5.140;1812;vault1;radiussecret.dat
```
![RadiusServersInfo](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d2315761-2ee0-4729-ad11-82c2e0e77d0d)



Now start the privateark service and Cyberark ENE service. Loin into the 'privateark client' need create user in vault to map the radius account `bob`.

![vault Newuser bob](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/569f5c02-3695-477d-a9d7-2fea55171977)

Change authentication method 'RADIUS Authentication' for 'bob' user. click ok Account will be created.
![Radius Authentication](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/94315fda-056b-42b7-bb5b-a0da3e53c7de)

login PVWA UI with administrator cred and enable Radius Authentication. Go to 'Administration' select 'option'

![Administration](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/f3647a44-f8c7-4440-9a14-6ae01cc1cb90)

Go to Authentiation Methods>Radius. Give the vaule 'Enabled=Yes' click apply and ok.

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/64a4a616-3707-4b58-b057-0344aeacfa56)

After signing out from pvwa UI you can see radius authentication. 
![pvwa radius authentication](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/41141fb6-0ba6-44e8-ac4f-4442a5eb4cac)

click 'radius' and give bob user creds and login
not able to login checked Privateark server getting below error. (from radius server authentication is not happening)

"ITATS539E RADIUS authentication failure for user. (Diagnostic information: 14, 0)".

# Trobleshooting radius server steps: 

Check the status of the radiusd service:
```
sudo systemctl status radiusd.service
```

excecuted the below cmd, no entries found.
```
sudo journalctl -u radiusd
```
![no entries](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a57dadda-ed86-44d3-8520-a7e05d3a0a46)


Check radiusd.conf file. Example check the configuration are enabled like below
```
log {
    destination = files
    file = /var/log/radius/radius.log
    syslog_facility = daemon
    stripped_names = no
    auth = yes
    auth_badpass = yes
    auth_goodpass = yes
}
```
cmd
```
vi /etc/raddb/radiusd.conf
```
Edited file as per above example.
![Edited radiusd.conf](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/26b9d00b-2008-427f-a065-4a728b2b2961)

Restart the radiusd
```
sudo systemctl restart radiusd
```
Failed to restart the radiusd service
![Failed radiusd service](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/fa8c68dc-20b0-43e9-a957-c890ca2d95f4)

Run the configuration check manually: Below command runs FreeRADIUS in debug mode, providing detailed output
```
sudo radiusd -X
```


check the log to see if there's any specific error message that can provide more insight into the issue

```
sudo journalctl -xeu radiusd.service
```

## Radius Installation 
# The following instructions are for the following Linux or Unix platforms: RedHat/CentOS

Run the following command:
```
sudo yum install gcc pam pam-devel make -y
```
![pam-devel](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/31cb4cf1-2477-4eb7-a07a-95076c54c9f8)

At the prompt, enter the following lines:
```
sudo wget ftp://ftp.freeradius.org/pub/radius/pam_radius-x.x.x.tar.gz
```

![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6d95a791-c77d-44c4-b400-2340bdf73f1d)
