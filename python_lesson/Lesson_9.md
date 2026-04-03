# Lesson 9 of Python

**В данном уроке мы изучим строки...**

## Начинаем изучение

### Строки

- Вы уже замечали какие-то неизвестные функции (тот же .strip()) и думали что это? Давайте разберём

- Запишите (вы поймёте как работает):

```python
# Создать
text = "Hello, Elliot!"

# Длина
len(text)  # 14

# Получить символ
text[0]    # 'H'
text[-1]   # '!'

# Вырезать (срез)
text[0:5]  # 'Hello'
text[7:]   # 'Elliot!'

# Методы
text.lower()      # 'hello, elliot!'
text.upper()      # 'HELLO, ELLIOT!'
text.replace("Elliot", "Alexx")  # 'Hello, Alexx!'
text.split()      # ['Hello,', 'Elliot!']
text.split(",")   # ['Hello', ' Elliot!']

# Проверки
text.startswith("Hello")  # True
text.endswith("!")        # True
"Elliot" in text          # True

# Удалить пробелы
"  hi  ".strip()   # 'hi'

# Собрать из списка
words = ["Hello", "world"]
" ".join(words)    # 'Hello world'
```

- Да, вы скажете что это мало - но вы знаете многое, но изучать вам намного больше...

## Итог

- Вы молодцы! Знаете теперь как работать со строками и тд! На этот раз не будет Projects_Lesson_9.md

- Следующая остановка: Терминал программисту...
