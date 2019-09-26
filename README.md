# Make-and-Break

## Create and exploit a vulnerable Virtual Machine

### Description: Built a custom Virtual Machine, running Ubuntu 18.04.1 and Webmin 1.810. Using CVE-2019-15107 to exploit a backdoor in the Linux System Administration Interface

|PROOF of CONCEPT|
|----------------|
|Linux OS (Ubuntu 18.04.1) will be deployed containing security flaws that will allow an attacker to compromise the system to root level.|

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-33-32.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-28-25.png?raw=true)

### Installing SSH server
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2014-10-14.png?raw=true)

### Install Webmin 1.890
- **Create a username (deathstart) and password (readytograduate) serving on port 10000 by default**
- **Download webmin-1.890.tar.gz from https://sourceforge.net/projects/webadmin/files/webmin/**
- **Extracting the file and running the following commands within the extracted Webmin folder**
- **<sudo ./setup.sh /usr/local/webmin>**
- **Enter password for user deathstart when prompted**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-29-05.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-29-16.png?raw=true)
![](https://www.hostwinds.com/guide//wp-content/uploads/2017/03/IMG_Usermin_Login_Page.png)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-29-46.png?raw=true)

### Kali 
- **Recon steps: Kali VM and Ubuntu VM are on the same subnet**
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/wte.png?raw=true)

- **In Kali do an nmap scan for the Ubuntu machine, check for open ports and services**
- **Notice that port 10000 is open (a web server) and port 22. We will try to exploit port 10000, an http web server (miniServ 1.890) by using a known flaw, which let us connect remotely to it**
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-19%2015-09-27.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-19%2015-19-07.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-19%2015-19-39.png?raw=true)
