## Симуляция
В этом документе я покажу принципиальные схемы и результаты моделирования каждого блока Ночника. Все принципиальные схемы я нарисовал и просимулировал в Multisim. Далее я расскажу про каждый блок по отдельности, все формулы и анализ переходных процессов
## Содержание

1. [Блок стабилизатора питания](#блок-стабилизатора-питания)
2. [Блок датчика темноты и монтажное И](#блок-датчика-темноты-и-монтажное-и)
3. [Монтажное И, RC-цепь](#монтажное-и-rc-цепь)
4. [Генератор пилообразных сигналов](#генератор-пилообразных-сигналов)
5. [ШИМ компаратор и коммутация](#шим-компаратор-и-коммутация)
6. [Заключение](#заключение)
## Блок стабилизатора питания
"Ночник" питается от входных 12V которые преобразуются в положительные 5V. Преобразование происходит за счёт регулируемого стабилизатора напряжения LM317. 
Для получение нужного напряжения я использовал резисторы ряда Е24 : верхнее плечо 240Ω, нижнее 750Ω. Выходное напряжение ≈ 5V
Для нахождения нужного мне выходного напряжения я использовал стандартную формулу из документации :

$V_{out} = 1.25 \times \left(1 + \frac{R_2}{R_1}\right)$

В этой формуле:

$V_{out}$ - желаемое выходное напряжение в V

${R_2}$ - резистор делителя напряжения в 750Ω

${R_1}$ - резистор делителя напряжения в 240Ω ( его нам рекомендует [производитель](https://docs.yandex.ru/docs/view?tm=1787220899&tld=ru&lang=en&name=lm317.pdf&text=lm317%20datasheet&url=https%3A%2F%2Famperkot.ru%2Fstatic%2F3236%2Fuploads%2Fdatasheets%2Flm317.pdf&lr=158035&mime=pdf&l10n=ru&sign=faee9ea800e906b4f9e557e398590c02&keyno=0&nosw=1&serpParams=tm%3D1787220899%26tld%3Dru%26lang%3Den%26name%3Dlm317.pdf%26text%3Dlm317%2Bdatasheet%26url%3Dhttps%253A%2F%2Famperkot.ru%2Fstatic%2F3236%2Fuploads%2Fdatasheets%2Flm317.pdf%26lr%3D158035%26mime%3Dpdf%26l10n%3Dru%26sign%3Dfaee9ea800e906b4f9e557e398590c02%26keyno%3D0%26nosw%3D1) )

$V_{out} = 1.25 \times \left(1 + \frac{750}{240}\right) \approx 5.15\ \text{В}$

Вот тут хочу добавить одно НО. В реальности на моей макетной плате у меня вышло 5.2V по этому дальше в симуляции я буду использовать за VCC 5.2V

## Принципиальная схема

<img width="497" height="377" alt="image" src="https://github.com/user-attachments/assets/fbf179da-6eee-4d43-a81f-6cff36f3f890" />

Конденсаторы С1 и С2 я не стал ставить большей ёмкости. Так как устройство и так простое я думаю фильтрации в 0.1uF на входе и выходе стабилизатора хватит за глаза.

## Анализ переходных процессов

<img width="497" height="377" alt="image" src="https://github.com/user-attachments/assets/8ced6504-c643-41ed-a145-329f26b6cc5e" />

Тут я думаю больше и не стоит показывать. Да я сначала использовал резистор 680Ω и имел 4.9V на выходе, потом решил поиграться с законом Ома и последовательно поставил резисторы для получения ровно 5V... Но потом подумал, и понял, что для такого простого устройства это совсем не обязательно, нет каких высокоточных блоков где делители напряжения должны быть с точностью до милливольт и тем более нет прецизионных интегральных микросхем. По этому я остановился на резисторе в 750 Ом и получил напряжение с запасом. Тем более что попадаю в 5% точности

[Скачать power_supply.ms14](power_supply.ms14)
## Блок датчика темноты и монтажное И

Вот тут уже представлена основная логика работы аналогового Ночника. Я не стал разбивать их на отдельные блоки в Multisim и запихнул в один файл симуляции. И давайте разберем их.
### Пиродатчик AM312

Я признаюсь честно не очень люблю использовать в своих DIY проектах готовые модули, по этому я взял не блок пиродатчика, а миниатюрный датчик для удобства. Плюс этот датчик мне очень понравился по [характеристикам](https://docs.yandex.ru/docs/view?tm=1787170202&tld=ru&lang=ru&name=32087.pdf&text=am312%20datasheet&url=https%3A%2F%2Forion43.ru%2Fdatasheets%2F32087.pdf&lr=158035&mime=pdf&l10n=ru&sign=b2fbc2ff950190029611fee32c97dadd&keyno=0&nosw=1&serpParams=tm%3D1787170202%26tld%3Dru%26lang%3Dru%26name%3D32087.pdf%26text%3Dam312%2Bdatasheet%26url%3Dhttps%253A%2F%2Forion43.ru%2Fdatasheets%2F32087.pdf%26lr%3D158035%26mime%3Dpdf%26l10n%3Dru%26sign%3Db2fbc2ff950190029611fee32c97dadd%26keyno%3D0%26nosw%3D1) и цене ( он очень дешёвый ) за свою цену мы получаем довольно хороший радиус срабатывания это 4-5 метров, всего 3 пина - GND,VCC и OUT и маленький ток потребления < 60 мкА.

AM312 — это не плата-модуль с обвязкой и линзой, а миниатюрный готовый датчик. Я выбрал его за простоту интеграции и малые габариты.
### Датчик темноты
Для датчика темноты я использовал сдвоенный компаратор LM393, вторая его часть пригодится в блоке Коммутации, но об этом погорим позже. Так как LM393 с открытым коллектор я подтянул его к питанию через подтяжку из резистора в 10kΩ. Так же я его взял из за его высокоимпедансного входа.
Сравнение темноты происходит благодаря делителя напряжения из фоторезистора GL5537 и резистора 10kΩ.

Расчёт я произвёл благодаря обычной формулы делителя напряжения :
### Для светлого состояния

$V_{(+)} = V_{CC} \times \frac{R_3}{R_{photo} + R_3}$

$V_{CC}$ - питание которое идёт на верхнее плечо делителя

${R_{photo}}$ - верхнее плечо делителя которым является фоторезистор

${R_3}$ - нижнее плечо делителя напряжения 

$V_{(+)} = 5 \times \frac{10000}{10000 + 10000} = 4.85\ \text{В}$

### Для тёмного состояния 

$V_{(+)} = 5 \times \frac{10000}{100000 + 10000} = 1.11\ \text{В}$

Так же имеется возможность подстройки порога срабатывания благодаря потенциометра! Можно настроить когда срабатывать нашему блоку темноты
## Принципиальная схема

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/43b20b8a-0fed-46d7-9b32-74496c642671" />

### Анализ переходных процессов

Логический уровень АМ312 находится в диапазоне 3.3V И его эквивалент в Multisim я сделал... Из обычного тумблера и питания. В реальности благодаря [пироэлектрического эффекта](https://ru.wikipedia.org/wiki/Пироэлектрики) он поднимается моментально в ≈ 3.3V и держится в этом диапазоне где то несколько секунд.

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/1cd1151e-de55-4e38-9ba3-0b508e3dc1e0" />

Для более гибких тестов я взял подстроечный резистор как эквивалент фоторезистора чтобы можно было посмотреть пороги срабатывания и поменять плечо делителя напряжения, но в принципе резистора в 10kΩ хватает достаточно. Если потребуются другие пороги этот резистора всегда можно будет демонтировать и поменять на другой чтобы сделать датчик темноты более гибким если это понадобится.

<img width="1060" height="866" alt="image" src="https://github.com/user-attachments/assets/97660760-372d-4db4-8948-d04660d80650" />

Это осциллограмма Блока датчика темноты. 

Зелёным показан сигнал с выхода АМ312, его показывает PR1

Красным показан сигнал с выхода датчика темноты, он показан как PR4

Синим курсором я показал когда фоторезистор находится в полной темноте и датчик зафиксировал движение. На жёлтом курсоре уже пропал сигнал с АМ312 и фоторезистор находится в полной освещённости. Потом я начал менять порог срабатывания с помощью R4 с 50% до 100%, подал сигнал с АМ312 и дал освещённость приблизительно 52%.

## Монтажное И, RC-цепь

<img width="1028" height="477" alt="image" src="https://github.com/user-attachments/assets/8ffab4e4-3e19-4b99-bb11-6219d7ce7b31" />

Тут стоит самый главный блок - 2И. Чтобы наша светодиодная лента включилась нам нужно чтобы сигналы с АМ312 и Блока датчика темноты совпали, тут нам поможет логический 2И. Так как устройство полностью аналоговое и по замыслу никак нельзя ставить логический вентиль. Так как по закону Кирхгофа наш ток будет равен, что на входе, что и на выходе я объединил его с помощью транзисторного 2И. Так же из за схемы транзисторного повторителя и из за сборки с общим эмиттером мы получили большое падение напряжения ( 1.4V ), по этому на выходе блока стоит ОУ с коэффициентом усиления 2. Так как амплитуда пилообразного сигнала ( тоже поговорим об этом немного позже ) 3.3V, а выход с логике только 2.4В. Нам нужно чтобы наша логика имел амплитуду не меньше 3.4В

Таблица истинности совершенно такая же как у вентиля 2И
| Движение (AM312) | Темнота (Датчик) | Выход 2И |
|:---:|:---:|:---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/4bfe563d-2c14-4099-8cb4-ded12f9397d8" />

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/ba47d36d-9a37-4049-a83c-a1ed8638538d" />

Так и зачем нужна RC-цепь? Если её не ставить, то ни о какой плавности зажигания светодиодной ленты речи быть и не может. Она будет срабатывать как стробоскоп и будет больше подходить не как ночник, а как устройство для дезориентации на полицейский щит для штурма всяких негодяев. 

Но и чтобы плавность была больше приятна глазу я рассчитал примерно на 5 секунд по этой формуле :

$\tau = R \times C$

Где :

$R$ - время задающий резистор R8

$C$ - электролитический конденсатор С1

$\tau = 47\,000\ \text{Ом} \times 0.0001\ \text{Ф} = 4.7\ \text{с}$

И вот! Прибор для штурма зданий превратился в приятный глазу ночник для дома

<img width="1912" height="872" alt="image" src="https://github.com/user-attachments/assets/ed23aa71-b742-4fc8-ba24-af780451cb06" />

Время полной зарядки конденсатора
Красным показан сигнал снимаемый с выхода RC-цепи и показывается пробником PR3 ( c режима Интерактив )

<img width="1912" height="867" alt="image" src="https://github.com/user-attachments/assets/85313311-d98f-429d-b5f7-f038961e1ac3" />

Осциллограмма при появлении и пропаже сигнала с AM312 

Про операционный усилитель уже говорил выше, он просто усиливает логику в 2 раза 

<img width="488" height="477" alt="image" src="https://github.com/user-attachments/assets/faf1e9ea-fc10-449f-a2ae-1be5aa2e2342" />

<img width="1913" height="865" alt="image" src="https://github.com/user-attachments/assets/bf05d990-ba0b-44c5-b774-fbd9cb5bd45c" />
Время полной зарядки конденсатора
Красным показан сигнал снимаемый с выхода ОУ и показывается пробником PR1 ( c режима Интерактив )

<img width="1917" height="862" alt="image" src="https://github.com/user-attachments/assets/b25a6749-4532-4da0-bd24-b56723685b8e" />

Осциллограмма при появлении и пропаже сигнала с AM312 

Коэффициент усиления неинвертирующего ОУ рассчитывается по следующей формуле:

$K_u = 1 + \frac{R_2}{R_1}$

Где:

$K_u$ - желаемый коэффициент усиления

$K_u = 1 + \frac{10000}{10000} = 2$

[Скачать light_sensor and_gate_rc](light_sensor%20and_gate_rc.ms14)

## Генератор пилообразных сигналов

Тоже не менее важный блок. Благодаря блока пилы происходит сравнение сигналов Logic_AMP и нашей пилы на ШИМ-Компараторе, и когда напряжение с нашей пилы оказывается больше, тогда наша пила и формирует плавное затухание. Но и тут при тесте на макетной плате у меня не всё прошло гладко :( Когда ночник плавно зажигался он всё равно переходил в режим "штурмовика" и напоминая о своём прошлом опять превращался в стробоскоп. Тут был мой косяк - я рассчитал нужную амплитуду, но не учёл частоту. На тот момент у меня она составляла где 150-200 Гц из за того, что ёмкость время задающего конденсатора была 0.47uF. Поменяв на 1.5nF я получил ≈ 2 кГц и вернулся к плавному затуханию.

### Принципиальная схема

<img width="893" height="503" alt="image" src="https://github.com/user-attachments/assets/8ce23cc6-2f14-4765-b33a-ffcd3133433f" />

Формула для расчёта частоты NE555 берём прямо из [документации](https://static.chipdip.ru/lib/034/DOC032034492.pdf)

$f \approx \frac{1.44}{(R_A + R_B) \times C_t}$

В этой формуле :

$f$ - частота сигнала

$R_A$- резистор R1 = 1000Ω

$R_B$ - резистор R3 = 10000Ω

$C_t$ - время задающий конденсатор С1 = 0.0000000015 F

$f \approx \frac{1.44}{(1000 + 10000) \times 0.0000000015} = \frac{1.44}{11000 \times 15^{-9}} \approx 2000 \ \text{Гц}$

### Анализ переходных процессов

<img width="893" height="503" alt="image" src="https://github.com/user-attachments/assets/762112a8-be38-4d70-9054-a95d56e1f762" />

<img width="1913" height="902" alt="image" src="https://github.com/user-attachments/assets/9ca54b1e-1395-431c-9dbc-cb3acee3e3f2" />

Красным показан сигнал с PR1

### Для любителей классики 
<img width="1302" height="867" alt="image" src="https://github.com/user-attachments/assets/2eb70e74-830b-4730-b213-9c859929f95b" />

[Скачать ramp_generator](ramp_generator.ms14)

## ШИМ-Компаратор и коммутации

Финальный блок аналогового  ночника!

Задача блока сравнивать пилообразный сигнал с усиленным сигналом логики и RC цепи.

 ### Принцип работы 
- Когда напряжение RC больше пилы → выход HIGH ( плавное включение светодиодной ленты )
- Когда напряжение RC меньше пилы → выход LOW ( плавное затухание светодиодной ленты )

Вот тут как раз и используется вторая часть сдвоенного компаратора LM393. Всё так же из за открытого коллектора подтягиваем его к +5V через подтяжку 10kΩ

## Принципиальная схема

<img width="758" height="460" alt="image" src="https://github.com/user-attachments/assets/9b5b282f-0403-4941-bf3f-11ddf112bae3" />

На затворе полевого транзистора получаем переменную ( и красивую ) изменяемую ШИМ-скважность 

| Напряжение RC | Скважность |
|:---|:---|
| 0.6В | ~0% |
| 1.7В | ~50% |
| 3.5В | ~100% |

Рассчитываем скважность сигнала : 

$D = \frac{t_{on}}{T} \times 100\%$

Где :

$D$ - скважность сигнала

$T$ - весь период

$t_{on}$ - длительность импульса высокого уровня 

$D = \frac{0.382}{0.764} \times 100 \approx 50\%$

И так под каждый отдельный период


Полевой ключ управляет светодиодной лентой с помощью ШИМ и коммутирует на землю. Ограничение затвора в 100Ω помогает растянуть фронт импульса тока чтобы выброс того же тока с выхода LM393 не перегружал 2N7002. Почему 560 kΩ? У меня не было под рукой резистора номинала меньше... Но просимулировав на макетной плате с этим номиналом я не увидел какой либо критичной ошибки. В принципе 100 kΩ хватило бы с головой чтобы подтянуть затвор к земле и лишить его неопределённости.

### Анализ переходных процессов 

<img width="929" height="460" alt="image" src="https://github.com/user-attachments/assets/d9edad72-feda-4209-97cf-905ef57a7792" />

<img width="1912" height="903" alt="image" src="https://github.com/user-attachments/assets/2f2cc760-9deb-4d48-bcb7-997448f32af1" />

Красным показан сигнал с PR1 ( выход ШИМ компаратора, вход затвора 2N7002 )

Синим курсором показан момент когда присутствует сигнал с АM312 и идёт увеличение скважности 

Жёлтым курсором показан момент когда сигнала с AM312 нет и идёт спад скважности 

### Увеличение скважности 

<img width="556" height="447" alt="image" src="https://github.com/user-attachments/assets/55c770fb-828a-4746-8f12-540de0d03edb" />

### Спад скважности 

<img width="552" height="442" alt="image" src="https://github.com/user-attachments/assets/36496bfc-493c-466f-bd80-49236508c034" />

Полный цикл работы:

Нет движения → лента выключена

Движение + темнота → плавный розжиг

Движение пропало → плавное затухание

[Скачать pwm_comparator](pwm_comparator.ms14)

### Заключение 

Все схемы работают корректно и по отдельности и все вместе! Так же представлен файл где все блоки находятся на одной принципиальной схеме для удобства в симулировании 

<img width="1739" height="1358" alt="image" src="https://github.com/user-attachments/assets/0d571da7-5628-449f-8694-5ea30b40ca4a" />

[Скачать full_circuit](full_circuit.ms14)

## Simulation

In this document I will show the circuit diagrams and simulation results of each block of the Night Light. I drew and simulated all circuit diagrams in Multisim. Next I will describe each block separately, all formulas and transient analysis.

## Table of Contents

1. [Power Supply Block](#power-supply-block)
2. [Light Sensor and Wired AND](#light-sensor-and-wired-and)
3. [Wired AND, RC Circuit](#wired-and-rc-circuit)
4. [Ramp Generator](#ramp-generator)
5. [PWM Comparator and Switching](#pwm-comparator-and-switching)
6. [Conclusion](#conclusion)

## Power Supply Block

The Night Light is powered from 12V input, which is converted to positive 5V. The conversion is performed by the adjustable voltage regulator LM317.

To obtain the required voltage, I used E24 series resistors: upper arm 240Ω, lower arm 750Ω. Output voltage ≈ 5V.

To find the required output voltage, I used the standard formula from the datasheet:

$V_{out} = 1.25 \times \left(1 + \frac{R_2}{R_1}\right)$

In this formula:

$V_{out}$ - desired output voltage in V

${R_2}$ - voltage divider resistor of 750Ω

${R_1}$ - voltage divider resistor of 240Ω (recommended by the [manufacturer](https://docs.yandex.ru/docs/view?tm=1787220899&tld=ru&lang=en&name=lm317.pdf&text=lm317%20datasheet&url=https%3A%2F%2Famperkot.ru%2Fstatic%2F3236%2Fuploads%2Fdatasheets%2Flm317.pdf&lr=158035&mime=pdf&l10n=ru&sign=faee9ea800e906b4f9e557e398590c02&keyno=0&nosw=1&serpParams=tm%3D1787220899%26tld%3Dru%26lang%3Den%26name%3Dlm317.pdf%26text%3Dlm317%2Bdatasheet%26url%3Dhttps%253A%2F%2Famperkot.ru%2Fstatic%2F3236%2Fuploads%2Fdatasheets%2Flm317.pdf%26lr%3D158035%26mime%3Dpdf%26l10n%3Dru%26sign%3Dfaee9ea800e906b4f9e557e398590c02%26keyno%3D0%26nosw%3D1))

$V_{out} = 1.25 \times \left(1 + \frac{750}{240}\right) \approx 5.15\ \text{V}$

Here I want to add one note. In reality, on my breadboard I got 5.2V, so further in the simulation I will use 5.2V as VCC.

## Circuit Diagram

<img width="497" height="377" alt="image" src="https://github.com/user-attachments/assets/fbf179da-6eee-4d43-a81f-6cff36f3f890" />

I did not use larger capacitors C1 and C2. Since the device is simple, I think 0.1uF filtering on the input and output of the regulator is more than enough.

## Transient Analysis

<img width="497" height="377" alt="image" src="https://github.com/user-attachments/assets/8ced6504-c643-41ed-a145-329f26b6cc5e" />

I think there is no need to show more here. At first I used a 680Ω resistor and had 4.9V at the output, then I decided to play with Ohm's law and put resistors in series to get exactly 5V... But then I thought and realized that for such a simple device this is not necessary at all. There are no high-precision blocks where voltage dividers must be accurate to a millivolt, and there are no precision integrated circuits. So I settled on a 750Ω resistor and got voltage with a margin. Moreover, I stay within 5% accuracy.

[Download power_supply.ms14](power_supply.ms14)

## Light Sensor and Wired AND

Here is the main logic of the analog Night Light. I did not split them into separate blocks in Multisim and put them into one simulation file. Let's analyze them.

### PIR Sensor AM312

Honestly, I do not really like using ready-made modules in my DIY projects, so I took not a PIR module, but a miniature sensor for convenience. Also I really liked this sensor because of its [characteristics](https://docs.yandex.ru/docs/view?tm=1787170202&tld=ru&lang=ru&name=32087.pdf&text=am312%20datasheet&url=https%3A%2F%2Forion43.ru%2Fdatasheets%2F32087.pdf&lr=158035&mime=pdf&l10n=ru&sign=b2fbc2ff950190029611fee32c97dadd&keyno=0&nosw=1&serpParams=tm%3D1787170202%26tld%3Dru%26lang%3Dru%26name%3D32087.pdf%26text%3Dam312%2Bdatasheet%26url%3Dhttps%253A%2F%2Forion43.ru%2Fdatasheets%2F32087.pdf%26lr%3D158035%26mime%3Dpdf%26l10n%3Dru%26sign%3Db2fbc2ff950190029611fee32c97dadd%26keyno%3D0%26nosw%3D1) and price (it is very cheap). For its price we get a fairly good detection range of 4-5 meters, only 3 pins - GND, VCC and OUT, and low current consumption < 60 µA.

AM312 is not a module board with external circuitry and lens, but a miniature ready-made sensor. I chose it for ease of integration and small dimensions.

### Light Sensor

For the light sensor I used the dual comparator LM393; its second half will be used in the Switching block, but we will talk about that later. Since the LM393 has an open collector, I pulled it up to the power supply through a 10kΩ pull-up resistor. I also chose it because of its high-impedance input.

Darkness detection is performed using a voltage divider consisting of the GL5537 photoresistor and a 10kΩ resistor.

I performed the calculation using the standard voltage divider formula:

### For Light State

$V_{(+)} = V_{CC} \times \frac{R_3}{R_{photo} + R_3}$

$V_{CC}$ - power supply that goes to the upper arm of the divider

${R_{photo}}$ - upper arm of the divider, which is the photoresistor

${R_3}$ - lower arm of the voltage divider

$V_{(+)} = 5 \times \frac{10000}{10000 + 10000} = 4.85\ \text{V}$

### For Dark State

$V_{(+)} = 5 \times \frac{10000}{100000 + 10000} = 1.11\ \text{V}$

There is also the possibility of adjusting the threshold using a potentiometer! You can set when our darkness block should trigger.

## Circuit Diagram

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/43b20b8a-0fed-46d7-9b32-74496c642671" />

### Transient Analysis

The AM312 logic level is in the 3.3V range, and I made its equivalent in Multisim... using a regular switch and a power supply. In reality, thanks to the [pyroelectric effect](https://en.wikipedia.org/wiki/Pyroelectricity), it rises almost instantly to ≈ 3.3V and stays in this range for several seconds.

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/1cd1151e-de55-4e38-9ba3-0b508e3dc1e0" />

For more flexible tests, I used a trimmer resistor as a photoresistor equivalent so that I could check the thresholds and change the divider arm. In principle, a 10kΩ resistor is sufficient. If other thresholds are needed, this resistor can always be removed and replaced with another one to make the light sensor more flexible if necessary.

<img width="1060" height="866" alt="image" src="https://github.com/user-attachments/assets/97660760-372d-4db4-8948-d04660d80650" />

This is the oscillogram of the Light Sensor block.

Green shows the signal from the AM312 output, displayed by PR1.

Red shows the signal from the light sensor output, displayed by PR4.

With the blue cursor I marked the moment when the photoresistor is in complete darkness and the sensor detected motion. At the yellow cursor, the AM312 signal has already disappeared and the photoresistor is in full illumination. Then I started changing the trigger threshold using R4 from 50% to 100%, applied the AM312 signal, and set illumination to approximately 52%.

## Wired AND, RC Circuit

<img width="1028" height="477" alt="image" src="https://github.com/user-attachments/assets/8ffab4e4-3e19-4b99-bb11-6219d7ce7b31" />

Here is the most important block — the AND gate. To turn on our LED strip, the signals from the AM312 and the Light Sensor block must match. The logic AND gate will help us here. Since the device is fully analog and by design no logic gate IC is allowed... Since according to Kirchhoff's law the current will be the same at the input and output, I combined it using a transistor AND gate. Also, because of the emitter follower circuit and the common-emitter configuration, we got a large voltage drop (1.4V), so at the output of the block there is an op-amp with a gain of 2. The amplitude of the ramp signal (we will also talk about this a little later) is 3.3V, while the logic output is only 2.4V. We need our logic to have an amplitude of at least 3.4V.

The truth table is exactly the same as for an AND gate:

| Motion (AM312) | Darkness (Sensor) | AND Output |
|:---:|:---:|:---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/4bfe563d-2c14-4099-8cb4-ded12f9397d8" />

<img width="1271" height="822" alt="image" src="https://github.com/user-attachments/assets/ba47d36d-9a37-4049-a83c-a1ed8638538d" />

So why do we need the RC circuit? If it is not installed, there can be no talk of smooth LED strip dimming. It will trigger like a strobe light and would be more suitable not as a night light, but as a disorientation device on a police shield for storming buildings full of bad guys.

But to make the smoothness more pleasing to the eye, I calculated approximately 5 seconds using this formula:

$\tau = R \times C$

Where:

$R$ - timing resistor R8

$C$ - electrolytic capacitor C1

$\tau = 47\,000\ \text{Ω} \times 0.0001\ \text{F} = 4.7\ \text{s}$

And here we go! The building assault device turned into a pleasant night light for the home.

<img width="1912" height="872" alt="image" src="https://github.com/user-attachments/assets/ed23aa71-b742-4fc8-ba24-af780451cb06" />

Full capacitor charging time.
Red shows the signal from the RC circuit output, displayed by probe PR3 (in Interactive mode).

<img width="1912" height="867" alt="image" src="https://github.com/user-attachments/assets/85313311-d98f-429d-b5f7-f038961e1ac3" />

Oscillogram when the AM312 signal appears and disappears.

I already talked about the op-amp above; it simply amplifies the logic by 2 times.

<img width="488" height="477" alt="image" src="https://github.com/user-attachments/assets/faf1e9ea-fc10-449f-a2ae-1be5aa2e2342" />

<img width="1913" height="865" alt="image" src="https://github.com/user-attachments/assets/bf05d990-ba0b-44c5-b774-fbd9cb5bd45c" />
Full capacitor charging time.
Red shows the signal from the op-amp output, displayed by probe PR1 (in Interactive mode).

<img width="1917" height="862" alt="image" src="https://github.com/user-attachments/assets/b25a6749-4532-4da0-bd24-b56723685b8e" />

Oscillogram when the AM312 signal appears and disappears.

The gain of a non-inverting op-amp is calculated using the following formula:

$K_u = 1 + \frac{R_2}{R_1}$

Where:

$K_u$ - desired gain

$K_u = 1 + \frac{10000}{10000} = 2$

[Download light_sensor and_gate_rc](light_sensor%20and_gate_rc.ms14)

## Ramp Generator

This is also a very important block. Thanks to the ramp block, the Logic_AMP signal and our ramp are compared on the PWM Comparator, and when the ramp voltage becomes higher, then our ramp forms smooth fading. But here, when testing on a breadboard, not everything went smoothly :( When the night light smoothly turned on, it still switched to "assault mode" and, reminding me of its past, turned into a strobe light again. It was my mistake — I calculated the required amplitude but did not take frequency into account. At that time it was about 150-200 Hz because the timing capacitor capacitance was 0.47uF. After replacing it with 1.5nF I got ≈ 2 kHz and returned to smooth fading.

### Circuit Diagram

<img width="893" height="503" alt="image" src="https://github.com/user-attachments/assets/8ce23cc6-2f14-4765-b33a-ffcd3133433f" />

The NE555 frequency calculation formula is taken directly from the [datasheet](https://static.chipdip.ru/lib/034/DOC032034492.pdf).

$f \approx \frac{1.44}{(R_A + R_B) \times C_t}$

In this formula:

$f$ - signal frequency

$R_A$ - resistor R1 = 1000Ω

$R_B$ - resistor R3 = 10000Ω

$C_t$ - timing capacitor C1 = 0.0000000015 F

$f \approx \frac{1.44}{(1000 + 10000) \times 0.0000000015} = \frac{1.44}{11000 \times 1.5 \times 10^{-9}} \approx 87\,272\ \text{Hz}$

### Transient Analysis

<img width="893" height="503" alt="image" src="https://github.com/user-attachments/assets/762112a8-be38-4d70-9054-a95d56e1f762" />

<img width="1913" height="902" alt="image" src="https://github.com/user-attachments/assets/9ca54b1e-1395-431c-9dbc-cb3acee3e3f2" />

Red shows the signal from PR1.

### For lovers of classics

<img width="1302" height="867" alt="image" src="https://github.com/user-attachments/assets/2eb70e74-830b-4730-b213-9c859929f95b" />

[Download ramp_generator](ramp_generator.ms14)

## PWM Comparator and Switching

The final block of the analog night light!

The task of the block is to compare the ramp signal with the amplified logic and RC circuit signal.

### Operating Principle

- When the RC voltage is higher than the ramp → output HIGH (smooth turning on of the LED strip)
- When the RC voltage is lower than the ramp → output LOW (smooth fading of the LED strip)

This is where the second half of the dual comparator LM393 is used. As before, because of the open collector, we pull it up to +5V through a 10kΩ pull-up resistor.

## Circuit Diagram

<img width="758" height="460" alt="image" src="https://github.com/user-attachments/assets/9b5b282f-0403-4941-bf3f-11ddf112bae3" />

On the gate of the field-effect transistor we get a variable (and beautiful) PWM duty cycle.

| RC Voltage | Duty Cycle |
|:---|:---|
| 0.6V | ~0% |
| 1.7V | ~50% |
| 3.5V | ~100% |

We calculate the signal duty cycle:

$D = \frac{t_{on}}{T} \times 100\%$

Where:

$D$ - signal duty cycle

$T$ - full period

$t_{on}$ - high-level pulse duration

$D = \frac{0.382}{0.764} \times 100 \approx 50\%$

And so on for each individual period.

The field-effect switch controls the LED strip using PWM and switches it to ground. The 100Ω gate resistor helps stretch the current pulse front so that the current surge from the LM393 output does not overload the 2N7002. Why 560 kΩ? I did not have a smaller resistor on hand... But after simulating on a breadboard with this value, I did not see any critical error. In principle, 100 kΩ would be more than enough to pull the gate to ground and remove its uncertainty.

### Transient Analysis

<img width="929" height="460" alt="image" src="https://github.com/user-attachments/assets/d9edad72-feda-4209-97cf-905ef57a7792" />

<img width="1912" height="903" alt="image" src="https://github.com/user-attachments/assets/2f2cc760-9deb-4d48-bcb7-997448f32af1" />

Red shows the signal from PR1 (PWM comparator output, gate input of 2N7002).

The blue cursor marks the moment when the AM312 signal is present and duty cycle is increasing.

The yellow cursor marks the moment when the AM312 signal is absent and duty cycle is falling.

### Duty Cycle Increase

<img width="556" height="447" alt="image" src="https://github.com/user-attachments/assets/55c770fb-828a-4746-8f12-540de0d03edb" />

### Duty Cycle Decrease

<img width="552" height="442" alt="image" src="https://github.com/user-attachments/assets/36496bfc-493c-466f-bd80-49236508c034" />

Full operation cycle:

No motion → LED strip off

Motion + darkness → smooth turn-on

Motion stopped → smooth fade-out

[Download pwm_comparator](pwm_comparator.ms14)

## Conclusion

All circuits work correctly both separately and all together! Also provided is a file where all blocks are on one circuit diagram for convenient simulation.

<img width="1739" height="1358" alt="image" src="https://github.com/user-attachments/assets/0d571da7-5628-449f-8694-5ea30b40ca4a" />

[Download full_circuit](full_circuit.ms14)















































