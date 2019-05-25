# Security-Notepad
## My random notes on different topics

### Reference

### **RE**
#### RE - Links
* [Reversing Basics](https://medium.com/bugbountywriteup/bolo-reverse-engineering-part-1-basic-programming-concepts-f88b233c63b7)
* [Intel instruction-set-reference-manual](https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-instruction-set-reference-manual-325383.pdf)
* [moveax.me - writeups](https://moveax.me/)
#### RE - other

### **GDB**
#### GDB - Enhancements
* [GDB gef](https://github.com/hugsy/gef)
* [GDB peda](https://github.com/longld/peda)
* [GDB peda-install](http://security.cs.pub.ro/hexcellents/wiki/kb/toolset/peda)
#### GDB - Commands

### **Radare2**
#### Radare2 - Cheatsheets
#### Radare2 - Basics
#### Radare2 - other

### **Python**
#### Python - Links
* [quick deepdive](https://www.binary-zone.com/course/HTID/Python4Infosec.pdf)
* [pip-install](https://pip.pypa.io/en/stable/installing/)
#### Python - pwntools
* [pwntools-docs](https://docs.pwntools.com/en/stable/search.html?q=irc&check_keywords=yes&area=default)

#### Python - other
Python SimpleHTTP Server
```bash
python -m SimpleHTTPServer 80
```

Get ip of a specific interface
```python
import netifaces as ni
ni.ifaddresses('tun0')
IP_TUNNEL = ni.ifaddresses('tun0')[ni.AF_INET][0]['addr']
```

Setup a simple interactive Listener and Upgrade shell if possible
```python
import os
l = listen(port=13337, bindaddr = "0.0.0.0")
c = l.wait_for_connection()
c.send("""python -c 'import pty; pty.spawn("/bin/bash")'\n""")
log.info('shell upgraded from sh to tty-bash')
c.interactive()
```
### **GO**
#### GO - install and setup
Debian Systems
sudo apt install go-golang
Arch
sudo pacman -S go
OR
For example on a raspbian
Download and extract the tar.gz archive to /usr/local/go

Setup $GOROOT and $GOPATH for compiling and other stuff
add those two lines to your ~/.profile and source it
/usr/local/go/bin is where your go installation lives
and add gopath to path variable
```bash
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```


### **Microcontroller**
#### Microcontroller - Links
#### Microcontroller - other

### **LINUX**
#### Linux - Cheatsheets
#### Linux - bash oneliners
From sudo to root
* [](http://touhidshaikh.com/blog/?p=790)
Search filesystem for 20 biggest files
```bash
du -hsx * | sort -rh | head -20
```
Extract all kinds of archives in a new subdirectory with one tool
```bash
sudo apt-get install dtrx
dtrx something.zip
```
Extract all kinds of archives without extra tools
```bash
[.tar]    tar -xvf
[.tar.gz] tar -zxvf
[.gz]
[.tar.bz] tar -xjvf
[.zip]
[.7z]
[.rar]
```
Find info on zip-Archive incl. Encryption Algorithm
```bash
7z l -slt example.zip
```
Standard Bash for-Loop
```bash
for i in {1..10} ; do <COMMAND> ; done
```
Find RSA Private keys in filesystem
```bash
grep -rnw '/' -e 'RSA PRIVATE'
```
#### Linux - SSH
Copy files over SSH
```bash
scp USER@HOST:/<PATH TO REMOTE FILE> <PATH TO LOCAL FILE>
```
Copy files over SSH recursively
```bash
scp -rp USER@HOST:/<PATH TO REMOTE FILE> <PATH TO LOCAL FILE>
```
Copy files over SSH specific port
```bash
scp -P 22022 USER@HOST:/<PATH TO REMOTE FILE> <PATH TO LOCAL FILE>
```
Tunnel localhost services on Remote Host to Local Host
```bash
ssh -L LPORT:localhost:RPORT USER@HOST
```
#### Linux - SSH Keys
* [DO Set Up SSH KeyPair](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
Generate KeyPair
```bash
ssh-keygen -t rsa
```
Use RSA Private Key to Connect(directly from file)
```bash
ssh -i <PATH TO FILE> host@example.com
```
Find rsa private keys
```bash
cat /home/<USER>/.ssh/id_rsa
cat /home/<USER>/.ssh/rsa_key
cat /home/<USER>/.ssh/key_rsa
cat /home/<USER>/.ssh/rsa_priv
cat /root/.ssh/<FILENAME>
```
#### Linux - Users, Groups and File Permissions
#### Linux - VI/M
* [Best vimrc out there](https://github.com/amix/vimrc)
#### Linux - tmux
* [tmux Cheat Sheet](http://atkinsam.com/documents/tmux.pdf)
* [tmux Introduction by IppSec](https://www.youtube.com/watch?v=Lqehvpe_djs)
* [tmux /powerline](https://github.com/gpakosz/.tmux)
#### Linux - Docker
* [Docker Basics]()
* [Official Docker Cheatsheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf)
* [more Docker Cheatsheets](https://dockercheatsheet.painlessdocker.com/)
* [more Docker Cheatsheets](https://github.com/wsargent/docker-cheat-sheet)
#### Linux - Enumeration
* [LinEnum.sh](https://github.com/rebootuser/LinEnum)
```bash
./LinEnum.sh -r report -e /tmp/LinEnum/ -t
```
#### Linux - openvpn Server
* [DO Setup Tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)

### **Fuzzing with afl - Basics**
#### find a target
To be filled...
#### install afl-latest
```bash
wget http://lcamtuf.coredump.cx/afl/releases/afl-latest.tgz
tar -xvf afl-latest.tgz
cd afl-latest
make
sudo make install
```
#### start fuzzing and afl usage
* [fuzzing 101](https://research.aurainfosec.io/hunting-for-bugs-101/)

The process of using AFL is pretty straight forward

 - Compile a binary using AFL’s compiler wrappers
 ```bash
 afl-gcc target.c -o target
 ```
 - Fuzz the binary using afl-fuzz <— this is where the magic happens.
 - Review any unique crashes reported by afl-fuzz. Unique crashes occur if any of the afl-fuzz modified input files, result in the target binary crashing.

### **QEMU**
#### QEMU Debian install
```bash
apt-get install qemu-system-x86
apt-get install qemu-system
apt-get install qemu-user 
```

#### QEMU basic usage
#### QEMU Advanced usage
#### Fuzzing with QEMU



### **Docker**
#### How to install docker && docker-compose
First you need to install the official docker CE linux package on your system (in my case Debian based way). There is a complete guide for most systems available here [Docker install Docs](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository)

Now update your apt
```bash
sudo apt-get update
```
After that you have to install a few packages, in most cases you will already have most of them installed.
```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common
```
In order to connect with the Docker Repo you need to import the actual GPG-Key
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```
You just want to add the stable Repo to your apt source.list or source.list.d/
```bash
echo "deb [arch=amd64] https://download.docker.com/linux/debian stretch stable" > /etc/apt/sources.list.d/docker.list
apt update
```
Now we can finally install the actual docker-ce build via apt
```bash
sudo apt-get install docker-ce
```
Wait until installation is finished and also install docker-compose, you'll need it
```bash
sudo apt-get install docker-compose
```
The last step of installation is adding the current user into the docker group relogin and check settings 
```bash
sudo usermod -a -G docker $USER
sudo reboot
id
```

#### How to build an image
#### How to run and stop a container
#### How to check status
```bash
docker container stats --all
docker ps 
```
#### How to manage users
#### How to manage containers
#### How to delete a container
#### How to create a volume
```bash
```
#### How to backup a container
Find the container ID and Backup container
```bash
docker ps
docker commit -p CONTAINERID IMAGENAME
```
List container images
```bash
docker images
```
Load docker images
```bash
docker run IMAGENAME
```
Export container as .tar archive
```bash
docker save -o ~/container1.tar IMAGENAME
```

#### How to connect to a container
#### Networking with Docker
* [Docker Docs Networking](https://docs.docker.com/network/)
* [Container Networking](https://docs.docker.com/config/containers/container-networking/)

See network config
```bash
docker network ls
docker network inspect DOCKNETID
```


### **Windows**
#### Powershell
* [PSEmpire](http://www.powershellempire.com/)
* [PowerUpSQL](https://github.com/NetSPI/PowerUpSQL)
* [Awesome PS](https://github.com/janikvonrotz/awesome-powershell)
* [PS Basics](https://www.darkoperator.com/powershellbasics/)

#### Tools
#### OS
SMB Enumeration
```bash

```

### **Markdown**
#### Markdown - Links
* [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
#### Markdown - other

### **CTF**
#### CTF - Online
* [CTFTime](https://ctftime.org/event/list/upcoming)
#### CTF - Wargames
* [RPISEC Modern Binary Exploitation](https://github.com/RPISEC/MBE)
* [Exploit-Exercises Protostar](https://exploit-exercises.com/protostar/)This one is outdated - contact me for the image
* [root-me.org](https://www.root-me.org/?lang=de)
#### PwnAdventure 3: Pwnie Island
* [Download PwnAdventure 3](http://www.pwnadventure.com/)
* [LiveOverflow PwnAdventure GitRepo](https://github.com/LiveOverflow/PwnAdventure3) Go here for docker server setup
##### PwnAdventure 3: Pwnie Island - Writeups

### **Tools**
#### Tools - Links
#### Tools - john the ripper
unshadow the hash
```bash
umask 077
unshadow /etc/passwd /etc/shadow > mypasswd
```
Crack Linux SHA-256 unshadowed Hash file (defaultmode)
```bash
john mypasswd
```
Crack Linux SHA-256 unshadowed Hash file (specific)
```bash
john --wordlist=passwords.lst --rules mypasswd
```
#### Tools - Nmap
Nmap Quick Scan
```bash
nmap -T4 -F 10.10.10.1/24
```
Basic full TCP scan all Ports, run Scripts and Output all Formats
```bash
nmap -sV -sC -p 1-65535 -T4 -A -v 10.10.10.1/24 -oA ./<REPORT>
```
#### Tools - WireShark
Wiresharek quick check filters
```bash
HTTP contains POST
```
#### Tools - other
* [Official Docs](https://www.sublimetext.com/docs/3/linux_repositories.html)
Install Sublime 3 from Repo
Setup Repo
```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | apt-key add -
apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | tee /etc/apt/sources.list.d/sublime-text.list
```
Install and Update Sublime
```bash
apt-get update
apt-get install sublime-text
```
#### Tools - vncpwd 
install vncpwd
```bash
git clone https://github.com/jeroennijhof/vncpwd.git
cd vncpwd
make
make install
```
Decrypt $USER/.vnc/passwd file
```bash
vncpwd passwd
Password: secretvncpw
```
### **YouTube**
#### Youtube - Channels
* [GynvaelEN](https://www.youtube.com/channel/UCCkVMojdBWS-JtH7TliWkVg)
* [LiveOverflow](https://www.youtube.com/channel/UClcE-kVhqyiHCcjYwcpfj9w)
* [MurmusCTF](https://www.youtube.com/channel/UCUB9vOGEUpw7IKJRoR4PK-A)
* [IppSec](https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA)
* [Derek Rook](https://www.youtube.com/channel/UCMACXuWd2w6_IEGog744UaA)
* [13Cubed](https://www.youtube.com/channel/UCy8ntxFEudOCRZYT1f7ya9Q)
* [Guided Hacking](https://www.youtube.com/channel/UCCMi6F5Ac3kQDfffWXQGZDw)

### **Awesome 1337 stuff**
* [Awesome Shells](https://terminalsare.sexy/)
* [more Awesome Shell Stuff](https://github.com/alebcay/awesome-shell)
* [Awesome Shell Parrot](https://github.com/hugomd/parrot.live)
* [more Awesome Parrots](http://cultofthepartyparrot.com/)

Rayquazid - Whitehat, Datacenter-Security-Engineer, Wannabe Hacker
https://twitter.com/DennisDeLarge
>Günther
>
> Igor ist ein merkwürdiges Kind. Er berührt Dinge um sie zu verstehen, malt Kreise auf Hauswände und sortiert Schachteln in Schachteln ein
