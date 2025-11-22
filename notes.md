configurar vlan

conf t
vlan XX
name [nome]

no roteador
entrar na int Gi0/0

✅ Manual de Configuração da Rede com DHCP Centralizado

1. Configuração dos Switches
Switch1
Shellenableconfigure terminal! Criar VLANs
vlan 10 
name Office
vlan 20 
name Production
vlan 30 
name Finance
vlan 40 
name Quality
vlan 50 
name Human-Resource
vlan 60 
name Maintenance
vlan 70 
name Salesv
lan 80 
name Logistics
vlan 99 
name Shared-Resources

Configurar porta do servidor na VLAN99interface fa0/1
switchport mode access switchport access vlan 99

Configurar trunks para roteador e Switch2interface gi0/1
switchport mode trunk 
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,99
interface gi0/2 switchport mode trunk 
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,99
end
write memory


Switch2
Shellenableconfigure terminal! Criar VLANs (mesmas do Switch1)

vlan 10 
name Officevlan 20 
name Production
vlan 30 name Financevlan 40 
name Quality
vlan 50 
name Human-Resource
vlan 60 
name Maintenance
vlan 70 
name Sales
vlan 80 
name Logistics
vlan 99 
name Shared-Resources 

Configurar portas dos PCs na VLAN20 (exemplo)
interface range fa0/1 - 10 switchport mode access switchport access vlan 20

Configurar trunk para Switch1
interface gi0/2 
switchport mode trunk 
switchport trunk allowed vlan 10,20,30,40,50,60,70,80,99
end
write memory

2. Configuração do Roteador
Subinterfaces para VLANs
Shell
enable
configure terminal
interface g0/0 
no shutdown
VLAN10

interface g0/0.10 
encapsulation dot1Q 10 
ip address 192.168.10.254 255.255.255.0 
ip helper-address 192.168.99.1
VLAN20
interface g0/0.20 
encapsulation dot1Q 20 
ip address 192.168.20.254 255.255.255.0 
ip helper-address 192.168.99.1
VLAN30
interface g0/0.30 
encapsulation dot1Q 30 
ip address 192.168.30.254 255.255.255.0 
ip helper-address 192.168.99.1
VLAN40
interface g0/0.40 
encapsulation dot1Q 40 
ip address 192.168.40.254 255.255.255.0 
ip helper-address 192.168.99.1
VLAN99
 (sem helper, pois servidor está nela)
 interface g0/0.99 
 encapsulation dot1Q 99 
 ip address 192.168.99.254 255.255.255.0
 end
 write memory

Interface para Cloud (ISP)
Shellinterface g0/1 
ip address 200.200.200.2 255.255.255.252 
no shutdown

3. Configuração do Servidor DHCP

IP estático:
IP: 192.168.99.1
Máscara: 255.255.255.0
Gateway: 192.168.99.254
DNS: 8.8.8.8


Pools DHCP:

VLAN10 → Network: 192.168.10.0 / Gateway: 192.168.10.254
VLAN20 → Network: 192.168.20.0 / Gateway: 192.168.20.254
(Repita para todas as VLANs)




✅ Checklist Final
✔ VLANs criadas nos switches.
✔ Portas dos PCs atribuídas às VLANs corretas.
✔ Trunks configurados e VLANs permitidas.
✔ Subinterfaces no roteador com ip helper-address.
✔ Servidor DHCP com IP estático e pools corretos.
✔ PCs configurados para DHCP.


✅ Para apagar uma VLAN
Shellenableconfigure terminalno vlan <ID>endwrite memoryShow more lines
Exemplo:
Shellno vlan 30Show more lines
Isso remove a VLAN 30 da tabela do switch.

✅ Para editar o nome da VLAN
Shellenableconfigure terminalvlan <ID> name <NovoNome>endwrite memoryShow more lines
Exemplo:
Shellvlan 20 name ProduçãoShow more lines

⚠ Importante:

Se você apagar uma VLAN, todas as portas associadas voltam para VLAN 1 (default).
Não é possível mudar o número da VLAN (ID). Se quiser outro número, você precisa criar uma nova VLAN e mover as portas para ela.


✅ Como configurar HSRP no roteador
Suponha que você tenha dois roteadores conectados à mesma VLAN (ex.: VLAN10) e quer usar HSRP:
Roteador 1
interface g0/0.10 
encapsulation dot1Q 10 
ip address 192.168.10.2 255.255.255.0 
ip helper-address 192.168.99.1
standby 10 ip 192.168.10.254 
standby 10 priority 110 
standby 10 preempt

Roteador 2
Shellinterface g0/0.10 
encapsulation dot1Q 10 
ip address 192.168.10.3 255.255.255.0 
ip helper-address 192.168.99.1 <- neste caso porque é o ip do meu servidor dhcp
standby 10 ip 192.168.10.254 
standby 10 priority 100 
standby 10 preempt

✅ Explicação:

standby 10 ip 192.168.10.254 → IP virtual usado como gateway pelos PCs.
priority → define quem é o ativo (maior prioridade = ativo).
preempt → permite que o roteador reassuma se voltar a ficar disponível.

⚠Problemas:


HSRP está errado:
O IP virtual do HSRP não pode ser igual ao IP da subinterface.
Você usou standby 98 ip 192.168.98.254, que é o mesmo IP da interface.
O IP virtual deve ser diferente, por exemplo:

standby 98 ip 192.168.98.1
