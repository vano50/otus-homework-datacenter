### Соединительные сети для eBGP:
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
!
interface Ethernet2
   no switchport
   ip address 10.1.20.1/30
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
!
interface Management1
!
ip routing
!
router bgp 65101
   router-id 172.16.0.1
   maximum-paths 4 ecmp 4
   neighbor 10.1.10.2 remote-as 65100
   neighbor 10.1.20.2 remote-as 65100
   !
   address-family ipv4
      neighbor 10.1.10.2 activate
      neighbor 10.1.20.2 activate
      network 10.1.10.0/30
      network 10.1.20.0/30
      network 172.16.0.1/32
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
!
interface Ethernet2
   no switchport
   ip address 10.2.20.1/30
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
!
interface Management1
!
ip routing
!
router bgp 65102
   router-id 172.16.0.2
   maximum-paths 4 ecmp 4
   neighbor 10.2.10.2 remote-as 65100
   neighbor 10.2.20.2 remote-as 65100
   !
   address-family ipv4
      neighbor 10.2.10.2 activate
      neighbor 10.2.20.2 activate
      network 10.2.10.0/30
      network 10.2.20.0/30
      network 172.16.0.2/32
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
!
interface Ethernet2
   no switchport
   ip address 10.3.20.1/30
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
!
interface Management1
!
ip routing
!
router bgp 65103
   router-id 172.16.0.3
   maximum-paths 4 ecmp 4
   neighbor 10.3.10.2 remote-as 65100
   neighbor 10.3.20.2 remote-as 65100
   !
   address-family ipv4
      neighbor 10.3.10.2 activate
      neighbor 10.3.20.2 activate
      network 10.3.10.0/30
      network 10.3.20.0/30
      network 172.16.0.3/32
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
!
interface Ethernet2
   no switchport
   ip address 10.2.10.2/30
!
interface Ethernet3
   no switchport
   ip address 10.3.10.2/30
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
!
interface Management1
!
ip routing
!
router bgp 65100
   router-id 172.16.10.1
   maximum-paths 4 ecmp 4
   neighbor 10.1.10.1 remote-as 65101
   neighbor 10.2.10.1 remote-as 65102
   neighbor 10.3.10.1 remote-as 65103
   !
   address-family ipv4
      neighbor 10.1.10.1 activate
      neighbor 10.2.10.1 activate
      neighbor 10.3.10.1 activate
      network 10.1.10.0/30
      network 10.2.10.0/30
      network 10.3.10.0/30
      network 172.16.10.1/32
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
!
interface Ethernet2
   no switchport
   ip address 10.2.20.2/30
!
interface Ethernet3
   no switchport
   ip address 10.3.20.2/30
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
!
interface Management1
!
ip routing
!
router bgp 65100
   router-id 172.16.20.1
   maximum-paths 4 ecmp 4
   neighbor 10.1.20.1 remote-as 65101
   neighbor 10.2.20.1 remote-as 65102
   neighbor 10.3.20.1 remote-as 65103
   !
   address-family ipv4
      neighbor 10.1.20.1 activate
      neighbor 10.2.20.1 activate
      neighbor 10.3.20.1 activate
      network 10.1.20.0/30
      network 10.2.20.0/30
      network 10.3.20.0/30
      network 172.16.20.1/32
!
end

```

### show ip route bgp

#### LEAF1
```
 B E      10.2.10.0/30 [200/0] via 10.1.10.2, Ethernet1
 B E      10.2.20.0/30 [200/0] via 10.1.20.2, Ethernet2
 B E      10.3.10.0/30 [200/0] via 10.1.10.2, Ethernet1
 B E      10.3.20.0/30 [200/0] via 10.1.20.2, Ethernet2
 B E      172.16.0.2/32 [200/0] via 10.1.10.2, Ethernet1
                                via 10.1.20.2, Ethernet2
 B E      172.16.0.3/32 [200/0] via 10.1.10.2, Ethernet1
                                via 10.1.20.2, Ethernet2
 B E      172.16.10.1/32 [200/0] via 10.1.10.2, Ethernet1
 B E      172.16.20.1/32 [200/0] via 10.1.20.2, Ethernet2
```
#### LEAF2
```
 B E      10.1.10.0/30 [200/0] via 10.2.10.2, Ethernet1
 B E      10.1.20.0/30 [200/0] via 10.2.20.2, Ethernet2
 B E      10.3.10.0/30 [200/0] via 10.2.10.2, Ethernet1
 B E      10.3.20.0/30 [200/0] via 10.2.20.2, Ethernet2
 B E      172.16.0.1/32 [200/0] via 10.2.10.2, Ethernet1
                                via 10.2.20.2, Ethernet2
 B E      172.16.0.3/32 [200/0] via 10.2.10.2, Ethernet1
                                via 10.2.20.2, Ethernet2
 B E      172.16.10.1/32 [200/0] via 10.2.10.2, Ethernet1
 B E      172.16.20.1/32 [200/0] via 10.2.20.2, Ethernet2
