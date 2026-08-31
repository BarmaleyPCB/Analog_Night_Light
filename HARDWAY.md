# Hardware Prototype
В этом файле я сначала покажу свою макетную плату и большую часть TP, а потом собранную печатную плату. Сразу скажу, что я держался кабель менеджменту : использовал красные и чёрные провода как силовые, определённые провода которые показывают определённый сигнал... Но провода нужных цветов просто закончились. По этому заранее прошу прощения у эстетов
## Макетная плата
Про [симуляцию](Simulation.md) и [топологию](PCB%20Design.md) печатной платы я ничего говорить не буду так как уже описал их в других файлах. 
### Блоки
Краткое напоминание TP :
| Test-point | Сигнал |
|:---|:---|
| TP1 | +5В |
| TP2 | Выход AM312 |
| TP3 | Выход датчика темноты |
| TP4 | Пилообразный сигнал |
| TP5 | Выход RC-цепи |
| TP6 | Затвор MOSFET |
## Макетная плата
Вот сама макетная плата и "куст" из проводов
<img width="1920" height="1080" alt="0c96d938-aee6-4802-9a00-018a0de24985" src="https://github.com/user-attachments/assets/5eee5bcc-b70a-4808-a095-f1e08e2e012f" />
<img width="1080" height="1920" alt="a3ad4d92-b805-4206-bd23-61680e0facb8" src="https://github.com/user-attachments/assets/71b32da0-b4a1-4cb4-8a45-71e0fde1cf40" />
<img width="1920" height="1080" alt="2957231d-a6b4-41a8-9f16-cd539f25e01c" src="https://github.com/user-attachments/assets/32d5eeb1-5d55-4790-a249-edbe212e21da" />
<img width="1920" height="1080" alt="f796b7ca-c7d2-4cb0-b45b-eba0343b1b2c" src="https://github.com/user-attachments/assets/598b8c58-c0f7-475c-add9-5edd16a33477" />

## Силовая часть 
На лабораторном блоке питания выставляем следующие характеристики : 12 V, 0.1 A

<img width="1920" height="1080" alt="c81ee30f-a627-42d7-969d-8e8f30e27dd9" src="https://github.com/user-attachments/assets/bdaa05b2-3beb-459b-b751-85184489479b" />

При 12 входящих Вольт на выходе LM317 получаем 5.2 V ( показания с Вольтметра взяты не с выхода LM317, а выведены отдельным проводом на макетной плате )
<img width="1080" height="1920" alt="5206265d-a252-4a2f-9a39-10dff1d5b974" src="https://github.com/user-attachments/assets/374ea689-3299-41d3-9b10-ac7eb9482332" />
## AM312
Работает максимально просто : есть движение на выходе сигнал высокого уровня 3.3 V
<img width="1920" height="1080" alt="9865d84b-59c1-4907-afe2-6a82da75c454" src="https://github.com/user-attachments/assets/67a67708-a266-47c7-a3f4-313002f36fbb" />

https://github.com/user-attachments/assets/ed6206b0-8b9e-4b82-a8dd-8758b66b2553
## Генератор пилообразных сигналов
<img width="1080" height="1920" alt="13fd9d1d-04b9-4110-89f1-3739e7068539" src="https://github.com/user-attachments/assets/953370c8-4064-4bba-a1ba-8e8323dc273d" />
<img width="1920" height="1080" alt="058eaf05-7bde-44a3-94d8-14d190c59fe4" src="https://github.com/user-attachments/assets/4b762efa-99a5-4cd5-ba7a-4c940d095e5e" />

## Светодиодная лента
Светодиодная лента короткая, но я думаю больше одного метра в этом устройстве не пригодится

Фото светодиодной ленты и показания с лабораторного блока питания при свечении светодиодной ленты
<img width="1920" height="1080" alt="15da9e50-62af-43cd-a03f-d77c420215b1" src="https://github.com/user-attachments/assets/d07ec6db-a291-4297-8a31-20f027ef5574" />
<img width="1920" height="1080" alt="9df0a628-0125-49e9-bfef-76b5a593ef13" src="https://github.com/user-attachments/assets/0136f479-880c-471a-b6ad-6251f77a50e8" />

