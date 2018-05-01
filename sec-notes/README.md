# Security-Notepad
## My random notes on different topics

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

### **Microcontroller**
#### Microcontroller - Links
#### Microcontroller - other

### **LINUX**
#### Linux - Cheatsheets
#### Linux - bash oneliners
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
to be filled...
```

#### Linux - tmux
#### Linux - Docker
* [Docker Basics]()
* [Official Docker Cheatsheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf)
* [more Docker Cheatsheets](https://dockercheatsheet.painlessdocker.com/)
* [more Docker Cheatsheets](https://github.com/wsargent/docker-cheat-sheet)

##### How to install docker && docker-compose
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

##### How to build an image
##### How to run and stop a container
##### How to check status
```bash
docker container stats --all
docker ps 
```
##### How to manage users
##### How to manage containers
##### How to delete a container
##### How to create a volume
```bash
```
##### How to backup a container
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

##### How to connect to a container
##### Networking with Docker
* [Docker Docs Networking](https://docs.docker.com/network/)
* [Container Networking](https://docs.docker.com/config/containers/container-networking/)

See network config
```bash
docker network ls
docker network inspect DOCKNETID
```

### **ElasticSearch & Kibana**
#### ElasticSearch & Kibana - Installation
#### Collecting Data
#### Search for Data
#### Building a Dashboard
#### Monitoring/Networking

### **Windows**
#### Powershell
* [PSEmpire](http://www.powershellempire.com/)
* [PowerUpSQL](https://github.com/NetSPI/PowerUpSQL)
* [Awesome PS](https://github.com/janikvonrotz/awesome-powershell)
* [PS Basics](https://www.darkoperator.com/powershellbasics/)

#### Tools
#### OS

### **Markdown**
#### Markdown - Links
* [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
#### Markdown - other

### **CTF**
#### CTF - Online
* [CTFTime](https://ctftime.org/event/list/upcoming)
#### CTF - Wargames
* [RPISEC Modern Binary Exploitation](https://github.com/RPISEC/MBE)
* [Exploit-Exercises Protostar](https://exploit-exercises.com/protostar/)
* [root-me.org](https://www.root-me.org/?lang=de)
#### PwnAdventure 3: Pwnie Island
* [Download PwnAdventure 3](http://www.pwnadventure.com/)
* [LiveOverflow PwnAdventure GitRepo](https://github.com/LiveOverflow/PwnAdventure3) Go here for docker server setup
##### PwnAdventure 3: Pwnie Island - Writeups

### **Tools**
#### Tools - Links
#### Tools - other

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
>
>
> Günther
