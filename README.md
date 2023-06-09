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

## Урок 2. Технология Ethernet. Протокол IP.

**MTU (Maximum Transmission Unit; максимальная единица передачи)** -  максимальный размер пакета, который может быть передан по сети без фрагментации. Для Ethernet это значение составляет 1500 байт.

Основная задача коммутатора изучить какие устройства с какими MAC адресами находятся за каждым из портов. Для этого каждый коммутатор имеет специальную таблицу **“МАС address table”**. В одном столбце таблицы находится номер порта, а в другом МАС-адреса устройств, которые находятся за этим портом. Эта таблица заполняется динамически, когда трафик проходит через коммутатор. Согласно этой таблице коммутатор пересылает пакет адресно конкретному устройству. Благодаря такому подходу в сети не флудятся лишние пакеты, как например делает это хаб. Следовательно, у нас не могут возникать коллизии, если на портах full-duplex

отправителю известен Destination МАС, который он вставлял в пакет. Но обычно изначально МАС адрес, к которому хочет обратиться узел, неизвестен. Чтобы его узнать, хост рассылает специальный широковещательный пакет, в котором он спрашивает какой MAC адрес у определенного компьютера.Задача коммутатора определить такой специальный пакет и размножить во все активные порты (кроме того порта, с которого он пришел). В таком широковещательном пакете Destination MAC адрес состоит из всех битов равных единице, в шестнадцатеричном формате это 12 букв F. Таким образом широковещательный пакет так или иначе разлетится до всех участников сети и собственно в этом его задача. Все компьютеры которые получат такой пакет, прочитают его и увидят, что кто-то ищет МАС адрес РС4 и проигнорируют его. Но как только сам компьютер РС4 поймет, что спрашивают его MAC адрес, он уже юникастом ответит пакетом, в котором будет содержаться его МАС адрес.

**Spanning Tree Protocol - STP** - протокол, блокируя определенные порты, превращает любую топологию в дерево. STP заблокирует один из  линков, у нас броадкаст пакеты не смогут породить шторм, они просто  разойдутся по сети и достигнут каждого узла в сети. При этом STP ещё носит задачу по резервированию каналов связи. Если один из зелёных линков сломается, STP сможет перестроить топологию в другое дерево, разблокировав один из линков.

**L3 уровень** который позволяет делать отдельные сети, как группы узлов, а также нужно отдельное устройство, которое режет бродкаст рассылки, и которое позволяет передавать пакеты из сети в сеть. Основным протоколом на L3 в стеке TCP/IP является IP - Internet Protocol. Адресация называется IP-адресация, а устройство называется роутер или маршрутизатор.

**IP адрес** - это специальный адрес длиной 32 бита, который уникально идентифицирует компьютер в сети. Он задаётся уже не на заводе производителе сетевых карт, а администратором сети. IP адрес записывают в формате четырех чисел, разделенных точкой, где каждое число лежит в диапазоне от 0 до 255 (что занимает ровно 8 бит). Когда компьютер создает пакет для отправки по сети, на уровне L2 он заполняет src и dst МАС адреса, а на уровне L3 он заполняет src и dst IP адресаю

**Роутер, он же маршрутизатор** - это устройство, главная задача которого перенаправлять пакеты между сетевыми интерфейсами. Он смотрит на все входящие пакеты, в пакете считывает Destination IP адрес, ищет у себя в специальной таблице куда по этому Destination IP надо направить пакет, и отправляет дальше в сеть. На каждом интерфейсе роутера назначается свой IP адрес.

**IP маска** - это всегда сначала только единицы, а потом только нули, между единицами не может быть нулей, и между нулей не может быть единиц. Следовательно масок может быть всего 32. Маску в более коротком виде так и записывают /21 /23 /28 - по количеству единиц.

**Internet Protocol (IP, Интернет протокол или межсетевой протокол)** является маршрутизируемым протоколом сетевого уровня. На основе протокола IP работает большинство современных сетей. 

- Первые 4 бита отводятся под версию протокола IP. В нашем случае это IP версии 4. Еще существует IP версии 6, в котором у нас IP адрес занимает 128 бит вместо 32-ух.

- Дальше у нас идёт header length - это длина заголовка IP пакета в 32- битных “словах”. То есть по сути это количество вот таких 32- битных строк. Обычно их 5.

- Следующие 8 бит служат для приоритезации трафика и уведомления о перегрузках на маршрутизаторе. Про них мы особо ничего говорить не будем, так как это отдельная тема в сетевом инжиниринге.

- После этого идёт длина идёт длина пакета в байтах, включая заголовок и сами данные.

- Следующие 3 поля служат для правильной сборки фрагментированных пакетов. Напомню, что фрагментация у нас получается, когда различаются MTU на входном и выходном 
интерфейсе. Здесь тоже особо заострять внимание не будем.

