# Projects for Lesson 6 of Python

Проект для Lesson 5 of Python и Lesson 6 of Python

## Проект

- Мы знаем многое и напишем программу с функциями

### Новый Auth - Теперь Lux Bot

- Я захотел переименовать наш Auth на Lux Bot

- Создайте файл `lux_bot.py` и напечатайте там:

```python
import sys
import time
import os
import getpass
from datetime import datetime
from pathlib import Path

print(f"[*] Ты в папке {Path.cwd()}")
print(f'[*] Пользователь в системе: {getpass.getuser()}')

print("\n=== Lux Bot ===")
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
    time.sleep(1)
    print("\n=== Ваши данные ===")
    print(f'Ваше имя: {name}')
    
    # Сохраняем в файл
    with open("meta.txt", "w", encoding='utf-8') as f:
        f.write(f"""=== Meta ===
name = {name}
password = {paswd}
time = {datetime.now()}
""")
    
    # Меню после успешного входа
    while True:
        print("\n=== Меню ===")
        print("/exit - Выход")
        print("/whoami - Кто я")
        print("/calculator - Калькулятор")
        
        choice = input("Введите команду: ").strip()
        
        if choice == "/exit":
            print("[+] До свидания!")
            sys.exit(0)
        
        elif choice == "/whoami":
            print(f"[*] В программе: {name}")
            print(f"[*] В системе: {getpass.getuser()}")
        
        elif choice == "/calculator":
            try:
                num1 = float(input("Введите первое число: "))
                sign = input("Введите знак (+, -, *, /): ").strip()
                num2 = float(input("Введите второе число: "))
                
                if sign == "+":
                    result = num1 + num2
                elif sign == "-":
                    result = num1 - num2
                elif sign == "*":
                    result = num1 * num2
                elif sign == "/":
                    if num2 == 0:
                        raise ZeroDivisionError("Деление на ноль")
                    result = num1 / num2
                else:
                    print("[-] Неизвестный знак")
                    continue
                
                print(f"[+] Результат: {result}")
            
            except ValueError:
                print("[-] Ошибка: нужно ввести числа!")
            except ZeroDivisionError as e:
                print(f"[-] Ошибка: {e}")
        
        else:
            print("[-] Неизвестная команда")
    
    break  # Выходим из цикла входа после успеха

else:
    print("[-] Слишком много попыток. Доступ закрыт.")
    sys.exit(1)
```

- Сразу говорю: в данном проекте мало функции, потому что нет ООП (позже узнаете), изучив ООП, наша программа станет удобной и лучше, а сейчас её архитектура без ООП - плохая (не делайте проекты серьёзные без ООП)

## Итог

- Мы обновили снова Auth (Lux Bot), теперь там есть функции, да слабая программа, ведь нет там ООП (скоро)

- Вы молодцы! Не забывайте гуглить свои ошибки или спрашивать ИИ, ответ найдётся!

## Примечания

- 