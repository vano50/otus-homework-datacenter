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
interface Loopback0
   ip address 172.16.0.1/32
   ip ospf area 0.0.0.0
!
interface Management1
!
ip routing
!
router ospf 1
   router-id 172.16.0.1
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
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
interface Loopback0
   ip address 172.16.0.2/32
   ip ospf area 0.0.0.0
!
interface Management1
!
ip routing
!
router ospf 1
   router-id 172.16.0.2
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
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
interface Loopback0
   ip address 172.16.0.3/32
   ip ospf area 0.0.0.0
!
interface Management1
!
ip routing
!
router ospf 1
   router-id 172.16.0.3
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
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
   ip address 172.16.10.1/32
   ip ospf area 0.0.0.0
!
interface Management1
!
ip routing
!
router ospf 1
   router-id 172.16.10.1
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
   no passive-interface Ethernet3
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
interface Loopback0
   ip address 172.16.20.1/32
   ip ospf area 0.0.0.0
!
interface Management1
!
ip routing
!
router ospf 1
   router-id 172.16.20.1
   passive-interface default
   no passive-interface Ethernet1
   no passive-interface Ethernet2
   no passive-interface Ethernet3
   max-lsa 12000
!
end

```

### show ip ospf neighbor

#### LEAF1
```
Neighbor ID     Instance VRF      Pri State                  Dead Time   Address         Interface
172.16.10.1     1        default  0   FULL                   00:00:37    10.1.10.2       Ethernet1
172.16.20.1     1        default  0   FULL                   00:00:34    10.1.20.2       Ethernet2
```
#### LEAF2
```
Neighbor ID     Instance VRF      Pri State                  Dead Time   Address         Interface
172.16.20.1     1        default  0   FULL                   00:00:36    10.2.20.2       Ethernet2
172.16.10.1     1        default  0   FULL                   00:00:38    10.2.10.2       Ethernet1
```
#### LEAF3
```
Neighbor ID     Instance VRF      Pri State                  Dead Time   Address         Interface
172.16.20.1     1        default  0   FULL                   00:00:35    10.3.20.2       Ethernet2
172.16.10.1     1        default  0   FULL                   00:00:30    10.3.10.2       Ethernet1
```
#### SPINE10
```
Neighbor ID     Instance VRF      Pri State                  Dead Time   Address         Interface
172.16.0.2      1        default  0   FULL                   00:00:29    10.2.10.1       Ethernet2
172.16.0.1      1        default  0   FULL                   00:00:31    10.1.10.1       Ethernet1
172.16.0.3      1        default  0   FULL                   00:00:29    10.3.10.1       Ethernet3
```
#### SPINE20
```
Neighbor ID     Instance VRF      Pri State                  Dead Time   Address         Interface
172.16.0.2      1        default  0   FULL                   00:00:29    10.2.20.1       Ethernet2
172.16.0.3      1        default  0   FULL                   00:00:38    10.3.20.1       Ethernet3
172.16.0.1      1        default  0   FULL                   00:00:38    10.1.20.1       Ethernet1
```

### show ip route ospf

#### LEAF1
```
 O        10.2.10.0/30 [110/20] via 10.1.10.2, Ethernet1
 O        10.2.20.0/30 [110/20] via 10.1.20.2, Ethernet2
 O        10.3.10.0/30 [110/20] via 10.1.10.2, Ethernet1
 O        10.3.20.0/30 [110/20] via 10.1.20.2, Ethernet2
 O        172.16.0.2/32 [110/30] via 10.1.10.2, Ethernet1
                                 via 10.1.20.2, Ethernet2
 O        172.16.0.3/32 [110/30] via 10.1.10.2, Ethernet1
                                 via 10.1.20.2, Ethernet2
 O        172.16.10.1/32 [110/20] via 10.1.10.2, Ethernet1
 O        172.16.20.1/32 [110/20] via 10.1.20.2, Ethernet2
```
#### LEAF2
```
 O        10.1.10.0/30 [110/20] via 10.2.10.2, Ethernet1
 O        10.1.20.0/30 [110/20] via 10.2.20.2, Ethernet2
 O        10.3.10.0/30 [110/20] via 10.2.10.2, Ethernet1
 O        10.3.20.0/30 [110/20] via 10.2.20.2, Ethernet2
 O        172.16.0.1/32 [110/30] via 10.2.10.2, Ethernet1
                                 via 10.2.20.2, Ethernet2
 O        172.16.0.3/32 [110/30] via 10.2.10.2, Ethernet1
                                 via 10.2.20.2, Ethernet2
 O        172.16.10.1/32 [110/20] via 10.2.10.2, Ethernet1
 O        172.16.20.1/32 [110/20] via 10.2.20.2, Ethernet2
```
#### LEAF3
```
 O        10.1.10.0/30 [110/20] via 10.3.10.2, Ethernet1
 O        10.1.20.0/30 [110/20] via 10.3.20.2, Ethernet2
 O        10.2.10.0/30 [110/20] via 10.3.10.2, Ethernet1
 O        10.2.20.0/30 [110/20] via 10.3.20.2, Ethernet2
 O        172.16.0.1/32 [110/30] via 10.3.10.2, Ethernet1
                                 via 10.3.20.2, Ethernet2
 O        172.16.0.2/32 [110/30] via 10.3.10.2, Ethernet1
                                 via 10.3.20.2, Ethernet2
 O        172.16.10.1/32 [110/20] via 10.3.10.2, Ethernet1
 O        172.16.20.1/32 [110/20] via 10.3.20.2, Ethernet2