Вообще ограничение я ставил 150 мкА, но когда игрался с ограничением по току не стал менять со 100 мкА

## Коммутация


https://github.com/user-attachments/assets/e4a824a5-5326-4761-bd0c-d3a4cc7636f6

# Hardware Prototype

In this file I will first show my breadboard and most of the test points, and then the assembled PCB. Let me say right away that I tried to maintain cable management: I used red and black wires for power, and specific wires for specific signals... But the wires of the required colors simply ran out. So I apologize in advance to the aesthetes.

## Breadboard

I will not talk about the [simulation](Simulation.md) and [PCB layout](PCB%20Design.md), as I have already described them in other files.

### Blocks

A quick reminder of the test points:

| Test-point | Signal |
|:---|:---|
| TP1 | +5V |
| TP2 | AM312 output |
| TP3 | Light sensor output |
| TP4 | Ramp signal |
| TP5 | RC circuit output |
| TP6 | MOSFET gate |

## Breadboard

Here is the breadboard itself and the "bush" of wires.

<img width="1920" height="1080" alt="0c96d938-aee6-4802-9a00-018a0de24985" src="https://github.com/user-attachments/assets/5eee5bcc-b70a-4808-a095-f1e08e2e012f" />

<img width="1080" height="1920" alt="a3ad4d92-b805-4206-bd23-61680e0facb8" src="https://github.com/user-attachments/assets/71b32da0-b4a1-4cb4-8a45-71e0fde1cf40" />

<img width="1920" height="1080" alt="2957231d-a6b4-41a8-9f16-cd539f25e01c" src="https://github.com/user-attachments/assets/32d5eeb1-5d55-4790-a249-edbe212e21da" />

<img width="1920" height="1080" alt="f796b7ca-c7d2-4cb0-b45b-eba0343b1b2c" src="https://github.com/user-attachments/assets/598b8c58-c0f7-475c-add9-5edd16a33477" />

## Power Section

On the laboratory power supply we set the following parameters: 12 V, 0.1 A.

<img width="1920" height="1080" alt="c81ee30f-a627-42d7-969d-8e8f30e27dd9" src="https://github.com/user-attachments/assets/bdaa05b2-3beb-459b-b751-85184489479b" />

With 12 V at the input, the LM317 output gives 5.2 V (the voltmeter readings were not taken from the LM317 output, but from a separate wire on the breadboard).

<img width="1080" height="1920" alt="5206265d-a252-4a2f-9a39-10dff1d5b974" src="https://github.com/user-attachments/assets/374ea689-3299-41d3-9b10-ac7eb9482332" />

## AM312

It works very simply: when motion is detected, the output is a high-level signal of 3.3 V.

<img width="1920" height="1080" alt="9865d84b-59c1-4907-afe2-6a82da75c454" src="https://github.com/user-attachments/assets/67a67708-a266-47c7-a3f4-313002f36fbb" />

https://github.com/user-attachments/assets/ed6206b0-8b9e-4b82-a8dd-8758b66b2553

## Ramp Generator

<img width="1080" height="1920" alt="13fd9d1d-04b9-4110-89f1-3739e7068539" src="https://github.com/user-attachments/assets/953370c8-4064-4bba-a1ba-8e8323dc273d" />

<img width="1920" height="1080" alt="058eaf05-7bde-44a3-94d8-14d190c59fe4" src="https://github.com/user-attachments/assets/4b762efa-99a5-4cd5-ba7a-4c940d095e5e" />

## LED Strip

The LED strip is short, but I think more than one meter will not be needed in this device.

Photo of the LED strip and readings from the laboratory power supply when the LED strip is lit.

<img width="1920" height="1080" alt="15da9e50-62af-43cd-a03f-d77c420215b1" src="https://github.com/user-attachments/assets/d07ec6db-a291-4297-8a31-20f027ef5574" />

<img width="1920" height="1080" alt="9df0a628-0125-49e9-bfef-76b5a593ef13" src="https://github.com/user-attachments/assets/0136f479-880c-471a-b6ad-6251f77a50e8" />

Actually, I set the current limit to 150 µA, but when I was playing with the current limit, I did not change it from 100 µA.

## Switching

https://github.com/user-attachments/assets/e4a824a5-5326-4761-bd0c-d3a4cc7636f6














