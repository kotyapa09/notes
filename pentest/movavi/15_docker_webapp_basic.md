

#### Задача 

создать докерфайл убунту сервером, на котором запушен простейший питон веб сервер, который запускает страничку с index.html из нужной лиректории. 
на которой реализуется простейший счетчик на js. 
с проброшеными портами для ssh b http. 

#### про docker

**Docker** — это платформа контейнеризации с открытым исходным кодом, которая позволяет разработчикам создавать, тестировать и развертывать приложения в изолированных средах, называемых контейнерами. Контейнеры упаковывают все необходимые компоненты приложения, включая библиотеки и зависимости, что обеспечивает его быструю и надежную работу в различных вычислительных средах.

Docker значительно упрощает процесс разработки и доставки приложений, позволяя разработчикам сосредоточиться на написании кода, а не на конфигурации окружения. Это достигается благодаря легковесной виртуализации, которая позволяет запускать множество контейнеров на одном хосте без значительных затрат ресурсов.

##### Основные команды Docker

Вот некоторые из ключевых команд Docker, которые полезны для управления контейнерами и образами:

- **docker ps**: показывает список запущенных контейнеров. Используйте `docker ps -a` чтобы увидеть все контейнеры, включая остановленные.

- **docker pull [image]**: загружает образ из Docker Hub. Например, `docker pull ubuntu` загрузит образ Ubuntu.

- **docker run [options] [image]**: создает и запускает контейнер из указанного образа. Например, `docker run -d -p 80:80 nginx` запустит контейнер с Nginx в фоновом режиме и пробросит порт 80.

- **docker build -t [name] .**: собирает образ из Dockerfile в текущем каталоге. Параметр `-t` задает имя образа.

- **docker exec -it [container_id] bash**: выполняет команду внутри запущенного контейнера, позволяя получить доступ к его командной строке.

- **docker stop [container_id]**: останавливает запущенный контейнер.

- **docker rm [container_id]**: удаляет контейнер. Используйте `-f`, чтобы принудительно остановить и удалить работающий контейнер.

- **docker images**: показывает список всех загруженных образов на вашем устройстве.

- **docker logs [container_id]**: выводит логи указанного контейнера, что полезно для отладки.


###### Что понадобится
```zsh
# собираем образ 
docker build -t my_test_server .  

# запускаем контейнер 
docker run -d -p 2222:22 -p 8000:8000 --name my_run_ssh_http my_test_server
```
 
##### THM Easy Theory
https://tryhackme.com/r/room/introtodockerk8pdqk


-------

#### Дополнительное удобство - gmd 
##### Установка Go (Golang) в Kali Linux

###### Способ 1: Установка из репозитория

1. **Обновите список пакетов**:
   ```bash
   sudo apt update
   ```

2. **Установите Go**:
   ```bash
   sudo apt install -y golang
   ```

3. **Настройте переменные окружения**:
   Откройте файл `.bashrc` или `.zshrc` (в зависимости от используемого шелла) для редактирования:
   ```bash
   nano ~/.bashrc
   ```
   или
   ```bash
   nano ~/.zshrc
   ```

   Добавьте следующие строки в конец файла:
   ```bash
   export GOROOT=/usr/lib/go
   export GOPATH=$HOME/go
   export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
   ```

4. **Примените изменения**:
   ```bash
   source ~/.bashrc
   ```
   или
   ```bash
   source ~/.zshrc
   ```

5. **Проверьте установку**:
   ```bash
   go version
   ```

##### Установка TUI приложения для работы с Docker (gmd)

   ```bash
   git clone https://github.com/ajayd-san/gomanagedocker.git
   ```

   ```bash
   cd gomanagedocker
   go build
   ```

   ```bash
   ./gmd
   ```


#### web & html & css & js

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Increment</title>
	<link rel="stylesheet" href="static/styles.css">
</head>
<body>
	<div class="container">
		<h1>Plus One</h1>
		<p id="number">0</p>
		<button id="incrementButton">Increase Count on Click</button>
		</div>
	<script>
		let count = 0;
		const numberDisplay = document.getElementById('number');
		const incrementButton = document.getElementById('incrementButton');
		
		incrementButton.addEventListener('click', () => {
			count += 1;
			numberDisplay.textContent = count;
		});
	</script>
