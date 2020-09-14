#on web01:
sudo firewall-cmd --zone=public --permanent --add-port=80/tcp
sudo firewall-cmd --zone=public --permanent --add-port=22/tcp
yum install -y httpd
yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
systemctl restart sshd
systemctl restart httpd


#On Both VyOs systems:
configure
set nat source rule 10 description “NAT FROM DMZ to WAN”
set nat source rule 10 outbound-interface eth0
set nat source rule 10 source address 10.0.5.0/24
set nat source rule 10 translation address masquerade
commit
save(edited)
set service dns forwarding listen-address 10.0.5.1
set service dns forwarding allow from 10.0.5.0/24
commit
save
set nat destination rule 10 destination port 80
set nat destination rule 10 inbound-interface eth0
set nat destination rule 10 protocol tcp
set nat destination rule 10 translation address 10.0.5.100
commit
save
set service dns forwarding listen-address 10.0.17.76
set service dns forwarding allow from 10.0.17.0/24
set nat destination rule 15 destination port 22
set nat destination rule 15 inbound-interface eth0
set nat destination rule 15 protocol tcp
set nat destination rule 15 translation address 10.0.5.100
commit
save
</body>
</html>