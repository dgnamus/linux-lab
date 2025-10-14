The task was to install the iptables and it's dependencies, and ensure that only our server with ip 172.16.238.14 is able to access the port 3004 on the host. The below were commands to solve this: 

sudo su -
yum install iptables-services
systemctl start iptables && systemctl enable iptables
iptables -A INPUT -p tcp --destination-port 3004 -s 172.16.238.14 -j ACCEPT
iptables -A INPUT -p tcp --destination-port 3004 -j DROP
iptables -L --line-numbers
iptables -R INPUT 5 -p icmp -j REJECT
service iptables save 
systemctl restart iptables && systemctl status iptables

NOTES
-------------------------------------------
It's much easier in this case to do everything as root, because otherwise you need sudo for everything. 

ICMP stands for Internet Control Message Protocol. It's not for sending user messages, but for devices to communicate about network conditions (like pinging). In that line, we blocked the ability for soemone to ping the server, they would get "Destination host unreachable".

We need to save iptables configuration for it to persist after system being restarted. 
