# RamFi - Beta

```markdown
*RamFI 8.0* — это скрипт на Python, предоставляющий несколько системных утилит в удобном интерфейсе командной строки. Скрипт включает функции изменения MAC-адреса, просмотра сохранённых паролей Wi-Fi и отображения системной информации. Интерфейс имеет красочное ASCII-меню с градиентом, что делает использование программы более приятным.

## Возможности

- *Изменение MAC-адреса*: Позволяет изменить MAC-адрес указанного сетевого интерфейса.
- *Просмотр пароля Wi-Fi*: Отображает сохранённый пароль для указанного SSID Wi-Fi.
- *Системная информация*: Показывает информацию об операционной системе, имени устройства и текущем MAC-адресе.
- *Стильный интерфейс*: Цветное ASCII-меню с плавным градиентом для выбора опций.
- *Авторы*: Отображает информацию об авторах проекта.

## Требования

- Python 3.x
- Необходимы права `sudo` для выполнения некоторых функций, таких как изменение MAC-адреса или доступ к конфигурационным файлам Wi-Fi.

## Установка

1. Клонируйте репозиторий:
    ```bash
    git clone https://github.com/masovskiy/RamFI.git
    cd multitool
    ```

2. Установите необходимые зависимости:
    ```bash
    pip install -r requirements.txt
    ```

## Использование

1. Запустите скрипт через Python:
    ```bash
    python main.py
    ```

2. Следуйте инструкциям на экране для выбора опции:

```                                   8.0
██████╗  █████╗ ███╗   ███╗███████╗██╗
██╔══██╗██╔══██╗████╗ ████║██╔════╝██║
██████╔╝███████║██╔████╔██║█████╗  ██║
██╔══██╗██╔══██║██║╚██╔╝██║██╔══╝  ██║
██║  ██║██║  ██║██║ ╚═╝ ██║██║     ██║
╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝     ╚═╝
```

3. Доступные опции меню:
    1. **Изменить MAC-адрес**: Введите имя сетевого интерфейса (например, `eth0`, `wlan0`) и новый MAC-адрес.
    2. **Показать пароль Wi-Fi**: Введите SSID Wi-Fi сети для отображения пароля.
    3. **Показать системную информацию**: Показывает информацию об ОС, имени устройства и MAC-адресе.
    4. **Авторы**: Показывает информацию об авторах скрипта.
    5. **Выход**: Выход из программы.

## Пример

Пример изменения MAC-адреса:
```bash
[+] Изменение MAC-адреса для wlan0 на 00:11:22:33:44:55
[+] MAC-адрес успешно изменён на 00:11:22:33:44:55!
```

Пример получения пароля Wi-Fi:
```bash
[+] Пароль от Wi-Fi для MyNetwork: mypassword123
```

## Заметки

- **Изменение MAC-адреса**: Убедитесь, что у вас есть права на изменение сетевых конфигураций.
- **Пароль Wi-Fi**: Данная опция работает только в том случае, если вы уже подключались к сети, и у вас есть необходимые конфигурационные файлы.
- Скрипт тестировался на **Linux** с использованием **NetworkManager**.

## Авторы

- **Роман Масовский** (unimas.maiers)
- **Артем RamOf** (ram_off47)

## Лицензия

Этот проект распространяется под лицензией GNU. Подробнее см. файл [LICENSE](LICENSE).
```

