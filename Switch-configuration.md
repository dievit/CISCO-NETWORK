## VLANs

```bash
Switch1#sh vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    
10   Office                           active    Fa0/2, Fa0/3, Fa0/4, Fa0/5
20   Production                       active    
30   Finance                          active    Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17
40   Quality                          active    
50   Human-Resources                  active    
60   Maintenance                      active    Fa0/10, Fa0/11, Fa0/12
70   Sales                            active    Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24
80   Logistics                        active    Fa0/6, Fa0/7, Fa0/8, Fa0/9
98   IoT-1                            active    
99   Shared-Resources                 active    Fa0/1
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

## PORTS SW1
```bash
Switch1#sh int status
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1                        connected    99         a-full  a-100 10/100BaseTX
Fa0/2                        connected    10         a-full  a-100 10/100BaseTX
Fa0/3                        connected    10         a-full  a-100 10/100BaseTX
Fa0/4                        connected    10         a-full  a-100 10/100BaseTX
Fa0/5                        connected    10         a-full  a-100 10/100BaseTX
Fa0/6                        connected    80         a-full  a-100 10/100BaseTX
Fa0/7                        connected    80         a-full  a-100 10/100BaseTX
Fa0/8                        connected    80         a-full  a-100 10/100BaseTX
Fa0/9                        connected    80         a-full  a-100 10/100BaseTX
Fa0/10                       connected    60         a-full  a-100 10/100BaseTX
Fa0/11                       connected    60         a-full  a-100 10/100BaseTX
Fa0/12                       connected    60         a-full  a-100 10/100BaseTX
Fa0/13                       connected    30         a-full  a-100 10/100BaseTX
Fa0/14                       connected    30         a-full  a-100 10/100BaseTX
Fa0/15                       connected    30         a-full  a-100 10/100BaseTX
Fa0/16                       connected    30         a-full  a-100 10/100BaseTX
Fa0/17                       connected    30         a-full  a-100 10/100BaseTX
Fa0/18                       connected    70         a-full  a-100 10/100BaseTX
Fa0/19                       connected    70         a-full  a-100 10/100BaseTX
Fa0/20                       connected    70         a-full  a-100 10/100BaseTX
Fa0/21                       connected    70         a-full  a-100 10/100BaseTX
Fa0/22                       connected    70         a-full  a-100 10/100BaseTX
Fa0/23                       connected    70         a-full  a-100 10/100BaseTX
Fa0/24                       connected    70         a-full  a-100 10/100BaseTX
Gig0/1                       connected    trunk      a-full  a-100 10/100/1000BaseTX
Gig0/2                       connected    trunk      a-full  a-100 10/100/1000BaseTX
```

## PORTS SW2
```bash
Switch2#sh int status
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1                        connected    20         a-full  a-100 10/100BaseTX
Fa0/2                        connected    20         a-full  a-100 10/100BaseTX
Fa0/3                        connected    20         a-full  a-100 10/100BaseTX
Fa0/4                        connected    20         a-full  a-100 10/100BaseTX
Fa0/5                        connected    20         a-full  a-100 10/100BaseTX
Fa0/6                        connected    20         a-full  a-100 10/100BaseTX
Fa0/7                        connected    20         a-full  a-100 10/100BaseTX
Fa0/8                        connected    20         a-full  a-100 10/100BaseTX
Fa0/9                        connected    20         a-full  a-100 10/100BaseTX
Fa0/10                       connected    20         a-full  a-100 10/100BaseTX
Fa0/11                       connected    50         a-full  a-100 10/100BaseTX
Fa0/12                       connected    50         a-full  a-100 10/100BaseTX
Fa0/13                       connected    50         a-full  a-100 10/100BaseTX
Fa0/14                       connected    50         a-full  a-100 10/100BaseTX
Fa0/15                       connected    50         a-full  a-100 10/100BaseTX
Fa0/16                       connected    50         a-full  a-100 10/100BaseTX
Fa0/17                       connected    40         a-full  a-100 10/100BaseTX
Fa0/18                       connected    40         a-full  a-100 10/100BaseTX
Fa0/19                       connected    40         a-full  a-100 10/100BaseTX
Fa0/20                       connected    40         a-full  a-100 10/100BaseTX
Fa0/21                       notconnect   1          auto    auto  10/100BaseTX
Fa0/22                       notconnect   1          auto    auto  10/100BaseTX
Fa0/23                       notconnect   1          auto    auto  10/100BaseTX
Fa0/24                       connected    trunk      a-full  a-100 10/100BaseTX
Gig0/1                       connected    trunk      a-full  a-100 10/100/1000BaseTX
Gig0/2                       connected    trunk      a-full  a-100 10/100/1000BaseTX
```

## PORTS SW3
```bash
Switch3#sh int status
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1                        connected    trunk      a-full  a-100 10/100BaseTX
Fa0/2                        connected    20         a-full  a-100 10/100BaseTX
Fa0/3                        connected    20         a-full  a-100 10/100BaseTX
Fa0/4                        connected    20         a-full  a-100 10/100BaseTX
Fa0/5                        connected    10         a-full  a-100 10/100BaseTX
Fa0/6                        connected    50         a-full  a-100 10/100BaseTX
Fa0/7                        connected    80         a-full  a-100 10/100BaseTX
Fa0/8                        connected    80         a-full  a-100 10/100BaseTX
Fa0/9                        connected    40         a-full  a-100 10/100BaseTX
Fa0/10                       connected    70         a-full  a-100 10/100BaseTX
Fa0/11                       notconnect   1          auto    auto  10/100BaseTX
Fa0/12                       notconnect   1          auto    auto  10/100BaseTX
Fa0/13                       notconnect   1          auto    auto  10/100BaseTX
Fa0/14                       notconnect   1          auto    auto  10/100BaseTX
Fa0/15                       notconnect   1          auto    auto  10/100BaseTX
Fa0/16                       notconnect   1          auto    auto  10/100BaseTX
Fa0/17                       notconnect   1          auto    auto  10/100BaseTX
Fa0/18                       notconnect   1          auto    auto  10/100BaseTX
Fa0/19                       notconnect   1          auto    auto  10/100BaseTX
Fa0/20                       notconnect   1          auto    auto  10/100BaseTX
Fa0/21                       notconnect   1          auto    auto  10/100BaseTX
Fa0/22                       notconnect   1          auto    auto  10/100BaseTX
Fa0/23                       notconnect   1          auto    auto  10/100BaseTX
Fa0/24                       notconnect   1          auto    auto  10/100BaseTX
Gig0/1                       notconnect   1          auto    auto  10/100/1000BaseTX
Gig0/2                       notconnect   1          auto    auto  10/100/1000BaseTX

```
