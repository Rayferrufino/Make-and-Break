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

- **We use exploit 2019-15107 Unauthenticated Remote Code Execution in Metasploit to get root access.**
- **Open msfconsole on Kali, search for webmin, and use exploit unix/webapp/webmin_backdoor**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2013-05-14.png?raw=true)

- **Set options accordingly - RHOST, LHOST**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2013-05-29.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2013-05-43.png?raw=true)


- **Run the exploit and get a shell**
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2013-06-04.png?raw=true)


- **We tried to spawn our shell but we were unsuccessful. In addition we can't change directories even though we are "root" but fortunately we can cat files and list directories including the /etc/shadow! file that contains the hashed passwords**

- **We copied the content of the shadow file and passwd file into a shadows.txt and passwd.txt file and we procced to crack the hash using John the Ripper**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-35-09.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-37-50.png?raw=true)


- **Type unshadow passwd.txt shadow.txt > password.txt  in order to combine both files and use John**
- **We already created our own password list (fullstack.txt) with common passwords, which we will use with John in order to obtain the password**
- **Type john --wordlist=fullstack.txt password.txt in order to crack and reveal the password**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-40-27.png?raw=true)

- **Cracking successful, password for *deathstart* is *readytograduate* SSH to this user ssh deathstart@192,168.44.132 and type the password readytograduate when prompted**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-38-42.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-39-04.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-39-20.png?raw=true)
![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2016-39-44.png?raw=true)

## At this point we have fully compromised the machine and gained control of the system.











