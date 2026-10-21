# Hardware Prototype
В этом файле я сначала покажу свою макетную плату и большую часть TP, а потом собранную печатную плату. Сразу скажу, что я держался кабель менеджменту : использовал красные и чёрные провода как силовые, определённые провода которые показывают определённый сигнал... Но провода нужных цветов просто закончились. По этому заранее прошу прощения у эстетов
## Макетная плата
Про [симуляцию](Simulation.md) и [топологию](PCB%20Design.md) печатной платы я ничего говорить не буду так как уже описал их в других файлах. 
### Блоки
Краткое напоминание TP :
| Test-point | Сигнал |
|:---|:---|
| TP1 | Выход датчика темноты |
| TP2 | Выход RC-цепи |
| TP3 | Выход датчика AM312 |
| TP4 | +5 |
| TP5 | Пилообразный сигнал |
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

### Собранная печатная плата
Вот и долгожданная плата. Перед описанием хочу добавить, что плата ехала чуть больше месяца. Это не проблема самого PCBpi так как само производство печатной платы ( аудит, производство, контроль импеданса ) заняло чуть меньше 2-х недель, плата ехала с таможни практически месяц. А так сама плата выглядит очень достойно : маска качественная, переходные отверстия закрыты аккуратно и так же качественно. Единственный обидный косяк я забыл скинуть файлы маски... Маской были закрыты все пады и пришлось аккуратно счищать маску скальпелем. 
<img width="1609" height="1416" alt="image" src="https://github.com/user-attachments/assets/12790851-4c18-4a74-9d43-830875676bdd" />
<img width="1548" height="1444" alt="image" src="https://github.com/user-attachments/assets/81559bfc-000c-409f-b338-3cb08fff7c08" />
## Cнятая маска
<img width="1549" height="1301" alt="image" src="https://github.com/user-attachments/assets/97c14765-a783-480a-8703-86c697fbd863" />
<img width="1440" height="1920" alt="image" src="https://github.com/user-attachments/assets/9c4b0320-9503-4084-a537-0bc85cc4c9fa" />

## Собранная плата сверху и снизу

<img width="1200" height="1001" alt="image" src="https://github.com/user-attachments/assets/2fd08d9b-603b-4b8a-8786-97e4181c44ad" />
<img width="1420" height="1131" alt="image" src="https://github.com/user-attachments/assets/b03f992b-0dc1-48be-a0df-2bf11d3afb13" />

### Снятие сигналов с Тест - поинтов

В некоторых случаях 1 квадрат на осциллограмме соответствует 1/V. Обращайте внимание на развёртку осциллографа.
## TP1

Снятие сигнала с выхода Датчика темноты

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/737bbde1-a8cb-4ec9-abf8-5ba5fe6a7bc2" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/5f7daa40-9ee9-444a-b70b-e15736e47e40" />
Подстройка порога срабатывания происходит с помощью потенциометра в центре. Для теста сделал порог срабатывания самым минимальным

## TP2

Снятие сигнала с выхода RC-цепи
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/4c439292-e630-42fd-b8bb-2030661ec490" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/f5813b48-a561-4e4a-bc66-6c0bca4863c8" />

## TP3

Снятие сигнала с выхода пироэлектрического датчика АМ312

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/46f7a416-df62-4d72-9fe8-c484765d5826" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/78b5b50a-9777-45e8-9021-c748c4b98894" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/c5e0d41b-2b56-4053-9132-964f4e728c34" />

## TP4

Снятие выходного сигнала с LM317

<img width="1152" height="532" alt="image" src="https://github.com/user-attachments/assets/78aeb03e-b669-48fa-81c5-64fc25398c4b" />

## TP5

Выход с генератора пилообразных сигналов

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/f0c2239e-ad59-4177-ba2b-7f8a2c1b9ec5" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/06bc285e-691a-41de-b5da-9ff30f036025" />

Мне очень нравится этот блок особенно какая красивая пила по итогу вышла.

## TP6

 ШИМ-Компоратор

https://github.com/user-attachments/assets/7b0deda1-3c4d-4122-befd-ddaa311a932d

## Демонстрация работы без сигналов


https://github.com/user-attachments/assets/0acb130c-9748-47a6-9404-83e3e99bafca

## Заключение

Проект успешно пройден по всем этапам: от симуляции в Multisim до сборки и отладки реального устройства на печатной плате. Полностью аналоговая схема (без единой строки кода) доказала свою работоспособность. Все ключевые блоки - датчики, логика, генератор пилы, ШИМ и силовой ключ — работают стабильно и согласованно.

