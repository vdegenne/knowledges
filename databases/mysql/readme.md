# MySql

## fedora 25

# mysql -u root -p

> create database dbname;
> use mysql; (use the administration database)
> select host, user from user where user='username'; (to check information)
> create user 'username'@'1.2.3.4' IDENTIFIED BY 'password'; (the ip is the ip of the client that wants to connect on the database of the server you configuring right now)
> grant all on dbname.* to 'username'@'1.2.3.4';


firewall-cmd --permanent --zone=public --add-port=3306/tcp
systemctl restart firewalld

emacs /etc/sysconfig/iptables
-A INPUT -m state --state NEW -m tcp -p tcp --dport 3306 -j ACCEPT

systemctl restart iptables
