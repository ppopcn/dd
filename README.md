
 yum -y install nano wget perl gcc gcc-c++
 
 yum -y install psmisc net-tools systemd-devel libdb-devel 
 
 yum -y install perl-DBI xfsprogs rsyslog logrotate crontabs file

 firewall-cmd --zone=public --add-port=2222/tcp --permanent

 firewall-cmd --zone=public --add-port=21/tcp --permanent

 firewall-cmd --zone=public --add-port=80/tcp --permanent

 firewall-cmd --zone=public --add-port=25/tcp --permanent

 firewall-cmd --reload

 wget https://raw.githubusercontent.com/ppopcn/dd/master/setup.sh

 chmod +x setup.sh && ./setup.sh

 systemctl restart directadmin

 cd /usr/local/directadmin/conf/

 service directadmin stop

 rm -rf /usr/local/directadmin/conf/license.key

 wget -O /usr/local/directadmin/conf/license.key https://www.plesk.com.vn/license.key

 chmod 600 /usr/local/directadmin/conf/license.key

 chown diradmin:diradmin /usr/local/directadmin/conf/license.key

 ifconfig eth0:100 103.237.147.148 netmask 255.0.0.0 up

 echo 'DEVICE=eth0:100' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

 echo 'IPADDR=103.237.147.148' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

 echo 'NETMASK=255.0.0.0' >> /etc/sysconfig/network-scripts/ifcfg-eth0:100

 service network restart

 vi /usr/local/directadmin/conf/directadmin.conf

 service directadmin start
