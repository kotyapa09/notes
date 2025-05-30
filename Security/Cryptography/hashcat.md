```bash
# https://crackstation.net/
# paste ur hash cli
hash-identifier

#prepare hash file
echo -n "279412f945939ba78ce0758d3fd83daa" > hash_n.txt 

#1: MD5
hashcat -m 0 hash1.txt /usr/share/wordlists/rockyou.txt

#2: SHA-1
hashcat -m 0 hash2.txt /usr/share/wordlists/rockyou.txt
```
