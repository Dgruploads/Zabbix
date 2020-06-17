Step 1 : Update the machine
   sudo apt-get update -y

Step 2 : Install apache server and php
    sudo apt-get install apache2 libapache2-mod-php -y

Step 3 : Install mysql server
    sudo apt-get install mysql-server -y

Step 4 : Install php modules
    sudo apt-get install php php-mbstring php-gd php-xml php-bcmath php-ldap php-mysql -y

Step 5 : Download the zabbix repositories
    wget https://repo.zabbix.com/zabbix/5.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.0-1+bionic_all.deb

Step 6 : Run the Zabbix repositories
    sudo dpkg -i zabbix-release_5.0-1+bionic_all.deb

Step 7 : Update the machine.
    sudo apt update -y 

Step 8 : Install Zabbix server, agent and the required modules.
    sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent -y

Step 9 : Connect to the database
    sudo mysql --defaults-file=/etc/mysql/debian.cnf

Step 10 : Create a database "zabbix"
    create database zabbix character set utf8 collate utf8_bin;

Step 11 : Create a DB user "zabbix"
    create user zabbix@localhost identified by 'zabbix';

Step 12 : Grant permissions to the user "zabbix"
    grant all privileges on zabbix.* to zabbix@localhost;

Step 13 : Exit from the DB
    quit;
  
Step 14 : Copy the schema to the DB  
    sudo zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix

Step 15 : Setup the DB password in the server configuration file
    sudo vi /etc/zabbix/zabbix_server.conf ---- Set the "DBPassword=zabbix"

Step 16 : Setup the time zone in the apache configuration file
    sudo vi /etc/zabbix/apache.conf ---- Set php_value date.timezone "Asia/Kolkata"
    
Step 17 : Restart the server and the agent
    sudo systemctl restart zabbix-server zabbix-agent apache2

Step 18 : Enable the server and the agent
    sudo systemctl enable zabbix-server zabbix-agent apache2

Step 19 : Allow the rules if you are using Cloud (in my case AWS).
    Edit the security group and add 10050 and 10051 rules

Step 20 : Access the application using the IP address
    Access the app ---ip-address/zabbix
