# Ancora-Education-Ucertify-Lab39
# Configuring IPSec

Internet Protocol Security (IPsec) is a set of security protocols used to transfer IP packets confidentially across the Internet. 

> **Original Lab Source**
> 
> This lab was available through:
>
> [https://ancoraeducation.ucertify.com/app/?func=navigate_items&item_sequence=3]

## Lab Objective 
This lab session demonstrates the steps involved in configuring IPSec. Upon completion of this lab, you will be able to: Understand how IPSec provides authentication to verify the identity of communicating parties. Lab Prerequisite For this lab, the following prerequisite should be met: Basic understanding of IPSec concepts, including authentication methods and configuration of files. Lab/Machine Environment You are provided with the Linux virtual machine.
## PART A: Editing the ipsec.conf File
Launch the Terminal window and execute the command to open the ipsec.conf file and add the connection options. Then, open the ipsec.conf file and keep the secret key as 69EA16F2C5DCED8B29E74A7D1B0FE99E69F6BDCD3E44. 
### STEP 1 
From the bottom-left bar, click the Ubuntu tab, and then click On/Connect to power on the machine. 
### STEP 2 
On the left sidebar, click the Terminal icon to open its window. 
### STEP 3 
In the Terminal window, execute the following command to open the ipsec.conf file:
```bash
sudo nano /etc/ipsec.conf
```
### CAUTION
Enter the password as ucertify, when asked. The user will not be able to see the password while typing.
### Note 
GNU nano is a text editor for Linux-like computing systems or operating environments using a command-line interface. 
### STEP 4 
In the ipsec.conf file, add the following connection options at the end of the file:
```bash
conn L2TP-PSK-NAT
         rightsubnet=vhost:%priv
         also=L2TP-PSK-noNAT
conn L2TP-PSK-noNAT
         authby=secret
         pfs=no
         auto=add
         keyingtries=3
         ikelifetime=8h
         keylife=1h
         type=transport
         left=172.16.1.1
         leftprotoport=17/1701
         right=%any
         rightprotoport=17/%any
```
### STEP 5 
Press Ctrl+X, type y, and then press Enter to save the file. 
### STEP 6
In the Terminal window, execute the following command to open the ipsec.conf file to keep the secret key:
```bash
sudo nano /etc/ipsec.secrets
```
### STEP 7
Type the secret key at the end of the ipsec.conf secret file:
```bash
%SERVERIP% %any: PSK "69EA16F2C5DCED8B29E74A7D1B0FE99E69F6BDCD3E44"
```
### STEP 8 
Press Ctrl+X, type y, and then press Enter to save the file. 
### STEP 9 
Close all windows. 
## Lab Summary 
This lab session provides you with a straightforward and practical understanding of configuring IPSec and how to examine it. Here's a summary of what you have learned: How to configure IPSec using a secret key. Now, you are equipped with the knowledge and skills to configure IPSec effectively.
## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments
