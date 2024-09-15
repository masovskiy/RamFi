import sys
import subprocess
import platform
import uuid


# Функция для создания градиента между двумя цветами
def interpolate_color(color1, color2, factor):
    return tuple(int(color1[i] + factor * (color2[i] - color1[i])) for i in range(3))


# ANSI код для цвета текста (градиент фиолетово-розовый)
def gradient_text(text):
    # Основные цвета градиента
    start_color = (148, 0, 211)  # Фиолетовый
    end_color = (255, 20, 147)  # Ярко-розовый

    lines = text.splitlines()  # Разбиваем текст на строки
    total_lines = len(lines)  # Получаем количество строк

    reset_color = "\033[0m"

    # Проходим по каждой строке
    for i, line in enumerate(lines):
        # Вычисляем коэффициент для плавного перехода по цвету
        factor = i / (total_lines - 1) if total_lines > 1 else 1
        # Интерполируем цвет для текущей строки
        color = interpolate_color(start_color, end_color, factor)
        # Преобразуем цвет в ANSI-формат
        ansi_color = f"\033[38;2;{color[0]};{color[1]};{color[2]}m"
        # Выводим строку с нужным цветом
        sys.stdout.write(f"{ansi_color}{line}{reset_color}\n")


# Функция для изменения MAC-адреса
def change_mac(interface, new_mac):
    try:
        print(f"[+] Изменение MAC-адреса для {interface} на {new_mac}")
        subprocess.run(["sudo", "ifconfig", interface, "down"])
        input('sudo>')
        subprocess.run(["sudo", "ifconfig", interface, "hw", "ether", new_mac])
        input('sudo>')
        subprocess.run(["sudo", "ifconfig", interface, "up"])
        input('sudo>')
        print(f"[+] MAC-адрес успешно изменён на {new_mac}!")
    except Exception as e:
        print(f"[-] Ошибка при изменении MAC-адреса: {e}")


# Функция для просмотра пароля Wi-Fi
def show_wifi_password(ssid):
    try:
        result = subprocess.run(
            ["sudo", "cat", f"/etc/NetworkManager/system-connections/{ssid}.nmconnection"],
            capture_output=True, text=True)

        if "psk=" in result.stdout:
            password = result.stdout.split("psk=")[1].split("\n")[0]
            print(f"[+] Пароль от Wi-Fi для {ssid}: {password}")
        else:
            print(f"[-] Пароль для сети {ssid} не найден.")
    except Exception as e:
        print(f"[-] Не удалось получить пароль Wi-Fi: {e}")


# Функция для вывода системной информации
def system_info():
    system = platform.system()
    node = platform.node()
    mac = ':'.join(['{:02x}'.format((uuid.getnode() >> elements) & 0xff)
                    for elements in range(0, 2 * 6, 8)][::-1])

    print(f"Операционная система: {system}")
    print(f"Имя устройства: {node}")
    print(f"MAC-адрес: {mac}")


# Красивое ASCII-меню для выбора
def ascii_menu():
    menu = r'''
    ██████████████████████████████████████
    ████ 1. Изменить MAC-адрес        ████
    ██████████████████████████████████████
    ████ 2. Показать пароль Wi-Fi     ████
    ██████████████████████████████████████
    ████ 3. Показать системную инфо   ████
    ██████████████████████████████████████
    ████ 4. Авторы                    ████
    ██████████████████████████████████████
    ██████████████████████████████████████
    ████ 5. Выход                     ████
    ██████████████████████████████████████
    '''
    gradient_text(menu)


# Меню для запуска функций
def main_menu():
    banner = r'''
                                          8.0
    ██████╗  █████╗ ███╗   ███╗███████╗██╗
    ██╔══██╗██╔══██╗████╗ ████║██╔════╝██║
    ██████╔╝███████║██╔████╔██║█████╗  ██║
    ██╔══██╗██╔══██║██║╚██╔╝██║██╔══╝  ██║
    ██║  ██║██║  ██║██║ ╚═╝ ██║██║     ██║
    ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═╝     ╚═╝                                                                    
    '''

    gradient_text(banner)

    ascii_menu()

    choice = input(">")

    if choice == "1":
        interface = input("Введите имя интерфейса (например, eth0 или wlan0): ")
        new_mac = input("Введите новый MAC-адрес: ")
        change_mac(interface, new_mac)
    elif choice == "2":
        ssid = input("Введите SSID Wi-Fi сети: ")
        show_wifi_password(ssid)
    elif choice == "3":
        system_info()
    elif choice == "4":
        gradient_text("Авторы: Roman Masovskiy(unimas.maiers), Artem RamOf(ram_off47)")
        sys.exit()
    elif choice == "5":
        print("Выход...")
        sys.exit()
    else:
        print("Некорректный выбор. Попробуйте снова.")
        main_menu()


# Запуск мультитула
if __name__ == "__main__":
    main_menu()
