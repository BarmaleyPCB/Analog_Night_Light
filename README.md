# Analog_Night_Light
Полностью Аналоговый ночник с подстройкой срабатывания в темноте и плавным зажиганием и затуханием, никаких МК.

A fully analog night light with adjustable activation in the dark and smooth lighting and fading, no microcontrollers.
## Функции

- Датчик движения PIR (AM312)
- Датчик освещенности с регулируемым порогом (фоторезистор + компаратор)
- Плавное включение / выключение (~4-5 секунд)
- ШИМ-регулировка яркости (~ 2000 Гц)
- Нет микроконтроллера, полностью аналоговый дизайн

## Устройство

<img width="1080" height="1920" alt="image" src="https://github.com/user-attachments/assets/2228dc04-a7d9-46e6-980b-871a9f0969bd" />


## Структурная схема
<img width="772" height="442" alt="Блок-схема ночника drawio" src="https://github.com/user-attachments/assets/81ce2aeb-d739-4148-a335-5a4db56e940b" />


## Текстовый блок

Силовая часть устройства это LM317 которая преобразует из 12 V в 5 V.

Датчик темноты - это компаратор LM393 который сравнивает значения с делителя напряжения из фоторезистора и резистора и потенциометра который подстраивает порог срабатывания темноты

2-И из транзисторов который сравнивает сигналы с AM312 и с блока датчика темноты. На выходе стоит RC-цепь для плавного розжига ленты

ОУ LM358 с коэффициентом усиления 2 ( усиления сигнала после RC-цепи )

Генератор пилообразных сигналов на NE555

ШИМ - Компаратор который сравнивает пилу и сигнал с 2-И

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

## Device

<img width="1080" height="1920" alt="image" src="https://github.com/user-attachments/assets/170ae3c7-5e75-4c75-8cbb-6dfa418d1309" />


## Block Diagram
<img width="792" height="441" alt="Блок-схема ночника ENG" src="https://github.com/user-attachments/assets/4459ea39-d300-4188-9355-0ea4fc222cdd" />




## Block Components
The power stage of the device is based on an LM317, which converts 12V to 5V.

The darkness sensor uses an LM393 comparator, which compares the voltage from a divider—consisting of a photoresistor and a fixed resistor—against a threshold set by a potentiometer.

An AND gate (implemented using transistors) compares the signal from an AM312 sensor with the output from the darkness sensor circuit. An RC network is placed at the output to ensure a smooth "fade-in" (gradual illumination) of the LED strip.

An LM358 operational amplifier, configured with a gain of 2, amplifies the signal following the RC network.

An NE555 timer is used to generate a sawtooth waveform.

A PWM comparator compares this sawtooth signal with the output from the AND gate.

### Simulation
[Here](Simulation.md) you can familiarize yourself with the explanation and simulation of each block of the “Night Light”.
### PCB Design
You can find the PCB topology for the analog “Night Light” [here](PCB%20Design.md)
### Prototype and real board
[Here](HARDWAY.md) you can see the very prototype of the printed circuit board and the printed circuit board itself. It was ordered through PCBpi (the Russian representative office JLCPCB) 

## Status
The prototype has been assembled and tested; the printed circuit board has arrived and been assembled.
