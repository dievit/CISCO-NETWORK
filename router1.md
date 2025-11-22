
# Router Configuration

## Versão
---

## DHCP Pools
```bash
ip dhcp excluded-address 192.168.10.1 192.168.10.10

ip dhcp pool VLAN10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8

ip dhcp pool VLAN20
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.254
 dns-server 8.8.8.8

ip dhcp pool VLAN30
 network 192.168.30.0 255.255.255.0
 default-router 192.168.30.254
 dns-server 8.8.8.8

ip dhcp pool VLAN40
 network 192.168.40.0 255.255.255.0
 default-router 192.168.40.254
 dns-server 8.8.8.8

ip dhcp pool VLAN50
 network 192.168.50.0 255.255.255.0
 default-router 192.168.50.254
 dns-server 8.8.8.8

ip dhcp pool VLAN60
 network 192.168.60.0 255.255.255.0
 default-router 192.168.60.254
 dns-server 8.8.8.8

ip dhcp pool VLAN70
 network 192.168.70.0 255.255.255.0
 dns-server 8.8.8.8

ip dhcp pool VLAN80
 network 192.168.80.0 255.255.255.0
 dns-server 8.8.8.8

ip dhcp pool VLAN99
 network 192.168.99.0 255.255.255.0
 dns-server 8.8.8.8
```

## INTERFACES

```bash
interface GigabitEthernet0/0
 no ip address
 ip nat inside
 duplex auto
 speed auto

interface GigabitEthernet0/0.1
 encapsulation dot1Q 1 native
 ip address 192.168.1.1 255.255.255.0

interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0

interface GigabitEthernet0/0.40
 encapsulation dot1Q 40
 ip address 192.168.40.1 255.255.255.0

interface GigabitEthernet0/0.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.0

interface GigabitEthernet0/0.60
 encapsulation dot1Q 60
 ip address 192.168.60.1 255.255.255.0

interface GigabitEthernet0/0.70
 encapsulation dot1Q 70
 ip address 192.168.70.1 255.255.255.0

interface GigabitEthernet0/0.80
 encapsulation dot1Q 80
 ip address 192.168.80.1 255.255.255.0

interface GigabitEthernet0/0.98
 encapsulation dot1Q 98
 ip address 192.168.98.254 255.255.255.0
 ip helper-address 192.168.99.1
 standby 98 ip 192.168.98.1
 standby 98 priority 110
 standby 98 preempt

interface GigabitEthernet0/0.99
 encapsulation dot1Q 99
 ip address 192.168.99.1 255.255.255.0

interface GigabitEthernet0/1
 ip address 200.0.0.1 255.255.255.252
 ip nat outside
 duplex auto
 speed auto
```
## NAT e ACL
```bash

ip nat inside source list 1 interface GigabitEthernet0/1 overload
access-list 1 permit 192.168.1.0 0.0.0.255
```


