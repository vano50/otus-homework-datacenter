### Вопрос:
В лекции, на стенде с OSPF ещё были сделаны интерфейсы loopback на роутерах.

Я так и не понял, для чего они нужны в фабрике и обязательно ли их делать в этом домашнем задании?

### Соединительные сети для OSPF:
10.1.10.0/30

10.2.10.0/30

10.3.10.0/30

10.1.20.0/30

10.2.20.0/30

10.3.20.0/30


![img.png](img.png)

### КОНФИГУРАЦИИ ОБОРУДОВАНИЯ:

#### LEAF1:
```
leaf1#show runn
! Command: show running-config
! device: leaf1 (vEOS-lab, EOS-4.29.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
hostname leaf1
!
spanning-tree mode mstp
!
interface Ethernet1
   no switchport
   ip address 10.1.10.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet2
   no switchport
   ip address 10.1.20.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet3
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Management1
!
ip routing
!
router ospf 1
   max-lsa 12000
!
end

```

#### LEAF2:
```
leaf2#show runn
! Command: show running-config
! device: leaf2 (vEOS-lab, EOS-4.29.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
hostname leaf2
!
spanning-tree mode mstp
!
interface Ethernet1
   no switchport
   ip address 10.2.10.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet2
   no switchport
   ip address 10.2.20.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet3
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Management1
!
ip routing
!
router ospf 1
   max-lsa 12000
!
end

```

#### LEAF3:
```
leaf3#show runn
! Command: show running-config
! device: leaf3 (vEOS-lab, EOS-4.29.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
hostname leaf3
!
spanning-tree mode mstp
!
interface Ethernet1
   no switchport
   ip address 10.3.10.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet2
   no switchport
   ip address 10.3.20.1/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet3
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Management1
!
ip routing
!
router ospf 1
   max-lsa 12000
!
end

```

#### SPINE10:
```
spine10#show runn
! Command: show running-config
! device: spine10 (vEOS-lab, EOS-4.29.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
hostname spine10
!
spanning-tree mode mstp
!
interface Ethernet1
   no switchport
   ip address 10.1.10.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet2
   no switchport
   ip address 10.2.10.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet3
   no switchport
   ip address 10.3.10.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Loopback0
   ip address 2.2.2.2/32
!
interface Management1
!
ip routing
!
router ospf 1
   max-lsa 12000
!
end

```

#### SPINE20:
```
spine20#show runn
! Command: show running-config
! device: spine20 (vEOS-lab, EOS-4.29.2F)
!
! boot system flash:/vEOS-lab.swi
!
no aaa root
!
transceiver qsfp default-mode 4x10G
!
service routing protocols model ribd
!
hostname spine20
!
spanning-tree mode mstp
!
interface Ethernet1
   no switchport
   ip address 10.1.20.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet2
   no switchport
   ip address 10.2.20.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet3
   no switchport
   ip address 10.3.20.2/30
   ip ospf network point-to-point
   ip ospf area 0.0.0.0
!
interface Ethernet4
!
interface Ethernet5
!
interface Ethernet6
!
interface Ethernet7
!
interface Ethernet8
!
interface Management1
!
ip routing
!
router ospf 1
   max-lsa 12000
!
end

```

#### Пинги со SPINE20 до LEAF1 Eth1 (на всякий случай):
```
spine20#ping 10.1.10.1
PING 10.1.10.1 (10.1.10.1) 72(100) bytes of data.
80 bytes from 10.1.10.1: icmp_seq=1 ttl=64 time=17.6 ms
80 bytes from 10.1.10.1: icmp_seq=2 ttl=64 time=14.4 ms
80 bytes from 10.1.10.1: icmp_seq=3 ttl=64 time=13.2 ms
80 bytes from 10.1.10.1: icmp_seq=4 ttl=64 time=12.9 ms
80 bytes from 10.1.10.1: icmp_seq=5 ttl=64 time=9.90 ms
```