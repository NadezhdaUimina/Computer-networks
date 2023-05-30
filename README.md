# Computer-networks

## Урок 1. Основы компьютерных сетей. Технология Ethernet.

**Виды связей**
- Simplex — односторонняя связь.  Один источник данных, а остальные все только получают эти данные. Пример: Теле- и радиовещание. Передача сигнала от спутников GPS.

- Half-duplex — двусторонняя связь. Но в один момент времени может передавать только одно устройство. Пример: Общение по рации, когда можно либо слушать. Канал, либо, нажав кнопку, передавать в него.

- Full-duplex или просто duplex — двусторонняя передача. Оба устройства могут одновременно вести передачу. Пример: Разговор по телефону.

**Виды коммутации**

- Коммутация каналов: В сети с коммутацией каналов между двумя конечными устройствами устанавливается физический канал. Пример: телефонная сеть.

- Коммутация пакетов: В сети с коммутацией пакетов информация от каждого устройства делится на небольшие пакеты, и данные передаются по одним и тем же физическим каналам. Пример: компьютерные сети

**Методы передачи данных**

- Unicast — передача данных единственному адресату.

- Broadcast — широковещательная передача данных всем устройствам.

- Multicast — передача данных группе устройств.

**Классификация и топология сетей**

Классификация сетей по административно-территориальному признаку. 

LAN — локальная вычислительная сеть Local Area Network.

WAN — Wide Area Network, окружающая нас сеть.

**Топология сети**

Топология - это схема сети.

- полносвязная - каждый узел сети связан с каждым другим узлом сети. Самоя надежная, но при этом и самоя дорогая. Если мы настроим сеть некорректно, то есть вероятность, что некоторые пакеты попадут в петлю и будут вечно пересылается между узлами, засоряя сеть.

- кольцевая - минимально отказоустойчивая. При такой связности, при разрыве одного линка, всегда остаётся один резервный путь для связи узла А с узлом Б. Если мы настроим сеть некорректно, то есть вероятность, что некоторые пакеты попадут в петлю и будут вечно пересылается между узлами, засоряя сеть.

- иерархическая звезда (дерево) -  в ней нет места для возникновения петель, как в полносвязной и кольцевой.

- общая шина - в одну среду передачи данных подключается сразу несколько участников сети. В такой сети есть возможность для возникновения коллизий, поэтому в общей шине передача данных будет идти в халф-дуплексе. Если рвется линк в одном месте, то одна половина сети сразу ломается и становится недоступной.

- звезда - при разрыве кабеля, из строя выйдет только один узел.

- смешанная топология - Обычно сети не строятся только согласно одной выбранной топологии, встречается сочетание нескольких топологий.

**Модель OSI и TCP/IP**

| стек TCP/IP | модель ISO |
| --- | --- |
| 4. прикладной | 7. Прикладной |
|  | 6. Представления|
|  | 5. Сеансовый|
| | |
| 3. Транспортный | 4. Транспортный |
| | |
| 2. Сетевой | 3. Сетевой |
| | |
| 1. Канальный | 2. Канальный |
|  | 1. Сеансовый |

- L1 -это физика,
- L2 - канальный уровень,
- L3 сетевой,
- L4 транспортный,
- и L7 прикладной

**Стек TCP/IP. Инкапсуляция**

Сетевое устройство которое пересылает пакеты, принимает решение куда дальше направить пакет, на основе заголовка определённого уровня. На каждом уровне пакет носит своё название. На L2 - это Фрейм, на L3 - это пакет, на L4 - это сегмент. Но такие названия больше используются в официальной литературе, на практике все обычно просто говорят пакет.

**Уровни L1 и L2**

L1 -  уровень, предназначен для определения физических характеристик и величин, на которых должны работать устройства, чтобы понимать друг друга. Самые распространненые протоколы на данном уровни входят в стандарт под номером 802.3 - Ethernet. Данный Стандарт был описан в IEEE - в институте инженеров по электронике электротехнике. КУ ним относятся коаксиальный кабель, витая пара, оптоволокно.

L2  - заголовок, описывается стандартом Ethernet, структура заголовка: Первые 6 байт отведены под Destination адрес, то есть адрес кому этот пакет предназначен, вторые 6 байт выделены под Source адрес, то есть адрес узла, который отправил этот пакет, эти адреса называются MAC адресами, они в основном назначаются на сетевые интерфейсы оборудования, серверов, узлов сети.


