## CLIENT-SERVER ARCHITECTURE WITH MYSQL
### TASK – Implement a Client Server Architecture using MySQL Database Management System (DBMS).
![Client-Server Architecture](/images/client-server-architecture.jpg)

1. Create and configure two Linux-based virtual servers (EC2 instances in AWS).  
Server A name - `mysql server`  
Server B name - `mysql client`  
![Client-Server Instances](/images/two_virtual_servers.jpg)

2. On mysql server Linux Server install MySQL Server software.  
Update ubuntu - `sudo apt update`  
Upgrade ubuntu - `sudo apt upgrade`  
`sudo apt install mysql-server`
![Install MySQL Server](/images/mysql-server-install.jpg)

Make sure to enable the MySQL.service after installing  
`sudo systemctl enable mysql`

3. On mysql client Linux Server install MySQL Client software.  
![Install MySQL Client](/images/mysql-client-install.jpg)

4. By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ – allow access only to the specific local IP address of your ‘mysql client’.  
![Network Security](/images/network_security.jpg)  

5. For MySQL secure installation use the following,  
`sudo mysql_secure_installation`  














Create and configure two Linux-based virtual servers (EC2 instances in AWS).

On mysql server Linux Server install MySQL Server software.

On mysql client Linux Server install MySQL Client software.

Create a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups, MySQL server uses TCP port 3306 by default.

You might need to configure MySQL server to allow connections from remote hosts.
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf

Replace ‘127.0.0.1’ to ‘0.0.0.0’ like this:

From mysql client Linux Server connect remotely to mysql server Database
Check that you have successfully connected to a remote MySQL server and can perform SQL queries
Show databases;


