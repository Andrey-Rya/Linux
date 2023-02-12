**Урок 5. Настройка сети в Linux. Работа с IPtables**

*Задание:*
**1. Настроить статическую конфигурацию (без DHCP) в Ubuntu через ip и netplan. 
   Настроить IP, маршрут по умолчанию и DNS-сервера (1.1.1.1 и 8.8.8.8). Проверить работоспособность сети.**
   
   root@LINUX-VIRTUAL:/etc/netplan# sudo su

	ip link set enp0s3 up
	
	ip addr add 192.168.0.171/255.255.255.0 dev enp0s3
	
	ip route add default via 192.168.0.1
	
	/home/vboxuser# ping ya.ru


**2. Настроить правила iptables для доступности сервисов на TCP-портах 22, 80 и 443. 
   Также сервер должен иметь возможность устанавливать подключения к серверу обновлений. Остальные подключения запретить.**

	iptables -A INPUT -p tcp --dport=22 -j ACCEPT
	
	iptables -A INPUT -p tcp --dport=80 -j ACCEPT
	
	iptables -A INPUT -p tcp --dport=443 -j ACCEPT
	
	iptables -t filter -A INPUT -s ubuntu.com -j ACCEPT
	
	iptables -P INPUT DROP

**3. Запретить любой входящий трафик с IP 3.4.5.6.**

	iptables -t filter -A INPUT -s 3.4.5.6 -j DROP
	
	mkdir /etc/iptables-conf/
	
	iptables-save -f /etc/iptables-conf/iptables_rules.ipv4
  
