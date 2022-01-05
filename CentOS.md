# CentOS

## Step 1: Configuring firewall rules

`sudo firewall-cmd --add-service={http,https} --permanent`  
`sudo firewall-cmd --add-port={8088/tcp,7080/tcp} --permanent`  
`sudo firewall-cmd --reload`  

## Step 2: Install OpenLiteSpeed Web Server and PHP

`sudo rpm -Uvh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el8.noarch.rpm`  
`sudo dnf install epel-release`  
`sudo dnf update`  
`sudo dnf install openlitespeed lsphp74`  

#### Create softlink for PHP

`sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5`  

## Step 3: Setting admin password

`sudo /usr/local/lsws/admin/misc/admpass.sh` 

## Step 4: Install MySQL Database Server

`sudo apt-get install mysql-client mysql-server`

##### Optional: Install MariaDB

`sudo apt-get install mariadb-server mariadb-client`

##### Optional: (Recommended) Run a security script to remove insecure default settings and protect the database system.

`sudo mysql_secure_installation`

###### Firstly, you will be asked to install the ‘validate_password’ plugin, so type in Y/Yes and press Enter and also choose the default password strength level.

![alt text](https://github.com/chathu5002/WP_OpenLiteSpeed/Images/Set-MySQL-Root-Password.png?raw=true)

###### For the remaining questions, press Y and hit the ENTER key at each prompt.
