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
service routing protocols model multi-agent
!
hostname leaf1
!
spanning-tree mode mstp
!
vlan 10,20
!
interface Ethernet1
   mtu 9000
   no switchport
   ip address 10.1.10.1/30
!
interface Ethernet2
   mtu 9000
   no switchport
   ip address 10.1.20.1/30
!
interface Ethernet3
   switchport access vlan 10
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
interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 10 vni 1010
!
ip routing
!
router bgp 65101
   router-id 172.16.0.1
   maximum-paths 4 ecmp 4
   neighbor 10.1.10.2 remote-as 65100
   neighbor 10.1.20.2 remote-as 65100
   neighbor 172.16.10.1 remote-as 65100
   neighbor 172.16.10.1 update-source Loopback0
   neighbor 172.16.10.1 ebgp-multihop 2
   neighbor 172.16.10.1 send-community extended
   neighbor 172.16.20.1 remote-as 65100
   neighbor 172.16.20.1 update-source Loopback0
   neighbor 172.16.20.1 ebgp-multihop 2
   neighbor 172.16.20.1 send-community extended
   !
   vlan 10
      rd 65000:10
      route-target both 65000:10
      redistribute learned
   !
   address-family evpn
      neighbor 172.16.10.1 activate
      neighbor 172.16.20.1 activate
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
service routing protocols model multi-agent
!
hostname leaf2
!
spanning-tree mode mstp
!
vlan 10,20
!
interface Ethernet1
   mtu 9000
   no switchport
   ip address 10.2.10.1/30
!
interface Ethernet2
   mtu 9000
   no switchport
   ip address 10.2.20.1/30
!
interface Ethernet3
   switchport access vlan 10
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
interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 10 vni 1010
!
ip routing
!
router bgp 65102
   router-id 172.16.0.2
   maximum-paths 4 ecmp 4
   neighbor 10.2.10.2 remote-as 65100
   neighbor 10.2.20.2 remote-as 65100
   neighbor 172.16.10.1 remote-as 65100
   neighbor 172.16.10.1 update-source Loopback0
   neighbor 172.16.10.1 ebgp-multihop 2
   neighbor 172.16.10.1 send-community extended
   neighbor 172.16.20.1 remote-as 65100
   neighbor 172.16.20.1 update-source Loopback0
   neighbor 172.16.20.1 ebgp-multihop 2
   neighbor 172.16.20.1 send-community extended
   !
   vlan 10
      rd 65000:10
      route-target both 65000:10
      redistribute learned
   !
   address-family evpn
      neighbor 172.16.10.1 activate
      neighbor 172.16.20.1 activate
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
service routing protocols model multi-agent
!
hostname leaf3
!
spanning-tree mode mstp
!
vlan 10,20
!
interface Ethernet1
   mtu 9000
   no switchport
   ip address 10.3.10.1/30
!
interface Ethernet2
   mtu 9000
   no switchport
   ip address 10.3.20.1/30
!
interface Ethernet3
   switchport access vlan 10
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
interface Vxlan1
   vxlan source-interface Loopback0
   vxlan udp-port 4789
   vxlan vlan 10 vni 1010
!
ip routing
!
router bgp 65103
   router-id 172.16.0.3
   maximum-paths 4 ecmp 4
   neighbor 10.3.10.2 remote-as 65100
   neighbor 10.3.20.2 remote-as 65100
   neighbor 172.16.10.1 remote-as 65100
   neighbor 172.16.10.1 update-source Loopback0
   neighbor 172.16.10.1 ebgp-multihop 2
   neighbor 172.16.10.1 send-community extended
   neighbor 172.16.20.1 remote-as 65100
   neighbor 172.16.20.1 update-source Loopback0
   neighbor 172.16.20.1 ebgp-multihop 2
   neighbor 172.16.20.1 send-community extended
   !
   vlan 10
      rd 65000:10
      route-target both 65000:10
      redistribute learned
   !
   address-family evpn
      neighbor 172.16.10.1 activate
      neighbor 172.16.20.1 activate
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
service routing protocols model multi-agent
!
hostname spine10
!
spanning-tree mode mstp
!
interface Ethernet1
   mtu 9000
   no switchport
   ip address 10.1.10.2/30
!
interface Ethernet2
   mtu 9000
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
   neighbor 172.16.0.1 remote-as 65101
   neighbor 172.16.0.1 update-source Loopback0
   neighbor 172.16.0.1 ebgp-multihop 2
   neighbor 172.16.0.1 send-community extended
   neighbor 172.16.0.2 remote-as 65102
   neighbor 172.16.0.2 update-source Loopback0
   neighbor 172.16.0.2 ebgp-multihop 2
   neighbor 172.16.0.2 send-community extended
   neighbor 172.16.0.3 remote-as 65103
   neighbor 172.16.0.3 update-source Loopback0
   neighbor 172.16.0.3 ebgp-multihop 2
   neighbor 172.16.0.3 send-community extended
   !
   address-family evpn
      neighbor 172.16.0.1 activate
      neighbor 172.16.0.2 activate
      neighbor 172.16.0.3 activate
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
service routing protocols model multi-agent
!
hostname spine20
!
spanning-tree mode mstp
!
interface Ethernet1
   mtu 9000
   no switchport
   ip address 10.1.20.2/30
!
interface Ethernet2
   mtu 9000
   no switchport
   ip address 10.2.20.2/30
