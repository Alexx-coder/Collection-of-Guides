# Projects for Lesson 3 of Python

Проект для Lesson 3

## Проект

### Обновленный Auth

- Мы переделаем прошлый код Auth (из Projects for Lesson 2 of Python)

- Напечатайте:

```python
import sys # Импорт модуля sys где встроены функции (Стандартная библиотека)

print("=== Auth ===")
name = input("[?] Имя: ")
if len(name) < 3:
    print("Нельзя")
    sys.exit(0) # Аварийное завершение программы

else:
    print("[*] Теперь пароль")
    pswd = input("[?] Пароль: ")
    if len(pswd) < 6:
        print("Нельзя")
        sys.exit(0)

    else:
        print("[+] Готово!")
        print("=== Ваши данные ===")
        print(f'[*] Имя: {name} | Пароль: {pswd}') # В реальных программах без вывода пароля - небезопасно
```

- Готово вы обновили Auth! На этом всё! Попробуйте написать свои программы или добавить что-то в Auth...

## Примечания

- Данный репозиторий лицензирован MIT LICENSE - см.файл LICENSE