```
#### LEAF3
```
 B E      10.1.10.0/30 [200/0] via 10.3.10.2, Ethernet1
 B E      10.1.20.0/30 [200/0] via 10.3.20.2, Ethernet2
 B E      10.2.10.0/30 [200/0] via 10.3.10.2, Ethernet1
 B E      10.2.20.0/30 [200/0] via 10.3.20.2, Ethernet2
 B E      172.16.0.1/32 [200/0] via 10.3.10.2, Ethernet1
                                via 10.3.20.2, Ethernet2
 B E      172.16.0.2/32 [200/0] via 10.3.10.2, Ethernet1
                                via 10.3.20.2, Ethernet2
 B E      172.16.10.1/32 [200/0] via 10.3.10.2, Ethernet1
 B E      172.16.20.1/32 [200/0] via 10.3.20.2, Ethernet2
```
#### SPINE10
```
 B E      10.1.20.0/30 [200/0] via 10.1.10.1, Ethernet1
 B E      10.2.20.0/30 [200/0] via 10.2.10.1, Ethernet2
 B E      10.3.20.0/30 [200/0] via 10.3.10.1, Ethernet3
 B E      172.16.0.1/32 [200/0] via 10.1.10.1, Ethernet1
 B E      172.16.0.2/32 [200/0] via 10.2.10.1, Ethernet2
 B E      172.16.0.3/32 [200/0] via 10.3.10.1, Ethernet3
```
#### SPINE20
```
 B E      10.1.10.0/30 [200/0] via 10.1.20.1, Ethernet1
 B E      10.2.10.0/30 [200/0] via 10.2.20.1, Ethernet2
 B E      10.3.10.0/30 [200/0] via 10.3.20.1, Ethernet3
 B E      172.16.0.1/32 [200/0] via 10.1.20.1, Ethernet1
 B E      172.16.0.2/32 [200/0] via 10.2.20.1, Ethernet2
 B E      172.16.0.3/32 [200/0] via 10.3.20.1, Ethernet3
```

### ping

#### ВСЕ УСТРОЙСТВА С LEAF1
```
leaf1#ping 172.16.10.1
PING 172.16.10.1 (172.16.10.1) 72(100) bytes of data.
80 bytes from 172.16.10.1: icmp_seq=1 ttl=64 time=9.61 ms
80 bytes from 172.16.10.1: icmp_seq=2 ttl=64 time=8.19 ms
80 bytes from 172.16.10.1: icmp_seq=3 ttl=64 time=7.75 ms
80 bytes from 172.16.10.1: icmp_seq=4 ttl=64 time=9.25 ms
80 bytes from 172.16.10.1: icmp_seq=5 ttl=64 time=11.8 ms

--- 172.16.10.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 43ms
rtt min/avg/max/mdev = 7.750/9.336/11.874/1.442 ms, ipg/ewma 10.810/9.558 ms
leaf1#ping 172.16.20.1
PING 172.16.20.1 (172.16.20.1) 72(100) bytes of data.
80 bytes from 172.16.20.1: icmp_seq=1 ttl=64 time=9.04 ms
80 bytes from 172.16.20.1: icmp_seq=2 ttl=64 time=11.3 ms
80 bytes from 172.16.20.1: icmp_seq=3 ttl=64 time=10.2 ms
80 bytes from 172.16.20.1: icmp_seq=4 ttl=64 time=10.3 ms
80 bytes from 172.16.20.1: icmp_seq=5 ttl=64 time=7.14 ms

--- 172.16.20.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 63ms
rtt min/avg/max/mdev = 7.145/9.616/11.318/1.436 ms, ipg/ewma 15.909/9.251 ms
leaf1#ping 172.16.0.2
PING 172.16.0.2 (172.16.0.2) 72(100) bytes of data.
80 bytes from 172.16.0.2: icmp_seq=1 ttl=63 time=15.9 ms
80 bytes from 172.16.0.2: icmp_seq=2 ttl=63 time=37.9 ms
80 bytes from 172.16.0.2: icmp_seq=3 ttl=63 time=32.8 ms
80 bytes from 172.16.0.2: icmp_seq=4 ttl=63 time=55.5 ms
80 bytes from 172.16.0.2: icmp_seq=5 ttl=63 time=36.8 ms

--- 172.16.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 82ms
rtt min/avg/max/mdev = 15.917/35.818/55.566/12.656 ms, pipe 3, ipg/ewma 20.729/26.331 ms
leaf1#ping 172.16.0.3
PING 172.16.0.3 (172.16.0.3) 72(100) bytes of data.
80 bytes from 172.16.0.3: icmp_seq=1 ttl=63 time=119 ms
80 bytes from 172.16.0.3: icmp_seq=2 ttl=63 time=114 ms
80 bytes from 172.16.0.3: icmp_seq=3 ttl=63 time=147 ms
80 bytes from 172.16.0.3: icmp_seq=4 ttl=63 time=146 ms
80 bytes from 172.16.0.3: icmp_seq=5 ttl=63 time=144 ms

--- 172.16.0.3 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 45ms
rtt min/avg/max/mdev = 114.323/134.556/147.657/14.458 ms, pipe 5, ipg/ewma 11.327/127.986 ms
```
