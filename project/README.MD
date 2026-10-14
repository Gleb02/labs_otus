  # Проектная работа - Построение сети с нуля

- [Проектная работа - Построение сети с нуля](#проектная-работа---построение-сети-с-нуля)
  - [Топология](#топология)
  - [Таблица адресации](#таблица-адресации)
  - [Таблица VLAN](#таблица-vlan)
  - [Часть 1. Настройка сетей VLAN на коммутаторах.](#часть-1-настройка-сетей-vlan-на-коммутаторах)
    - [Шаг 1. Создание сетей VLAN на коммутаторах.](#шаг-1-создание-сетей-vlan-на-коммутаторах)
    - [Шаг 2. Настройка портов на коммутаторах.](#шаг-2-настройка-портов-на-коммутаторах)
    - [Шаг 3. Проверка.](#шаг-3-проверка)
  - [Часть 2. Настройка Trunk и резервирования](#часть-2-настройка-trunk-и-резервирования)
    - [Шаг 1. Настройка Trunk соединений.](#шаг-1-настройка-trunk-соединений)
    - [Шаг 2. Настройка режима STP.](#шаг-2-настройка-режима-stp)
    - [Шаг 3. Проверка Root Bridge и резервирования](#шаг-3-проверка-root-bridge-и-резервирования)
    - [Шаг 4. Настройка PortFast на портах ПК](#шаг-4-настройка-portfast-на-портах-пк)
    - [Шаг 5. Включение BPDU Guard на портах ПК](#шаг-5-включение-bpdu-guard-на-портах-пк)
    - [Шаг 6. Проверка итоговых конфигураций](#шаг-6-проверка-итоговых-конфигураций)
  - [Часть 3. Настройка IPv4 и Router-on-a-Stick](#часть-3-настройка-ipv4-и-router-on-a-stick)
    - [Шаг 1. Настройка интерфейсов на R1](#шаг-1-настройка-интерфейсов-на-r1)
    - [Шаг 2. Настройка интерфейсов на R2](#шаг-2-настройка-интерфейсов-на-r2)
    - [Шаг 3. Настройка интерфейсов на R3](#шаг-3-настройка-интерфейсов-на-r3)
    - [Шаг 4. Настрйока Management VLAN на коммутаторах](#шаг-4-настрйока-management-vlan-на-коммутаторах)
    - [Шаг 5. Проверки сетевой связанности маршрутизаторов и коммутаторов](#шаг-5-проверки-сетевой-связанности-маршрутизаторов-и-коммутаторов)
  - [Часть 4. Настройка DHCPv4](#часть-4-настройка-dhcpv4)
    - [Шаг 1. Исключение служебных адресов и создание пулов на R1](#шаг-1-исключение-служебных-адресов-и-создание-пулов-на-r1)
    - [Шаг 2. Исключение служебных адресов и создание пулов на R2](#шаг-2-исключение-служебных-адресов-и-создание-пулов-на-r2)
    - [Шаг 3. Ping шлюзов с ПК](#шаг-3-ping-шлюзов-с-пк)
  - [Часть 5. Статическая и динамическая маршрутизация](#часть-5-статическая-и-динамическая-маршрутизация)
    - [Шаг 1. Статический маршрут по умолчанию на R1](#шаг-1-статический-маршрут-по-умолчанию-на-r1)
    - [Шаг 2. Настройка OSPF на R1](#шаг-2-настройка-ospf-на-r1)
    - [Шаг 3. Отключение OSPF Hello-пакеты в пользовательских VLAN](#шаг-3-отключение-ospf-hello-пакеты-в-пользовательских-vlan)
    - [Шаг 4. Маршрут по умолчанию через OSPF](#шаг-4-маршрут-по-умолчанию-через-ospf)
    - [Шаг 5. Настройте OSPF на R2](#шаг-5-настройте-ospf-на-r2)
    - [Шаг 6. Проверка OSPF-маршрутов на маршрутизаторах](#шаг-6-проверка-ospf-маршрутов-на-маршрутизаторах)
    - [Шаг 7. Проверка маршрутизации на ПК](#шаг-7-проверка-маршрутизации-на-пк)
    - [Шаг 8. Настройка IPv6-маршрутизации на R1/R2](#шаг-8-настройка-ipv6-маршрутизации-на-r1r2)
    - [Шаг 9. Проверка IPv6-маршрутизации на ПК](#шаг-9-проверка-ipv6-маршрутизации-на-пк)
    - [Шаг 10. Итоговая проверка OSPF](#шаг-10-итоговая-проверка-ospf)
  - [Часть 6. ACL](#часть-6-acl)
    - [Шаг 1. Определение политик безопасности](#шаг-1-определение-политик-безопасности)
    - [Шаг 2. ACL для HQ Guest](#шаг-2-acl-для-hq-guest)
    - [Шаг 3. ACL для HQ Users](#шаг-3-acl-для-hq-users)
    - [Шаг 4. ACL для Branch Guest](#шаг-4-acl-для-branch-guest)
    - [Шаг 5. ACL для Branch Users](#шаг-5-acl-для-branch-users)
  - [Часть 7. Настройка NAT/PAT](#часть-7-настройка-natpat)
    - [Шаг 1. Внешний NAT-интерфейс](#шаг-1-внешний-nat-интерфейс)
    - [Шаг 2. Внутренние NAT-интерфейсы](#шаг-2-внутренние-nat-интерфейсы)
    - [Шаг 3. ACL для адресов NAT](#шаг-3-acl-для-адресов-nat)
    - [Шаг 4. PAT через R1](#шаг-4-pat-через-r1)
    - [Шаг 5. Проверка PAT](#шаг-5-проверка-pat)
    - [Шаг 6. Static NAT для PC-A](#шаг-6-static-nat-для-pc-a)
  - [Часть 8. Настройка и проверка CDP и LLDP](#часть-8-настройка-и-проверка-cdp-и-lldp)
    - [Шаг 1. Проверка работы CDP на роутерах и маршрутизаторах](#шаг-1-проверка-работы-cdp-на-роутерах-и-маршрутизаторах)
    - [Шаг 2. Отключение CDP на всех устройствах для проверки LLDP](#шаг-2-отключение-cdp-на-всех-устройствах-для-проверки-lldp)
    - [Шаг 3. Проверка LLDP](#шаг-3-проверка-lldp)
  - [Часть 9. Настройка NTP](#часть-9-настройка-ntp)
    - [Шаг 1. Проверка и настройка R1 как NTP Master](#шаг-1-проверка-и-настройка-r1-как-ntp-master)
    - [Шаг 2. Настройка клиентов](#шаг-2-настройка-клиентов)
    - [Шаг 3. Проверка работы NTP](#шаг-3-проверка-работы-ntp)

## Топология 

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/topology.png)

## Таблица адресации

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/address.png)

## Таблица VLAN

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/vlan.png)

## Часть 1. Настройка сетей VLAN на коммутаторах.
### Шаг 1. Создание сетей VLAN на коммутаторах.

Настройка VLAN коммутатора S1.

    S1>
    S1>en
    S1>enable 
    S1#conf t
    S1(config)#vlan 10
    S1(config-vlan)#name Managment
    S1(config-vlan)#ex
    S1(config)#vlan 20
    S1(config-vlan)#name Administration
    S1(config-vlan)#ex
    S1(config)#vlan 30
    S1(config-vlan)#name Users
    S1(config-vlan)#ex
    S1(config)#vlan 50
    S1(config-vlan)#name OSPF_TRANSIT
    S1(config-vlan)#ex
    S1(config)#vlan 999
    S1(config-vlan)#name ParkingLot
    S1(config-vlan)#ex
    S1(config)#vlan 1000
    S1(config-vlan)#name Native
    S1(config-vlan)#ex
    S1(config)#
    S1#

Настройка VLAN коммутатора S2.

    S2>
    S2>en
    S2>enable 
    S2#conf t
    S2(config)#vlan 10
    S2(config-vlan)#name Managment
    S2(config-vlan)#ex
    S2(config)#vlan 20
    S2(config-vlan)#name Administration
    S2(config-vlan)#ex
    S2(config)#vlan 30
    S2(config-vlan)#name Users
    S2(config-vlan)#ex
    S2(config)#vlan 40
    S2(config-vlan)#name Guest
    S2(config-vlan)#ex
    S2(config)#vlan 50
    S2(config-vlan)#name OSPF_TRANSIT
    S2(config-vlan)#ex
    S2(config)#vlan 999
    S2(config-vlan)#name ParkingLot
    S2(config-vlan)#ex
    S2(config)#vlan 1000
    S2(config-vlan)#name Native
    S2(config-vlan)#ex
    S2(config)#
    S2#

Настройка VLAN коммутатора S3.

    S3>
    S3>en
    S3>enable 
    S3#conf t
    S3(config)#vlan 110
    S3(config-vlan)#name Managment
    S3(config-vlan)#ex
    S3(config)#vlan 120
    S3(config-vlan)#name Users
    S3(config-vlan)#ex
    S3(config)#vlan 140
    S3(config-vlan)#name Guest
    S3(config-vlan)#ex
    S3(config)#vlan 999
    S3(config-vlan)#name ParkingLot
    S3(config-vlan)#ex
    S3(config)#vlan 1000
    S3(config-vlan)#name Native
    S3(config-vlan)#ex

### Шаг 2. Настройка портов на коммутаторах.

Настройка портов коммутатора S1.

    S1#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S1(config)#int
    S1(config)#interface fa0/6
    S1(config-if)#des
    S1(config-if)#description PC-A Administration
    S1(config-if)#swi
    S1(config-if)#switchport mod
    S1(config-if)#switchport mode acc
    S1(config-if)#switchport mode access 
    S1(config-if)#swit
    S1(config-if)#switchport acc
    S1(config-if)#switchport access vlan 20
    S1(config-if)#no shu
    S1(config-if)#no shutdown 
    S1(config-if)#ex
    S1(config)#interface range fa0/7-8
    S1(config-if-range)#des
    S1(config-if-range)#description Users
    S1(config-if-range)#sw
    S1(config-if-range)#switchport mode access 
    S1(config-if-range)#sw
    S1(config-if-range)#switchport  acc
    S1(config-if-range)#switchport  access vlan 30
    S1(config-if-range)#no shutdown 
    S1(config-if-range)#ex
    S1(config)#interface range fa0/3-4, fa0/9-24
    S1(config-if-range)#swi
    S1(config-if-range)#switchport m
    S1(config-if-range)#switchport mode acc
    S1(config-if-range)#switchport mode access 
    S1(config-if-range)#sw
    S1(config-if-range)#switchport acc
    S1(config-if-range)#switchport access vlan 999
    S1(config-if-range)#des
    S1(config-if-range)#description UNUSED
    S1(config-if-range)#shutdown
    S1(config-if-range)#ex
    S1(config)#interface range gi0/1-2
    S1(config-if-range)#switchport mod
    S1(config-if-range)#switchport mode acces
    S1(config-if-range)#switchport access vlan 999
    S1(config-if-range)#description UNUSED
    S1(config-if-range)#shutdown
    S1(config-if-range)#ex
    S1(config)#interface range gi0/1-2
    S1(config-if-range)#switchport mod
    S1(config-if-range)#switchport mode acces
    S1(config-if-range)#switchport acce
    S1(config-if-range)#switchport access vlan 999
    S1(config-if-range)#description UNUSED
    S1(config-if-range)#shutdown

Настройка портов коммутатора S2.

    S2(config)#interface fa0/5
    S2(config-if)#description OSPF Transit to R2
    S2(config-if)#switchport mode acc
    S2(config-if)#switchport mode access 
    S2(config-if)#switchport acc
    S2(config-if)#switchport access vlan 50
    S2(config-if)#no shutdown 
    S2(config-if)#ex
    S2(config)#interface  fa0/7
    S2(config-if)#description PC-E Guest
    S2(config-if)#switchport mode access 
    S2(config-if)#switchport access  vlan 40
    S2(config-if)#no shutdown 
    S2(config-if)#ex
    S2(config)#interface fa0/6
    S2(config-if)#description PC-D Administration
    S2(config-if)#switchport mode access 
    S2(config-if)#switchport access vlan 20
    S2(config-if)#no shutdown 
    S2(config-if)#ex
    S2(config)#interface range fa0/3-4, fa0/8-24
    S2(config-if-range)#switchport mode access
    S2(config-if-range)#switchport access vlan 999
    S2(config-if-range)#description UNUSED
    S2(config-if-range)#shutdown
    S2(config-if-range)#ex
    S2(config)#interface range gi0/1-2
    S2(config-if-range)#switchport mode access
    S2(config-if-range)#switchport access vlan 999
    S2(config-if-range)#description UNUSED
    S2(config-if-range)#shutdown

Настройка портов коммутатора S3.

    S3>enable
    S3#conf t
    S3(config)#interface fa0/6
    S3(config-if)#description PC-F Branch Users
    S3(config-if)#switchport mode access
    S3(config-if)#switchport access vlan 120
    S3(config-if)#no shutdown
    S3(config-if)#exit
    S3(config)#interface fa0/7
    S3(config-if)#description PC-G Branch Guest
    S3(config-if)#switchport mode access
    S3(config-if)#switchport access vlan 140
    S3(config-if)#no shutdown
    S3(config-if)#exit
    S3(config)#interface range fa0/1-4, fa0/8-24
    S3(config-if-range)#switchport mode access
    S3(config-if-range)#switchport access vlan 999
    S3(config-if-range)#description UNUSED
    S3(config-if-range)#shutdown
    S3(config-if-range)#exit
    S3(config)#interface range gi0/1-2
    S3(config-if-range)#switchport mode access
    S3(config-if-range)#switchport access vlan 999
    S3(config-if-range)#description UNUSED
    S3(config-if-range)#shutdown
    S3(config-if-range)#exit

### Шаг 3. Проверка.

    S1#show vlan brief 

    VLAN Name                             Status    Ports
    ---- -------------------------------- --------- -------------------------------
    1    default                          active    Fa0/1, Fa0/2, Fa0/5
    10   Managment                        active    
    20   Administration                   active    Fa0/6
    30   Users                            active    Fa0/7, Fa0/8
    50   OSPF_TRANSIT                     active    
    999  ParkingLot                       active    Fa0/3, Fa0/4, Fa0/9, Fa0/10
                                                Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24, Gig0/1, Gig0/2
    1000 Native                           active    
    1002 fddi-default                     active    
    1003 token-ring-default               active    
    1004 fddinet-default                  active    
    1005 trnet-default                    active 
   
    S1#show interfaces status 

    Port      Name               Status       Vlan       Duplex  Speed Type
    Fa0/1                        connected    1          auto    auto  10/100BaseTX
    Fa0/2                        connected    1          auto    auto  10/100BaseTX
    Fa0/3     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/4     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/5                        notconnect   1          auto    auto  10/100BaseTX
    Fa0/6     PC-A Administratio connected    20         auto    auto  10/100BaseTX
    Fa0/7     Users              connected    30         auto    auto  10/100BaseTX
    Fa0/8     Users              connected    30         auto    auto  10/100BaseTX
    Fa0/9     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/10    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/11    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/12    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/13    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/14    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/15    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/16    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/17    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/18    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/19    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/20    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/21    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/22    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/23    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/24    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Gig0/1    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Gig0/2    UNUSED             disabled 999        auto    auto  10/100BaseTX

    S2#show vlan brief 
    VLAN Name                             Status    Ports
    ---- -------------------------------- --------- -------------------------------
    1    default                          active    Fa0/1, Fa0/2
    10   Managment                        active    
    20   Administration                   active    Fa0/6
    30   Users                            active    
    40   Guest                            active    Fa0/7
    50   OSPF_TRANSIT                     active    Fa0/5
    999  ParkingLot                       active    Fa0/3, Fa0/4, Fa0/8, Fa0/9
                                                Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24, Gig0/1
                                                Gig0/2
    1000 Native                           active    
    1002 fddi-default                     active    
    1003 token-ring-default               active    
    1004 fddinet-default                  active    
    1005 trnet-default                    active 
    S2# show interfaces status 
    Port      Name               Status       Vlan       Duplex  Speed Type
    Fa0/1                        connected    1          auto    auto  10/100BaseTX
    Fa0/2                        connected    1          auto    auto  10/100BaseTX
    Fa0/3     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/4     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/5     OSPF Transit to R2 notconnect   50         auto    auto  10/100BaseTX
    Fa0/6     PC-D Administratio connected    20         auto    auto  10/100BaseTX
    Fa0/7     PC-E Guest         connected    40         auto    auto  10/100BaseTX
    Fa0/8     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/9     UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/10    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/11    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/12    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/13    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/14    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/15    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/16    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/17    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/18    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/19    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/20    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/21    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/22    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/23    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Fa0/24    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Gig0/1    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Gig0/2    UNUSED             disabled 999        auto    auto  10/100BaseTX

    S3#show vlan brief 
    VLAN Name                             Status    Ports
    ---- -------------------------------- --------- -------------------------------
    1    default                          active    Fa0/5
    110  Managment                        active    
    120  Users                            active    Fa0/6
    140  Guest                            active    Fa0/7
    999  ParkingLot                       active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/8, Fa0/9, Fa0/10, Fa0/11
                                                Fa0/12, Fa0/13, Fa0/14, Fa0/15
                                                Fa0/16, Fa0/17, Fa0/18, Fa0/19
                                                Fa0/20, Fa0/21, Fa0/22, Fa0/23
                                                Fa0/24, Gig0/1, Gig0/2
    1000 Native                           active    
    1002 fddi-default                     active    
    1003 token-ring-default               active    
    1004 fddinet-default                  active    
    1005 trnet-default                    active    

    S3#show interfaces status 
    Port      Name               Status       Vlan       Duplex  Speed Type
    Fa0/1     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/2     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/3     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/4     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/5                        notconnect   1          auto    auto  10/100BaseTX
    Fa0/6     PC-F Branch Users  connected    120        auto    auto  10/100BaseTX
    Fa0/7     PC-G Branch Guest  connected    140        auto    auto  10/100BaseTX
    Fa0/8     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/9     UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/10    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/11    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/12    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/13    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/14    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/15    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/16    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/17    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/18    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/19    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/20    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/21    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/22    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/23    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Fa0/24    UNUSED             notconnect   999        auto    auto  10/100BaseTX
    Gig0/1    UNUSED             disabled 999        auto    auto  10/100BaseTX
    Gig0/2    UNUSED             disabled 999        auto    auto  10/100BaseTX

## Часть 2. Настройка Trunk и резервирования
### Шаг 1. Настройка Trunk соединений.

    S1(config)#interface fa0/5
    S1(config-if)#description  TRUNK_TO_R1
    S1(config-if)#sw
    S1(config-if)#switchport mode trunk
    S1(config-if)#switchport trunk native vlan 1000
    S1(config-if)#switchport trunk allowed vlan 10,20,30,40,50,1000
    S1(config-if)#switchport nonegotiate 
    S1(config-if)#no shutdown 
    S1(config-if)#ex
    S1(config)#interface range fa0/1-2
    S1(config-if-range)#description TRUNK_TO_S2
    S1(config-if-range)#switchport mode trunk
    S1(config-if-range)#switchport trunk allowed vlan 10,20,30,40,50,1000
    S1(config-if-range)#switchport nonegotiate 
    S1(config-if-range)#no shu
    S1(config-if-range)#no shutdown 
    S1(config-if-range)#ex

    S2(config)#interface range fa0/1-2
    S2(config-if-range)#description TRUNK_TO_S1
    S2(config-if-range)#switchport mode trunk
    S2(config-if-range)#sw
    S2(config-if-range)#switchport trunk native vlan 1000
    S2(config-if-range)#switchport trunk allowed vlan 10,20,30,40,50,1000
    S2(config-if-range)#switchport none
    S2(config-if-range)#switchport nonegotiate 
    S2(config-if-range)#no shutdown 

    S3>en
    S3#conf t
    S3(config)#interface fa0/5
    S3(config-if)#description TRUNK_TO_R2
    S3(config-if)#switchport mode trunk 
    S3(config-if)#switchport trunk native vlan 1000
    S3(config-if)#switchport trunk allowed vlan 110,120,140,1000
    S3(config-if)#switchport nonegotiate 
    S3(config-if)#no shutdown 
    S3(config-if)#ex

### Шаг 2. Настройка режима STP.

    S1#conf t
    S1(config)#spanning-tree mode pvst
    S1(config)#spanning-tree vlan 10,20,30,40,50,1000 root primary 

    S2(config)#spanning-tree mode pvst
    S2(config)#spanning-tree vlan 10,20,30,40,50,1000 root secondary 

    S3(config)#spanning-tree mode pvst
    S3(config)#

### Шаг 3. Проверка Root Bridge и резервирования

    S1#show spanning-tree vlan 20
    VLAN0020
      Spanning tree enabled protocol ieee
      Root ID    Priority    24596
             Address     00D0.BC50.9A25
             This bridge is the root
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec

      Bridge ID  Priority    24596  (priority 24576 sys-id-ext 20)
             Address     00D0.BC50.9A25
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  20

    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/6            Desg FWD 19        128.6    P2p
    Fa0/1            Desg FWD 19        128.1    P2p
    Fa0/2            Desg FWD 19        128.2    P2p

    S2#show spanning-tree vlan 20
    VLAN0020
    Spanning tree enabled protocol ieee
    Root ID    Priority    24596
             Address     00D0.BC50.9A25
             Cost        19
             Port        1(FastEthernet0/1)
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec

    Bridge ID  Priority    28692  (priority 28672 sys-id-ext 20)
             Address     00E0.8FBD.0AA1
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  20

    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/6            Desg FWD 19        128.6    P2p
    Fa0/1            Root FWD 19        128.1    P2p

### Шаг 4. Настройка PortFast на портах ПК

    S1#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S1(config)#interface range fa0/6-8
    S1(config-if-range)#spa
    S1(config-if-range)#spanning-tree po
    S1(config-if-range)#spanning-tree portfast 
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/6 but will only
    have effect when the interface is in a non-trunking mode.
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/7 but will only
    have effect when the interface is in a non-trunking mode.
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/8 but will only
    have effect when the interface is in a non-trunking mode.
    S1(config-if-range)#ex
    S1(config)#

    S2#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S2(config)#int
    S2(config)#interface rang
    S2(config)#interface range fa0/6-7
    S2(config-if-range)#spa
    S2(config-if-range)#spanning-tree po
    S2(config-if-range)#spanning-tree portfast 
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/6 but will only
    have effect when the interface is in a non-trunking mode.
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/7 but will only
    have effect when the interface is in a non-trunking mode.
    S2(config-if-range)#ex
    S2(config)#

    S3(config)#interface range fa0/6-7
    S3(config-if-range)#sp
    S3(config-if-range)#spa
    S3(config-if-range)#spanning-tree p
    S3(config-if-range)#spanning-tree portfast 
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/6 but will only
    have effect when the interface is in a non-trunking mode.
    %Warning: portfast should only be enabled on ports connected to a single
    host. Connecting hubs, concentrators, switches, bridges, etc... to this
    interface  when portfast is enabled, can cause temporary bridging loops.
    Use with CAUTION

    %Portfast has been configured on FastEthernet0/7 but will only
    have effect when the interface is in a non-trunking mode.
    S3(config-if-range)#ex
    S3(config)#

### Шаг 5. Включение BPDU Guard на портах ПК

    S1(config)#interface range fa0/6-8
    S1(config-if-range)#spanning-tree bpduguard enable 
    S1(config-if-range)#ex
    S1(config)#

    S2(config)#interface range fa0/6-7
    S2(config-if-range)#spanning-tree bpduguard enable 
    S2(config-if-range)#ex
    S2(config)#

    S3(config)#interface range fa0/6-7
    S3(config-if-range)#spanning-tree bpduguard enable 
    S3(config-if-range)#ex
    S3(config)#

### Шаг 6. Проверка итоговых конфигураций

    S1#show interfaces trunk 
    Port        Mode         Encapsulation  Status        Native vlan
    Fa0/1       on           802.1q         trunking      1000
    Fa0/2       on           802.1q         trunking      1000

    Port        Vlans allowed on trunk
    Fa0/1       10,20,30,40,50,1000
    Fa0/2       10,20,30,40,50,1000

    Port        Vlans allowed and active in management domain
    Fa0/1       10,20,30,50,1000
    Fa0/2       10,20,30,50,1000

    Port        Vlans in spanning tree forwarding state and not pruned
    Fa0/1       10,20,30,50,1000
    Fa0/2       10,20,30,50,1000
    S1#show spanning-tree vlan 20
    VLAN0020
    Spanning tree enabled protocol ieee
    Root ID    Priority    24596
             Address     00D0.BC50.9A25
             This bridge is the root
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec

    Bridge ID  Priority    24596  (priority 24576 sys-id-ext 20)
             Address     00D0.BC50.9A25
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  20

    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/6            Desg FWD 19        128.6    P2p
    Fa0/1            Desg FWD 19        128.1    P2p
    Fa0/2            Desg FWD 19        128.2    P2p

    S2#show interfaces trunk 
    Port        Mode         Encapsulation  Status        Native vlan
    Fa0/1       on           802.1q         trunking      1000
    Fa0/2       on           802.1q         trunking      1000

    Port        Vlans allowed on trunk
    Fa0/1       10,20,30,40,50,1000
    Fa0/2       10,20,30,40,50,1000

    Port        Vlans allowed and active in management domain
    Fa0/1       10,20,30,40,50,1000
    Fa0/2       10,20,30,40,50,1000

    Port        Vlans in spanning tree forwarding state and not pruned
    Fa0/1       10,20,30,40,50,1000
    Fa0/2       40
    S2#show spanning-tree vlan 20
    VLAN0020
    Spanning tree enabled protocol ieee
    Root ID    Priority    24596
             Address     00D0.BC50.9A25
             Cost        19
             Port        1(FastEthernet0/1)
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec

    Bridge ID  Priority    28692  (priority 28672 sys-id-ext 20)
             Address     00E0.8FBD.0AA1
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  20

    Interface        Role Sts Cost      Prio.Nbr Type
    ---------------- ---- --- --------- -------- --------------------------------
    Fa0/6            Desg FWD 19        128.6    P2p
    Fa0/1            Root FWD 19        128.1    P2p
    Fa0/2            Altn BLK 19        128.2    P2p

    S3#show interfaces trunk
    Port      Mode     Encapsulation  Status      Native vlan
    Fa0/5     on       802.1q         trunking    1000

    Port      Vlans allowed on trunk
    Fa0/5     110,120,140,1000

    Port      Vlans allowed and active in management domain
    Fa0/5     110,120,140,1000

    Port      Vlans in spanning tree forwarding state and not pruned
    Fa0/5     110,120,140,1000

## Часть 3. Настройка IPv4 и Router-on-a-Stick
### Шаг 1. Настройка интерфейсов на R1

    R1>
    R1>en
    R1#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    R1(config)#int
    R1(config)#interface 
    R1(config)#interface 
    R1(config)#interface 
    R1(config)#interface g0/0
    %Invalid interface type and number
    R1(config)#
    R1(config)#end
    R1#vlan database
    % Warning: It is recommended to configure VLAN from config mode,
    as VLAN database mode is being deprecated. Please consult user
    documentation for configuring VTP/VLAN in config mode.

    R1(vlan)#
    %SYS-5-CONFIG_I: Configured from console by console

    R1(vlan)#exit
    APPLY completed.
    Exiting....
    R1#vlan database
    % Warning: It is recommended to configure VLAN from config mode,
      as VLAN database mode is being deprecated. Please consult user
      documentation for configuring VTP/VLAN in config mode.

    R1(vlan)#
    R1(vlan)#exit
    APPLY completed.
    Exiting....
    R1#configure terminal
    Enter configuration commands, one per line.  End with CNTL/Z.
    R1(config)#interface GigabitEthernet0/0/0
    R1(config-if)#
    R1(config-if)#exit
    R1(config)#interface GigabitEthernet0/0/0
    R1(config-if)#de
    R1(config-if)#des
    R1(config-if)#description LINK_TO_R3
    R1(config-if)#ip ad
    R1(config-if)#ip address 209.165.200.230 255.255.255.248
    R1(config-if)#no sh
    R1(config-if)#no shutdown 

    R1(config-if)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to up
    ex
    R1(config)#int
    R1(config)#interface g0/0/1
    R1(config-if)#des
    R1(config-if)#description TRUNK_TO_S1
    R1(config-if)#no ip add
    R1(config-if)#no ip address 
    R1(config-if)#no sh
    R1(config-if)#no shutdown 

    R1(config-if)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1, changed state to up
    ex
    R1(config)#interface g0/0/1.10
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.10, changed state to up

    R1(config-subif)#des
    R1(config-subif)#description VLAN10_MANAGEMENT
    R1(config-subif)#en
    R1(config-subif)#encapsulation do
    R1(config-subif)#encapsulation dot1Q  10
    R1(config-subif)#ip
    R1(config-subif)#ip ad
    R1(config-subif)#ip address 192.168.10.1 255.255.255.0
    R1(config-subif)#ex
    R1(config)#interface g0/0/1.20
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.20, changed state to up

    R1(config-subif)#description VLAN20_ADMINISTRATION
    R1(config-subif)#encapsulation dot1Q  20
    R1(config-subif)#ip add
    R1(config-subif)#ip address 192.168.20.1 255.255.255.0
    R1(config-subif)#ex
    R1(config)#interface g0/0/1.30
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.30, changed state to up
    description VLAN30_USERS
    R1(config-subif)#encapsulation dot1Q  30
    R1(config-subif)#ip address 192.168.30.1 255.255.255.0
    R1(config-subif)#ex
    R1(config)#interface g0/0/1.40
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.40, changed state to up

    R1(config-subif)#de
    R1(config-subif)#des
    R1(config-subif)#description VLAN40_GUEST
    R1(config-subif)#encapsulation dot1Q  40
    R1(config-subif)#ip address 192.168.40.1 255.255.255.0
    R1(config-subif)#ex
    R1(config)#in
    R1(config)#interface g0/0/1.50
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.50, changed state to up

    R1(config-subif)#des
    R1(config-subif)#description VLAN50_OSPF_TRANSIT
    R1(config-subif)#enca
    R1(config-subif)#encapsulation d
    R1(config-subif)#encapsulation dot1Q 50
    R1(config-subif)#ip add
    R1(config-subif)#ip address 10.255.0.1 255.255.255.252
    R1(config-subif)#ex
    R1(config)#int
    R1(config)#interface g0/0/1.1000
    R1(config-subif)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/1.1000, changed state to up

    R1(config-subif)#des
    R1(config-subif)#description NATIVE_VLAN
    R1(config-subif)#enca
    R1(config-subif)#encapsulation do
    R1(config-subif)#encapsulation dot1Q 1000 native
    R1(config-subif)#no ip add
    R1(config-subif)#no ip address 
    R1(config-subif)#ex
    R1(config)#

### Шаг 2. Настройка интерфейсов на R2

    R2(config)#int
    R2(config)#interface g0/0/0
    R2(config-if)#description OSPF_TRANSIT_TO_R1
    R2(config-if)#ip address 10.255.0.2 255.255.255.252
    R2(config-if)#no sh
    R2(config-if)#ex
    R2(config)#interface g0/0/1
    R2(config-if)#des
    R2(config-if)#description  TRUNK_TO_R3
    R2(config-if)#no ip ad
    R2(config-if)#no ip address 
    R2(config-if)#no shu
    R2(config-if)#no shutdown 
    R2(config-if)#ex
    R2(config)#interface g0/0/1.110
    R2(config-subif)#des
    R2(config-subif)#description  VLAN_110_MANAGEMENT
    R2(config-subif)#enc
    R2(config-subif)#encapsulation d
    R2(config-subif)#encapsulation dot1Q 110
    R2(config-subif)#ip add
    R2(config-subif)#ip address 192.168.110.1 255.255.255.0
    R2(config-subif)#ex
    R2(config)#interface g0/0/1.120
    R2(config-subif)#description  VLAN_120_USERS
    R2(config-subif)#enc
    R2(config-subif)#encapsulation d
    R2(config-subif)#encapsulation dot1Q 120
    R2(config-subif)#ipa
    R2(config-subif)#ipa
    R2(config-subif)#ip add
    R2(config-subif)#ip address 192.168.120.1 255.255.255.0
    R2(config-subif)#ex
    R2(config)#interface g0/0/1.1000
    R2(config-subif)#desc
    R2(config-subif)#description NATIVE_VLAN
    R2(config-subif)#enc
    R2(config-subif)#encapsulation d
    R2(config-subif)#encapsulation dot1Q 1000 native
    R2(config-subif)#no ip add
    R2(config-subif)#no ip address 
    R2(config-subif)#ex
    R2(config)#

### Шаг 3. Настройка интерфейсов на R3

    R3>en
    R3#conf
    Configuring from terminal, memory, or network [terminal]? 
    Enter configuration commands, one per line.  End with CNTL/Z.
    R3(config)#int
    R3(config)#interface g0/0/0
    R3(config-if)#des
    R3(config-if)#description  LINKE_TO_R1
    R3(config-if)#ip add
    R3(config-if)#ip address 209.165.200.225 255.255.255.248
    R3(config-if)#no sh

    R3(config-if)#
    %LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to up

    %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to up

    R3(config-if)#ex
    R3(config)#interface loopback 1

    R3(config-if)#
    %LINK-5-CHANGED: Interface Loopback1, changed state to up

    %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback1, changed state to up

    R3(config-if)#description INTERNET_TEST_NETWORK
    R3(config-if)#ip address 209.165.200.1 255.255.255.224
    R3(config-if)#ex
    R3(config)#

### Шаг 4. Настройка Management VLAN на коммутаторах

    S1>en
    S1#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S1(config)#int
    S1(config)#interface vlan 10
    S1(config-if)#
    %LINK-5-CHANGED: Interface Vlan10, changed state to up

    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan10, changed state to up

    S1(config-if)#description MANAGEMENT
    S1(config-if)#ip address 192.168.10.2 255.255.255.0
    S1(config-if)#no shutdown 
    S1(config-if)#ex
    S1(config)#ip default-gateway 192.168.10.1
    S1(config)#

    S2>en
    S2#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S2(config)#interface vlan 10
    S2(config-if)#
    %LINK-5-CHANGED: Interface Vlan10, changed state to up

    %LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan10, changed state to up
    S2(config-if)#description MANAGMENT
    S2(config-if)#ip address 192.168.10.3 255.255.255.0
    S2(config-if)#no sh
    S2(config-if)#ex
    S2(config)#ip default-gateway 192.168.10.1
    S2(config)#ex

    S3>
    S3>en
    S3#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S3(config)#interface vlan 10
    S3(config-if)#description MANAGMENT
    S3(config-if)#ip address 192.168.110.2 255.255.255.0
    S3(config-if)#no sh
    S3(config-if)#ex

### Шаг 5. Проверки сетевой связанности маршрутизаторов и коммутаторов

    S1#ping 192.168.10.1
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 192.168.10.1, timeout is 2 seconds:
    .!!!!
    Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/0 ms


    S1#ping 192.168.10.3
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 192.168.10.3, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms


    S2#ping 192.168.10.1
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 192.168.10.1, timeout is 2 seconds:
    .!!!!
    Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/0 ms

    S2#ping 192.168.10.2
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 192.168.10.2, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

    S3#ping 192.168.110.1
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 192.168.110.1, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

    R1#ping 10.255.0.2
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 10.255.0.2, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

    R1#ping 209.165.200.225
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 209.165.200.225, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

    R2#ping 10.255.0.1
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 10.255.0.1, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

    R3#ping 209.165.200.230
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 209.165.200.230, timeout is 2 seconds:
    .!!!!
    Success rate is 60 percent (3/5), round-trip min/avg/max = 0/0/0 ms\

## Часть 4. Настройка DHCPv4

R1 — головной офис
| VLAN	| Назначение |	Сеть            | DHCP |
--------|------------|------------------|------|
| 110   |	Management |192.168.110.0/24  |	Нет  |
| 120   |	Users	     |192.168.120.0/24	| Да   |
| 140	  | Guest      |192.168.140.0/24	| Да   |
------------------------------------------------
*Management VLAN не обслуживаем DHCP, потому что IP‑адреса сетевого оборудования должны быть постоянными.

R2 — филиал
|VLAN|Назначение      |	Сеть	         |DHCP |
|----|----------------|----------------|-----|
|10	 |Management	    |192.168.10.0/24 |	Нет|
|20	 |Administration	|192.168.20.0/24 |Да   |
|30  |Users	          |192.168.30.0/24 |Да   |
|40	 |Guest	          |192.168.40.0/24 |Да   |
|50	 |OSPF_TRANSIT    |	10.255.0.0/30	 |Нет  |
----------------------------------------------
*Примечание: PC‑A будет иметь статический IP, для будущей настройки static NAT.

### Шаг 1. Исключение служебных адресов и создание пулов на R1

    R1>en
    R1#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    R1(config)#ip dhcp
    R1(config)#ip dhcp ex
    R1(config)#ip dhcp excluded-address 192.168.20.1 192.168.20.10
    R1(config)#ip dhcp excluded-address 192.168.30.1 192.168.30.9
    R1(config)#ip dhcp excluded-address 192.168.40.1 192.168.40.9
    R1(config)#ip dh
    R1(config)#ip dhcp po
    R1(config)#ip dhcp pool HQ_ADMINISTRATION
    R1(dhcp-config)#netw
    R1(dhcp-config)#network 192.168.20.0 255.255.255.0
    R1(dhcp-config)#def
    R1(dhcp-config)#default-router 192.168.20.1
    R1(dhcp-config)#ex
    R1(config)#ip dh
    R1(config)#ip dhcp po
    R1(config)#ip dhcp pool HQ_USERS
    R1(dhcp-config)#netw
    R1(dhcp-config)#network 192.168.30.0 255.255.255.0
    R1(dhcp-config)#de
    R1(dhcp-config)#default-router 192.168.30.1
    R1(dhcp-config)#ex
    R1(config)#ip dhc
    R1(config)#ip dhcp po
    R1(config)#ip dhcp pool HQ_GUEST
    R1(dhcp-config)#net
    R1(dhcp-config)#network 192.168.40.0 255.255.255.0
    R1(dhcp-config)#de
    R1(dhcp-config)#default-router 192.168.40.1
    R1(dhcp-config)#ex


### Шаг 2. Исключение служебных адресов и создание пулов на R2

    R2#
    R2#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    R2(config)#ip dh
    R2(config)#ip dhcp ex
    R2(config)#ip dhcp excluded-address 192.168.120.1 192.168.120.9
    R2(config)#ip dhc
    R2(config)#ip dhcp ex
    R2(config)#ip dhcp po
    R2(config)#ip dhcp pool BRANCH_USERS
    R2(dhcp-config)#network 192.168.120.0 255.255.255.0
    R2(dhcp-config)#def
    R2(dhcp-config)#default-router 192.168.120.1
    R2(dhcp-config)#ex
    R2(config)#ip dhcp pool BRANCH_GUEST
    R2(dhcp-config)#network 192.168.140.0 255.255.255.0
    R2(dhcp-config)#default-router 192.168.140.1
    R2(dhcp-config)#ex
    R2(config)#


### Шаг 3. Ping шлюзов с ПК

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-A%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-B%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-C%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-D%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-E%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-F%20getway.png)

![alt text](https://github.com/Gleb02/labs_otus/blob/main/project/image/Ping%20PC-G%20getway.png)

## Часть 5. Статическая и динамическая маршрутизация

    Логика маршрутизации

              209.165.200.1
                  R3 Lo1
                    |
                    |
                   R3
              209.165.200.225
                    |
            Static Default Route
                    |
              209.165.200.230
                   R1
                    |
              10.255.0.1
                    |
                OSPF Area 0
                    |
              10.255.0.2
                   R2
### Шаг 1. Статический маршрут по умолчанию на R1

    R1>enable
    R1#conf t
    Enter configuration commands, one per line. End with CNTL/Z.
    R1(config)#ip route 0.0.0.0 0.0.0.0 209.165.200.225
    R1(config)#end
    R1#
    %SYS-5-CONFIG_I: Configured from console by console
    R1#show ip route
    Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
           D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
           N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
           E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
           i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
           * - candidate default, U - per-user static route, o - ODR
           P - periodic downloaded static route
    
    Gateway of last resort is 209.165.200.225 to network 0.0.0.0

         10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
    C       10.255.0.0/30 is directly connected, GigabitEthernet0/0/1.50
    L       10.255.0.1/32 is directly connected, GigabitEthernet0/0/1.50
     192.168.10.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.10.0/24 is directly connected, GigabitEthernet0/0/1.10
    L       192.168.10.1/32 is directly connected, GigabitEthernet0/0/1.10
     192.168.20.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.20.0/24 is directly connected, GigabitEthernet0/0/1.20
    L       192.168.20.1/32 is directly connected, GigabitEthernet0/0/1.20
     192.168.30.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.30.0/24 is directly connected, GigabitEthernet0/0/1.30
    L       192.168.30.1/32 is directly connected, GigabitEthernet0/0/1.30
     192.168.40.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.40.0/24 is directly connected, GigabitEthernet0/0/1.40
    L       192.168.40.1/32 is directly connected, GigabitEthernet0/0/1.40
     209.165.200.0/24 is variably subnetted, 2 subnets, 2 masks
    C       209.165.200.224/29 is directly connected, GigabitEthernet0/0/0
    L       209.165.200.230/32 is directly connected, GigabitEthernet0/0/0
    S*   0.0.0.0/0 [1/0] via 209.165.200.225
    R1#
    R1#ping 209.165.200.1
    Type escape sequence to abort.
    Sending 5, 100-byte ICMP Echos to 209.165.200.1, timeout is 2 seconds:
    !!!!!
    Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/0 ms
   
### Шаг 2. Настройка OSPF на R1

  OSPF process ID = 56

  Area = 0

  Router ID R1 = 1.1.1.1

  Router ID R2 = 2.2.2.2

    R1#conf t
    Enter configuration commands, one per line. End with CNTL/Z.
    R1(config)#router ospf 56
    R1(config-router)#router-id 1.1.1.1
    R1(config-router)#network 192.168.10.0 0.0.0.255 area 0
    R1(config-router)#network 192.168.20.0 0.0.0.255 area 0
    R1(config-router)#network 192.168.30.0 0.0.0.255 area 0
    R1(config-router)#network 192.168.40.0 0.0.0.255 area 0
    R1(config-router)#network 10.255.0.0 0.0.0.3 area 0
    R1(config-router)#

###  Шаг 3. Отключение OSPF Hello-пакеты в пользовательских VLAN

    R1(config-router)#passive-interface default
    R1(config-router)#no passive-interface g0/0/1/50

###  Шаг 4. Маршрут по умолчанию через OSPF

R1(config-router)#default-information originate
R1(config-router)#ex

### Шаг 5. Настройте OSPF на R2

    R2>enable
    R2#conf t
    Enter configuration commands, one per line. End with CNTL/Z.
    R2(config)#router ospf 56
    R2(config-router)#router-id 2.2.2.2
    R2(config-router)#network 192.168.110.0 0.0.0.255 area 0
    R2(config-router)#network 192.168.120.0 0.0.0.255 area 0
    R2(config-router)#network 192.168.140.0 0.0.0.255 area 0
    R2(config-router)#network 10.255.0.0 0.0.0.3 area 0
    R2(config-router)#passive-interface default
    R2(config-router)#no passive-interface g0/0/0
    R2(config-router)#exit
    R2(config)#end
    R2#
    %SYS-5-CONFIG_I: Configured from console by console
    R2#
    01:02:01: %OSPF-5-ADJCHG: Process 56, Nbr 1.1.1.1 on GigabitEthernet0/0/0 from LOADING to FULL, Loading Done
    R2#show ip ospf neighbor
    
    Neighbor ID     Pri   State           Dead Time   Address         Interface
    1.1.1.1         1     FULL/DR         00:00:36    10.255.0.1      GigabitEthernet0/0/0
    R2#

### Шаг 6. Проверка OSPF-маршрутов на маршрутизаторах
    R2#show ip route ospf
    O    192.168.10.0 [110/2] via 10.255.0.1, 00:01:16, GigabitEthernet0/0/0
    O    192.168.20.0 [110/2] via 10.255.0.1, 00:01:16, GigabitEthernet0/0/0
    O    192.168.30.0 [110/2] via 10.255.0.1, 00:01:16, GigabitEthernet0/0/0
    O    192.168.40.0 [110/2] via 10.255.0.1, 00:01:16, GigabitEthernet0/0/0
    O*E2 0.0.0.0/0 [110/1] via 10.255.0.1, 00:01:16, GigabitEthernet0/0/0

### Шаг 10. Итоговая проверка OSPF

R1#show ip ospf neighbor

    Neighbor ID     Pri   State           Dead Time   Address         Interface
    2.2.2.2         1     FULL/BDR        00:00:36    10.255.0.2      GigabitEthernet0/0/1.50
    
    R1#show ip ospf interface brief
    Interface   PID   Area   IP Address/Mask          Cost  State   Nbrs F/C
    Gig         56    0      192.168.10.1/255.255.255.0 1     WAIT    0/0
    Gig         56    0      192.168.20.1/255.255.255.0 1     WAIT    0/0
    Gig         56    0      192.168.30.1/255.255.255.0 1     WAIT    0/0
    Gig         56    0      192.168.40.1/255.255.255.0 1     WAIT    0/0
    Gig         56    0      10.255.0.1/255.255.255.252 1     DR      0/0
    
    R1#show ip protocols
    Routing Protocol is "ospf 56"
    Outgoing update filter list for all interfaces is not set
    Incoming update filter list for all interfaces is not set
    Router ID 1.1.1.1
    It is an autonomous system boundary router
    Redistributing External Routes from,
    Number of areas in this router is 1. 1 normal 0 stub 0 nssa
    Maximum path: 4
    Routing for Networks:
      192.168.10.0 0.0.0.255 area 0
      192.168.20.0 0.0.0.255 area 0
      192.168.30.0 0.0.0.255 area 0
      192.168.40.0 0.0.0.255 area 0
      10.255.0.0 0.0.0.3 area 0
    Passive Interface(s):
      Vlan1
      GigabitEthernet0/0/0
      GigabitEthernet0/0/1
      GigabitEthernet0/0/1.10
      GigabitEthernet0/0/1.20
      GigabitEthernet0/0/1.30
      GigabitEthernet0/0/1.40
      GigabitEthernet0/0/1.1000
    Routing Information Sources:

## Часть 6. ACL
### Шаг 1. Определение политик безопасности

| № | Источник | Назначение | Политика |
|---:|---|---|---|
| 1 | HQ Guest VLAN 40 | Все корпоративные IPv4-сети | **Deny** |
| 2 | Branch Guest VLAN 140 | Все корпоративные IPv4-сети | **Deny** |
| 3 | HQ Guest / Branch Guest | Internet | **Permit** |
| 4 | HQ Users VLAN 30 | Management VLAN 10 и 110 по SSH | **Deny TCP/22** |
| 5 | Branch Users VLAN 120 | Management VLAN 10 и 110 по SSH | **Deny TCP/22** |
| 6 | Administration VLAN 20 | Management | **Permit** |
| 7 | Остальной пользовательский трафик | Разрешённые сети | **Permit** |

### Шаг 2. ACL для HQ Guest

    R1(config)#ip access-list extended HQ_GUEST_IN
    R1(config-ext-nacl)#permit udp any eq bootpc any eq bootps
    R1(config-ext-nacl)#permit icmp 192.168.40.0 0.0.0.255 host 192.168.40.1 echo
    R1(config-ext-nacl)#deny ip 192.168.40.0 0.0.0.255 192.168.0.0 0.0.255.255
    R1(config-ext-nacl)#permit ip 192.168.40.0 0.0.0.255 any
    R1(config-ext-nacl)#exit
    R1(config)#interface g0/0/1.40
    R1(config-subif)#ip access-group HQ_GUEST_IN in
    R1(config-subif)#exit

### Шаг 3. ACL для HQ Users

    R1(config)#ip access-list extended HQ_USERS_IN
    R1(config-ext-nacl)#permit udp any eq bootpc any eq bootps
    R1(config-ext-nacl)#deny tcp 192.168.30.0 0.0.0.255 192.168.10.0 0.0.0.255 eq 22
    R1(config-ext-nacl)#deny tcp 192.168.30.0 0.0.0.255 192.168.110.0 0.0.0.255 eq 22
    R1(config-ext-nacl)#permit ip 192.168.30.0 0.0.0.255 any
    R1(config-ext-nacl)#exit
    R1(config)#interface g0/0/1.30
    R1(config-subif)#ip access-group HQ_USERS_IN in
    R1(config-subif)#exit

### Шаг 4. ACL для Branch Guest

    R2(config)#ip access-list extended BRANCH_GUEST_IN
    R2(config-ext-nacl)#permit udp any eq bootpc any eq bootps
    R2(config-ext-nacl)#permit icmp 192.168.140.0 0.0.0.255 host 192.168.140.1 echo
    R2(config-ext-nacl)#deny ip 192.168.140.0 0.0.0.255 192.168.0.0 0.0.255.255
    R2(config-ext-nacl)#permit ip 192.168.140.0 0.0.0.255 any
    R2(config-ext-nacl)#exit
    R2(config)#interface g0/0/1.140
    R2(config-subif)#ip access-group BRANCH_GUEST_IN in
    R2(config-subif)#exit

### Шаг 5. ACL для Branch Users

    R2(config)#ip access-list extended BRANCH_USERS_IN
    R2(config-ext-nacl)#permit udp any eq bootpc any eq bootps
    R2(config-ext-nacl)#deny tcp 192.168.120.0 0.0.0.255 192.168.110.0 0.0.0.255 eq 22
    R2(config-ext-nacl)#deny tcp 192.168.120.0 0.0.0.255 192.168.10.0 0.0.0.255 eq 22
    R2(config-ext-nacl)#permit ip 192.168.120.0 0.0.0.255 any
    R2(config-ext-nacl)#exit
    R2(config)#interface g0/0/1.120
    R2(config-subif)#ip access-group BRANCH_USERS_IN in
    R2(config-subif)#exit

## Часть 7. Настройка NAT/PAT

Логическая схема 

                INTERNET
                    |
                   R3
                    |
     209.165.200.224/29
                    |
                   R1
            NAT / PAT EDGE
               /         \
              /           \
  209.165.200.229       209.165.200.230
      Static NAT             PAT
          |                   |
        PC-A              остальные

### Шаг 1. Внешний NAT-интерфейс

    R1#conf t
    Enter configuration commands, one per line. End with CNTL/Z.
    R1(config)#interface g0/0/0
    R1(config-if)#ip nat outside
    R1(config-if)#exit

### Шаг 2. Внутренние NAT-интерфейсы 

    R1(config)#interface g0/0/1.10
    R1(config-subif)#ip nat inside
    R1(config-subif)#exit
    R1(config)#interface g0/0/1.20
    R1(config-subif)#ip nat inside
    R1(config-subif)#exit
    R1(config)#interface g0/0/1.30
    R1(config-subif)#ip nat inside
    R1(config-subif)#exit
    R1(config)#interface g0/0/1.40
    R1(config-subif)#ip nat inside
    R1(config-subif)#exit
    R1(config)#interface g0/0/1.50
    R1(config-subif)#ip nat inside
    R1(config-subif)#exit

### Шаг 3. ACL для адресов NAT

    R1(config)#access-list 1 permit 192.168.0.0 0.0.255.255

### Шаг 4. PAT через R1

    R1(config)#ip nat inside source list 1 interface g0/0/0 overload

### Шаг 5. Проверка PAT

    R1#show ip nat translations
    Pro  Inside global      Inside local       Outside local      Outside global
    icmp 209.165.200.230:13 192.168.30.10:13   209.165.200.1:13   209.165.200.1:13
    icmp 209.165.200.230:14 192.168.30.10:14   209.165.200.1:14   209.165.200.1:14
    icmp 209.165.200.230:15 192.168.30.10:15   209.165.200.1:15   209.165.200.1:15
    icmp 209.165.200.230:16 192.168.30.10:16   209.165.200.1:16   209.165.200.1:16
    
    R1#show ip nat statistics
    Total translations: 0 (0 static, 0 dynamic, 0 extended)
    Outside Interfaces: GigabitEthernet0/0/0
    Inside Interfaces: GigabitEthernet0/0/1.10 , GigabitEthernet0/0/1.20 , GigabitEthernet0/0/1.30 , GigabitEthernet0/0/1.40 , GigabitEthernet0/0/1.50
    Hits: 16  Misses: 16
    Expired translations: 16
    Dynamic mappings:


### Шаг 6. Static NAT для PC-A

    R1#show ip nat translations
    Pro  Inside global      Inside local       Outside local      Outside global
    icmp 209.165.200.230:13 192.168.30.10:13   209.165.200.1:13   209.165.200.1:13
    icmp 209.165.200.230:14 192.168.30.10:14   209.165.200.1:14   209.165.200.1:14
    icmp 209.165.200.230:15 192.168.30.10:15   209.165.200.1:15   209.165.200.1:15
    icmp 209.165.200.230:16 192.168.30.10:16   209.165.200.1:16   209.165.200.1:16
    
    R1(config)#ip nat inside source static 192.168.20.10 209.165.200.229
    R1(config)#end
    R1#
    %SYS-5-CONFIG_I: Configured from console by console
    
    R1#show ip nat translations
    Pro  Inside global      Inside local       Outside local      Outside global
    ---  209.165.200.229    192.168.20.10      ---                ---

    R1#show ip nat translations
    Pro  Inside global        Inside local         Outside local        Outside global
    icmp 209.165.200.229:1    192.168.20.10:1      209.165.200.1:1      209.165.200.1:1
    icmp 209.165.200.229:2    192.168.20.10:2      209.165.200.1:2      209.165.200.1:2
    icmp 209.165.200.229:2    192.168.20.10:2      209.165.200.225:2    209.165.200.225:2
    icmp 209.165.200.229:3    192.168.20.10:3      209.165.200.1:3      209.165.200.1:3
    icmp 209.165.200.229:3    192.168.20.10:3      209.165.200.225:3    209.165.200.225:3
    icmp 209.165.200.229:4    192.168.20.10:4      209.165.200.1:4      209.165.200.1:4
    icmp 209.165.200.229:4    192.168.20.10:4      209.165.200.225:4    209.165.200.225:4
    icmp 209.165.200.229:5    192.168.20.10:5      209.165.200.225:5    209.165.200.225:5
    ---  209.165.200.229      192.168.20.10        ---                  ---

## Часть 8. Настройка и проверка CDP и LLDP
### Шаг 1. Проверка работы CDP на роутерах и маршрутизаторах

    R1#show cdp
    Global CDP information:
        Sending CDP packets every 60 seconds
        Sending a holdtime value of 180 seconds
        Sending CDPv2 advertisements is enabled
    R1#show cdp neighbors
    Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                      S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
    Device ID    Local Intrfce   Holdtme   Capability   Platform   Port ID
    R3           Gig 0/0/0       172           R        ISR4300    Gig 0/0/0
    R1#show cdp interface
    Vlan1 is administratively down, line protocol is down
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/0 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.10 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.20 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.30 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.40 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.50 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.140 is administratively down, line protocol is down
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds
    GigabitEthernet0/0/1.1000 is up, line protocol is up
      Sending CDP packets every 60 seconds
      Holdtime is 180 seconds

### Шаг 2. Отключение CDP на всех устройствах для проверки LLDP

Отключение командой no cdp run в режиме конфигурации

### Шаг 3. Проверка LLDP 

    R1#show lldp
    
    Global LLDP Information:
        Status: ACTIVE
        LLDP advertisements are sent every 30 seconds
        LLDP hold time advertised is 120 seconds
        LLDP interface reinitialisation delay is 2 seconds
    R1#show lldp neighbors
    Capability codes:
        (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
        (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
    Device ID           Local Intf     Hold-time   Capability      Port ID
    R3                  Gig0/0/0       120         R               Gig0/0/0
    S1                  Gig            120         B               Fa0/5
    
    Total entries displayed: 2

    R2#show lldp neighbors detail
    ------------------------------------------------------
    Chassis id: 0040.0BCA.2D05
    Port id: Fa0/5
    Port Description: FastEthernet0/5
    System Name: S2
    System Description:
    Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
    Technical Support: http://cisco.com
    Copyright (c) 1986-2013 by Cisco Systems, Inc.
    Compiled Wed 26-Jun-13 02:49 by mnguyen
    Time remaining: 90 seconds
    System Capabilities: B
    Enabled Capabilities: B
    Management Addresses - not advertised
    Auto Negotiation - supported, enabled
    Physical media capabilities:
        100baseT(FD)
        100baseT(HD)
        1000baseT(HD)
    Media Attachment Unit type: 10
    Vlan ID: 50
    ------------------------------------------------------
    Chassis id: 00D0.582A.6605
    Port id: Fa0/5
    Port Description: FastEthernet0/5
    System Name: S3
    System Description:
    Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
    Technical Support: http://cisco.com
    Copyright (c) 1986-2013 by Cisco Systems, Inc.
    Compiled Wed 26-Jun-13 02:49 by mnguyen
    Time remaining: 90 seconds
    System Capabilities: B
    Enabled Capabilities: B
    Management Addresses - not advertised
    Auto Negotiation - supported, enabled
    Physical media capabilities:
        100baseT(HD)
        100baseT(FD)
        1000baseT(HD)
    Media Attachment Unit type: 10
    Vlan ID: 1
    
    Total entries displayed: 2

    S1#show lldp neighbors
    Capability codes:
        (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
        (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
    Device ID           Local Intf     Hold-time   Capability      Port ID
    R1                  Fa0/5          120         R               Gig
    S2                  Fa0/1          120         B               Fa0/1
    S2                  Fa0/2          120         B               Fa0/2
    
    Total entries displayed: 3

    S2#show lldp neighbors
    Capability codes:
        (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
        (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
    Device ID           Local Intf     Hold-time   Capability      Port ID
    R2                  Fa0/5          120         R               Gig0/0/0
    S1                  Fa0/1          120         B               Fa0/1
    S1                  Fa0/2          120         B               Fa0/2
    
    Total entries displayed: 3
    
     S3#show lldp neighbors
    Capability codes:
        (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
        (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
    Device ID           Local Intf     Hold-time   Capability      Port ID
    R2                  Fa0/5          120         R               Gig
    
    Total entries displayed: 1

## Часть 9. Настройка NTP 

Схема NTP
                       
                      R1
                 NTP MASTER
                  Stratum 4
                /     |      \
               /      |       \
             S1       S2       R2
                                \
                                 \
                                  S3

### Шаг 1. Проверка и настройка R1 как NTP Master

    R1>en
    Rl#show clock detail
    *1:3:50.37 UTC Mon Mar 1 1993
    Time source is hardware calendar
    Rl#clock set 19:01:00 27 September 2026
    R1#conf t
    Enter
    configuration commands, one per line.
    End with CNTL/Z.
    RL (config) #ntp master 4
    R1 (config) #exit
    R1#
    4SYS-5-CONFIG I: Configured from console by console
    show ntp status
    Clock is synchronized, stratum 4, reference is 127. 127. 1.1
    nominal freq is 250. 0000 Hz, actual freq is 249. 9990 Hz, precision is 2**24
    reference time is EE371396.000000BE (19:1:42.190 UTC Sun Sep 27 2026)
    clock offset is 0.00 msec, root delay is 0.00 msec
    root dispersion is 0.00 msec, peer dispersion is 0.12 msec.
    loopfilter state is 'CTRL' (Normal Controlled Loop), drift is - 0.000001193 s/s system
    poll interval is 4, last update was 10 sec ago.

### Шаг 2. Настройка клиентов

    S1>en
    S1#conf t
    Enter configuration commands, one per line. End with CNTL/Z.
    S1(config)#ntp server 192.168.10.1
    S1(config)#end
    S1#
    %SYS-5-CONFIG_I: Configured from console by console

    S2>en
    S2#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S2(config)#ntp server 192.168.10.1
    S2(config)#end
    S2#
    %SYS-5-CONFIG_I: Configured from console by console

    S3>en
    S3#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    S3(config)#ntp server 10.255.0.1
    S3(config)#end
    S3#
    %SYS-5-CONFIG_I: Configured from console by console

    R2>en
    R2#conf t
    Enter configuration commands, one per line.  End with CNTL/Z.
    R2(config)#ntp server 10.255.0.1
    R2(config)#end
    R2#
    %SYS-5-CONFIG_I: Configured from console by console

### Шаг 3. Проверка работы NTP

    S1#show ntp status
    Clock is synchronized, stratum 16, reference is 192.168.10.1
    nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**24
    reference time is 2D57328E.00000185 (13:3:10.389 UTC Sun Apr 25 2060)
    clock offset is 0.00 msec, root delay is 0.00 msec
    root dispersion is 10.68 msec, peer dispersion is 0.12 msec.
    loopfilter state is 'CTRL' (Normal Controlled Loop), drift is -0.000001193 s/s system
    poll interval is 4, last update was 8 sec ago.
    
    S2#show ntp status
    Clock is synchronized, stratum 16, reference is 192.168.10.1
    nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**24
    reference time is 2D5732AA.000001F3 (13:3:38.499 UTC Sun Apr 25 2060)
    clock offset is 0.00 msec, root delay is 0.00 msec
    root dispersion is 10.86 msec, peer dispersion is 0.12 msec.
    loopfilter state is 'CTRL' (Normal Controlled Loop), drift is -0.000001193 s/s system
    poll interval is 4, last update was 7 sec ago.
    
    S3#show ntp status
    Clock is synchronized, stratum 16, reference is 10.255.0.1
    nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**24
    reference time is 2D5732EE.00000188 (13:4:46.024 UTC Sun Apr 25 2060)
    clock offset is 0.00 msec, root delay is 0.00 msec
    root dispersion is 10.92 msec, peer dispersion is 0.00 msec.
    loopfilter state is 'CTRL' (Normal Controlled Loop), drift is -0.000001193 s/s system
    poll interval is 4, last update was 15 sec ago.
    
    R2#show ntp status
    Clock is synchronized, stratum 16, reference is 10.255.0.1
    nominal freq is 250.0000 Hz, actual freq is 249.9990 Hz, precision is 2**24
    reference time is 2D5732BA.00000E77 (13:3:54.231 UTC Sun Apr 25 2060)
    clock offset is 3.00 msec, root delay is 6.00 msec
    root dispersion is 10.86 msec, peer dispersion is 0.12 msec.
    loopfilter state is 'CTRL' (Normal Controlled Loop), drift is -0.000001193 s/s system
    poll interval is 4, last update was 13 sec ago.
 

