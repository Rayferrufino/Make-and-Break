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

### install Webmin 1.890
- **Create a username (deathstart) and password (readytograduate) serving on port 10000 by default**
- **Download webmin-1.890.tar.gz from https://sourceforge.net/projects/webadmin/files/webmin/**
- **Extracting the file and running the following commands within the extracted Webmin folder**
- **<sudo ./setup.sh /usr/local/webmin>**
- **Enter password for user deathstart when prompted**

![](https://github.com/Rayferrufino/Make-and-Break/blob/master/Screenshots/Screenshot%20from%202019-09-17%2010-29-05.png?raw=true)
