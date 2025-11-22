# CISCO-NETWORK
Repositório dedicado aos meus estudos com equipamentos de rede CISCO, basicamente redes montadas no packet tracer utilizando routers e switches CISCO

### A rede simula uma empresa, de maneira bem simplória na questão de equipamentos mas com uma certa complexidade na configuração da rede, ainda mais para alguém iniciante no assunto.
A rede consiste em setores separados por VLANs para garantir a segmentação e segurança de cada setor, também há uma impressora e um servidor de acesso comum.
O Server atende como file server, DNS server e DHCP server.
Temos APs destinados para a maioria das áreas, um laptop de teste conectado a um dos APs que é protegido por senha e cada AP destinado a uma área fica limitado ao acesso apenas daquela VLAN.
Por exemplo. WIFI Logistica só acessa a VLAN Logística, a ideia é a mesma do cabeamento.
Temos dois roteadores e dois links ISP para redundância, o servidor ainda não tem redundância de conexão com os outros switches para garantir que caso o SW1 caia, o restante não ficaria sem acesso tanto à
impressora compartilhada quanto ao servidor.

<img width="1159" height="696" alt="image" src="https://github.com/user-attachments/assets/648bc972-ed14-4410-8487-696b263b0e6a" />
