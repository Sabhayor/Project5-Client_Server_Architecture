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
`sudo systemctl status mysql`

3. On mysql client Linux Server install MySQL Client software.  
![Install MySQL Client](/images/mysql-client-install.jpg)

4. By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ – allow access only to the specific local IP address of your ‘mysql client’.  
![Network Security](/images/network_security.jpg)  

5. For MySQL secure installation use the following,  
`sudo mysql_secure_installation`  
6. Launch mysql server and create user and database
    `sudo mysql`
    ![mysql launch](/images/mysql-launch.jpg)
    Create user:  
    `CREATE USER 'remote_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`  
    Create database:  
    `CREATE DATABASE test_db;`  
    Grant all priviledges:  
    `GRANT ALL ON test_db. * TO 'remote_user'@'%' WITH GRANT OPTION;`  
    Flush priviledges:  
    `FLUSH PRIVILEGES;`
    ![mysql launch](/images/create_user_and_database.jpg)

7. Exit MySQL and restart the mySQL service using  
    `sudo systemctl restart mysql`  
8. Configure MySQL server to allow connections from remote  hosts.  
    `sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`
     ![Binding Address](/images/binding-address.jpg)
9. From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH. You must use the mysql utility to perform this action.  
Check that you have successfully connected to a remote MySQL server and can perform SQL queries:  
`sudo mysql -u remote_user -h 172.31.94.11`
![Connecting to DB](/images/connect_to_db.jpg)

Show database  
![Show DB](/images/Show_DB.jpg)  

If you see an output similar to the below image, then you have successfully completed this project – you have deloyed a fully functional MySQL Client-Server set up.

Thank You!!
