!
interface Ethernet3
   mtu 9000
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
   neighbor 172.16.0.1 remote-as 65101
   neighbor 172.16.0.1 update-source Loopback0
   neighbor 172.16.0.1 ebgp-multihop 2
   neighbor 172.16.0.1 send-community extended
   neighbor 172.16.0.2 remote-as 65102
   neighbor 172.16.0.2 update-source Loopback0
   neighbor 172.16.0.2 ebgp-multihop 2
   neighbor 172.16.0.2 send-community extended
   neighbor 172.16.0.3 remote-as 65103
   neighbor 172.16.0.3 update-source Loopback0
   neighbor 172.16.0.3 ebgp-multihop 2
   neighbor 172.16.0.3 send-community extended
   !
   address-family evpn
      neighbor 172.16.0.1 activate
      neighbor 172.16.0.2 activate
      neighbor 172.16.0.3 activate
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

### show bgp evpn summary

#### LEAF1
```
  Neighbor    V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc
  172.16.10.1 4 65100            250       256    0    0 03:16:57 Estab   2      2
  172.16.20.1 4 65100             27        29    0    0 00:06:06 Estab   2      2
```
#### LEAF2
```
  Neighbor    V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc
  172.16.10.1 4 65100            255       255    0    0 03:17:27 Estab   2      2
  172.16.20.1 4 65100             27        30    0    0 00:06:45 Estab   2      2
```
#### LEAF3
```
 Neighbor    V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc
  172.16.10.1 4 65100             49        48    0    0 00:17:28 Estab   2      2
  172.16.20.1 4 65100             29        30    0    0 00:07:22 Estab   2      2
```
#### SPINE10
```
  Neighbor   V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc
  172.16.0.1 4 65101            258       252    0    0 03:18:43 Estab   1      1
  172.16.0.2 4 65102            256       256    0    0 03:18:33 Estab   1      1
  172.16.0.3 4 65103             43        45    0    0 00:17:55 Estab   1      1
```
#### SPINE20
```
  Neighbor   V AS           MsgRcvd   MsgSent  InQ OutQ  Up/Down State   PfxRcd PfxAcc
  172.16.0.1 4 65101             31        29    0    0 00:08:22 Estab   1      1
  172.16.0.2 4 65102             32        29    0    0 00:08:22 Estab   1      1
  172.16.0.3 4 65103             31        30    0    0 00:08:20 Estab   1      1
```

### show bgp evpn route-type mac-ip

#### LEAF1
```
       Network                Next Hop              Metric  LocPref Weight  Path
 * >      RD: 65000:10 mac-ip 0050.7966.680b
                                 -                     -       -       0       i
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680c
                                 172.16.0.2            -       100     0       65100 65102 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680c
                                 172.16.0.2            -       100     0       65100 65102 i
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680d
                                 172.16.0.3            -       100     0       65100 65103 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680d
                                 172.16.0.3            -       100     0       65100 65103 i
```
#### LEAF2
```
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680b
                                 172.16.0.1            -       100     0       65100 65101 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680b
                                 172.16.0.1            -       100     0       65100 65101 i
 * >      RD: 65000:10 mac-ip 0050.7966.680c
                                 -                     -       -       0       i
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680d
                                 172.16.0.3            -       100     0       65100 65103 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680d
                                 172.16.0.3            -       100     0       65100 65103 i
```
#### LEAF3
```
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680b
                                 172.16.0.1            -       100     0       65100 65101 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680b
                                 172.16.0.1            -       100     0       65100 65101 i
 * >Ec    RD: 65000:10 mac-ip 0050.7966.680c
                                 172.16.0.2            -       100     0       65100 65102 i
 *  ec    RD: 65000:10 mac-ip 0050.7966.680c
                                 172.16.0.2            -       100     0       65100 65102 i
 * >      RD: 65000:10 mac-ip 0050.7966.680d
                                 -                     -       -       0       i

```

### show vxlan vtep

#### LEAF1
```
VTEP             Tunnel Type(s)
---------------- --------------
172.16.0.2       flood
172.16.0.3       flood
```
#### LEAF2
```
VTEP             Tunnel Type(s)
---------------- --------------
172.16.0.1       flood
172.16.0.3       flood

```
#### LEAF3
```
VTEP             Tunnel Type(s)
---------------- --------------
172.16.0.1       flood
172.16.0.2       flood

```

### ping

#### ВСЕ УСТРОЙСТВА С VPC 192.168.1.1
```
VPCS> ping 192.168.1.2

84 bytes from 192.168.1.2 icmp_seq=1 ttl=64 time=175.835 ms
84 bytes from 192.168.1.2 icmp_seq=2 ttl=64 time=32.662 ms
84 bytes from 192.168.1.2 icmp_seq=3 ttl=64 time=48.917 ms
84 bytes from 192.168.1.2 icmp_seq=4 ttl=64 time=34.112 ms
84 bytes from 192.168.1.2 icmp_seq=5 ttl=64 time=37.875 ms

VPCS> ping 192.168.1.3

84 bytes from 192.168.1.3 icmp_seq=1 ttl=64 time=272.621 ms
84 bytes from 192.168.1.3 icmp_seq=2 ttl=64 time=39.057 ms
84 bytes from 192.168.1.3 icmp_seq=3 ttl=64 time=44.939 ms
84 bytes from 192.168.1.3 icmp_seq=4 ttl=64 time=42.484 ms
84 bytes from 192.168.1.3 icmp_seq=5 ttl=64 time=35.889 ms
```