Этот прототип стал отличным примером того, как классическая схемотехника решает задачи, для которых сегодня часто используют микроконтроллеры.

# Hardware Prototype

In this file I will first show my breadboard and most of the test points, and then the assembled PCB. Let me say right away that I tried to maintain cable management: I used red and black wires for power, and specific wires for specific signals... But the wires of the required colors simply ran out. So I apologize in advance to the aesthetes.

## Breadboard

I will not talk about the [simulation](Simulation.md) and [PCB layout](PCB%20Design.md), as I have already described them in other files.

### Blocks

A quick reminder of the test points:

| Test-point | Signal |
|:---|:---|
| TP1 | Darkness sensor output |
| TP2 | RC circuit output |
| TP3 | AM312 sensor output|
| TP4 | +5 |
| TP5 | RAMP signal |
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

### Assembled Printed Circuit Board
Here is the long-awaited board. Before describing it, I should mention that it took a little over a month to arrive. This wasn't an issue with PCBpi itself—the actual manufacturing process (including design review, production, and impedance control) took less than two weeks—but the board spent nearly a month clearing customs. That said, the board itself looks very impressive: the solder mask is high-quality, and the vias are covered neatly and professionally. The only unfortunate oversight was that I forgot to submit the solder mask files... As a result, all the pads ended up covered by the mask, and I had to carefully scrape it off using a scalpel. <img width="1609" height="1416" alt="image" src="https://github.com/user-attachments/assets/12790851-4c18-4a74-9d43-830875676bdd" />
<img width="1548" height="1444" alt="image" src="https://github.com/user-attachments/assets/81559bfc-000c-409f-b338-3cb08fff7c08" />
## Removed mask
<img width="1549" height="1301" alt="image" src="https://github.com/user-attachments/assets/97c14765-a783-480a-8703-86c697fbd863" />
<img width="1440" height="1920" alt="image" src="https://github.com/user-attachments/assets/9c4b0320-9503-4084-a537-0bc85cc4c9fa" />

## Assembled board top and bottom

<img width="1200" height="1001" alt="image" src="https://github.com/user-attachments/assets/2fd08d9b-603b-4b8a-8786-97e4181c44ad" />
<img width="1420" height="1131" alt="image" src="https://github.com/user-attachments/assets/b03f992b-0dc1-48be-a0df-2bf11d3afb13" />

### Capturing Signals from Test Points

In some cases, one square on the oscilloscope waveform corresponds to 1/V. Pay attention to the oscilloscope’s scale settings.
## TP1

Capturing the signal from the output of the darkness sensor

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/737bbde1-a8cb-4ec9-abf8-5ba5fe6a7bc2" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/5f7daa40-9ee9-444a-b70b-e15736e47e40" />
The activation threshold is adjusted using the potentiometer located in the center. For the test, I set the trigger threshold to the minimum possible value.

## TP2

Signal acquisition from the output of the RC circuit
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/4c439292-e630-42fd-b8bb-2030661ec490" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/f5813b48-a561-4e4a-bc66-6c0bca4863c8" />

## TP3

Signal acquisition from the output of the AM312 pyroelectric sensor

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/46f7a416-df62-4d72-9fe8-c484765d5826" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/78b5b50a-9777-45e8-9021-c748c4b98894" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/c5e0d41b-2b56-4053-9132-964f4e728c34" />

## TP4

Signal acquisition from the output of the LM317

<img width="1152" height="532" alt="image" src="https://github.com/user-attachments/assets/78aeb03e-b669-48fa-81c5-64fc25398c4b" />

## TP5

Output of the sawtooth wave generator

<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/f0c2239e-ad59-4177-ba2b-7f8a2c1b9ec5" />
<img width="1920" height="885" alt="image" src="https://github.com/user-attachments/assets/06bc285e-691a-41de-b5da-9ff30f036025" />

I really like this block—especially how clean the resulting sawtooth wave turned out.

## TP6

PWM Comparator

https://github.com/user-attachments/assets/7b0deda1-3c4d-4122-befd-ddaa311a932d

## Demonstration of operation without input signals


https://github.com/user-attachments/assets/0acb130c-9748-47a6-9404-83e3e99bafca


## Conclusion

The project has been successfully completed through all its stages: from simulation in Multisim to the assembly and debugging of the actual device on a printed circuit board. The entirely analog circuit—containing not a single line of code—has proven to be fully functional. All key components—sensors, logic circuitry, the sawtooth wave generator, the PWM stage, and the power switch—operate reliably and in coordination.

This prototype serves as an excellent example of how classical circuit design can address tasks for which microcontrollers are frequently used today.










