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
3. Транзисторное И объединяют оба сигнала.
4. RC-схема создает медленно изменяющееся напряжение для плавного затемнения.
5. NE555 генерирует пилообразный сигнал.
6. Компаратор LM393 генерирует ШИМ-сигнал.
7. MOSFET переключает светодиодную ленту напряжением 12 В.

## Структурная схема
<img width="772" height="442" alt="Блок-схема ночника drawio" src="https://github.com/user-attachments/assets/81ce2aeb-d739-4148-a335-5a4db56e940b" />


## Текстовый блок

Силовая часть LM317, 12V -> 5V

Пиродатчик AM312

Блок темноты GL5537, LM358.

Монтажное И 2x BC817.

RC - память 47k, 100uF

Усилитель LM358, 2x 1k (gain = 2)

Генератор пилы NE555

ШИМ компаратор LM393

Силовой ключ 2N7002

Нагрузка 12V LED strip

### Симуляция
Вот [здесь](Simulation.md) можете ознакомится с объяснением и симуляцией каждого блока "Ночника"
### Разработка печатной платы
Вот [здесь](PCB%20Design.md) можете ознакомится с топологией печатной платы аналогового "Ночника"
### Прототип и реальная плата
Вот [здесь](HARDWAY.md) можете увидеть тот самый прототип печатной платы и саму печатную плата. Заказывалась она на PCBpi ( Российское представительство JLCPCB )

## Статус
Прототип собран и протестирован, печатная плата приехала и собрана.

## Features

- PIR motion detection (AM312)
- Light sensor with adjustable threshold (photoresistor + comparator)
- Smooth fade-in / fade-out (~4-5 seconds)
- PWM brightness control (~300 Hz)
- No MCU, fully analog design

## How It Works

1. AM312 PIR sensor detects motion.
2. Photoresistor + comparator check if it is dark.
3. A transistor AND gate combines both signals.
4. RC circuit creates a slowly changing voltage for smooth dimming.
5. The NE555 generates a sawtooth signal.
6. LM393 comparator generates PWM signal.
7. MOSFET switches the 12V LED strip.

## Block Diagram
<img width="792" height="441" alt="Блок-схема ночника ENG" src="https://github.com/user-attachments/assets/4459ea39-d300-4188-9355-0ea4fc222cdd" />




## Block Components
Power LM317, 12V -> 5V

Motion Sensor AM312

Light Sensor GL5537, LM358.

AND Gate 2x BC817.

RC Circuit 47k, 100uF

Amplifier LM358, 2x 1k (gain = 2)

Ramp Generator NE555.

PWM Comparator LM393

Power Switch 2N7002.

Load 12V LED strip

### Simulation
[Here](Simulation.md) you can familiarize yourself with the explanation and simulation of each block of the “Night Light”.
### PCB Design
You can find the PCB topology for the analog “Night Light” [here](PCB%20Design.md)
### Prototype and real board
[Here](HARDWAY.md) you can see the very prototype of the printed circuit board and the printed circuit board itself. It was ordered through PCBpi (the Russian representative office JLCPCB) 

## Status
The prototype has been assembled and tested; the printed circuit board has arrived and been assembled.
