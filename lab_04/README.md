### Лабораторная работа. Настройка IPv6-адресов на сетевых устройствах

## Топология

![](https://github.com/Gleb02/labs_otus/blob/main/lab_04/Топология.png)

## Таблицы адресации

Устройство |	Интерфейс	| IPv6-адрес |	Link local IPv6-адрес |	Длина префикса | Шлюз по умолчанию |
---------- | -----------|------------|------------------------|----------------|-------------------|
R1	       | G0/0/0     | 2001:db8:acad:a::1	| fe80::1 |	64 |	— |
R1         | G0/0/1 	  | 2001:db8:acad:1::1 	| fe80::1	| 64 |  — |
S1         | VLAN 1 	  | 2001:db8:acad:1::b	| fe80::b	| 64 | — |
PC-A	| NIC |	2001:db8:acad:1::3	| SLACC	| 64	| fe80::1 |
PC-B	| NIC	| 2001:db8:acad:a::3	| SLACC	| 64	| fe80::1 |
---------------------------------------------------------------------------------------------------

## Задачи

• Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора

• Часть 2. Ручная настройка IPv6-адресов

• Часть 3. Проверка сквозного соединения

### Часть 1.

### Шаг 1. Настройка маршрутизатора.

    Router>
    Router#conf t
    Router(config)#hostname R1
    R1(config)#service password-encryption 
    R1(config)#enable secret class
    R1(config)#banner motd #Unauthorized access is strictly prohibited.#
    R1(config)#line console 0
    R1(config-line)#logging synchronous 
    R1(config-line)#password cisco
    R1(config-line)#login
    R1(config-line)#exit
    R1(config)#interface gigabitEthernet 0/0/0
    R1(config-if)#no shutdown 
    R1(config-if)#exit
    R1(config)#interface gigabitEthernet 0/0/1
    R1(config-if)#no
    R1(config-if)#no sh
    R1(config-if)#no shutdown 
    R1(config-if)#exit

### Шаг 2. Настройка коммутатора.

    Switch>enable 
    Switch#conf t
    Switch(config)#hostname S1
    S1(config)#service password-encryption 
    S1(config)#enable secret class
    S1(config)#banner motd #Unauthorized access is strictly prohibited.#
    S1(config)#line console 0
    S1(config-line)#logging synchronous 
    S1(config-line)#password cisco
    S1(config-line)#login
    S1(config-line)#exit
    S1(config)#
    
### Часть 2.

### Шаг 1. Назначение  IPv6-адреса интерфейсам Ethernet на R1

    R1(config)#interface gigabitEthernet 0/0/0
    R1(config-if)#ipv6 address 2001:db8:acad:a::1/64
    R1(config-if)#ipv6 address fe80::1 link-local 
    R1(config-if)#no shutdown 
    R1(config-if)#exit
    R1(config)#interface gigabitEthernet 0/0/1
    R1(config-if)#ipv6 address 2001:db8:acad:1::1/64
    R1(config-if)#ipv6 address fe80::1 link-local 
    R1(config-if)#no shutdown 
    R1(config-if)#end
    R1#show ipv6 interface brief
	  GigabitEthernet0/0/0       [up/up]
    FE80::1
    2001:DB8:ACAD:A::1
    GigabitEthernet0/0/1       [up/up]
        FE80::1
        2001:DB8:ACAD:1::1
    Vlan1                      [administratively down/down]
        unassigned
*Какие группы многоадресной рассылки назначены интерфейсу G0/0?*

    R1#show ipv6 interface GigabitEthernet0/0/0
    GigabitEthernet0/0/0 is up, line protocol is up
      IPv6 is enabled, link-local address is FE80::1
      No Virtual link-local address(es):
      Global unicast address(es):
        2001:DB8:ACAD:A::1, subnet is 2001:DB8:ACAD:A::/64
      Joined group address(es):
        FF02::1
        FF02::2
        FF02::1:FF00:1

FF02::1	Все устройства

FF02::2	Все маршрутизаторы

FF02::1:FF00:1 Устройства с определенным окончанием адреса	FF02::1:FFXX:XXXX

### Шаг 2. Активируем IPv6 машрутизацию на R1

![](https://github.com/Gleb02/labs_otus/blob/main/lab_04/До.png)

Дальше вводим команду

    IPv6 unicast-routing

![](https://github.com/Gleb02/labs_otus/blob/main/lab_04/После.png)

### Шаг 3. Назначим IPv6-адреса интерфейсу управления (SVI) на S1

    S1(config)#interface vlan 1
    S1(config-if)#ipv6 address 2001:db8:acad:1::b/64
	S1(config-if)#ipv6 address fe80::b link-local 
	S1(config-if)#no shutdown 
    S1(config-if)#end
	S1#show ipv6 interface brief
    FastEthernet0/1            [down/down]
    FastEthernet0/2            [down/down]
    FastEthernet0/3            [down/down]
    FastEthernet0/4            [down/down]
    FastEthernet0/5            [up/up]
    FastEthernet0/6            [up/up]
    FastEthernet0/7            [down/down]
    FastEthernet0/8            [down/down]
    FastEthernet0/9            [down/down]
    FastEthernet0/10           [down/down]
    FastEthernet0/11           [down/down]
    FastEthernet0/12           [down/down]
    FastEthernet0/13           [down/down]
    FastEthernet0/14           [down/down]
    FastEthernet0/15           [down/down]
    FastEthernet0/16           [down/down]
    FastEthernet0/17           [down/down]
    FastEthernet0/18           [down/down]
    FastEthernet0/19           [down/down]
    FastEthernet0/20           [down/down]
    FastEthernet0/21           [down/down]
    FastEthernet0/22           [down/down]
    FastEthernet0/23           [down/down]
    FastEthernet0/24           [down/down]
    GigabitEthernet0/1         [down/down]
    GigabitEthernet0/2         [down/down]
    Vlan1                      [up/up]
        FE80::B
        2001:DB8:ACAD:1::B

### Шаг 4. Назначим статические IPv6-адреса.

![](https://github.com/Gleb02/labs_otus/blob/main/lab_04/Назначение%20IPv6.png)

Часть 3. Проверка сквозного соединения.

![](https://github.com/Gleb02/labs_otus/blob/main/lab_04/Проверка%20сквозного%20соединения.png)

### Вопросы для повторения

1.	Почему обоим интерфейсам Ethernet на R1 можно назначить один и тот же локальный адрес канала — FE80::1?
Ответ: Link-Local адреса действкют только в предел одного сетевого подключения, линка.

2.	Какой идентификатор подсети в индивидуальном IPv6-адресе 2001:db8:acad::aaaa:1234/64?
Ответ: Идентификатор подсети в индивидуальном 2001:0db8:acad:0000:0000:0000:aaaa:1234/64 это 0000
