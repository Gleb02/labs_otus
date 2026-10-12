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
    - [Шаг 4. Проверка переключения на резервный канал](#шаг-4-проверка-переключения-на-резервный-канал)
    - [Шаг 5. Настройка PortFast на портах ПК](#шаг-5-настройка-portfast-на-портах-пк)
    - [Шаг 6. Включение BPDU Guard на портах ПК](#шаг-6-включение-bpdu-guard-на-портах-пк)
    - [Шаг 7. Проверка итоговых конфигураций](#шаг-7-проверка-итоговых-конфигураций)
  - [Часть 3. Настройка IPv4 и Router-on-a-Stick](#часть-3-настройка-ipv4-и-router-on-a-stick)
    - [Шаг 1. Настройка интерфейсов на R1](#шаг-1-настройка-интерфейсов-на-r1)
    - [Шаг 2. Настройка интерфейсов на R2](#шаг-2-настройка-интерфейсов-на-r2)
    - [Шаг 3. Настройка интерфейсов на R3](#шаг-3-настройка-интерфейсов-на-r3)
    - [Шаг 4. Настрйока Management VLAN на коммутаторах](#шаг-4-настрйока-management-vlan-на-коммутаторах)
    - [Шаг 5. Проверки сетевой связанности маршрутизаторов и коммутаторов](#шаг-5-проверки-сетевой-связанности-маршрутизаторов-и-коммутаторов)
  - [Часть 4. Настройка DHCPv4](#часть-4-настройка-dhcpv4)
    - [Шаг 1. Исключение служебных адресов и создание пулов на R1](#шаг-1-исключение-служебных-адресов-и-создание-пулов-на-r1)
    - [Шаг 2. Исключение служебных адресов и создание пулов на R2](#шаг-2-исключение-служебных-адресов-и-создание-пулов-на-r2)
    - [Шаг 3. Настройка ПК](#шаг-3-настройка-пк)
    - [Шаг 4. Проверка адресов ПК](#шаг-4-проверка-адресов-пк)
    - [Шаг 5. Проверка DHCP на R1 и R2](#шаг-5-проверка-dhcp-на-r1-и-r2)
    - [Шаг 6. Ping шлюзов с ПК](#шаг-6-ping-шлюзов-с-пк)
    - [Шаг 7. Ping между ПК](#шаг-7-ping-между-пк)
  - [Часть 5. Настройка IPv6, SLAAC и DHCPv6](#часть-5-настройка-ipv6-slaac-и-dhcpv6)
    - [Шаг 1. IPv6-маршрутизация на R1 и R2](#шаг-1-ipv6-маршрутизация-на-r1-и-r2)
    - [Шаг 2. Настройка адресов IPv6, VLAN и DHCPv6 на R1](#шаг-2-настройка-адресов-ipv6-vlan-и-dhcpv6-на-r1)
    - [Шаг 3. Настройка адресов IPv6, VLAN и DHCPv6 на R2](#шаг-3-настройка-адресов-ipv6-vlan-и-dhcpv6-на-r2)
    - [Шаг 4. Ping R1 \<-\> R2 по IPv6](#шаг-4-ping-r1---r2-по-ipv6)
    - [Шаг 5. Настройка SLAAC на ПК](#шаг-5-настройка-slaac-на-пк)
    - [Шаг 6. Настройка DHCPv6 на ПК](#шаг-6-настройка-dhcpv6-на-пк)
    - [Шаг 7. Проверка DHCPv6 на маршрутизаторах](#шаг-7-проверка-dhcpv6-на-маршрутизаторах)
    - [Шаг 8. Проверка связи ПК со шлюзом](#шаг-8-проверка-связи-пк-со-шлюзом)
    - [Шаг 9. Проверка связи между ПК из разных VLAN](#шаг-9-проверка-связи-между-пк-из-разных-vlan)
    - [Шаг 10.  Проверка таблиц IPv6-маршрутизации](#шаг-10--проверка-таблиц-ipv6-маршрутизации)
  - [Часть 6. Статическая и динамическая маршрутизация](#часть-6-статическая-и-динамическая-маршрутизация)
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
  - [Часть 7. ACL](#часть-7-acl)
    - [Шаг 1. Определение политик безопасности](#шаг-1-определение-политик-безопасности)
    - [Шаг 2. ACL для HQ Guest](#шаг-2-acl-для-hq-guest)
    - [Шаг 3. ACL для HQ Users](#шаг-3-acl-для-hq-users)
    - [Шаг 4. ACL для Branch Guest](#шаг-4-acl-для-branch-guest)
    - [Шаг 5. ACL для Branch Users](#шаг-5-acl-для-branch-users)
    - [Шаг 6. Проверка HQ Guest](#шаг-6-проверка-hq-guest)
    - [Шаг 7. Проверка Branch Guest](#шаг-7-проверка-branch-guest)
    - [Шаг 8. Проверка Users](#шаг-8-проверка-users)
  - [Часть 8. Настройка NAT/PAT](#часть-8-настройка-natpat)
    - [Шаг 1. Внешний NAT-интерфейс](#шаг-1-внешний-nat-интерфейс)
    - [Шаг 2. Внутренние NAT-интерфейсы](#шаг-2-внутренние-nat-интерфейсы)
    - [Шаг 3. ACL для адресов NAT](#шаг-3-acl-для-адресов-nat)
    - [Шаг 4. PAT через R1](#шаг-4-pat-через-r1)
    - [Шаг 5. Проверка PAT](#шаг-5-проверка-pat)
    - [Шаг 6. Static NAT для PC-A](#шаг-6-static-nat-для-pc-a)
  - [Часть 9. Настройка и проверка CDP и LLDP](#часть-9-настройка-и-проверка-cdp-и-lldp)
    - [Шаг 1. Проверка работы CDP на роутерах и маршрутизаторах](#шаг-1-проверка-работы-cdp-на-роутерах-и-маршрутизаторах)
    - [Шаг 2. Отключение CDP на всех устройствах для проверки LLDP](#шаг-2-отключение-cdp-на-всех-устройствах-для-проверки-lldp)
    - [Шаг 3. Проверка LLDP](#шаг-3-проверка-lldp)
  - [Часть 10. Настройка NTP](#часть-10-настройка-ntp)
    - [Шаг 1. Проверка и настройка R1 как NTP Master](#шаг-1-проверка-и-настройка-r1-как-ntp-master)
    - [Шаг 2. Настройка клиентов](#шаг-2-настройка-клиентов)
    - [Шаг 3. Проверка работы NTP](#шаг-3-проверка-работы-ntp)
  - [Часть 11. Защищённое удалённое управление (SSH)](#часть-11-защищённое-удалённое-управление-ssh)
    - [Шаг 1. Настройка SSH на R1/2 и S1/2/3](#шаг-1-настройка-ssh-на-r12-и-s123)
    - [Шаг 2. Ограничение SSH административной сетью](#шаг-2-ограничение-ssh-административной-сетью)
    - [Шаг 3. Проверка SSH и ограничений](#шаг-3-проверка-ssh-и-ограничений)
## Топология 

![alt text](topology.png)

## Таблица адресации



## Таблица VLAN

![alt text](vlan.png)

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
### Шаг 2. Настройка режима STP.
### Шаг 3. Проверка Root Bridge и резервирования
### Шаг 4. Проверка переключения на резервный канал
### Шаг 5. Настройка PortFast на портах ПК
### Шаг 6. Включение BPDU Guard на портах ПК
### Шаг 7. Проверка итоговых конфигураций
## Часть 3. Настройка IPv4 и Router-on-a-Stick
### Шаг 1. Настройка интерфейсов на R1
### Шаг 2. Настройка интерфейсов на R2
### Шаг 3. Настройка интерфейсов на R3
### Шаг 4. Настрйока Management VLAN на коммутаторах
### Шаг 5. Проверки сетевой связанности маршрутизаторов и коммутаторов
## Часть 4. Настройка DHCPv4
### Шаг 1. Исключение служебных адресов и создание пулов на R1
### Шаг 2. Исключение служебных адресов и создание пулов на R2
### Шаг 3. Настройка ПК
DHCP включен на PC-B — PC-G
### Шаг 4. Проверка адресов ПК
### Шаг 5. Проверка DHCP на R1 и R2
### Шаг 6. Ping шлюзов с ПК
### Шаг 7. Ping между ПК
## Часть 5. Настройка IPv6, SLAAC и DHCPv6
### Шаг 1. IPv6-маршрутизация на R1 и R2
### Шаг 2. Настройка адресов IPv6, VLAN и DHCPv6 на R1
### Шаг 3. Настройка адресов IPv6, VLAN и DHCPv6 на R2
### Шаг 4. Ping R1 <-> R2 по IPv6
### Шаг 5. Настройка SLAAC на ПК
### Шаг 6. Настройка DHCPv6 на ПК
### Шаг 7. Проверка DHCPv6 на маршрутизаторах
### Шаг 8. Проверка связи ПК со шлюзом
### Шаг 9. Проверка связи между ПК из разных VLAN
### Шаг 10.  Проверка таблиц IPv6-маршрутизации
## Часть 6. Статическая и динамическая маршрутизация
### Шаг 1. Статический маршрут по умолчанию на R1
### Шаг 2. Настройка OSPF на R1
###  Шаг 3. Отключение OSPF Hello-пакеты в пользовательских VLAN
###  Шаг 4. Маршрут по умолчанию через OSPF
### Шаг 5. Настройте OSPF на R2
### Шаг 6. Проверка OSPF-маршрутов на маршрутизаторах
### Шаг 7. Проверка маршрутизации на ПК
### Шаг 8. Настройка IPv6-маршрутизации на R1/R2
### Шаг 9. Проверка IPv6-маршрутизации на ПК
### Шаг 10. Итоговая проверка OSPF
## Часть 7. ACL
### Шаг 1. Определение политик безопасности
### Шаг 2. ACL для HQ Guest
### Шаг 3. ACL для HQ Users
### Шаг 4. ACL для Branch Guest
### Шаг 5. ACL для Branch Users
### Шаг 6. Проверка HQ Guest
### Шаг 7. Проверка Branch Guest
### Шаг 8. Проверка Users
## Часть 8. Настройка NAT/PAT
### Шаг 1. Внешний NAT-интерфейс
### Шаг 2. Внутренние NAT-интерфейсы 
### Шаг 3. ACL для адресов NAT
### Шаг 4. PAT через R1
### Шаг 5. Проверка PAT
### Шаг 6. Static NAT для PC-A
## Часть 9. Настройка и проверка CDP и LLDP
### Шаг 1. Проверка работы CDP на роутерах и маршрутизаторах
### Шаг 2. Отключение CDP на всех устройствах для проверки LLDP
### Шаг 3. Проверка LLDP 
## Часть 10. Настройка NTP 
### Шаг 1. Проверка и настройка R1 как NTP Master
### Шаг 2. Настройка клиентов
### Шаг 3. Проверка работы NTP
## Часть 11. Защищённое удалённое управление (SSH)
### Шаг 1. Настройка SSH на R1/2 и S1/2/3
### Шаг 2. Ограничение SSH административной сетью  
### Шаг 3. Проверка SSH и ограничений
