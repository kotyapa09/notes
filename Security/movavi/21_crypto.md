### Для старта 

https://tryhackme.com/room/cryptographybasics
https://tryhackme.com/room/encryptioncrypto101
## Базa базовая  
### Типы данных, работа с числами и строками, f-strings

#### 1. Типы данных
В Python есть несколько основных типов данных, которые нужно знать:

- **Целые числа (int)**: `5`, `-3`, `42`
- **Числа с плавающей точкой (float)**: `3.14`, `-0.001`, `2.0`
- **Строки (str)**: `"Привет"`, `'Python'`, `"123"`
- **Логические (bool)**: `True`, `False`
- **Списки (list)**: `[1, 2, 3]`, `["яблоко", "банан"]`
- **Словари (dict)**: `{"имя": "Анна", "возраст": 25}`
- **Кортежи (tuple)**: `(1, 2, 3)`
- **Множества (set)**: `{1, 2, 3}`

Пример:
```python
x = 10          # int
y = 3.14        # float
name = "Alice"  # str
is_student = True  # bool
```
#### 2. Работа с числами
Основные операции с числами:
- Сложение: `+`
- Вычитание: `-`
- Умножение: `*`
- Деление: `/`
- Целочисленное деление: `//`
- Остаток от деления: `%`
- Возведение в степень: `**`

Пример:
```python
a = 10
b = 3

print(a + b)  # 13
print(a - b)  # 7
print(a * b)  # 30
print(a / b)  # 3.333...
print(a // b) # 3
print(a % b)  # 1
print(a ** b) # 1000
```
#### 3. Работа со строками
Строки можно складывать (конкатенация) и умножать на числа. Также можно обращаться к отдельным символам по индексу.

Пример:
```python
s1 = "Hello"
s2 = "World"

print(s1 + " " + s2)  # "Hello World"
print(s1 * 3)         # "HelloHelloHello"
print(s1[0])          # "H" (первый символ)
print(s1[-1])         # "o" (последний символ)
```

#### 4. f-strings
f-strings — это удобный способ форматирования строк. Внутри строки можно вставлять значения переменных, используя фигурные скобки `{}`.

Пример:
```python
name = "Alice"
age = 25

print(f"Меня зовут {name} и мне {age} лет.")  # "Меня зовут Alice и мне 25 лет."
```

Также можно выполнять простые выражения внутри f-strings:
```python
x = 10
y = 3

print(f"{x} + {y} = {x + y}")  # "10 + 3 = 13"
```
 ----
#### 1. Работа с list (списки)
Списки — это упорядоченные коллекции элементов. Элементы могут быть любого типа: числа, строки, другие списки и т.д.

Пример создания списка:
```python
fruits = ["яблоко", "банан", "вишня"]
numbers = [1, 2, 3, 4, 5]
mixed = [1, "яблоко", 3.14, True]
```

Основные операции со списками:
- Добавление элемента: `append()`
- Удаление элемента: `remove()`
- Доступ к элементу по индексу: `list[index]`
- Изменение элемента: `list[index] = новое_значение`
- Длина списка: `len(list)`

Пример:
```python
fruits = ["яблоко", "банан", "вишня"]

fruits.append("апельсин")  # ["яблоко", "банан", "вишня", "апельсин"]
fruits.remove("банан")     # ["яблоко", "вишня", "апельсин"]
print(fruits[0])           # "яблоко"
fruits[1] = "груша"        # ["яблоко", "груша", "апельсин"]
print(len(fruits))         # 3
```

#### 2. Срезы (slicing)
Срезы позволяют получать части списка. Синтаксис: `list[начало:конец:шаг]`.

- `[2:]` — все элементы, начиная с индекса 2 до конца.
- `[:2]` — все элементы от начала до индекса 1 (индекс 2 не включается).
- `[::-1]` — список в обратном порядке.
- `[1:4]` — элементы с индекса 1 до индекса 3 (4 не включается).
- `[::2]` — каждый второй элемент.

Пример:
```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numbers[2:])   # [2, 3, 4, 5, 6, 7, 8, 9]
print(numbers[:2])   # [0, 1]
print(numbers[::-1]) # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (обратный порядок)
print(numbers[1:4])  # [1, 2, 3]
print(numbers[::2])  # [0, 2, 4, 6, 8] (каждый второй элемент)
```