</body>
</html>
```


```html
<!DOCTYPE html>
```
**Эта строка** указывает, что документ написан на HTML5. Она помогает браузеру правильно интерпретировать содержимое страницы.

```html
<html lang="en">
```
**Элемент `<html>`** является корневым элементом HTML-документа. Атрибут `lang="ru"` указывает, что язык страницы — русский. Это важно для поисковых систем и для доступности.

```html
<head>
```
**Элемент `<head>`** содержит метаданные о документе, такие как заголовок, ссылки на стили и другие настройки, которые не отображаются на странице.

```html
<meta charset="UTF-8">
```
**Элемент `<meta>`** с атрибутом `charset="UTF-8"` указывает кодировку символов, используемую на странице. UTF-8 поддерживает большинство языков, включая русский.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
**Этот `<meta>` элемент** отвечает за адаптивность страницы. Он устанавливает ширину области просмотра равной ширине устройства и начальный масштаб равным 1. Это важно для корректного отображения на мобильных устройствах.

```html
<title>Инкрементатор</title>
```
**Элемент `<title>`** задает заголовок страницы, который отображается на вкладке браузера. В данном случае заголовок — "Инкрементатор".

```html
<link rel="stylesheet" href="static/styles.css">
```
**Элемент `<link>`** подключает внешний файл стилей (CSS), который определяет, как элементы на странице будут выглядеть. Здесь файл стилей находится по адресу `static/styles.css`.

```html
</head>
```
**Закрывающий тег `</head>`** завершает раздел метаданных.

```html
<body>
```
**Элемент `<body>`** содержит все видимые элементы страницы, такие как текст, изображения и кнопки.

```html
<div class="container">
```
**Элемент `<div>`** используется для группировки других элементов. Класс `container` может применяться для стилизации этого блока с помощью CSS.

```html
<h1>Plus One</h1>
```
**Элемент `<h1>`** — это заголовок первого уровня. Он выделяется на странице и обычно используется для основного заголовка. Здесь он содержит текст "Plus One".

```html
<p id="number">0</p>
```
**Элемент `<p>`** представляет собой параграф. Атрибут `id="number"` позволяет JavaScript обращаться к этому элементу. Внутри параграфа изначально отображается число 0.

```html
<button id="incrementButton">Increase Count on Click</button>
```
**Элемент `<button>`** создает кнопку, на которую можно нажимать. Атрибут `id="incrementButton"` позволяет JavaScript взаимодействовать с этой кнопкой. Текст на кнопке — "Increase Count on Click".

```html
</div>
```
**Закрывающий тег `</div>`** завершает блок контейнера.

```html
<script>
```
**Элемент `<script>`** используется для добавления JavaScript-кода, который добавляет интерактивность на страницу.

```javascript
let count = 0;
```
**Эта строка** объявляет переменную `count` и инициализирует ее значением 0. Она будет использоваться для отслеживания количества нажатий на кнопку.

```javascript
const numberDisplay = document.getElementById('number');
```
**Эта строка** находит элемент с `id="number"` (параграф, который показывает текущее значение) и сохраняет его в переменной `numberDisplay`.

```javascript
const incrementButton = document.getElementById('incrementButton');
```
**Эта строка** находит кнопку с `id="incrementButton"` и сохраняет ее в переменной `incrementButton`.

```javascript
incrementButton.addEventListener('click', () => {
```
**Эта строка** добавляет обработчик события на кнопку. Когда на кнопку нажимают, выполняется функция, определенная в следующей строке.

```javascript
count += 1;
```
**Эта строка** увеличивает значение переменной `count` на 1 каждый раз, когда кнопка нажата.

```javascript
numberDisplay.textContent = count;
```
**Эта строка** обновляет текст внутри элемента `numberDisplay`, чтобы отобразить текущее значение `count`.

```html
});
</script>
```
**Закрывающие теги** завершают блок JavaScript и элемент `<script>`.

```html
</body>
</html>
```
**Закрывающие теги** завершают тело документа и сам HTML-документ.


**CSS** (Cascading Style Sheets, или каскадные таблицы стилей) — это язык, используемый для описания внешнего вида и форматирования веб-страниц, написанных на HTML или XML. CSS позволяет разработчикам управлять стилем, цветом, шрифтами, отступами и многими другими аспектами отображения элементов на веб-странице. Основное преимущество CSS заключается в том, что он отделяет содержание (HTML) от представления (стили), что упрощает поддержку и изменение дизайна сайта.

**CSS-селекторы** — это шаблоны, используемые для выбора HTML-элементов, к которым будут применяться стили. Селекторы позволяют разработчикам точно указывать, какие элементы на странице должны быть стилизованы, основываясь на их тегах, классах, идентификаторах, атрибутах и других характеристиках

```css
body {
font-family: Arial, sans-serif;
display: flex;
justify-content: center;
align-items: center;
height: 100vh;
background-color: #f0f0f0;
}

.container {
text-align: center;
background-color: white;
padding: 20px;
border-radius: 8px;
box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

button {
padding: 10px 20px;
font-size: 16px;
cursor: pointer;
border: none;
border-radius: 5px;
background-color: #007bff;
color: white;
}

button:hover {
background-color: #0056b3;
}

```

###### Dorking Theory + Practice
https://tryhackme.com/r/room/googledorking

##### THM Easy Theory
https://tryhackme.com/r/room/httpindetail


------

#### OSINT THM Rooms 

##### Easy

https://tryhackme.com/r/room/ohsint
https://tryhackme.com/r/room/sakura
https://tryhackme.com/r/room/searchlightosint
https://tryhackme.com/r/room/geolocatingimages

##### Medium
https://tryhackme.com/r/room/somesint