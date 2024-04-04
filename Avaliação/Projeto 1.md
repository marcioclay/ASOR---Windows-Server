# ASOR 

### Passos para as tarefas do servidor:
1.	Preparando servidor:
•	Preparar a máquina virtual que será servidor, instalar o Windows 2016 standard, 64 bits, geração 1 (com suporte a máquinas 32 bits), 2 placas de redes (1ª rede interna e 2ª rede nat), memória RAM e HD de tamanho padrão.
•	Toda a formatação e preparação estão nos vídeos 1, 2, 3, 4 e 5.
•	Seu servidor deve ter o nome de ZEUS e o número do seu micro. Ex. Micro 01 ZEUS01. 
•	A placa rede interna de seu servidor terá o IP com o número de seu micro: 
•	EX. Micro 12 = IP 192.168.12.1 será de classe C (ou seja, terá máscara 255.255.255.0), o DNS e o gateway também terão este mesmo IP do servidor.
•	A rede quando não tem IP definido fica com um IP genérico iniciado por 169... esta deve ser a rede interna, mude o nome da conexão para poder identificar quem é rede interna e quem é rede NAT (rede externa, rede de internet, etc).
•	Não será necessário crack para ativar o servidor. Vocês já fizeram download de ISO que tem licença de 180 dias. Não esqueça como foi no vídeo 1.

2.	Preparando Clientes:
•	Serão instalados 2 clientes todos eles com placa de rede interna: 

•	1 cliente Windows 7 Professional com configuração padrão de memória e disco. 

Lembre-se de sempre fazer backup do servidor!!!

3.	Atualização do Servidor:
•	Fazer a atualização do servidor para que possamos fazer os outros serviços do servidor rodar perfeitamente.

5.	Tradução do Servidor para português pt-br:
•	Fazer a tradução.


![image](https://github.com/marcioclay/ASOR---Windows-Server/assets/48799029/501c7201-3ed9-4d8e-ae8d-bf176cec6d8e)





7.	Servidor DHCP(Placa de Rede Interna).
•	Instalar o servidor DHCP a placa de rede já deve ter o IP do conforme o seu micro: EX. Micro 12 = IP 192.168.12.1.
•	O range de IP de seu DHCP deve ser de 50 até 60.
•	Dentro deste range de IP você deve fazer DHCP reserva para 2 impressoras.
•	Use para IP do DNS o IP do servidor, o gateway deve estar em branco.
•	Para testar se o DHCP foi instalado com sucesso utilize o ipconfig no cliente, verifique se DHCP esta ativado e IP DHCP. Não esqueça de desabilitar o firewall durante as aulas, em produção (profissionalmente) desabilite apenas durante os testes que for fazer e volte com o firewall.






8.	Servidor DNS. 
•	O servidor DNS deve ser configurado para que se possa resolver nomes, tanto a zona de pesquisa direta quanto a zona de pesquisa inversa.
•	Testar se está funcionando, vá ao cliente faça ping para o servidor e depois digite o comando nslookup. Ex.:nslookup “IP” e nslookup “nome do servidor ou cliente”                              
•	Depois de instalado o AD você deve voltar aqui para verificar se tudo está ok, então este item é informativo.
Lembre-se de sempre fazer backup do servidor!!!
9.	Servidor de AD.
•	Instalar o servidor de AD, ao colocar o nome no domínio lembrar que o nome colocado para o DNS deve ser igual ao nome do domínio.
•	Instalar o DNS junto com o AD, lembre-se do nome do domínio.
•	Promover o AD como controlador de domínio.
•	Coloque o nome do seu servidor zeusXX.srv.com

10.	Servidor de AD.
•	Colocar os clientes (computadores) no domínio.
•	Seus clientes terão os seguintes nomes:
o	cliente1
o	cliente2

	Para colocar os clientes no domínio devemos observar as configurações abaixo:
	O DHCP deve estar funcionando.
	Quando é instalado um AD o DHCP pode parar de funcionar você deve ir até o DHCP para autorizar ele no domínio CASO ISSO ACONTEÇA.
	Verificar o DNS, não se esqueça de fazer a configuração caso necessário. Na checagem você pode notar a necessidade da configuração de zona ou ptr. Ficar atento para não ter erro.
	Para checar verifique com ping com o nome do domínio e com nslookup.
	O próximo passo é colocar os clientes no domínio. Para isso devem ser feitos os seguintes testes:
	Ipconfig /all 
	Verifica se o IP está atribuído e se há o IP do servidor de DNS, estando ok passamos para o próximo passo, e não estando ok temos que voltar para verificar se o DHCP está ok. Não é necessário configurar IP no cliente digitando o IP, se há servidor de DHCP todas as opções de IP devem estar no automático.
	Ipconfig /release - Com este comando você libera o IP que seu cliente tiver. Lembrando que deve estar no automático, caso esteja digitado um IP nas propriedades de IPv4 não vai funcionar o comando e você deve corrigir para que funcione.
	Ipconfig /renew - Com este comando você renova o IP do cliente e assim você volta ao Ipconfig /all verificando IP do cliente e IP do servidor de DNS que deve ser o mesmo do seu servidor.
	nslookup
	Com este comando você verifica se o servidor de DNS está resolvendo corretamente os nomes, deve aparecer o nome do servidor e o IP do servidor em que está instalado o DNS.
	A partir deste ponto deve-se colocar o cliente no domínio, tendo como usuário o administrador e a senha do servidor.
	Assim que o cliente estiver no domínio faça login com um dos usuários criados no AD.
Lembre-se de sempre fazer backup do servidor!!!
1.	Usuários e OU.
•	Criar uma OU chamada Olimpo.
•	Criar 8 usuários. (escolha os nomes e senhas a vontade)
•	Preencher os dados (mesmo que fictícios) dos usuários.
•	Todas suas tarefas devem ser feitas nesta OU criada.

1.	Criar grupos no AD.
•	Criar 3 grupos, sendo: pturno, sturno, adm.
•	Colocar 2 usuários definidos anteriormente no grupo adm.
•	Colocar 3 usuários no grupo pturno.
•	Colocar 3 usuários no grupo sturno.
•	Abrir o usuário administrador e verificar quais os grupos que ele está e colocar o grupo adm nos mesmos grupos.

2.	Fazer restrição de horário de logon.
•	Dos 8 usuários criados 2 você deve escolher como administradores 
•	Os usuários administradores não tem restrição de logon.
•	3 usuários farão uso do computador de 00hs até as 14hs todos os dias úteis (sábado e domingo não).
•	3 usuários farão uso do computador de 14hs até as 00hs todos os dias úteis (sábado e domingo não).

3.	Fazer restrição de micro cliente que o usuário pode fazer logon.
•	Os usuários que foram escolhidos como administradores não têm restrição de logon.
•	3 usuários farão logon no cliente1.
•	3 usuários farão logon no cliente2.

4.	NIC Teaming   Agrupamento de Placas de REDE.
•	Adicionar ao seu servidor mais duas placas de rede internas (NÃO coloque bridge ou nat).
•	Fazer um NIC Teaming com as 3 placas de redes internas (a que já existia e as duas acrescentadas).
•	Coloque o nome do Teaming de HERMES.
•	Configurar o NIC Teaming com o IP do servidor.
•	Checar o DHCP, AD e DNS.
Lembre-se de sempre fazer backup do servidor!!! 	
Avaliação do Projeto até aqui. Valor= 30 pontos.