#### 3. Создание составных списков (list comprehensions)
Составные списки — это списки, содержащие другие списки. Например, матрица (список списков).

Пример:
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matrix[0])      # [1, 2, 3]
print(matrix[1][2])   # 6 (вторая строка, третий элемент)
```
#### 4. Примеры использования срезов и списков
Пример 1: Получить первые 3 элемента списка:
```python
numbers = [10, 20, 30, 40, 50]
first_three = numbers[:3]
print(first_three)  # [10, 20, 30]
```

Пример 2: Получить каждый второй элемент списка:
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
every_second = numbers[::2]
print(every_second)  # [1, 3, 5, 7, 9]
```

Пример 3: Перевернуть строку с помощью срезов:
```python
text = "Python"
reversed_text = text[::-1]
print(reversed_text)  # "nohtyP"
```

---
### Часть 3: Циклы и их применение

Циклы позволяют выполнять повторяющиеся действия. В Python есть два основных типа циклов: `for` и `while`.

---
#### 1. Цикл `for`
Цикл `for` используется для перебора элементов последовательности (например, списка, строки или диапазона).

**Синтаксис:**
```python
for переменная in последовательность:
    # действия
```

Пример 1: Перебор списка
```python
fruits = ["яблоко", "банан", "вишня"]

for fruit in fruits:
    print(fruit)
```

Пример 2: Перебор строки
```python
word = "Python"

for letter in word:
    print(letter)
```

Пример 3: Использование `range()`
Функция `range()` создает последовательность чисел. Она часто используется в циклах.

```python
for i in range(5):  # от 0 до 4
    print(i)
```

Пример 4: Цикл с шагом
```python
for i in range(0, 10, 2):  # от 0 до 10 с шагом 2
    print(i)
```

---
#### 2. Цикл `while`
Цикл `while` выполняется, пока условие истинно.

**Синтаксис:**
```python
while условие:
    # действия
```

Пример 1: Простой цикл
```python
count = 0

while count < 5:
    print(count)
    count += 1
```

Пример 2: Бесконечный цикл с прерыванием
```python
while True:
    user_input = input("Введите 'стоп', чтобы выйти: ")
    if user_input == "стоп":
        break  # выход из цикла
    print(f"Вы ввели: {user_input}")
```

---
#### 3. Применение циклов для работы со списками

Пример 1: Создание списка с помощью цикла
```python
squares = []

for i in range(10):
    squares.append(i ** 2)  # добавляем квадраты чисел

print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

Пример 2: Фильтрация списка
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
even_numbers = []

for num in numbers:
    if num % 2 == 0:  # проверяем, четное ли число
        even_numbers.append(num)

print(even_numbers)  # [2, 4, 6, 8]
```

---
#### 4. Вложенные циклы
Циклы можно вкладывать друг в друга. Например, для работы с матрицами.

Пример: Перебор элементов матрицы
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:  # перебираем строки
    for num in row:  # перебираем элементы в строке
        print(num, end=" ")  # выводим элемент
    print()  # переход на новую строку
```

---
#### 5. Управление циклами: `break` и `continue`
- `break` — завершает цикл.
- `continue` — пропускает текущую итерацию и переходит к следующей.

Пример:
```python
for i in range(10):
    if i == 5:
        break  # выход из цикла при i = 5
    if i % 2 == 0:
        continue  # пропуск четных чисел
    print(i)
```

---

**Функции** — это блоки кода, которые выполняют определенную задачу. Они помогают избежать дублирования кода, делают его более читаемым и удобным для повторного использования.

---
#### 1. Создание функций
Функция создается с помощью ключевого слова `def`.

**Синтаксис:**
```python
def имя_функции(параметры):
    # тело функции
    return результат  # возврат значения (необязательно)
```

Пример 1: Простая функция
```python
def greet():
    print("Привет, мир!")

greet()  # Вызов функции
```

Пример 2: Функция с параметрами
```python
def greet(name):
    print(f"Привет, {name}!")