- Следующее поле “Time To Live”, и он нам помогает бороться с петлями на уровне L3. Поговорим об этом чуть попозже.

**Time To Live (TTL)**- время жизни пакета. Но это время жизни измеряется не в секундах. Это время в жизни измеряется в “прыжках” пакета между роутерами - в хопах. Операционная система компьютера, который посылает пакет, устанавливает это время жизни в определённое значение, например Linux, MacOS, Android устанавливает значение 64. Windows устанавливает 128.

- Далее следует поле, в котором находится информация о протоколе, который находится дальше, в заголовке L4. Помните, мы рассматривали, что обязательно в каждом заголовке должен быть указан нижележащий протокол, для более эффективной и более быстрой обработки пакетов. Здесь поле протокол играет именно эту роль.

- После этого идёт контрольная сумма заголовка. По аналогии с контрольной суммой, которая делается в Ethernet, она также защищает заголовок IP от помех.

- После всего идёт IP адрес отправителя и IP адрес получателя. Зачем они, мы уже знаем

## Урок 3. Технология Ethernet. Протокол IP.

**расчет IP-сети:**

10.177.216.125 - IP-адрес,

255.255.255.0 - маска

| 10. | 177. | 216. | 125 |
| --- | --- | --- | --- |
| 00001010 | 10110001 | 11011000 | 01111101 |
| 255. | 255. | 255. | 0 |
| 11111111 |  11111111 | 11111111 | 00000000 |
| --- | --- | --- | --- |
| 00001010 | 10110001 | 11011000 | 00000000 |
| 10. | 177. | 216. | 0 |

=> IP-сеть 10.177.216.0/24 (24 - колличество единиц в маске, маска любой быть не может, так как это последовательность сначала единиц, затем нулей)

диапазон данной сети 10.177.216.0 - 10.177.216.255, IP-адресов 256, реальных адресов на 2 меньше

10.177.216.0 - уходит под IP-адрес сети, его нельзя назнчать на хосты

10.177.216.255 - уходит под Broadcast

Чтобы увеличит или уменьшить деапазон IP-адресов необходимо поменять маску (например: маска 255.255.254.0 увеличит колличество IP-адресов в 2 раза, а маска 255.255.255.128 уменьшит в 2 раза) 

**Connected Nets** - непосредственно настроенные сети на роутере.

**Static Routes** - “статика” - статический маршрут, который прописывает администратор.

**Next Hop** - IP адрес интерфейса следующего роутера, куда необходимо отправлять пакеты.

Связность сетей А и В - состояние, когда сеть настроена таким образом, что пакеты могут идти из сеть А в сеть В и наоборот.

**Dynamic Routing** Динамические протоколы маршрутизации - специальные протоколы, которые позволяют автоматизировать заполнение таблицы маршрутизации на роутере. Они делятся на:

  - **Link State (LS)** протоколы - вид динамических протоколов маршрутизации, которые собирают всю информацию о топологии сети, и на её основе вырабатывают таблицу маршрутизации. Это: 
    - **OSPF** - Open Shortest Path First - Link State протокол маршрутизации, основанный на алгоритме Дейкстры, популярен в корпоративных сетях. Большие сети разбиваются на зоны (area) в каждой работает свой OSPF процесс, а затем информация можду зонами распространяется с помощью специальных роутеров area border router. Area - специально выделенная область сети со своим внутренним отдельным OSPF, необходима в больших сетях для упрощения расчета кратчайшего пути. Area 0 - главная area, к ней присоединяются все остальные.
    - **ISIS** - Intermediate System to Intermediate System - Link State протокол маршрутизации, также основанный на алгоритме Дейкстры, популярен во внутренних провайдерских сетях.

  - **Distance Vector (DV)** протоколы - вид динамических протоколов маршрутизации, где роутеры принимают маршруты только от своих ближайших соседей и уже потом заносят самые лучшие маршруты в таблицу маршрутизации.

**Administrative Distance** - специальная метрика, которая решает какой протокол главнее, в случае если есть несколько одинаковых маршрутов от разных протоколов.

**VLAN** - Virtual Local Area Network - технология разделения броадкаст доменов на коммутаторах (позволяет из одного коммутатора виртуально сделить несколько независимых с отдельными броадкаст домеными).

**Access Ports** - тип порта, который принадлежит только одному VLAN. На трафик, который приходит на порт, вешается тег - специальная VLAN вставка в заголовок пакета. С трафика, который выходит из порта, тег снимается.

**Trunk Ports** - тип порта, на котором может быть настроено несколько  VLAN. Трафик с и из такого порта ходит с тегами настроенных VLAN. подынтерфейс.

Настройка VLAN делается на свиче, точно так же можно настроить роутер.
