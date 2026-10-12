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