greet("Анна")  # Привет, Анна!
greet("Иван")  # Привет, Иван!
```

Пример 3: Функция с возвратом значения
```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 8
```

---

#### 2. Параметры и аргументы
- **Параметры** — это переменные, указанные в определении функции.
- **Аргументы** — это значения, которые передаются в функцию при вызове.

Пример:
```python
def multiply(a, b):  # a и b — параметры
    return a * b

result = multiply(4, 5)  # 4 и 5 — аргументы
print(result)  # 20
```

---

#### 3. Значения по умолчанию
Параметры функции могут иметь значения по умолчанию. Если аргумент не передается, используется значение по умолчанию.

Пример:
```python
def greet(name="Гость"):
    print(f"Привет, {name}!")

greet()        # Привет, Гость!
greet("Анна")  # Привет, Анна!
```

---
#### 4. Возврат нескольких значений
Функция может возвращать несколько значений с помощью кортежа.

Пример:
```python
def min_max(numbers):
    return min(numbers), max(numbers)

result = min_max([3, 1, 4, 1, 5, 9, 2])
print(result)  # (1, 9)
```

---
#### 5. Локальные и глобальные переменные
- **Локальные переменные** — переменные, объявленные внутри функции. Они существуют только внутри функции.
- **Глобальные переменные** — переменные, объявленные вне функции. Они доступны как внутри, так и вне функции.

Пример:
```python
x = 10  # Глобальная переменная

def my_func():
    y = 5  # Локальная переменная
    print(x + y)

my_func()  # 15
print(y)   # Ошибка: y не определена
```

---
#### 6. Рекурсия
Функция может вызывать саму себя. Это называется рекурсией.

Пример: Факториал числа
```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 120 (5! = 5 * 4 * 3 * 2 * 1)
```

---
#### 7. Практические примеры

Пример 1: Функция для подсчета суммы элементов списка
```python
def sum_list(numbers):
    total = 0
    for num in numbers:
        total += num
    return total

print(sum_list([1, 2, 3, 4, 5]))  # 15
```

Пример 2: Функция для фильтрации четных чисел
```python
def filter_even(numbers):
    return [num for num in numbers if num % 2 == 0]

print(filter_even([1, 2, 3, 4, 5, 6]))  # [2, 4, 6]
```

Пример 3: Функция для создания строки из списка
```python
def list_to_string(lst):
    return ", ".join(map(str, lst))