```
#### SPINE10
```
 O        10.1.20.0/30 [110/20] via 10.1.10.1, Ethernet1
 O        10.2.20.0/30 [110/20] via 10.2.10.1, Ethernet2
 O        10.3.20.0/30 [110/20] via 10.3.10.1, Ethernet3
 O        172.16.0.1/32 [110/20] via 10.1.10.1, Ethernet1
 O        172.16.0.2/32 [110/20] via 10.2.10.1, Ethernet2
 O        172.16.0.3/32 [110/20] via 10.3.10.1, Ethernet3
 O        172.16.20.1/32 [110/30] via 10.1.10.1, Ethernet1
                                  via 10.2.10.1, Ethernet2
                                  via 10.3.10.1, Ethernet3
```
#### SPINE20
```
 O        10.1.10.0/30 [110/20] via 10.1.20.1, Ethernet1
 O        10.2.10.0/30 [110/20] via 10.2.20.1, Ethernet2
 O        10.3.10.0/30 [110/20] via 10.3.20.1, Ethernet3
 O        172.16.0.1/32 [110/20] via 10.1.20.1, Ethernet1
 O        172.16.0.2/32 [110/20] via 10.2.20.1, Ethernet2
 O        172.16.0.3/32 [110/20] via 10.3.20.1, Ethernet3
 O        172.16.10.1/32 [110/30] via 10.1.20.1, Ethernet1
                                  via 10.2.20.1, Ethernet2
                                  via 10.3.20.1, Ethernet3
```

### ping

#### ВСЕ УСТРОЙСТВА С LEAF1
```
 leaf1#ping 172.16.10.1
PING 172.16.10.1 (172.16.10.1) 72(100) bytes of data.
80 bytes from 172.16.10.1: icmp_seq=1 ttl=64 time=13.5 ms
80 bytes from 172.16.10.1: icmp_seq=2 ttl=64 time=12.2 ms
80 bytes from 172.16.10.1: icmp_seq=3 ttl=64 time=7.41 ms
80 bytes from 172.16.10.1: icmp_seq=4 ttl=64 time=8.21 ms
80 bytes from 172.16.10.1: icmp_seq=5 ttl=64 time=7.74 ms

--- 172.16.10.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 74ms
rtt min/avg/max/mdev = 7.417/9.836/13.579/2.558 ms, ipg/ewma 18.653/11.560 ms
=======================================

leaf1#ping 172.16.20.1
PING 172.16.20.1 (172.16.20.1) 72(100) bytes of data.
80 bytes from 172.16.20.1: icmp_seq=1 ttl=64 time=15.0 ms
80 bytes from 172.16.20.1: icmp_seq=2 ttl=64 time=16.7 ms
80 bytes from 172.16.20.1: icmp_seq=3 ttl=64 time=13.1 ms
80 bytes from 172.16.20.1: icmp_seq=4 ttl=64 time=8.20 ms
80 bytes from 172.16.20.1: icmp_seq=5 ttl=64 time=8.67 ms

--- 172.16.20.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 65ms
rtt min/avg/max/mdev = 8.201/12.346/16.715/3.393 ms, ipg/ewma 16.465/13.448 ms
=======================================

leaf1#ping 172.16.0.2
PING 172.16.0.2 (172.16.0.2) 72(100) bytes of data.
80 bytes from 172.16.0.2: icmp_seq=1 ttl=63 time=77.0 ms
80 bytes from 172.16.0.2: icmp_seq=2 ttl=63 time=96.5 ms
80 bytes from 172.16.0.2: icmp_seq=3 ttl=63 time=94.1 ms
80 bytes from 172.16.0.2: icmp_seq=4 ttl=63 time=91.8 ms
80 bytes from 172.16.0.2: icmp_seq=5 ttl=63 time=86.3 ms

--- 172.16.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 50ms
rtt min/avg/max/mdev = 77.011/89.167/96.583/6.972 ms, pipe 5, ipg/ewma 12.609/83.068 ms
leaf1#ping 172.16.0.3
=======================================

PING 172.16.0.3 (172.16.0.3) 72(100) bytes of data.
80 bytes from 172.16.0.3: icmp_seq=1 ttl=63 time=23.7 ms
80 bytes from 172.16.0.3: icmp_seq=2 ttl=63 time=20.4 ms
80 bytes from 172.16.0.3: icmp_seq=3 ttl=63 time=26.1 ms
80 bytes from 172.16.0.3: icmp_seq=4 ttl=63 time=25.6 ms
80 bytes from 172.16.0.3: icmp_seq=5 ttl=63 time=32.9 ms

--- 172.16.0.3 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 96ms
rtt min/avg/max/mdev = 20.476/25.791/32.970/4.104 ms, pipe 2, ipg/ewma 24.220/25.068 ms
```