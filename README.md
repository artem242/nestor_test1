*****
Описание кода автоматизации действий в игре
Общая информация
Код представляет собой скрипт для автоматизации действий в игре, используя библиотеки pyautogui, keyboard и random. Скрипт выполняет клики мышью, нажатия клавиш и случайные движения.

Импорт библиотек
import pyautogui
import time
import keyboard
import random
Глобальные переменные
running = False  # Флаг для управления работой скрипта
Основные функции
right_click(delay)
Эмулирует правый клик с задержкой:

pyautogui.mouseDown(button='right')
time.sleep(delay / 1000)
pyautogui.mouseUp(button='right')
press_release_ctrl(duration)
Нажатие и отпускание левой клавиши Ctrl:

pyautogui.keyDown('ctrl left')
time.sleep(duration / 1000)
pyautogui.keyUp('ctrl left')
left_clicks()
Случайное количество левых кликов (4-8 раз):

numberOfClicks = random.randint(4, 8)
for _ in range(numberOfClicks):
    pyautogui.click(button='left')
    time.sleep(1)
random_direction()
Случайное движение (W/A/S/D) с задержкой 0.5-1.5 сек:

keys = ['w', 'a', 's', 'd']
key = random.choice(keys)
pyautogui.keyDown(key)
delay = random.randint(500, 1500) / 1000
time.sleep(delay)
pyautogui.keyUp(key)
click(x, y)
Клик по указанным координатам:

pyautogui.moveTo(x, y, 0.5)
pyautogui.click(x, y)
toggle_running(event)
Переключение состояния скрипта (F12 по умолчанию):

keyboard.on_press_key('F12', toggle_running)
Основная логика скрипта
def main():
    intro()
    try:
        while True:
            if running:
                # Клик по кнопкам (координаты для 1920x1080)
                click(1823, 917)  # Ready
                click(1819, 1022)  # Continue
                click(1372, 660)   # Continue Popup
                
                # Основные действия
                press_release_ctrl(3000)  # 3 сек
                for _ in range(10):
                    right_click(3000)
                    if _ % 5 == 0:
                        random_direction()
                random_direction()
                left_clicks()
                random_direction()
                left_clicks()
            time.sleep(0.1)
    except KeyboardInterrupt:
        print("Bot stopped")
Особенности реализации
Обработка исключений: скрипт корректно завершает работу при прерывании (Ctrl+C)

Адаптация под разрешения: в комментариях указаны координаты для 1280x720

Случайность: использование random для имитации человеческого поведения

Рекомендации по использованию
Перед запуском проверьте:

Установлены ли библиотеки: pip install pyautogui keyboard

Соответствует ли разрешение экрана указанным координатам

Для остановки скрипта:

Нажмите F12 (по умолчанию)

Или прервите выполнение (Ctrl+C в терминале)

Для изменения горячих клавиш:

keyboard.on_press_key('ваша_клавиша', toggle_running)