print(list_to_string([1, 2, 3, 4, 5]))  # "1, 2, 3, 4, 5"
```

---
#### 8. Лямбда-функции
Лямбда-функции — это анонимные функции, которые можно использовать для простых операций.

Пример:
```python
square = lambda x: x ** 2
print(square(5))  # 25
```

Лямбда-функции часто используются с функциями `map()`, `filter()` и `sorted()`.

Пример с `map()`:
```python
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # [1, 4, 9, 16, 25]
```

Пример с `filter()`:
```python
numbers = [1, 2, 3, 4, 5, 6]
even = list(filter(lambda x: x % 2 == 0, numbers))
print(even)  # [2, 4, 6]
```

---
### Пакетный менеджер `uv`

`uv` — это современный и быстрый пакетный менеджер для Python, созданный для управления зависимостями, виртуальными окружениями и сборкой проектов. Он разработан для замены таких инструментов, как `pip`, `pip-tools`, `virtualenv`, и `poetry`, предлагая более высокую производительность и удобство.
### Установка `uv`

Для установки `uv` выполните следующую команду:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

```bash
uv --version
```

### Базовые команды `uv`

#### 1. Создание виртуального окружения
`uv` позволяет быстро создавать виртуальные окружения.

```bash
uv init 
uv venv .venv
```

- `.venv` — это папка, в которой будет создано виртуальное окружение.
- `init`  инициализация проекта (сразу для гит)
- После создания активируйте окружение:
  - На Linux/macOS: `source .venv/bin/activate`
  - На Windows: `.venv\Scripts\activate`

---
#### 2. Установка пакетов
Для установки пакетов используйте команду `uv pip install`.
Пример: Установка одного пакета
```bash
uv pip install requests
```
Пример: Установка нескольких пакетов
```bash
uv pip install requests numpy pandas
```
Пример: Установка пакетов из файла `requirements.txt`
```bash
uv pip install -r requirements.txt
```

---
#### 3. Создание `requirements.txt`
`uv` позволяет легко создавать файл зависимостей.

Пример: Заморозка текущих зависимостей
```bash
uv pip freeze > requirements.txt
```

---
#### 4. Обновление пакетов
Для обновления пакетов используйте команду `uv pip install --upgrade`.
Пример: Обновление одного пакета
```bash
uv pip install --upgrade requests
```
Пример: Обновление всех пакетов
```bash
uv pip install --upgrade -r requirements.txt
```

---
#### 5. Удаление пакетов
Для удаления пакетов используйте команду `uv pip uninstall`.
Пример: Удаление пакета
```bash
uv pip uninstall requests
```

---
#### 6. Сборка проекта
`uv` поддерживает сборку проектов с помощью команды `uv build`.
Пример: Сборка проекта
```bash
uv build
```

---
#### 7. Управление зависимостями
`uv` позволяет синхронизировать зависимости с файлом `requirements.txt`.

Пример: Синхронизация зависимостей
```bash
uv pip sync requirements.txt
```

---
#### 8. Ускорение установки
`uv` использует кеширование для ускорения установки пакетов. Например, при повторной установке пакетов из `requirements.txt`:

```bash
uv pip install -r requirements.txt --cache-dir .uv_cache
```

---
### Пример рабочего процесса с `uv`

1. Создайте виртуальное окружение:
   ```bash
   uv venv .venv
   source .venv/bin/activate  # Активация окружения
   ```
2. Установите пакеты:
   ```bash
   uv pip install requests numpy pandas
   ```
3. Заморозьте зависимости:
   ```bash
   uv pip freeze > requirements.txt
   ```
4. Синхронизируйте зависимости (например, на другом компьютере):
   ```bash
   uv pip sync requirements.txt
   ```
5. Удалите пакет:
   ```bash
   uv pip uninstall pandas
   ```
6. Обновите пакеты:
   ```bash
   uv pip install --upgrade -r requirements.txt
   ```

---
### Модули в Python для решения базовых задач по криптографии

Python предоставляет множество встроенных модулей и функций, которые могут быть полезны для решения задач по криптографии. Рассмотрим некоторые из них.

---

### 1. Модуль `base64`
Модуль `base64` используется для кодирования и декодирования данных в формате Base64. Это полезно для преобразования бинарных данных в текстовый формат и обратно.
#### Основные функции:
- `base64.b64encode(data)` — кодирует данные в Base64.
- `base64.b64decode(data)` — декодирует данные из Base64.
Пример:
```python
import base64

# Кодирование
data = "Hello, World!"
encoded_data = base64.b64encode(data.encode('utf-8'))
print(encoded_data)  # b'SGVsbG8sIFdvcmxkIQ=='

# Декодирование
decoded_data = base64.b64decode(encoded_data).decode('utf-8')
print(decoded_data)  # Hello, World!
```

---
### 2. Преобразование hex в байты и обратно
Для работы с шестнадцатеричными строками (hex) можно использовать метод `bytes.fromhex()` и метод `.hex()`.
#### Пример:
```python
# Преобразование hex в байты
hex_string = "48656c6c6f"  # "Hello" в hex
byte_data = bytes.fromhex(hex_string)
print(byte_data)  # b'Hello'

# Преобразование байтов в hex
hex_data = byte_data.hex()
print(hex_data)  # 48656c6c6f
```

---
### 3. Кодирование и декодирование строк
Для работы с текстовыми данными часто используются методы `.encode()` и `.decode()`.
#### Пример:
```python
# Кодирование строки в байты
text = "Привет"
encoded_text = text.encode('utf-8')
print(encoded_text)  # b'\xd0\x9f\xd1\x80\xd0\xb8\xd0\xb2\xd0\xb5\xd1\x82'

# Декодирование байтов в строку
decoded_text = encoded_text.decode('utf-8')
print(decoded_text)  # Привет
```

---
### 4. Модуль `hashlib`
Модуль `hashlib` предоставляет функции для хеширования данных (например, MD5, SHA-1, SHA-256).
#### Основные функции:
- `hashlib.md5(data)` — хеширование с использованием MD5.
- `hashlib.sha256(data)` — хеширование с использованием SHA-256.
Пример:
```python
import hashlib

