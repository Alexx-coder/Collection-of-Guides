# Projects for Lesson 8 of Python

Проекты для Lesson 8 of Python

## Проекты 

### Переделанный снова Lux Bot (в проошлом Auth)

- Давайте перепишем наш Lux Bot под ООП, результат вам понравится

- Сразу говорю, тут не будет криптографии и тд (то что я применяю в своих проектах, а то что реально написать), максимум могу добавить некоторые функции которые не изучали (ну бывает)

- Напечатайте:

```python
import sys
import time
import os
import getpass
from datetime import datetime
from pathlib import Path

class LuxBot:
    def __init__(self):
        self.name = "Lux Bot"
        self.logged_in = False
        self.current_user = None
    
    def menu(self):
        print(f"[*] Ты в папке {Path.cwd()}")
        print(f'[*] Пользователь в системе: {getpass.getuser()}')

        while True:
            print("\n=== Lux Bot ===")
            print("1 - Регистрация")
            print("2 - Вход")
            print("3 - Выход")

            choice = input("[?] Введите (1-3): ").strip()
            if choice == "1":
                self.registr()
            elif choice == "2":
                self.login()
            elif choice == "3":
                print("[+] До свидания!")
                sys.exit(0)
            else:
                print("[-] Неизвестная команда.")
        
    def registr(self):
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
            
            with open("meta.txt", "w", encoding='utf-8') as f:
                f.write(f"""name = {name}
password = {paswd}
time = {datetime.now()}
""")
            
            self.current_user = name
            self.functions()
            return

        print("[-] Слишком много попыток. Доступ закрыт.")
        self.menu()

    def login(self):
        if not os.path.exists("meta.txt"):
            print("[-] Сначала зарегистрируйтесь...")
            self.menu()
            return

        with open("meta.txt", "r", encoding='utf-8') as f:
            lines = f.readlines()
        
        saved_name = lines[0].split("=")[1].strip()
        saved_pass = lines[1].split("=")[1].strip()

        for attempt in range(3):
            name = input("[?] Введите имя: ").strip()
            paswd = input("[?] Введите пароль: ").strip()

            if name == saved_name and paswd == saved_pass:
                print("[+] Вход выполнен!")
                self.current_user = name
                self.functions()
                return
            else:
                print(f"[-] Неверно. Осталось {2 - attempt} попыток")
                time.sleep(1.5)

        print("[-] Слишком много попыток. Доступ закрыт.")
        self.menu()


    def functions(self):
        print("===== МЕНЮ ФУНКЦИЙ =====")
        time.sleep(2)
        while True:
            print("/calculator - Калькулятор")
            print("/notes - Заметки")
            print("/exit - Выход")
            choice = input("Введите: ").strip()
            if choice == "/calculator":
                print("[*] Перехожу...")
                time.sleep(3)
                self.calc()
            elif choice == "/notes":
                print("[*] Перехожу...")
                time.sleep(3)
                self.notes()
            elif choice == "/exit":
                print("[*] Пока!")
                time.sleep(3)
                sys.exit(0)
            else:
                print("[-] Неизвестная команда")
                continue
    
    def calc(self):
                try: # Не обращайте на отступы все хорошо
                    num1 = float(input("[?] Первое число: "))
                    sign = input("[?] Знак (+, -, *, /): ").strip()
                    num2 = float(input("[?] Второе число: "))

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
                except ZeroDivisionError:
                    print("[-] Нелья делить на ноль!")


    def notes(self):
      while True:
        print("\n=== Заметки ===")
        print("/add - Добавить")
        print("/list - Список")
        print("/del - Удалить")
        print("/back - Назад")
        
        cmd = input("[?] > ").strip()
        
        if cmd == "/add":
            text = input("Текст: ")
            with open("notes.txt", "a", encoding='utf-8') as f:
                f.write(f"{text}\n")
            print("[+] Добавлено")
        
        elif cmd == "/list":
            try:
                with open("notes.txt", "r", encoding='utf-8') as f:
                    for i, line in enumerate(f, 1):
                        print(f"{i}. {line.strip()}")
            except:
                print("[-] Нет заметок")
        
        elif cmd == "/del":
            try:
                with open("notes.txt", "r", encoding='utf-8') as f:
                    lines = f.readlines()
                
                for i, line in enumerate(lines, 1):
                    print(f"{i}. {line.strip()}")
                
                num = int(input("Номер: ")) - 1
                del lines[num]
                
                with open("notes.txt", "w", encoding='utf-8') as f:
                    f.writelines(lines)
                print("[+] Удалено")
            except:
                print("[-] Ошибка")
        
        elif cmd == "/back":
            break

if __name__ == '__main__':
    bot = LuxBot()
    bot.menu()
```

## Итог

- Вы молодцы! Мы написали программу где видно магию ООП, я написал мало функций, но знайте добавляйте свои (я показал примерно)! Вы так же можете смотреть на мои другие репозитории (проекты) и анализировать что как (В профила GitHub Alexx-coder или alexx)

## Примечания

- Данный репозиторий лицензирован MIT License - см.файл LICENSE

- Создатель репозитория: Alexx-coder или alexx