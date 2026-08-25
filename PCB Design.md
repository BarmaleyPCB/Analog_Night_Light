### Топология печатной платы
В этом документе я расскажу о топологии печатной платы. Покажу компоновку каждого блока и правила которые настроил для проекта. Печатная плата разработана в Altium Designer, проект будет так же представлен в открытом доступе, но в отличие от документа с Симуляцией я выложу весь проект целиком в конце с GERBER файлами и отдельно файлы для производства.  

### Схемотехника
Начну этот документ с перерисованной схемой из Multisim. Перерисовал я её опираясь на Российский ГОСТ 2.702-2011 «Единая система конструкторской документации. Правила выполнения электрических схем». 

Объяснять и описывать каждый блок я не буду, так как это уже сделано [тут](Simulation.md)

[Принципиальная схема в PDF](https://github.com/user-attachments/files/31415455/Shematic.PDF.PDF)
## Сама принципиальная схема
<img width="1352" height="908" alt="Снимок экрана 2026-08-25 130828" src="https://github.com/user-attachments/assets/eb3d42e9-f220-421e-aa76-606f9c1449f9" />
Так как скриншот из самого САПР не очень хорошего качества я прикрепил файл PDF выше

### Параметры Печатной платы

| Параметр | Значение |
|:---|:---|
| Материал | FR-4 |
| Количество слоёв | 2 |
| Толщина текстолита | 1.5 мм |
| Толщина меди | 35 мкм (1 oz) |
| Форма | Т-образная |
| Размеры | 75 × 60 мм |
| Ширина сигнальных цепей | 0.3 mm |
| Ширина силовых цепей | 0.6 mm |
| Зазор  между элементами токопроводящих слоев  | 0.4 mm |
| Зазор между проводниками и полигонами | 0.5 mm |
| Минимальный отступ от края платы | 1 mm | 
| Диаметр монтажных отверстий (ТНТ элементы)  | 0.7 mm |
| Диаметром контактной площадки (пояска) | 1.1 mm |
| Диаметр монтажных отверстий (TP)  | 0.76 mm |
| Диаметром контактной площадки (пояска TP) | 1.5 mm |
| Диаметр переходных отверстий | 0.5 mm |
| Диаметром контактной площадки (пояска VIA) | 1 mm |
| Толщина линий шелкографии  | 0.2 mm |
| Высота линий шелкографии  | 1.2 mm |
| Переходные отверстия (VIA) | Закрыты паяльной маской (tenting) |

Все выводные элементы расположены на верхнем слое печатной платы. Элементы поверхностного монтажа находятся на нижнем слое печатной платы. 

Печатная плата имеет T образную форму специально чтобы светодиодная лента не засвечивала фоторезистор и он не думал, что постоянно темно. АМ312 выведен так же на противоположную сторону чтобы другие выводные элементы не перекрывали его.

### Внешний вид Печатной платы
3D вид сверху и снизу печатной платы
<img width="940" height="806" alt="3D t" src="https://github.com/user-attachments/assets/f0652883-fe97-42ac-8342-5018b1828619" />
<img width="996" height="760" alt="3D b" src="https://github.com/user-attachments/assets/44ba1171-e65c-4c88-a30c-bcba230be0a7" />


[PDF файл с 3D видом и принципиальной схемой](https://github.com/user-attachments/files/31417628/3D.PDF)

## Компоновка элементов
Компоновка печатной платы соответствует лучшим правилам проектирования. Все элементы определённого блока сгруппированы в одном месте.

На печатной плате есть полигон который находится на нижнем и верхнем слое платы. Он соединён с землёй. Не подключённых частей нет, все "мёртвые острова" удалены. Далее полигон будет удалён для демонстрации каждого блока. Все свободные выводы с сигналом GND подключены к полигону земли.

## Перечень элементов 


| Обозначение | Компонент | Номинал | Корпус | Кол-во |
|:---|:---|:---|:---|:---:|
| — | AM312 | PIR-датчик движения | Модуль | 1 |
| C1, C2 | Конденсатор керамический | 0.1 мкФ | 0805 | 2 |
| C4 | Конденсатор керамический | 1.5 нФ | 0805 | 1 |
| C3,C5 | Конденсатор керамический | 10 нФ | 0805 | 2 |
| C6 | Конденсатор электролитический |100 мкФ | выводной | 1 |
| CN1 | Штыревой разъём | DS1023-1x4 | DS1023-1x4 | 2 |
| DA1 | Стабилизатор напряжения | LM317 | SOT-223 | 1 |
| DA2 | Таймер | NE555 | SOIC-8 | 1 |
| DA3 | Операционный усилитель | LM358 | SOIC-8 | 1 |
| DA4, DA5 | Компаратор | LM393 | SOIC-8 | 2 |
| R1, R2, R16 | Резистор | 1 кОм | 0805 | 3 |
| R3 | Резистор | 240 Ом | 0805 | 1 |
| R4 | Резистор | 750 Ом | 0805 | 1 |
| R5, R7, R8, R10, R12, R13, R15, R17 | Резистор | 10 кОм | 0805 | 8 |
| R6 | Резистор подстроечный | 10 кОм | CA6V | 1 |
| R9 | Резистор | 100 Ом | 0805 | 1 |
| R11 | Резистор | 560 кОм | 0805 | 1 |
| R14 | Резистор | 47 кОм | 0805 | 1 |
| RP1 | Потенциометр | 100 кОм | CA6V | 1 |
| VT1 | Транзистор PNP | BC807 | SOT-23 | 1 |
| VT2 | Транзистор MOSFET | 2N7002 | SOT-23 | 1 |
| VT3, VT4 | Транзистор NPN | BC817 | SOT-23 | 2 |
| XP1 | Клеммник 2-контактный | TB-11A, 5 мм, прямой | — | 1 |
| XP2 | Клеммник 2-контактный | TB-11A, 5 мм, прямой | — | 1 |

### Питание схемы 

<img width="1347" height="903" alt="image" src="https://github.com/user-attachments/assets/0dd130f6-ce52-4203-bef3-0f02106f5cc5" />

### Генератор пилообразных сигналов 

<img width="1343" height="909" alt="image" src="https://github.com/user-attachments/assets/9af87ace-29b7-48c5-9f59-84516904fc85" />

Тут важный момент. Вторая часть LM358 используется так же в другом блоке и находится дальше от NE555

### Датчик темноты

<img width="1347" height="904" alt="image" src="https://github.com/user-attachments/assets/5ea0f574-78a9-4d48-a19e-d7718f7e0eac" />

PR1 выведен на центр платы для удобства использования и компоновки.

### Логика плавного включения и её усиление

<img width="1352" height="904" alt="image" src="https://github.com/user-attachments/assets/d512301c-3d67-4518-b37e-4f8b0472650d" />

### Коммутация

<img width="1347" height="904" alt="image" src="https://github.com/user-attachments/assets/449b085d-3d0a-4cf1-a8a5-773a9e7d56eb" />

## Тест - поинты
Для моего устройства я вывел TP. Они здорово помогли при тестах и монтаже когда исправлялись ошибки и с них можно получить интересные сигналы. Их я показал на этапе [Симуляции](Simulation.md) и в физическом Прототипе устройства.

| Test-point | Сигнал |
|:---|:---|
| TP1 | +5В |
| TP2 | Выход AM312 |
| TP3 | Выход датчика темноты |
| TP4 | Пилообразный сигнал |
| TP5 | Выход RC-цепи |
| TP6 | Затвор MOSFET |

## Крепёжные отверстия 
На печатной плате предусмотрены 4 крепёжных отверстия диаметром 3.2 мм под винты M3. На момент написания этого документа у меня нет корпуса под устройство. Но как он появится я его продемонстрирую отдельным документом.
### Проект
Вот весь [проект](Night_Light_Altium.zip) Altium в котором вы сможете найти всё что захотите включая файлы для производства

## PCB Layout

In this document I will describe the PCB layout, show the placement of each block, and the design rules I configured for the project. The PCB was designed in Altium Designer. The project will also be publicly available, but unlike the Simulation document, I will provide the entire project at the end, including GERBER files and separate production files.

### Schematic

I will start this document with the schematic redrawn from Multisim. I redrew it following the Russian standard GOST 2.702-2011 "Unified System for Design Documentation. Rules for Execution of Electric Diagrams."

I will not explain and describe each block here, as it has already been done [here](Simulation.md).

[Schematic in PDF](https://github.com/user-attachments/files/31415455/Shematic.PDF.PDF)

## Schematic Diagram

<img width="1352" height="908" alt="Снимок экрана 2026-08-25 130828" src="https://github.com/user-attachments/assets/eb3d42e9-f220-421e-aa76-606f9c1449f9" />

Since the screenshot from the CAD itself is not of very good quality, I attached the PDF file above.

### PCB Parameters

| Parameter | Value |
|:---|:---|
| Material | FR-4 |
| Number of layers | 2 |
| PCB thickness | 1.5 mm |
| Copper thickness | 35 µm (1 oz) |
| Shape | T-shaped |
| Dimensions | 75 × 60 mm |
| Signal trace width | 0.3 mm |
| Power trace width | 0.6 mm |
| Clearance between conductive layer elements | 0.4 mm |
| Clearance between traces and polygons | 0.5 mm |
| Minimum distance from board edge | 1 mm |
| Mounting hole diameter (THT components) | 0.7 mm |
| Pad diameter (annular ring) | 1.1 mm |
| Mounting hole diameter (TP) | 0.76 mm |
| Pad diameter (TP annular ring) | 1.5 mm |
| Via diameter | 0.5 mm |
| Pad diameter (VIA annular ring) | 1 mm |
| Silkscreen line thickness | 0.2 mm |
| Silkscreen line height | 1.2 mm |
| Vias | Tented (covered with solder mask) |

All through-hole components are placed on the top layer of the PCB. Surface-mount components are located on the bottom layer.

The PCB has a T-shape specifically so that the LED strip does not illuminate the photoresistor and make it think that it is constantly dark. The AM312 is also placed on the opposite side so that other through-hole components do not block it.

### PCB Appearance

3D view from top and bottom of the PCB.

<img width="940" height="806" alt="3D t" src="https://github.com/user-attachments/assets/f0652883-fe97-42ac-8342-5018b1828619" />

<img width="996" height="760" alt="3D b" src="https://github.com/user-attachments/assets/44ba1171-e65c-4c88-a30c-bcba230be0a7" />

[PDF file with 3D view and schematic](https://github.com/user-attachments/files/31417628/3D.PDF)

## Component Placement

The PCB layout follows good design practices. All components of a particular block are grouped in one place.

The PCB has a ground polygon on both the bottom and top layers. It is connected to ground. There are no unconnected parts; all "dead islands" have been removed. The polygon will be hidden below to demonstrate each block. All unconnected GND pins are connected to the ground polygon.

## Bill of Materials

| Designator | Component | Value | Package | Qty |
|:---|:---|:---|:---|:---:|
| — | AM312 | PIR motion sensor | Module | 1 |
| C1, C2 | Ceramic capacitor | 0.1 µF | 0805 | 2 |
| C4 | Ceramic capacitor | 1.5 nF | 0805 | 1 |
| C3, C5 | Ceramic capacitor | 10 nF | 0805 | 2 |
| C6 | Electrolytic Capacitor | 100 uF| THT | 1 |
| CN1 | Pin header | DS1023-1x4 | DS1023-1x4 | 2 |
| DA1 | Voltage regulator | LM317 | SOT-223 | 1 |
| DA2 | Timer | NE555 | SOIC-8 | 1 |
| DA3 | Operational amplifier | LM358 | SOIC-8 | 1 |
| DA4, DA5 | Comparator | LM393 | SOIC-8 | 2 |
| R1, R2, R16 | Resistor | 1 kΩ | 0805 | 3 |
| R3 | Resistor | 240 Ω | 0805 | 1 |
| R4 | Resistor | 750 Ω | 0805 | 1 |
| R5, R7, R8, R10, R12, R13, R15, R17 | Resistor | 10 kΩ | 0805 | 8 |
| R6 | Trimmer resistor | 10 kΩ | CA6V | 1 |
| R9 | Resistor | 100 Ω | 0805 | 1 |
| R11 | Resistor | 560 kΩ | 0805 | 1 |
| R14 | Resistor | 47 kΩ | 0805 | 1 |
| RP1 | Potentiometer | 100 kΩ | CA6V | 1 |
| VT1 | PNP transistor | BC807 | SOT-23 | 1 |
| VT2 | MOSFET transistor | 2N7002 | SOT-23 | 1 |
| VT3, VT4 | NPN transistor | BC817 | SOT-23 | 2 |
| XP1 | Terminal block 2-pin | TB-11A, 5 mm, straight | — | 1 |
| XP2 | Terminal block 2-pin | TB-11A, 5 mm, straight | — | 1 |

### Power Supply

<img width="1347" height="903" alt="image" src="https://github.com/user-attachments/assets/0dd130f6-ce52-4203-bef3-0f02106f5cc5" />

### Ramp Generator

<img width="1343" height="909" alt="image" src="https://github.com/user-attachments/assets/9af87ace-29b7-48c5-9f59-84516904fc85" />

There is an important note here. The second half of the LM358 is also used in another block and is located farther from the NE555.

### Light Sensor

<img width="1347" height="904" alt="image" src="https://github.com/user-attachments/assets/5ea0f574-78a9-4d48-a19e-d7718f7e0eac" />

PR1 is placed in the center of the board for ease of use and placement.

### Smooth Turn-On Logic and Its Amplification

<img width="1352" height="904" alt="image" src="https://github.com/user-attachments/assets/d512301c-3d67-4518-b37e-4f8b0472650d" />

### Switching

<img width="1347" height="904" alt="image" src="https://github.com/user-attachments/assets/449b085d-3d0a-4cf1-a8a5-773a9e7d56eb" />

## Test Points

I added test points to my device. They were very helpful during testing and assembly when errors were being fixed, and you can get interesting signals from them. I showed them in the [Simulation](Simulation.md) stage and in the physical Prototype of the device.

| Test-point | Signal |
|:---|:---|
| TP1 | +5V |
| TP2 | AM312 output |
| TP3 | Light sensor output |
| TP4 | Ramp signal |
| TP5 | RC circuit output |
| TP6 | MOSFET gate |

## Mounting Holes

The PCB has 4 mounting holes with a diameter of 3.2 mm for M3 screws. At the time of writing this document, I do not have an enclosure for the device. As soon as it appears, I will demonstrate it in a separate document.

### Project

Here is the entire Altium [project](Night_Light_Altium.zip) where you can find everything you want, including production files.








