# Analog_Night_Light
Полностью Аналоговый ночник с подстройкой срабатывания в темноте и плавным зажиганием и затуханием, никаких МК.

A fully analog night light with adjustable activation in the dark and smooth lighting and fading, no microcontrollers.
## Функции

- Датчик движения PIR (AM312)
- Датчик освещенности с регулируемым порогом (фоторезистор + компаратор)
- Плавное включение / выключение (~4-5 секунд)
- ШИМ-регулировка яркости (~ 2000 Гц)
- Нет микроконтроллера, полностью аналоговый дизайн

## Как это работает

1. Датчик AM312 PIR обнаруживает движение.
2. Фоторезистор + компаратор проверяют, не потемнел ли он.
3. Транзистор И затвор объединяют оба сигнала.
4. RC-схема создает медленно изменяющееся напряжение для плавного затемнения.
5. NE555 генерирует линейный сигнал для ШИМ.
6. Компаратор LM358 генерирует ШИМ-сигнал.
7. MOSFET переключает светодиодную ленту напряжением 12 В.

## Структурная схема
![Блок-схема устройства]<img width="970" height="1061" alt="i" src="https://github.com/user-attachments/assets/1d3f8e8a-38b8-451b-85e0-d86f2d07c3c3" />

## Перечень элементов
Силовая часть LM317, 12V -> 5V
Пиродатчик AM312
Блок темноты GL5537, LM358, 100k pot
Монтажное И 2x BC817, 10k resistors
RC - память 47k, 100uF
Усилитель LM358, 2x 1k (gain = 2)
Генератор пилы NE555, BC807, 1k, 10k, 100nF
ШИМ компаратор LM358
Силовой ключ 2N7002, 100 Ohm, 510k
Нагрузка 12V LED strip

### Симуляция
Вот [здесь](Simulation.md) можете ознакомится с объяснением и симуляцией каждого блока "Ночника"

## Статус
Прототип собран и протестирован, печатная плата заказана

## Features

- PIR motion detection (AM312)
- Light sensor with adjustable threshold (photoresistor + comparator)
- Smooth fade-in / fade-out (~4-5 seconds)
- PWM brightness control (~300 Hz)
- No MCU, fully analog design

## How It Works

1. AM312 PIR sensor detects motion.
2. Photoresistor + comparator check if it is dark.
3. Transistor AND gate combines both signals.
4. RC circuit creates a slowly changing voltage for smooth dimming.
5. NE555 generates a ramp signal for PWM.
6. LM358 comparator generates PWM signal.
7. MOSFET switches the 12V LED strip.

## Block Diagram
![Block Diagram]<img width="970" height="1017" alt="i (1)" src="https://github.com/user-attachments/assets/1bb71fd0-0665-44b9-8f39-d9f2b1522ba8" />


## Block Components
Power LM317, 12V -> 5V
Motion Sensor AM312
Light Sensor GL5537, LM358, 100k pot
AND Gate 2x BC817, 10k resistors
RC Circuit 47k, 100uF
Amplifier LM358, 2x 1k (gain = 2)
Ramp Generator NE555, BC807, 1k, 10k, 100nF
PWM Comparator LM358
Power Switch 2N7002, 100 Ohm, 510k
Load 12V LED strip

### Simulation
[Here](Simulation.md) you can familiarize yourself with the explanation and simulation of each block of the “Night Light”.

## Status
The prototype has been assembled and tested, the printed circuit board has been ordered.
