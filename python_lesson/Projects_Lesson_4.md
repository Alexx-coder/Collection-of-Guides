# Projects for Lesson 4 of Python

Проекты для Lesson 4 of Python

## Проекты

### Обновлённый Auth

- Мы опять перепишем и улучишим прошлый код `Auth` (из Projects for Lesson 4 of Python)

- В том же файле напечатайте:

```python
import time

print("=== Auth ===")
max_attempts = 3

for attempt in range(max_attempts):
    name = input("[?] Введите имя: ")
    if len(name) < 3:
        print("[-] Короткое имя!")
        time.sleep(1.5)
        continue
    elif len(name) > 40:
        print('[-] Большое имя!')
        time.sleep(1.5)
        continue
    
    paswd = input("[?] Введите пароль: ")
    if len(paswd) < 6:
        print("[-] Короткий пароль!")
        time.sleep(1.5)
        continue
    
    confirm = input("[?] Подтвердите пароль: ")
    if confirm != paswd:
        print("[-] Пароли не совпадают")
        time.sleep(1.5)
        continue
    
    print("[+] Готово!")
    time.sleep(3)
    print("\n=== Ваши данные ===")
    print(f'Ваше имя: {name}')
    break  # Выход из цикла for
else:
    print("[-] Слишком много попыток. Доступ закрыт.")
```

- Поздравляю программа написана! Вы можете сделать лучше и добавить свои функции! Вы молодцы, на этом всё!

## Примечания

- Данный репозиторий лицензирован MIT License - см.файл LICENSE

- Создатель репозитория: Alexx-coder или alexx