# Хеширование строки
data = "Hello, World!"
hash_object = hashlib.sha256(data.encode('utf-8'))
hex_dig = hash_object.hexdigest()

print(hex_dig)  # SHA-256 хеш строки "Hello, World!"
```

---
### 5. Модуль `os.urandom`
Модуль `os` предоставляет функцию `urandom()` для генерации криптографически безопасных случайных байтов.
#### Пример:
```python
import os

# Генерация 16 случайных байтов
random_bytes = os.urandom(16)
print(random_bytes)  # b'\x1a\x2b\x3c\x4d...'
```

---
### 6. Модуль `secrets`
Модуль `secrets` предназначен для генерации криптографически безопасных случайных чисел и строк.
#### Основные функции:
- `secrets.token_bytes(n)` — генерация `n` случайных байтов.
- `secrets.token_hex(n)` — генерация `n` случайных байтов в виде hex-строки.
- `secrets.choice(sequence)` — выбор случайного элемента из последовательности.

Пример:
```python
import secrets

# Генерация случайной hex-строки
random_hex = secrets.token_hex(16)
print(random_hex)  # Случайная hex-строка длиной 32 символа

# Выбор случайного элемента из списка
items = ["apple", "banana", "cherry"]
random_item = secrets.choice(items)
print(random_item)  # Случайный элемент из списка
```

---
### 7. Модуль `binascii`
Модуль `binascii` предоставляет функции для преобразования между бинарными и текстовыми данными.
#### Основные функции:
- `binascii.hexlify(data)` — преобразование байтов в hex-строку.
- `binascii.unhexlify(hex_string)` — преобразование hex-строки в байты.
Пример:
```python
import binascii

# Преобразование байтов в hex
data = b"Hello"
hex_data = binascii.hexlify(data)
print(hex_data)  # b'48656c6c6f'

# Преобразование hex в байты
byte_data = binascii.unhexlify(hex_data)
print(byte_data)  # b'Hello'
```

---
### 8. Модуль `struct`
Модуль `struct` используется для работы с бинарными данными. Он позволяет упаковывать и распаковывать данные в бинарный формат.
#### Основные функции:
- `struct.pack(format, data)` — упаковка данных в бинарный формат.
- `struct.unpack(format, binary_data)` — распаковка бинарных данных.

Пример:
```python
import struct

# Упаковка данных
packed_data = struct.pack('>I', 12345)  # '>I' — big-endian, unsigned int
print(packed_data)  # b'\x0009'

# Распаковка данных
unpacked_data = struct.unpack('>I', packed_data)
print(unpacked_data)  # (12345,)
```

---
### Пример решения задачи по криптографии
Задача: Закодировать строку в Base64, затем декодировать её и вычислить SHA-256 хеш.
```python
import base64
import hashlib

# Исходная строка
text = "Hello, Crypto!"

# Кодирование в Base64
encoded_text = base64.b64encode(text.encode('utf-8'))
print("Base64:", encoded_text)

# Декодирование из Base64
decoded_text = base64.b64decode(encoded_text).decode('utf-8')
print("Decoded:", decoded_text)

# Вычисление SHA-256 хеша
hash_object = hashlib.sha256(decoded_text.encode('utf-8'))
hex_dig = hash_object.hexdigest()
print("SHA-256:", hex_dig)
```

---
### Задачи 
1. вывести ascii table в виде красивой таблицы 
2. ROT13 - написать функцию реализации шифра 
3. xor шифрование и обмен значений для переменных 

потом
https://cryptohack.org/courses/intro

```python
# Исходное сообщение
message = "HELLO"

# байты ASCII
ascii_bytes = [ord(char) for char in message]

# байты ASCII в шестнадцатеричные значения
hex_bytes = [hex(byte) for byte in ascii_bytes]

# base-16
base16_str = "0x" + "".join([hex_byte[2:] for hex_byte in hex_bytes])
base16_int = int(base16_str, 16)

# base-16 в base-10
base10_int = int(base16_str, 16)

# Выводим результаты
print("Message:", message)
print("ASCII bytes:", ascii_bytes)
print("Hex bytes:", hex_bytes)
print("Base-16:", base16_str)
print("Base-10:", base10_int)
```

